---
title: Funktionsweise von Patches
description: Erfahren Sie mehr über die verschiedenen Arten von Patches für Adobe Commerce und Magento Open Source und deren Funktionsweise.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---


# Funktionsweise von Patches

>[!WARNING]
>
>Es wird dringend empfohlen, alle Patches in einer Staging- oder Entwicklungsumgebung zu testen, bevor sie in die Produktion bereitgestellt werden. Wir empfehlen außerdem dringend, Ihre Daten vor der Anwendung eines Patches zu sichern. Siehe [Sichern und Zurücksetzen des Dateisystems](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Patch-Dateien (oder diff-Dateien) sind Textdateien, die Folgendes beachten:

- Die zu ändernden Dateien.
- Die Zeilennummer, die mit der Änderung beginnen soll, und die Anzahl der zu ändernden Zeilen.
- Der neue Code, der ausgetauscht werden soll.

Wenn die [Patch](https://en.wikipedia.org/wiki/Patch_(Unix)) -Programm ausgeführt, diese Datei gelesen und die angegebenen Änderungen an den Dateien vorgenommen werden.

Es gibt drei Arten von Patches:

- **Hotfixes**—Patches, die von Adobe im [Sicherheitszentrum](https://magento.com/security/patches).
- **Einzelne Patches**—Patches, die der Adobe Commerce-Support individuell erstellt und verteilt.
- **Benutzerdefinierte Patches**—Unoffizielle Patches, die Sie aus einem Git-Commit erstellen können.

## Hotfixes

Hotfixes sind Patches, die für viele Händler wichtige Sicherheits- oder Qualitätsreparaturen enthalten. Diese Fehlerbehebungen werden auf die nächste Patch-Version der entsprechenden kleineren Version angewendet. Adobe gibt bei Bedarf Hotfixes frei.

Hotfixes finden Sie im [Sicherheitszentrum](https://magento.com/security/patches). Befolgen Sie die Anweisungen auf der Seite, um die Patch-Datei herunterzuladen, je nach Version und Installationstyp. Verwenden Sie die [Befehlszeile](../patches/apply.md#) oder [Verfasser](../patches/apply.md) um Hotfix-Patches anzuwenden.

>[!NOTE]
>
>Hotfixes können abwärtskompatible Änderungen enthalten.

## Einzelne Patches

Einzelne Patches enthalten Korrekturen mit geringer Auswirkung auf die Qualität für ein bestimmtes Problem. Diese Fehlerbehebungen werden auf die zuletzt unterstützte Nebenversion angewendet (z. B. 2.4.x), könnten jedoch in der vorherigen unterstützten Nebenversion (z. B. 2.3.x) fehlen. Adobe veröffentlicht bei Bedarf einzelne Patches.

Verwenden Sie die [Werkzeug für Qualitätsmuster](https://devdocs.magento.com/quality-patches/tool.html) um einzelne Patches anzuwenden.

>[!NOTE]
>
>Einzelne Patches enthalten keine abwärtskompatiblen Änderungen.

## Benutzerdefinierte Patches

Manchmal dauert es eine Weile, bis das Adobe Engineering-Team eine Fehlerbehebung für GitHub in eine Adobe Commerce- oder Magento Open Source Composer-Version einbezieht. In der Zwischenzeit können Sie einen Patch von GitHub erstellen und die [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) -Plug-in, um es auf Ihre Composer-basierte Installation anzuwenden.

Verwenden Sie die [Befehlszeile] oder [Verfasser] , um benutzerdefinierte Patches anzuwenden.

Es gibt viele Möglichkeiten, benutzerdefinierte Patch-Dateien zu erstellen. Das folgende Beispiel konzentriert sich auf das Erstellen eines Patches aus einem bekannten Git-Commit.

So erstellen Sie einen benutzerdefinierten Patch:

1. Erstellen Sie eine `patches/composer` in Ihrem lokalen Projekt.
1. Identifizieren Sie die GitHub-Commit- oder Pull-Anforderung, die für den Patch verwendet werden soll. In diesem Beispiel wird die [`2d31571`](https://github.com/magento/magento2/commit/) Commit, verknüpft mit GitHub-Problem [#6474](https://github.com/magento/magento2/issues/6474).
1. Anhängen der `.patch` oder `.diff` Erweiterungen der Commit-URL. Verwendung `.diff` für eine kleinere Dateigröße. Beispiel: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Speichern Sie die Seite als Datei im `patches/composer` Verzeichnis. Beispiel: `github-issue-6474.diff`.
1. Datei bearbeiten und entfernen `app/code/<VENDOR>/<PACKAGE>` aus allen Pfaden, sodass sie relativ zum `vendor/<VENDOR>/<PACKAGE>` Verzeichnis.

   >[!NOTE]
   >
   >Texteditoren, die nachfolgende Leerzeichen automatisch entfernen oder neue Zeilen hinzufügen, können den Patch beschädigen. Verwenden Sie einen einfachen Texteditor, um diese Änderungen vorzunehmen.

Das folgende Beispiel zeigt die zuvor erwähnte DIFF-Datei, nachdem alle Instanzen von `app/code/Magento/Payment`:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
              clearTimeout: function () {
                  clearTimeout(this.timeoutId);
                  this.fail();
                  return this;
            },
```

## Anwenden von Patches

Sie können Patches mit einer der folgenden Methoden anwenden:

- [Werkzeug für Qualitätsmuster](https://devdocs.magento.com/quality-patches/tool.html)
- [Befehlszeile](../patches/apply.md#command-line)
- [Verfasser](../patches/apply.md#composer)

>[!NOTE]
>
>Informationen zum Anwenden eines Patches auf ein Adobe Commerce-Projekt in der Cloud-Infrastruktur finden Sie unter [Anwenden von Patches](https://devdocs.magento.com/cloud/project/project-patch.html) im _Cloud-Handbuch_.
