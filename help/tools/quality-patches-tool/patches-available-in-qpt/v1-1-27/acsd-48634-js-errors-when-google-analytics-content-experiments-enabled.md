---
title: 'ACSD-48634: [!DNL JS] errors, wenn [!DNL Google Analytics Content Experiments] aktiviert'
description: Wenden Sie den ACSD-48634 Patch an, um  [!DNL JS]  Fehler auf einer  [!DNL staging]  zu beheben, wenn  [!DNL Google Analytics Content Experiments]  aktiviert ist.
feature: Catalog Management, Categories, Console, Page Content
role: Admin
exl-id: 99368346-157f-4283-bb8c-192a62501717
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48634: Bei aktiviertem [!DNL Google Analytics Content Experiments] werden Fehler [!DNL JS]

Der Patch ACSD-48634 behebt [!DNL JS] Fehler auf einer [!DNL staging] Aktualisierungsseite, wenn [!DNL Google Analytics Content Experiments] aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID ist ACSD-48634. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL JS] Fehler treten auf einer [!DNL staging] Update-Seite auf, wenn [!DNL Google Analytics Content Experiments] aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie unter **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** eine zusätzliche Website, einen zusätzlichen Store und eine zusätzliche **[!UICONTROL Store View]**. Stellen Sie sicher, dass die **[!UICONTROL Store View]** *[!UICONTROL Enabled]* ist.
1. Konfigurieren Sie **[!DNL Configure Google Analytics]** über **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Für **[!DNL Main]** und weitere Websites [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** für andere Felder *[!UICONTROL Use Default]*, sie jedoch nicht ändern.
   * Für **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Deaktivieren Sie **[!DNL Configure Google Analytics]** auf **[!DNL Default Config]** [!DNL scope], indem Sie **[!UICONTROL Enable]** von *[!UICONTROL Yes]* auf *[!UICONTROL No]* ändern. Achten Sie darauf, nichts anderes zu ändern!
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Erstellen und bearbeiten Sie alle **[!UICONTROL category]** und fügen Sie eine geplante Aktualisierung hinzu:
   * Beliebiger Name, Startdatum in der Zukunft, Enddatum in der Zukunft und jede Änderung der **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Speichern Sie die Aktualisierung und überprüfen Sie die [!DNL browser developer console] auf Fehler.

<u>Erwartete Ergebnisse</u>:

Es wurden keine [!DNL JS] Fehler und die Änderungen am [!DNL staging] Update erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

[!DNL JS] Fehler sind in der Konsole sichtbar, das Formular ist fehlerhaft und die [!DNL spinner] wird nach dem Speichern nie deaktiviert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
