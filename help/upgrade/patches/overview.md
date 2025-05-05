---
title: Funktionsweise von Patches
description: Erfahren Sie mehr über die verschiedenen Arten von Patches für Adobe Commerce und wie sie funktionieren.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Funktionsweise von Patches

>[!WARNING]
>
>Es wird dringend empfohlen, alle Patches in einer Staging- oder Entwicklungsumgebung zu testen, bevor sie in der Produktion bereitgestellt werden. Es wird außerdem dringend empfohlen, vor der Installation eines Patches eine Sicherungskopie der Daten zu erstellen. Siehe [Sichern und Zurücksetzen des Dateisystems](../../installation/tutorials/backup.md).

Patch- (oder diff-) Dateien sind Textdateien, die Folgendes beachten:

- Die zu ändernden Dateien.
- Die Zeilennummer, mit der die Änderung gestartet werden soll, und die Anzahl der zu ändernden Zeilen.
- Der neue Code zum Austauschen.

Wenn das Patch-Programm ausgeführt wird, wird diese Datei eingelesen und die angegebenen Änderungen werden an der/den Datei(en) vorgenommen.

Es gibt drei Arten von Patches:

- **Hotfixes** - Patches, die von Adobe im [Sicherheitscenter](https://magento.com/security/patches) veröffentlicht werden.
- **Individuelle Patches** - Patches, die vom Adobe Commerce-Support auf individueller Basis erstellt und verteilt werden.
- **Benutzerdefinierte Patches**: Inoffizielle Patches, die Sie aus einem Git-Commit erstellen können.

## Hotfixes

Hotfixes sind Patches mit wirkungsvollen Sicherheits- oder Qualitätskorrekturen, die sich auf viele Händler auswirken. Diese Fehlerbehebungen werden auf die nächste Patch-Version für die entsprechende Nebenversion angewendet. Adobe veröffentlicht Hotfixes nach Bedarf.

Hotfixes finden Sie im [Sicherheitscenter](https://magento.com/security/patches). Folgen Sie den Anweisungen auf der Seite, um die Patch-Datei je nach Version und Installationstyp herunterzuladen. Verwenden Sie die [Befehlszeile](../patches/apply.md#) oder [Composer](../patches/apply.md), um Hotfix-Patches anzuwenden.

>[!NOTE]
>
>Hotfixes können abwärtsinkompatible Änderungen enthalten.

## Einzelne Patches

Einzelne Patches enthalten Korrekturen von geringer Qualität für ein bestimmtes Problem. Diese Fehlerbehebungen werden auf die zuletzt unterstützte Nebenversion angewendet (z. B. 2.4.x), könnten jedoch in der vorherigen unterstützten Nebenversion (z. B. 2.3.x) fehlen. Adobe veröffentlicht bei Bedarf einzelne Patches.

Verwenden Sie die [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de){target="_blank"}, um einzelne Patches anzuwenden.

>[!NOTE]
>
>Einzelne Patches enthalten keine rückwärts inkompatiblen Änderungen.

## Benutzerdefinierte Patches

Manchmal dauert es eine Weile, bis das Adobe-Engineering-Team eine Fehlerbehebung auf GitHub in einer Adobe Commerce Composer-Version implementiert. In der Zwischenzeit können Sie einen Patch von GitHub aus erstellen und das [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/)-Plug-in verwenden, um ihn auf Ihre Composer-basierte Installation anzuwenden.

Verwenden Sie die [Befehlszeile](apply.md#command-line) oder [Composer](apply.md#composer), um benutzerdefinierte Patches anzuwenden.

Es gibt viele Möglichkeiten, benutzerdefinierte Patch-Dateien zu erstellen. Das folgende Beispiel konzentriert sich auf die Erstellung eines Patches aus einem bekannten Git-Commit.

So erstellen Sie einen benutzerdefinierten Patch:

1. Erstellen Sie ein `patches/composer` in Ihrem lokalen Projekt.
1. Identifizieren Sie die für den Patch zu verwendende GitHub-Commit- oder Pull-Anfrage. In diesem Beispiel wird der [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede)-Commit verwendet, der mit dem GitHub-Problem [ verknüpft #6474](https://github.com/magento/magento2/issues/6474).
1. Hängen Sie die `.patch` oder die `.diff` Erweiterungen an die Commit-URL an. Verwenden Sie `.diff` für eine kleinere Dateigröße. Beispiel: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Speichern Sie die Seite als Datei im `patches/composer`. Beispiel: `github-issue-6474.diff`.
1. Bearbeiten Sie die Datei und entfernen Sie `app/code/<VENDOR>/<PACKAGE>` aus allen Pfaden, sodass sie relativ zum `vendor/<VENDOR>/<PACKAGE>` sind.

   >[!NOTE]
   >
   >Texteditoren, die automatisch nachfolgende Leerzeichen entfernen oder neue Zeilen hinzufügen, können den Patch beschädigen. Verwenden Sie für diese Änderungen einen einfachen Texteditor.

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

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de){target="_blank"}
- [Befehlszeile](/help/upgrade/patches/apply.md#command-line)
- [Komponist](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Informationen zum Anwenden eines Patches auf ein Adobe Commerce in Cloud-Infrastrukturprojekt finden Sie [Anwenden von Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im _Handbuch zu Commerce in Cloud_.
