---
title: 'ACSD-51792: Seite hat kein Impressionsereignis'
description: Wenden Sie den Patch ACSD-51792 an, um das Adobe Commerce-Leistungsproblem zu beheben, bei dem eine Seite nicht über das Impressionsereignis verfügt, wenn Google Tag Manager 4 aktiviert ist.
exl-id: f9465a44-2c65-4af0-b949-1fe1f4a942ae
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-51792: Seite hat kein Impressionsereignis

Der Patch ACSD-51792 behebt das Leistungsproblem, bei dem eine Seite nicht über das Impressionsereignis verfügt, wenn [!DNL Google Tag Manager] 4 aktiviert ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51792. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Seite weist nicht das Impressionsereignis auf, wenn [!DNL Google Tag Manager] 4 aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**.
1. Konfigurieren Sie die **[!DNL GoogleTag Manager]** -Integration.
1. Wechseln Sie zu [Google Tag Assistant](https://tagassistant.google.com/) und führen Sie die Schritte aus, die für die Verbindung mit Ihrer Website erforderlich sind.
1. Öffnen Sie eine Kategorieseite mit einer Produktliste auf der Storefront.
1. Suchen Sie im Tag Assistant-Beobachter nach dem Impressions-Ereignis.

<u>Erwartete Ergebnisse</u>:

Das Impressionsereignis sollte mit allen Produkten auf der Seite beginnen.

<u>Tatsächliche Ergebnisse</u>:

Die Seite weist im Tag-Assistenten-Beobachter kein Impressionsereignis auf.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
