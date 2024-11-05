---
title: "ACSD-53704: Bilanzverlauf der Treuepunkte nach Ablauf falsch berechnet"
description: Wenden Sie den Patch ACSD-53704 an, um das Adobe Commerce-Problem zu beheben, bei dem der Bilanzverlauf der Punkte nach dem Ablaufdatum der Bonuspunkte falsch berechnet wird.
feature: Rewards
role: Admin, Developer
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-53704: Saldoverlauf der Punkte wurde nach Ablauf falsch berechnet

Der Patch ACSD-53704 behebt das Problem, bei dem der Bilanzverlauf der Punkte nach dem Ablaufdatum der Bonuspunkte falsch berechnet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.39 installiert ist. Die Patch-ID ist ACSD-53704. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Verlauf des Guthabenbilds wird nach dem Ablaufdatum der Bonuspunkte falsch berechnet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Kunden in der Storefront.
1. Fügen Sie Belohnungspunkte für den Kunden mit unterschiedlichen Ablaufdaten hinzu.
1. Überprüfen Sie die Tabelle `magento_reward_history` und legen Sie das Ablaufdatum für den neuesten Datensatz mit Belohnungspunkten auf ein vergangenes Datum fest:

   ```
   UPDATE magento_reward_history SET expired_at_static = '2023-08-24 10:47:38' WHERE history_id = 3;
   ```

1. Überprüfen Sie das Belohnungsverlaufsraster in **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit customer]** > **[!UICONTROL Reward points]** > **[!UICONTROL Reward Points History]** und **[!UICONTROL Reward Points Balance]**.

<u>Erwartete Ergebnisse</u>:

Der Saldo der belohnten Punkte zeigt nur die nicht abgelaufenen Punkte an.

<u>Tatsächliche Ergebnisse</u>:

Der Saldo der belohnten Punkte spiegelt den Betrag wider, der die abgelaufenen Punkte enthält.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool]-Handbuch, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
