---
title: 'ACSD-66153: Die Seite gibt einen 500-Fehler aufgrund einer zwischengespeicherten falschen Layout-Struktur zurück'
description: Wenden Sie den Patch ACSD-66153 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Seite aufgrund einer zwischengespeicherten falschen Layout-Struktur einen Fehler-Code 500 zurückgibt.
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: 70c7255e369ef366407d539488f0d815eb93f48a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACSD-66153: Die Seite gibt einen 500-Fehler aufgrund einer zwischengespeicherten falschen Layout-Struktur zurück

Der Patch ACSD-66153 behebt das Problem, dass eine Seite aufgrund einer zwischengespeicherten falschen Layout-Struktur einen Fehler-Code 500 zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-66153. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p10

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine Seite gibt aufgrund einer zwischengespeicherten falschen Layout-Struktur einen 500-Fehler zurück.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie `2.4-develop`.
1. Benutzerdefiniertes Modul erstellen und installieren:
1.1 Fügen Sie dem `catalog_category_view`-Layout einen benutzerdefinierten Block hinzu.
1.1 Fügen Sie `Magento\Framework\View\Result\Layout` über den Konstruktor in den benutzerdefinierten Block ein.
1. Erstellen Sie die **[!UICONTROL shop]**.
1. **[!UICONTROL two terminal windows]** öffnen:
   1. **Terminal 1**: Reinigen Sie den Layout-Cache kontinuierlich:

      ```
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **Terminal 2**: Simultane Anforderungen an die Kategorieseite simulieren:

      ```
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. Einige Anfragen schlagen nach dem Zufallsprinzip mit einem 500-Status-Code fehl, und die `var/log/support_report.log` zeigt den folgenden Fehler an:

   ```
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>Erwartete Ergebnisse</u>:

Alle Anfragen geben 200 OK zurück.

<u>Tatsächliche Ergebnisse</u>:

Einige Anfragen geben gelegentlich 500 interne Server-Fehler zurück.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
