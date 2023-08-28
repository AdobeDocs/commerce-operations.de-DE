---
title: Best Practices für die Verteilung von Patches in großem Maßstab
description: Erfahren Sie, wie Sie durch zentrales Patchen für Adobe Commerce Unternehmensprojekte verwalten können.
role: Developer
feature: Best Practices
badge: label="Mitwirkende von Anton Evers, Sr. Technischer Architekt, Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Beitragt von Anton Evers"
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# Best Practices für die skalierte Verteilung von Adobe Commerce-Patches

Wenn Sie mehrere Adobe Commerce-Installationen verwalten, [Patchen](../../../upgrade/patches/apply.md) kann ein komplexer Prozess sein. _Zentralisiertes Patchen_ ist ein wesentlicher Teil von [globale Referenzarchitektur](../../architecture/global-reference/overview.md) und bewährten Verfahren für Unternehmen. Dies hilft Ihnen, die richtigen Patches auf alle Ihre Adobe Commerce-Installationen anzuwenden. In diesem Thema wird erläutert, wie eine zentralisierte Patch-Verteilung für alle Adobe Commerce-Typen erreicht werden kann [Patches](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>Der folgende Inhalt wurde ursprünglich im [Verteilen von Adobe Commerce-Patches im Maßstab](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) posten Sie auf dem Adobe Tech Blog. Es wurde geändert, um sich auf die Schritte und Codebeispiele zur Implementierung einer zentralisierten Patchingstrategie zu konzentrieren. Weitere Informationen zu den verschiedenen Arten von Patches, die hier beschrieben werden, finden Sie im ursprünglichen Beitrag .

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Strategie

Da es viele verschiedene Arten von Patches gibt und viele Möglichkeiten, sie anzuwenden, wie wissen Sie, welcher Patch zuerst angewendet wird? Je mehr Patches Sie haben, desto größer ist die Wahrscheinlichkeit, dass sie auf dieselbe Datei oder auf dieselbe Codezeile angewendet werden. Patches werden in der folgenden Reihenfolge angewendet:

1. **Sicherheitspatches** sind Teil der statischen Codebasis einer Adobe Commerce-Version.
1. **Komponentenpatches** bis `composer install` und `composer update` Plug-ins wie [Cweagans/Composer-Patches](https://packagist.org/packages/cweagans/composer-patches).
1. Alle **erforderliche Patches** enthalten in [Cloud-Patches für Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) Paket.
1. Ausgewählt **Qualitätsmuster** enthalten in [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **Benutzerdefinierte Patches** und Adobe Commerce-Support-Patches in der `/m2-hotfixes` Verzeichnis in alphabetischer Reihenfolge nach Patch-Name.

   >[!IMPORTANT]
   >
   >Je mehr Patches Sie anwenden, desto komplexer wird Ihr Code. Komplexer Code kann die Aktualisierung auf eine neue Adobe Commerce-Version erschweren und Ihre Gesamtbetriebskosten erhöhen.

Wenn Sie für die Verwaltung mehrerer Installationen von Adobe Commerce verantwortlich sind, kann es schwierig sein, sicherzustellen, dass alle Instanzen denselben Satz von installierten Patches aufweisen. Jede Installation verfügt über ein eigenes Git-Repository. `/m2-hotfixes` Verzeichnis und `composer.json` -Datei. Die einzige Garantie, die Sie haben, ist, dass die **Sicherheitspatches** und **erforderliche Patches** für Cloud-Benutzer sind alle als Teil Ihrer Adobe Commerce-Hauptversion installiert.

Derzeit gibt es keine zentrale Lösung für dieses Problem, aber Composer bietet eine Möglichkeit, die Lücke zu schließen. Die [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) -Paket ermöglicht es Ihnen, [Patches von Abhängigkeiten anwenden](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Sie können ein Composer-Paket erstellen, das alle Ihre Patches installiert, und dieses Paket dann in allen Projekten benötigen.

Diese **Sicherheitspatches**, **erforderliche Patches**, und **Komponentenpatches**, aber was ist mit Qualitäts-Patches und dem Inhalt der `/m2-hotfixes` Verzeichnis?

## Anwenden von Qualitäts-Patches und Hotfixes

Sie können mithilfe der `vendor/bin/magento-patches apply` Befehl. Sie müssen sicherstellen, dass `vendor/bin/magento-patches apply` Befehl wird ausgeführt nach `composer install` Vorgänge.

>[!NOTE]
>
>In der Cloud-Infrastruktur können Sie auch Qualitäts-Patches installieren, indem Sie sie in der `.magento.env.yaml` -Datei. Für das hier beschriebene Beispiel muss die `vendor/bin/magento-patches apply` Befehl.

Sie können die Patches angeben, die im `composer.json` Datei eines benutzerdefinierten Composer-Komponentenpakets erstellen und dann ein Plugin-Paket erstellen, das den Befehl nach `composer install` Vorgänge.

Zusammenfassend muss für dieses zentralisierte Patchingbeispiel zwei benutzerdefinierte Composer-Pakete erstellt werden:

- **Komponentenpaket:** `centralized-patcher`

   - Definiert die Liste der Qualitäts-Patches und `m2-hotfixes` installieren
   - Erfordert die `centralized-patcher-composer-plugin` -Paket, das die `vendor/bin/magento-patches apply` Befehl nach `composer install` Vorgänge

- **Plugin-Paket:** `centralized-patcher-composer-plugin`

   - Definiert eine `CentralizedPatcher` PHP-Klasse, die die Qualitäts-Patchliste aus dem `centralized-patcher` package
   - Führt die `vendor/bin/magento-patches apply` -Befehl zum Installieren der Liste von Qualitäts-Patches nach `composer install` Vorgänge

### `centralized-patcher`

Sie können ein Komponentenpaket erstellen (`centralized-patcher`) zur zentralen Verwaltung aller Qualitäts-Patches und `/m2-hotfixes` über all Ihre Adobe Commerce-Installationen hinweg.

Das Komponentenpaket muss:

- Kopieren Sie den Inhalt der `/m2-hotfixes` in all Ihre Installationen während der Bereitstellung.
- Definieren Sie die Liste der zu installierenden Qualitätssicherungen.
- Führen Sie die `vendor/bin/magento-patches` -Befehl zum Installieren derselben Liste von Qualitäts-Patches für alle Installationen (mithilfe der [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) Plug-in-Paket als Abhängigkeit).

So erstellen Sie die `centralized-patcher` Komponentenpaket:

1. Erstellen Sie eine `composer.json` -Datei mit dem folgenden Inhalt:

   >[!NOTE]
   >
   >Die `require` -Attribut im folgenden Beispiel zeigt ein `require` Abhängigkeit von der [Plugin-Paket](#centralized-patcher-composer-plugin) , die Sie später in diesem Beispiel erstellen müssen.

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

1. Erstellen Sie eine `/m2-hotfixes` -Verzeichnis in Ihrem Paket und fügen Sie es zu `map` -Attribut in `composer.json` -Datei. Die `map` -Attribut enthält Dateien, die aus diesem Paket in den Stammordner des Zielprojekts kopiert werden sollen, das Sie patchen möchten.

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
   >Die `centralized-patcher` package kopiert den Inhalt der `/m2-hotfixes` Verzeichnis in das Verzeichnis m2-hotfixes des Zielprojekts auf `composer install`.  Da die Cloud-Bereitstellungsskripte m2-hotfixes nach anwenden `composer install`festgelegt ist, werden alle Hotfixes vom Bereitstellungsmechanismus installiert.

1. Definieren Sie die Qualitäts-Patches, die im Abschnitt `quality-patches` -Attribut.

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


Die `quality-patches` -Attribut im vorherigen Codebeispiel enthält zwei Patches aus der [Vollständige Patch-Liste](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) als Beispiel.  Diese Qualitäts-Patches werden auf jedem Projekt installiert, für das die `centralized-patcher` -Paket mit `vendor/bin/magento-patches apply` Befehl.

Zu Testzwecken können Sie einen Beispiel-Patch (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Sie sollten Ihre eigenen Patches in die `m2-hotfixes` -Verzeichnis zusammen mit Patches, die Sie direkt vom Adobe Commerce-Support erhalten.

Beispiel einer Patch-Datei (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

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

Da in diesem Beispiel die lokale Methode zum Installieren von Qualitäts-Patches verwendet wird, müssen Sie sicherstellen, dass die Variable `vendor/bin/magento-patches apply` Befehl wird ausgeführt nach `composer install` Vorgänge. Dieses Plug-in wird ausgelöst nach `composer install` -Vorgänge, bei denen die `vendor/bin/magento-patches apply` Befehl.

So erstellen Sie die `centralized-patcher-compose-plugin` Komponentenpaket:

1. Erstellen Sie eine `composer.json` -Datei mit dem folgenden Inhalt:

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

1. Erstellen Sie eine PHP-Datei und definieren Sie eine `CentralizedPatcher` -Klasse, um die Liste der Qualitäts-Patches aus der [`centralized-patcher`](#centralized-patcher) Komponenten-Paket installieren und sofort nach jedem `composer install` Vorgang.

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
>Siehe Abschnitt [code-example](#code-examples) um die beiden in diesem Beispiel beschriebenen Pakete in Aktion zu sehen.


## Vorgehensweise bei projektspezifischen Patches

Möglicherweise sind in allen Projekten nur 95 % der Patches erforderlich, während einige Patches nur für eine bestimmte Instanz gelten. Die reguläre Methode zum Anwenden von Patches funktioniert weiterhin. Sie können projektspezifische Patches im `/m2-hotfixes` und installieren Sie Qualitäts-Patches pro Projekt.

Wenn Sie diesen Ansatz verwenden, **nicht** alle Patches im `/m2-hotfixes` in das Projekt kopiert wurden, das von der `centralized-patcher` Komponentenpaket. Sie können versehentliche Commits verhindern, indem Sie `/m2-hotfixes` auf `.gitignore` -Datei. Nach dem Aktualisieren der `.gitignore` -Datei, denken Sie daran, dass alle projektspezifischen `/m2-hotfixes` muss mit der `git add –force` Befehl.

## Ausführen verschiedener Adobe Commerce-Versionen

Stellen Sie sicher, dass Sie die richtige Abhängigkeit im `centralized-patcher` Komponentenpaket. Beispielsweise benötigen Sie möglicherweise Adobe Commerce 2.4.5-p2 für eine bestimmte Version Ihres Pakets, das nur Patches bereitstellt, die mit Adobe Commerce 2.4.5-p2 kompatibel sind. Möglicherweise haben Sie eine andere Version dieses Pakets, die mit Adobe Commerce 2.4.4 kompatibel ist.

## Ergebnis verstehen

Wie bei Adobe Commerce in der Cloud-Infrastruktur geht dieser Artikel davon aus, dass Ihr Implementierungsprozess die `composer install` Befehl und nicht `composer update` oder `git pull` , um neuen Code für Ihre Server bereitzustellen. Der Fluss der zentralisierten Patch-Installation sieht dann wie folgt aus:

1. Komponenteninstallation

   - Installiert Adobe Commerce, einschließlich Sicherheits- und Funktionspatches für -p1 oder -p2
   - Kombiniert zentralisierte `/m2-hotfixes` und unterstützen Patches mit projektspezifischen `/m2-hotfixes` und Support-Patches
   - Wendet alle Patches an, die mit dem `cweagans/composer-patches` Composer-Paket

1. Nachher `composer install`

   - Das Composer-Plug-in installiert zentralisierte Qualitäts-Patches

1. Implementierung

   - Erforderliche Patches und projektspezifische Qualitäts-Patches werden basierend auf dem `.magento.env.yaml` -Datei (Adobe Commerce nur bei Cloud-Infrastrukturprojekten).
   - Benutzerdefinierte Patches und Support-Patches aus dem `/m2-hotfixes` werden in alphabetischer Reihenfolge nach Patch-Namen installiert.

Auf diese Weise können Sie alle Patches zentral für alle Installationen verwalten und die Sicherheit und Stabilität Ihrer Adobe Commerce Stores besser gewährleisten. Verwenden Sie die folgenden Methoden, um den Patch-Status zu überprüfen:

- [Cloud-Infrastrukturprojekte](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Vor-Ort-Projekte](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Codebeispiele

- [Zentralisierte Patches in Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Zentralisierte Patches in Adobe Commerce auf Cloud-Infrastruktur](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Zentralisiertes Patcher Composer-Plug-in](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Zentralisierte Patcher-Komponente](https://github.com/AntonEvers/centralized-patcher)
