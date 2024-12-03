---
title: 'MDVA-42046: Falscher Wert für das Produktattribut zugewiesen'
description: Der Patch MDVA-42046 behebt das Problem, dass für das Produktattribut ein falscher Wert zugewiesen wird, während ein Produkt mit einem Datumseingabefeld aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Attributes, Products
role: Admin
exl-id: ff5903ff-70b3-4274-a8a1-450c2fde9750
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-42046: Falscher Wert für das Produktattribut zugewiesen

Der Patch MDVA-42046 behebt das Problem, dass für das Produktattribut ein falscher Wert zugewiesen wird, während ein Produkt mit einem Datumseingabefeld aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.3.5-p2 und 2.4.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach dem Speichern eines Produkts mit den Feldern `news_from_date` und/oder `news_to_date` werden die Werte aus diesen Feldern auf den Standardwert zurückgesetzt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Exportieren Sie das in Schritt 1 erstellte Produkt.
1. Fügen Sie in der exportierten CSV-Datei einige Werte in die Felder `news_from_date` und `news_to_date` ein. Beispiel: 15.05.2021 und 2021-06-18.
1. Importieren Sie das Produkt mit der modifizierten CSV-Datei.
1. Fügen Sie dem Produktraster zusätzliche Spalten &quot;Produkt als neu vom Datum festlegen&quot;und &quot;Produkt als neu auf Datum festlegen&quot;hinzu.
1. Öffnen Sie die Bearbeitungsseite für das Produkt und klicken Sie ohne Änderungen auf **Speichern**.
1. Gehen Sie zurück zum Produktraster und überprüfen Sie die Daten für das Produkt.

<u>Erwartete Ergebnisse</u>:

Sowohl &quot;Produkt vom Datum als neu festlegen&quot;als auch &quot;Produkt als neu auf Datum festlegen&quot;sind dieselben wie vor dem Speichern.

<u>Tatsächliche Ergebnisse</u>:

* Die Werte in den Spalten &quot;Produkt als neu vom Datum festlegen&quot;und &quot;Produkt als neu auf Datum festlegen&quot;werden geändert.

* Die Spalte &quot;Produkt als neu vom Datum festlegen&quot;zeigt das aktuelle Datum und die Spalte &quot;Produkt als neu auf Datum festlegen&quot;ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
