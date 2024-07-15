---
title: Funktionsweise von Patches
description: Erfahren Sie mehr über die verschiedenen Arten von Patches für Adobe Commerce und deren Funktionsweise.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Funktionsweise von Patches

>[!WARNING]
>
>Es wird dringend empfohlen, alle Patches in einer Staging- oder Entwicklungsumgebung zu testen, bevor sie in die Produktion bereitgestellt werden. Wir empfehlen außerdem dringend, Ihre Daten vor der Anwendung eines Patches zu sichern. Siehe [Sichern und Zurücksetzen des Dateisystems](../../installation/tutorials/backup.md).

Patch-Dateien (oder diff-Dateien) sind Textdateien, die Folgendes beachten:

- Die zu ändernden Dateien.
- Die Zeilennummer, die mit der Änderung beginnen soll, und die Anzahl der zu ändernden Zeilen.
- Der neue Code, der ausgetauscht werden soll.

Wenn das Patch-Programm ausgeführt wird, wird diese Datei gelesen und die angegebenen Änderungen werden an den Dateien vorgenommen.

Es gibt drei Arten von Patches:

- **Hotfixes** - Patches, die Adobe im [Sicherheitscenter](https://magento.com/security/patches) veröffentlicht.
- **Individuelle Patches** - Patches, die der Adobe Commerce-Support individuell erstellt und verteilt.
- **Benutzerdefinierte Patches**—Unoffizielle Patches, die Sie aus einem Git-Commit erstellen können.

## Hotfixes

Hotfixes sind Patches, die für viele Händler wichtige Sicherheits- oder Qualitätsreparaturen enthalten. Diese Fehlerbehebungen werden auf die nächste Patch-Version der entsprechenden kleineren Version angewendet. Adobe gibt bei Bedarf Hotfixes frei.

Sie finden Hotfixes im [Sicherheitszentrum](https://magento.com/security/patches). Befolgen Sie die Anweisungen auf der Seite, um die Patch-Datei herunterzuladen, je nach Version und Installationstyp. Verwenden Sie die [Befehlszeile](../patches/apply.md#) oder den [Composer](../patches/apply.md), um Hotfix-Patches anzuwenden.

>[!NOTE]
>
>Hotfixes können abwärtskompatible Änderungen enthalten.

## Einzelne Patches

Einzelne Patches enthalten Korrekturen mit geringer Auswirkung auf die Qualität für ein bestimmtes Problem. Diese Fehlerbehebungen werden auf die zuletzt unterstützte Nebenversion angewendet (z. B. 2.4.x), könnten jedoch in der vorherigen unterstützten Nebenversion (z. B. 2.3.x) fehlen. Adobe veröffentlicht bei Bedarf einzelne Patches.

Verwenden Sie den [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, um einzelne Patches anzuwenden.

>[!NOTE]
>
>Einzelne Patches enthalten keine abwärtskompatiblen Änderungen.

## Benutzerdefinierte Patches

Manchmal dauert es eine Weile, bis das Adobe Engineering-Team eine Fehlerbehebung auf GitHub in eine Adobe Commerce Composer-Version einbezieht. In der Zwischenzeit können Sie einen Patch von GitHub erstellen und das Plug-in [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) verwenden, um ihn auf Ihre Composer-basierte Installation anzuwenden.

Verwenden Sie die [Befehlszeile](apply.md#command-line) oder den [Composer](apply.md#composer), um benutzerdefinierte Patches anzuwenden.

Es gibt viele Möglichkeiten, benutzerdefinierte Patch-Dateien zu erstellen. Das folgende Beispiel konzentriert sich auf das Erstellen eines Patches aus einem bekannten Git-Commit.

So erstellen Sie einen benutzerdefinierten Patch:

1. Erstellen Sie ein Verzeichnis mit dem Namen &quot;`patches/composer`&quot; in Ihrem lokalen Projekt.
1. Identifizieren Sie die GitHub-Commit- oder Pull-Anforderung, die für den Patch verwendet werden soll. In diesem Beispiel wird der [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) -Befehl verwendet, der mit dem GitHub-Problem [#6474](https://github.com/magento/magento2/issues/6474) verknüpft ist.
1. Hängen Sie die Erweiterungen `.patch` oder `.diff` an die Commit-URL an. Verwenden Sie `.diff` für eine kleinere Dateigröße. Beispiel: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Speichern Sie die Seite als Datei im Verzeichnis &quot;`patches/composer`&quot;. Beispiel: `github-issue-6474.diff`.
1. Bearbeiten Sie die Datei und entfernen Sie &quot;`app/code/<VENDOR>/<PACKAGE>`&quot; aus allen Pfaden, sodass sie relativ zum Verzeichnis &quot;`vendor/<VENDOR>/<PACKAGE>`&quot; sind.

   >[!NOTE]
   >
   >Texteditoren, die nachfolgende Leerzeichen automatisch entfernen oder neue Zeilen hinzufügen, können den Patch beschädigen. Verwenden Sie einen einfachen Texteditor, um diese Änderungen vorzunehmen.

Das folgende Beispiel zeigt die zuvor erwähnte DIFF-Datei, nachdem alle Instanzen von `app/code/Magento/Payment` entfernt wurden:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();

                 return this;
             },
```

## Anwenden von Patches

Sie können Patches mit einer der folgenden Methoden anwenden:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Befehlszeile](/help/upgrade/patches/apply.md#command-line)
- [Verfasser](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Informationen zum Anwenden eines Patches auf ein Adobe Commerce-Cloud-Infrastrukturprojekt finden Sie unter [Anwenden von Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Leitfaden _Commerce on Cloud_ .
