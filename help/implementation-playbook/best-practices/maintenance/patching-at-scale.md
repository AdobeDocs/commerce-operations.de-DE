---
title: Best Practices für die Verteilung von Patches in großem Maßstab
description: Erfahren Sie, wie Sie durch zentrales Patchen für Adobe Commerce Unternehmensprojekte verwalten können.
role: Developer
feature: Best Practices
badge: label="Mitwirkende von Anton Evers, Sr. Technischer Architekt, Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Beitragt von Anton Evers"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Best Practices für die skalierte Verteilung von Adobe Commerce-Patches

Wenn Sie mehrere Adobe Commerce-Installationen verwalten, kann [Patchen](../../../upgrade/patches/apply.md) ein komplexer Prozess sein. _Zentralisiertes Patchen_ ist eine Best Practice für Unternehmen. Dies hilft Ihnen, die richtigen Patches auf alle Ihre Adobe Commerce-Installationen anzuwenden. In diesem Thema wird erläutert, wie Sie eine zentralisierte Patch-Verteilung für alle Typen von Adobe Commerce [Patches](../../../upgrade/patches/overview.md) erreichen.

>[!NOTE]
>
>Der folgende Inhalt wurde ursprünglich im Beitrag [Verteilen von Adobe Commerce-Patches auf Skala](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) im Adobe Tech Blog veröffentlicht. Es wurde geändert, um sich auf die Schritte und Codebeispiele zur Implementierung einer zentralisierten Patchingstrategie zu konzentrieren. Weitere Informationen zu den verschiedenen Arten von Patches, die hier beschrieben werden, finden Sie im ursprünglichen Beitrag .

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Strategie

Da es viele verschiedene Arten von Patches gibt und viele Möglichkeiten, sie anzuwenden, wie wissen Sie, welcher Patch zuerst angewendet wird? Je mehr Patches Sie haben, desto größer ist die Wahrscheinlichkeit, dass sie auf dieselbe Datei oder auf dieselbe Codezeile angewendet werden. Patches werden in der folgenden Reihenfolge angewendet:

1. **Sicherheits-Patches** sind Teil der statischen Codebasis einer Adobe Commerce-Version.
1. **Der Composer patcht** durch `composer install` und `composer update` Plug-ins wie [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. Alle **erforderlichen Patches**, die im Paket [Cloud-Patches für Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) enthalten sind.
1. Ausgewählte **Qualitäts-Patches**, die im [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md) enthalten sind.
1. **Benutzerdefinierte Patches** und Adobe Commerce-Support-Patches im Verzeichnis `/m2-hotfixes` in alphabetischer Reihenfolge nach Patch-Name.

   >[!IMPORTANT]
   >
   >Je mehr Patches Sie anwenden, desto komplexer wird Ihr Code. Komplexer Code kann die Aktualisierung auf eine neue Adobe Commerce-Version erschweren und Ihre Gesamtbetriebskosten erhöhen.

Wenn Sie für die Verwaltung mehrerer Installationen von Adobe Commerce verantwortlich sind, kann es schwierig sein, sicherzustellen, dass alle Instanzen denselben Satz von installierten Patches aufweisen. Jede Installation verfügt über ein eigenes Git-Repository, ein `/m2-hotfixes` -Verzeichnis und eine `composer.json` -Datei. Die einzige Garantie, die Sie haben, ist, dass die **Sicherheits-Patches** und **erforderlichen Patches** für Cloud-Benutzer alle als Teil Ihrer Adobe Commerce-Hauptversion installiert sind.

Derzeit gibt es keine zentrale Lösung für dieses Problem, aber Composer bietet eine Möglichkeit, die Lücke zu schließen. Mit dem Paket [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) können Sie [Patches von Abhängigkeiten anwenden](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Sie können ein Composer-Paket erstellen, das alle Ihre Patches installiert, und dieses Paket dann in allen Projekten benötigen.

Dies umfasst **Sicherheits-Patches**, **erforderliche Patches** und **Composer-Patches**, aber was ist mit Qualitäts-Patches und dem Inhalt des Verzeichnisses `/m2-hotfixes`?

## Anwenden von Qualitäts-Patches und Hotfixes

Mit dem Befehl `vendor/bin/magento-patches apply` können Sie Qualitäts-Patches sowohl in der Cloud-Infrastruktur als auch in lokalen Installationen installieren. Sie müssen sicherstellen, dass der Befehl `vendor/bin/magento-patches apply` nach `composer install` Vorgängen ausgeführt wird.

>[!NOTE]
>
>In der Cloud-Infrastruktur können Sie auch Qualitäts-Patches installieren, indem Sie sie in der Datei &quot;`.magento.env.yaml`&quot;Ihres Projekts auflisten. Für das hier beschriebene Beispiel ist der Befehl `vendor/bin/magento-patches apply` erforderlich.

Sie können die Patches angeben, die in der Datei `composer.json` eines benutzerdefinierten Composer-Komponentenpakets angewendet werden sollen, und dann ein Plugin-Paket erstellen, das den Befehl nach `composer install` -Vorgängen ausführt.

Zusammenfassend muss für dieses zentralisierte Patchingbeispiel zwei benutzerdefinierte Composer-Pakete erstellt werden:

- **Komponentenpaket:** `centralized-patcher`

   - Definiert die Liste der zu installierenden Qualitäts-Patches und `m2-hotfixes`
   - Erfordert das Paket `centralized-patcher-composer-plugin` , das den Befehl `vendor/bin/magento-patches apply` nach `composer install` Vorgängen ausführt

- **Plugin-Paket:** `centralized-patcher-composer-plugin`

   - Definiert eine `CentralizedPatcher` PHP-Klasse, die die Liste der Qualitäts-Patches aus dem `centralized-patcher`-Paket liest
   - Führt den Befehl `vendor/bin/magento-patches apply` aus, um die Liste der Qualitäts-Patches nach `composer install` Vorgängen zu installieren

### `centralized-patcher`

Sie können ein Composer-Komponentenpaket (`centralized-patcher`) erstellen, um alle Qualitäts-Patches und `/m2-hotfixes` in allen Ihren Adobe Commerce-Installationen zentral zu verwalten.

Das Komponentenpaket muss:

- Kopieren Sie den Inhalt des Ordners &quot;`/m2-hotfixes`&quot; während der Bereitstellung in alle Ihre Installationen.
- Definieren Sie die Liste der zu installierenden Qualitätssicherungen.
- Führen Sie den Befehl `vendor/bin/magento-patches` aus, um dieselbe Liste von Qualitäts-Patches für alle Installationen zu installieren (unter Verwendung des Plug-in-Pakets [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) als Abhängigkeit).

Erstellen des `centralized-patcher`-Komponentenpakets:

1. Erstellen Sie eine `composer.json` -Datei mit folgendem Inhalt:

   >[!NOTE]
   >
   >Das Attribut `require` im folgenden Beispiel zeigt eine `require` -Abhängigkeit vom [Plugin-Paket](#centralized-patcher-composer-plugin), die Sie später in diesem Beispiel erstellen müssen.

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. Erstellen Sie ein Verzeichnis `/m2-hotfixes` in Ihrem Paket und fügen Sie es dem Attribut `map` in Ihrer Datei `composer.json` hinzu. Das Attribut `map` enthält Dateien, die aus diesem Paket in den Stammordner des Zielprojekts kopiert werden sollen, das Sie patchen möchten.

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >Das Paket `centralized-patcher` kopiert den Inhalt des Verzeichnisses `/m2-hotfixes` in das Verzeichnis m2-hotfixes des Zielprojekts auf `composer install`.  Da die Cloud-Bereitstellungsskripte m2-Hotfixes nach `composer install` anwenden, werden alle Hotfixes vom Bereitstellungsmechanismus installiert.

1. Definieren Sie die Qualitäts-Patches, die im Attribut `quality-patches` installiert werden sollen.

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


Das Attribut `quality-patches` im vorherigen Codebeispiel enthält zwei Patches aus der [vollständigen Patch-Liste](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) als Beispiel.  Diese Qualitäts-Patches werden auf jedem Projekt installiert, für das das Paket `centralized-patcher` mit dem Befehl `vendor/bin/magento-patches apply` erforderlich ist.

Zu Testzwecken können Sie einen Beispiel-Patch (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`) erstellen.

>[!NOTE]
>
>Sie sollten Ihre eigenen Patches zusammen mit Patches, die Sie direkt vom Adobe Commerce-Support erhalten, im Verzeichnis `m2-hotfixes` platzieren.

Beispiel für eine Patch-Datei (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

Da in diesem Beispiel die lokale Methode zum Installieren von Qualitäts-Patches verwendet wird, müssen Sie sicherstellen, dass der Befehl `vendor/bin/magento-patches apply` nach `composer install` -Vorgängen ausgeführt wird. Dieses Plug-in wird nach `composer install` -Vorgängen ausgelöst, bei denen der Befehl `vendor/bin/magento-patches apply` ausgeführt wird.

Erstellen des `centralized-patcher-compose-plugin`-Komponentenpakets:

1. Erstellen Sie eine `composer.json` -Datei mit folgendem Inhalt:

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. Erstellen Sie eine PHP-Datei und definieren Sie eine `CentralizedPatcher` -Klasse, um die Liste der Qualitäts-Patches aus dem [`centralized-patcher`](#centralized-patcher) -Komponentenpaket zu lesen und sie unmittelbar nach jedem `composer install` -Vorgang zu installieren.

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>Unter [Codebeispiele](#code-examples) finden Sie die beiden in diesem Beispiel beschriebenen Pakete in Aktion.


## Vorgehensweise bei projektspezifischen Patches

Möglicherweise sind in allen Projekten nur 95 % der Patches erforderlich, während einige Patches nur für eine bestimmte Instanz gelten. Die reguläre Methode zum Anwenden von Patches funktioniert weiterhin. Sie können projektspezifische Patches im Verzeichnis `/m2-hotfixes` beibehalten und Qualitäts-Patches pro Projekt installieren.

Wenn Sie diesen Ansatz verwenden, dürfen **keine Patches im Verzeichnis `/m2-hotfixes` übertragen, die vom Komponentenpaket `centralized-patcher` in Ihr Projekt kopiert wurden.** Sie können versehentliche Commits verhindern, indem Sie Ihrer `.gitignore` -Datei `/m2-hotfixes` hinzufügen. Beachten Sie nach dem Aktualisieren der Datei &quot;`.gitignore`&quot;, dass alle projektspezifischen `/m2-hotfixes` mit dem Befehl `git add –force` hinzugefügt werden müssen.

## Ausführen verschiedener Adobe Commerce-Versionen

Stellen Sie sicher, dass Sie die richtige Abhängigkeit im `centralized-patcher` -Komponentenpaket festlegen. Beispielsweise benötigen Sie möglicherweise Adobe Commerce 2.4.5-p2 für eine bestimmte Version Ihres Pakets, das nur Patches bereitstellt, die mit Adobe Commerce 2.4.5-p2 kompatibel sind. Möglicherweise haben Sie eine andere Version dieses Pakets, die mit Adobe Commerce 2.4.4 kompatibel ist.

## Ergebnis verstehen

Wie bei Adobe Commerce in der Cloud-Infrastruktur geht dieser Artikel davon aus, dass Ihr Bereitstellungsprozess den Befehl `composer install` und nicht `composer update` oder `git pull` verwendet, um neuen Code für Ihre Server bereitzustellen. Der Fluss der zentralisierten Patch-Installation sieht dann wie folgt aus:

1. Komponenteninstallation

   - Installiert Adobe Commerce, einschließlich Sicherheits- und Funktionspatches für -p1 oder -p2
   - Kombiniert zentralisierte `/m2-hotfixes` und Support-Patches mit projektspezifischem `/m2-hotfixes` und Support-Patches
   - Wendet alle Patches an, die mit dem `cweagans/composer-patches` Composer-Paket installiert sind

1. Nach `composer install`

   - Das Composer-Plug-in installiert zentralisierte Qualitäts-Patches

1. Implementierung

   - Erforderliche Patches und projektspezifische Qualitäts-Patches werden basierend auf der Datei `.magento.env.yaml` installiert (Adobe Commerce nur bei Cloud-Infrastrukturprojekten).
   - Benutzerdefinierte Patches und Support-Patches aus dem Verzeichnis `/m2-hotfixes` werden in alphabetischer Reihenfolge nach Patch-Name installiert.

Auf diese Weise können Sie alle Patches zentral für alle Installationen verwalten und die Sicherheit und Stabilität Ihrer Adobe Commerce Stores besser gewährleisten. Verwenden Sie die folgenden Methoden, um den Patch-Status zu überprüfen:

- [Cloud-Infrastrukturprojekte](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Vor-Ort-Projekte](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Codebeispiele

- [Zentralisierte Patches in Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Zentralisierte Patches in Adobe Commerce in der Cloud-Infrastruktur](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Zentralisiertes Patcher Composer-Plug-in](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Zentralisierte Patcher-Komponente](https://github.com/AntonEvers/centralized-patcher)
