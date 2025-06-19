---
title: 'ACSD-48773: E-Mail-Vorlage für Belohnungspunkte aus dem falschen Store'
description: Wenden Sie den ACSD-48773 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die E-Mail-Vorlage für Belohnungspunkte aus dem falschen Store abgerufen wird.
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
exl-id: db8b6196-3e13-4c1b-8ae8-040487180817
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-48773: E-Mail-Vorlage für Belohnungspunkte aus dem falschen Store

Mit dem Patch ACSD-48773 wird das Problem behoben, dass die E-Mail-Vorlage für Belohnungspunkte aus dem falschen Store abgerufen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48773. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Neuindizierung des Produktpreises funktioniert nicht, wenn das Produktpaket keiner Website zugewiesen ist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Websites, zwei Stores und zwei Store-Ansichten.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** und aktivieren Sie **[!UICONTROL Reviews]**.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**.
Wechseln Sie zur **[!DNL default website scope]** und legen Sie die **[!UICONTROL Customer Support Sender Email]** fest (z. B.: *support_base@example.com*).
Wechseln Sie zur **[!DNL second website scope]** und setzen Sie die **[!UICONTROL Customer Support Sender Email]** auf einen anderen Wert (z. B.: *support_second@example.com*).
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]** und setzen Sie **[!UICONTROL Share Customer Accounts]** = *pro Website*.
1. Legen Sie unter **[!UICONTROL Reward Points]** Folgendes fest:
   **[!UICONTROL Enable Reward Points Functionality]** = *Ja*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *Ja*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** and set **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** und **[!UICONTROL Email Sender]** = *Support*
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** und legen Sie die Wechselkurse für die zweite Website sowohl für **[!UICONTROL Points/Currency]** als auch für **[!UICONTROL Currency/Points]** fest.
1. Erstellen Sie auf der zweiten Website ein Kundenkonto.
1. Melden Sie sich auf der zweiten Website als Kunde an.
1. Stellen Sie sicher, dass Sie **[!UICONTROL Subscribe]** für **[!UICONTROL Balance Updates]** aktivieren.
1. Reichen Sie eine Produktbewertung ein.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**.
1. Ändern Sie den Status der neuen Überprüfung in ***[!UICONTROL Approved]*** und **[!UICONTROL Save]**.
1. Warten Sie, bis die E-Mail eintrifft.

<u>Erwartete Ergebnisse</u>:

Die E-Mail zur Aktualisierung der Belohnungspunkte sollte von dem E-Mail-Absender gesendet worden sein, der im zweiten Website-Bereich konfiguriert wurde.

<u>Tatsächliche Ergebnisse</u>:

Die Aktualisierungs-E-Mail für Belohnungspunkte wurde von dem E-Mail-Absender gesendet, der im Standard-Website-Umfang konfiguriert ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
