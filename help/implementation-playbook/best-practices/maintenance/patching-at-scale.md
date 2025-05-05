---
title: Best Practices für die Verteilung von Patches im großen Maßstab
description: Erfahren Sie, wie zentralisiertes Patchen für Adobe Commerce Ihnen bei der Verwaltung von Unternehmensprojekten helfen kann.
role: Developer
feature: Best Practices
badge: label="Beiträge von Tony Evers, Sr. Technical Architect, Adobe" type="Informative" url="https://www.linkedin.com/in/evers-tony/" tooltip="Beiträge von Tony Evers"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 2c9f827326315bc4ef77d511dddce81e059a1092
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Best Practices für die skalierte Verteilung von Adobe Commerce-Patches

Wenn Sie mehrere Adobe Commerce-Installationen verwalten[ kann ](../../../upgrade/patches/apply.md)Patchen“ ein komplexer Prozess sein. _Zentralisiertes Patchen_ ist eine Best Practice für Unternehmen. Damit können Sie die richtigen Patches auf alle Ihre Adobe Commerce-Installationen anwenden. In diesem Abschnitt wird erläutert, wie Sie eine zentralisierte Patch-Verteilung für alle Adobe Commerce-Typen [Patches) ](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>Der folgende Inhalt wurde ursprünglich im Beitrag [Verteilen von Adobe Commerce-Patches in großem Maßstab](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) im Adobe Tech Blog veröffentlicht. Er wurde so geändert, dass er sich auf die Schritte und Codebeispiele zur Implementierung einer zentralisierten Patching-Strategie konzentriert. Weitere Informationen zu den verschiedenen hier beschriebenen Patchtypen finden Sie im ursprünglichen Beitrag .

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Strategie

Da es viele verschiedene Arten von Patches und viele Möglichkeiten gibt, sie anzuwenden, woher wissen Sie, welches Patch zuerst angewendet wird? Je mehr Patches vorhanden sind, desto größer ist die Chance, dass sie auf dieselbe Datei oder auf dieselbe Codezeile angewendet werden. Patches werden in der folgenden Reihenfolge angewendet:

1. **Sicherheits** Patches sind Teil der statischen Code-Basis einer Adobe Commerce-Version.
1. **Composer Patches** durch `composer install` und `composer update` Plugins wie [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. Alle **erforderlichen Patches** im Paket [Cloud-Patches für Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html?lang=de) enthalten.
1. Ausgewählte **Qualitäts-Patches** in der [[!DNL [Quality Patches Tool]]](../../../tools/quality-patches-tool/usage.md) enthalten.
1. **Benutzerdefinierte Patches** und Adobe Commerce-Support-Patches im `/m2-hotfixes`-Verzeichnis in alphabetischer Reihenfolge nach Patch-Namen.

   >[!IMPORTANT]
   >
   >Je mehr Patches Sie anwenden, desto komplexer wird Ihr Code. Komplexer Code kann das Upgrade auf eine neue Version von Adobe Commerce erschweren und die Gesamtbetriebskosten erhöhen.

Wenn Sie für die Verwaltung mehrerer Installationen von Adobe Commerce verantwortlich sind, kann es eine Herausforderung sein, sicherzustellen, dass auf allen Instanzen derselbe Satz von Patches installiert ist. Jede Installation verfügt über ein eigenes Git-Repository, `/m2-hotfixes` Verzeichnis und `composer.json`. Die einzige Garantie, die Sie haben, ist **dass die** Sicherheits-Patches **und erforderlichen Patches** für Cloud-Benutzer alle als Teil Ihrer Adobe Commerce-Hauptversion installiert sind.

Derzeit gibt es keine einzige zentralisierte Lösung für dieses Problem, aber Composer bietet eine Möglichkeit, die Lücke zu schließen. Mit dem [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) können Sie [Patches aus Abhängigkeiten anwenden](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Sie können ein Composer-Paket erstellen, das alle Ihre Patches installiert und dieses Paket dann in allen Ihren Projekten benötigt.

Das umfasst **Sicherheits**, **erforderliche** und **Composer-**. Aber was ist mit hochwertigen Patches und dem Inhalt des `/m2-hotfixes`?

## Anwenden von hochwertigen Patches und Hotfixes

Mit dem Befehl `vendor/bin/magento-patches apply` können Sie Qualitäts-Patches sowohl für die Cloud-Infrastruktur als auch für lokale Installationen installieren. Sie müssen sicherstellen, dass der `vendor/bin/magento-patches apply`-Befehl nach `composer install` ausgeführt wird.

>[!NOTE]
>
>In der Cloud-Infrastruktur können Sie auch Qualitäts-Patches installieren, indem Sie diese in der `.magento.env.yaml` Ihres Projekts auflisten. Für das hier beschriebene Beispiel ist die Verwendung des Befehls `vendor/bin/magento-patches apply` erforderlich.

Sie können die Patches angeben, die in der `composer.json`-Datei eines benutzerdefinierten Komponentenpakets angewendet werden sollen, und dann ein Plug-in-Paket erstellen, das den Befehl nach `composer install` Vorgängen ausführt.

Zusammenfassend lässt sich sagen, dass Sie für dieses zentralisierte Patch-Beispiel zwei benutzerdefinierte Composer-Pakete erstellen müssen:

- **Komponentenpaket:** `centralized-patcher`

   - Definiert die Liste der zu installierenden Qualitäts-Patches und -`m2-hotfixes`
   - Erfordert das `centralized-patcher-composer-plugin`-Paket, das den Befehl `vendor/bin/magento-patches apply` nach `composer install` Vorgängen ausführt

- **Plug-in-Paket:** `centralized-patcher-composer-plugin`

   - Definiert eine `CentralizedPatcher` PHP-Klasse, die die Quality Patches-Liste aus dem `centralized-patcher` liest
   - Führt den Befehl `vendor/bin/magento-patches apply` aus, um die Liste der Qualitäts-Patches nach `composer install` zu installieren

### `centralized-patcher`

Sie können ein Composer-Komponentenpaket (`centralized-patcher`) erstellen, um alle Quality Patches und `/m2-hotfixes` für alle Adobe Commerce-Installationen zentral zu verwalten.

Das Komponentenpaket muss:

- Kopieren Sie während der Bereitstellung den Inhalt des `/m2-hotfixes` Verzeichnisses in alle Installationen.
- Definieren Sie die Liste der zu installierenden Qualitäts-Patches.
- Führen Sie den Befehl `vendor/bin/magento-patches` aus, um dieselbe Liste von Qualitäts-Patches für alle Installationen zu installieren (unter Verwendung des [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin)-Plug-in-Pakets als Abhängigkeit).

So erstellen Sie das `centralized-patcher` Komponentenpaket:

1. Erstellen Sie eine `composer.json`-Datei mit folgendem Inhalt:

   >[!NOTE]
   >
   >Das Attribut `require` im folgenden Beispiel zeigt eine `require` Abhängigkeit vom [Plug-in-Paket](#centralized-patcher-composer-plugin) die Sie später in diesem Beispiel erstellen müssen.

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

1. Erstellen Sie ein `/m2-hotfixes` in Ihrem Paket und fügen Sie es dem `map`-Attribut in Ihrer `composer.json` hinzu. Das `map`-Attribut enthält Dateien, die aus diesem Paket in den Stamm des Zielprojekts, das Sie patchen möchten, kopiert werden sollen.

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
   >Das `centralized-patcher`-Paket kopiert den Inhalt des `/m2-hotfixes`-Verzeichnisses in das Verzeichnis m2-hotfixes des Zielprojekts auf `composer install`.  Da die Cloud-Bereitstellungsskripte m2-Hotfixes nach der `composer install` anwenden, werden alle Hotfixes vom Bereitstellungsmechanismus installiert.

1. Definieren Sie die Qualitäts-Patches, die im `quality-patches` installiert werden sollen.

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


Das Attribut `quality-patches` im vorherigen Codebeispiel enthält als Beispiel zwei Patches aus [vollständigen ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de)).  Diese Qualitäts-Patches werden mit dem Befehl `vendor/bin/magento-patches apply` auf jedem Projekt installiert, für das das `centralized-patcher`-Paket erforderlich ist.

Zu Testzwecken können Sie einen Beispiel-Patch erstellen (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Sie sollten Ihre eigenen Patches zusammen mit Patches, die Sie direkt vom Adobe Commerce-Support erhalten, im `m2-hotfixes`-Verzeichnis platzieren.

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

Da in diesem Beispiel die On-Premise-Methode zum Installieren von Qualitäts-Patches verwendet wird, müssen Sie sicherstellen, dass der `vendor/bin/magento-patches apply`-Befehl nach `composer install`-Vorgängen ausgeführt wird. Dieses Plug-in wird nach `composer install`-Vorgängen ausgelöst, wodurch der `vendor/bin/magento-patches apply`-Befehl ausgeführt wird.

So erstellen Sie das `centralized-patcher-compose-plugin` Komponentenpaket:

1. Erstellen Sie eine `composer.json`-Datei mit folgendem Inhalt:

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

1. Erstellen Sie eine PHP-Datei und definieren Sie eine `CentralizedPatcher`-Klasse, um die Quality Patches-Liste aus dem [`centralized-patcher`](#centralized-patcher) Komponentenpaket zu lesen und sie sofort nach jedem `composer install` Vorgang zu installieren.

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
>Unter [Code-Beispiele](#code-examples) sehen Sie die beiden in diesem Beispiel beschriebenen Pakete in Aktion.


## Vorgehensweise bei projektspezifischen Patches

Möglicherweise sind in allen Projekten nur 95 % der Patches erforderlich, während einige Patches nur für eine bestimmte Instanz gelten. Die übliche Methode zum Anwenden von Patches funktioniert weiterhin. Sie können projektspezifische Patches im `/m2-hotfixes` Verzeichnis behalten und Qualitätspatches pro Projekt installieren.

Wenn Sie diesen Ansatz verwenden **übertragen** keine Patches im `/m2-hotfixes`, die vom `centralized-patcher`-Komponentenpaket in Ihr Projekt kopiert wurden. Sie können versehentliche Commits verhindern, indem Sie `/m2-hotfixes` zu Ihrer `.gitignore` hinzufügen. Beachten Sie nach dem Aktualisieren der `.gitignore`-Datei, dass alle projektspezifischen `/m2-hotfixes` mit dem Befehl `git add –force` hinzugefügt werden müssen.

## Ausführen verschiedener Adobe Commerce-Versionen

Stellen Sie sicher, dass Sie im `centralized-patcher`-Komponentenpaket die richtige Abhängigkeit festlegen. Beispielsweise benötigen Sie möglicherweise Adobe Commerce 2.4.5-p2 für eine bestimmte Version Ihres Pakets, das nur Patches bereitstellt, die mit Adobe Commerce 2.4.5-p2 kompatibel sind. Möglicherweise haben Sie eine andere Version dieses Pakets, die mit Adobe Commerce 2.4.4 kompatibel ist.

## Das Ergebnis verstehen

Wie bei Adobe Commerce in der Cloud-Infrastruktur wird in diesem Artikel davon ausgegangen, dass Ihr Bereitstellungsprozess den `composer install`-Befehl verwendet und nicht `composer update` oder `git pull`, um neuen Code auf Ihren Servern bereitzustellen. Der Ablauf einer zentralisierten Patch-Installation sieht dann wie folgt aus:

1. Composer-Installation

   - Installiert Adobe Commerce, einschließlich Sicherheits- und Funktions-Patches von -p1 oder -p2
   - Kombiniert zentralisierte `/m2-hotfixes`- und Support-Patches mit projektspezifischen `/m2-hotfixes`- und Support-Patches
   - Wendet alle Patches an, die mit dem `cweagans/composer-patches` Composer-Paket installiert werden

1. Nach dem `composer install`

   - Composer-Plug-in installiert zentralisierte Quality-Patches

1. Bereitstellung

   - Erforderliche Patches und projektspezifische Qualitäts-Patches werden basierend auf der `.magento.env.yaml` installiert (nur Adobe Commerce für Cloud-Infrastrukturprojekte).
   - Benutzerdefinierte Patches und Support-Patches aus dem `/m2-hotfixes` werden in alphabetischer Reihenfolge nach Patch-Namen installiert.

Auf diese Weise können Sie alle Ihre Patches für alle Ihre Installationen zentral verwalten und die Sicherheit und Stabilität Ihrer Adobe Commerce-Stores besser gewährleisten. Verwenden Sie die folgenden Methoden, um den Patch-Status zu überprüfen:

- [Cloud-Infrastrukturprojekte](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de#view-available-patches-and-status)
- [On-Premise-Projekte](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Code-Beispiele

- [Zentralisierte Patches in der Magento Open Source ](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Zentralisierte Patches in Adobe Commerce auf Cloud-Infrastruktur](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Centralized Patcher Composer-Plug-in](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Zentralisierte Patcher-Komponente](https://github.com/AntonEvers/centralized-patcher)
