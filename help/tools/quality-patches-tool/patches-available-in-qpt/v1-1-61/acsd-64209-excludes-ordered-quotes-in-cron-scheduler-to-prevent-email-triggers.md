---
title: 'ACSD-64209: Cron Scheduler ruft verhandelbare Anführungszeichen ab, ohne [!UICONTROL Ordered] Anführungszeichen auszuschließen'
description: Wenden Sie den Patch ACSD-64209 an, um das Adobe Commerce-Problem zu beheben, bei dem der Cron-Scheduler alle verhandelbaren Anführungszeichen abruft, ohne diejenigen mit dem Status [!UICONTROL Ordered] auszuschließen, wodurch eine E-Mail oder E-Mails ausgelöst werden.
feature:  B2B, Communications
role: Admin, Developer
exl-id: 51ba0edc-ad0c-4e32-acd7-2337a62bff53
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209: Cron Scheduler ruft verhandelbare Anführungszeichen ab, ohne [!UICONTROL Ordered] Anführungszeichen auszuschließen

Der Patch von ACSD-64209 behebt das Problem, dass der Cron-Scheduler alle verhandelbaren Anführungszeichen abruft, ohne diejenigen mit dem Status **[!UICONTROL Ordered]** auszuschließen, wodurch eine E-Mail oder E-Mails ausgelöst werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 installiert ist. Die Patch-ID ist ACSD-64209. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Cron-Scheduler ruft alle verhandelbaren Anführungszeichen ab, ohne diejenigen mit dem Status **[!UICONTROL Ordered]** auszuschließen, wodurch eine E-Mail oder E-Mails ausgelöst werden.

<u>Schritte zur Reproduktion</u>:


1. Navigieren Sie in der *Admin*-Seitenleiste zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** und aktivieren Sie „Unternehmens- und B2B-Angebot“.
1. **[!UICONTROL Default Expiration Period]** auf *1* in *Admin* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]**.
1. Erstellen Sie eine Firma, aktivieren Sie sie und melden Sie sich als Unternehmensadministrator an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Angebot anfordern.
1. Navigieren Sie in der *Admin*-Seitenleiste zu **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Wählen Sie das erstellte Angebot aus und klicken Sie auf **[!UICONTROL Send]** , um das Angebot an den Käufer zurückzusenden.
1. Melden Sie sich als Unternehmensadministrator in der Storefront an.
1. Wählen Sie das Angebot aus und klicken Sie auf **[!UICONTROL Proceed to checkout]** , um den Kauf abzuschließen.
1. Vergewissern Sie sich, dass der Status des Angebots **[!UICONTROL Ordered]** ist und keine weiteren Aktionen in der Storefront möglich sind.
1. Trigger des `negotiable_quote_send_emails` Cron-Auftrags.


<u>Erwartete Ergebnisse</u>:

Da das Angebot bestellt wurde und keine weiteren Aktionen durchgeführt werden können, sollten keine E-Mails über den Ablauf des Angebots gesendet werden.

<u>Tatsächliche Ergebnisse</u>:

Eine E *Mail (Angebot läuft bald ab* wird gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
