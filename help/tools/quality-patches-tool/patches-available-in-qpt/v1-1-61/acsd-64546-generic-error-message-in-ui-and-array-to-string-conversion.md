---
title: 'ACSD-64546: Allgemeine Fehlermeldung in Benutzeroberfläche und Ausnahme bei der Konvertierung von Arrays in Zeichenfolgen während der Erstellung der UPS-Kennzeichnung'
description: Wenden Sie den Patch ACSD-64546 an, um das Adobe Commerce-Problem zu beheben, bei dem eine generische Fehlermeldung in der Benutzeroberfläche angezeigt wird und bei der Erstellung der UPS-Kennzeichnung die Ausnahme für die Konvertierung des Arrays in die Zeichenfolge protokolliert wird. Der Patch stellt sicher, dass der richtige Fehler in der Benutzeroberfläche und in den Protokollen angezeigt wird.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-64546: Allgemeine Fehlermeldung in Benutzeroberfläche und *Array-zu-Zeichenfolge-Konvertierung* Ausnahme bei der Erstellung der UPS-Kennzeichnung

Mit dem Patch ACSD-64546 wird das Problem behoben, dass eine generische Fehlermeldung in der Benutzeroberfläche angezeigt wird und die Ausnahme *Array-in-*-Konvertierung) während der Erstellung der UPS-Kennzeichnung protokolliert wird, um sicherzustellen, dass in der Benutzeroberfläche und den Protokollen der richtige Fehler angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 installiert ist. Die Patch-ID ist ACSD-64546. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

In der Benutzeroberfläche wird eine allgemeine Fehlermeldung angezeigt und die *Array-in-Zeichenfolge-Konvertierung* tritt während der Erstellung der UPS-Kennzeichnung auf.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Kundenkonto mit einer gültigen Adresse.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]** und fügen Sie eine gültige Adresse hinzu.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]** und fügen Sie eine gültige Adresse hinzu.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]** und konfigurieren Sie UPS.
1. Bestellen Sie mit [!UICONTROL UPS].
1. Entfernen Sie die UPS-Benutzer-ID und das Kennwort aus der `core_config_data` in der Datenbank.
1. Konfigurationscache leeren.
1. Öffnen Sie die erstellte Bestellung im **[!UICONTROL Admin]**.
1. Erstellen Sie eine neue Sendung.
   1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Create Shipping Label]** .
   1. Klicken Sie auf **[!UICONTROL Submit shipment]**.
   1. Fügen Sie das Produkt zu einem Paket hinzu. Geben Sie die Paketgröße (Länge, Breite und Höhe) an.
   1. Klicken Sie auf **[!UICONTROL Save]**.

<u>Erwartete Ergebnisse</u>:

Die tatsächliche Fehlermeldung wird in der Benutzeroberfläche und in den Protokollen angezeigt.

<u>Tatsächliche Ergebnisse</u>:

* Der folgende Fehler wird in der Benutzeroberfläche angezeigt:
  *Fehler beim Erstellen des Versandtitels.*
* Die Ausnahme *Konvertierung von Array in*) verhindert, dass die tatsächliche Fehlermeldung angezeigt oder in den Protokollen gespeichert wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:
* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: Upgrades und Patches > Anwenden von Patches im Handbuch zu Commerce in Cloud-Infrastruktur .

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:
* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
