---
title: 'ACSD-53704: Bilanz der Belohnungspunkte nach Ablauf falsch berechnet'
description: Wenden Sie den ACSD-53704 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem der Saldoverlauf der Prämienpunkte nach dem Ablaufdatum der Prämienpunkte falsch berechnet wird.
feature: Rewards
role: Admin, Developer
exl-id: 8cd297cc-9e9d-4615-b817-283065a79c2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-53704: Bilanz der Belohnungspunkte nach Ablauf falsch berechnet

Mit dem Patch ACSD-53704 wird das Problem behoben, dass der Belohnungspunktverlauf nach dem Ablaufdatum der Belohnungspunkte falsch berechnet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 installiert ist. Die Patch-ID ist ACSD-53704. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Belohnungspunktebilanz wird nach dem Ablaufdatum der Belohnungspunkte falsch berechnet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Kunden in der Storefront.
1. Fügen Sie Prämienpunkte für Kunden mit unterschiedlichen Ablaufdaten hinzu.
1. Überprüfen Sie die `magento_reward_history` Tabelle und legen Sie das Ablaufdatum für den neuesten Eintrag von Belohnungspunkten auf ein früheres Datum fest:

   ```
   UPDATE magento_reward_history SET expired_at_static = '2023-08-24 10:47:38' WHERE history_id = 3;
   ```

1. Überprüfen Sie das Raster Belohnungshistorie unter **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit customer]** > **[!UICONTROL Reward points]** > **[!UICONTROL Reward Points History]** und **[!UICONTROL Reward Points Balance]**.

<u>Erwartete Ergebnisse</u>:

Die Prämienpunktebilanz zeigt nur die nicht abgelaufenen Punkte an.

<u>Tatsächliche Ergebnisse</u>:

Der Punktestand spiegelt den Betrag wider, der die abgelaufenen Punkte enthält.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > &#x200B;](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
