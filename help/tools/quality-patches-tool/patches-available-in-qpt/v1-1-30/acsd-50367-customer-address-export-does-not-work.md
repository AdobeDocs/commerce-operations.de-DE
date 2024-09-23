---
title: "ACSD-50367: Export von Kundenadressen funktioniert nicht mit Attribut mit Mehrfachauswahl"
description: Wenden Sie den Patch ACSD-50367 an, um das Adobe Commerce-Problem zu beheben, bei dem der Export von Kundenadressen nicht funktioniert, wenn ein Attribut mit Mehrfachauswahl **"Kundenadresse"** ohne Werte erstellt wird.
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-50367: Export von Kundenadressen funktioniert nicht

Der Patch ACSD-50367 behebt das Problem, dass der Export von Kundenadressen nicht funktioniert, wenn ein Mehrfachauswahlattribut **`Customer Address`** ohne Werte erstellt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-50367. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Export von Kundenadressen funktioniert nicht, wenn ein Mehrfachauswahlattribut **`Customer Address`** ohne Werte erstellt wird.

<u>Voraussetzungen</u>:

Erstellen Sie einen Kunden mit einer Adresse.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Attribut mit Mehrfachauswahl **`Customer Address`** in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** und wählen Sie den Entitätstyp **`Customer Address`** aus.
1. Exportieren Sie die Kundenadressen. Sie werden sehen, dass nichts exportiert wird.
1. Löschen Sie das Attribut mit Mehrfachauswahl **`Customer Address`** und exportieren Sie die Kundenadressen erneut. Dieses Mal wird die CSV-Datei der Adressen generiert.

<u>Erwartete Ergebnisse</u>:

Die Kundenadressen können als CSV-Datei exportiert werden, wenn ein Attribut mit mehreren Auswahlen **`Customer Address`** erstellt wird.

<u>Tatsächliche Ergebnisse</u>:

Die Kundenadressen können nicht als CSV-Datei exportiert werden, wenn ein Attribut mit mehreren Auswahlen **`Customer Address`** erstellt wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
