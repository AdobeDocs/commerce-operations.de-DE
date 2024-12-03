---
title: 'ACSD-48634: [!DNL JS] Fehler bei aktiviertem [!DNL Google Analytics Content Experiments] '
description: Wenden Sie den Patch ACSD-48634 an, um [!DNL JS] Fehler auf einer [!DNL staging] Aktualisierungsseite zu beheben, wenn  [!DNL Google Analytics Content Experiments] aktiviert ist.
feature: Catalog Management, Categories, Console, Page Content
role: Admin
exl-id: 99368346-157f-4283-bb8c-192a62501717
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48634: [!DNL JS] Fehler bei aktiviertem [!DNL Google Analytics Content Experiments]

Der Patch ACSD-48634 behebt [!DNL JS]-Fehler auf einer [!DNL staging] Aktualisierungsseite, wenn [!DNL Google Analytics Content Experiments] aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID lautet ACSD-48634. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

[!DNL JS] -Fehler treten auf einer [!DNL staging] -Aktualisierungsseite auf, wenn [!DNL Google Analytics Content Experiments] aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** eine zusätzliche Website, einen weiteren Store und **[!UICONTROL Store View]**. Stellen Sie sicher, dass der **[!UICONTROL Store View]** *[!UICONTROL Enabled]* ist.
1. Konfigurieren Sie **[!DNL Configure Google Analytics]**, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** gehen:
   * Für **[!DNL Main]** und zusätzliche Websites [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
      * **[!DNL Uncheck]** *[!UICONTROL Use Default]* für andere Felder, aber ändern Sie sie nicht.
   * Für **[!DNL Default Config]** [!DNL scope]:
      * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Deaktivieren Sie **[!DNL Configure Google Analytics]** für **[!DNL Default Config]** [!DNL scope], indem Sie **[!UICONTROL Enable]** von *[!UICONTROL Yes]* auf *[!UICONTROL No]* ändern. Achten Sie darauf, nichts anderes zu ändern!
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Erstellen und bearbeiten Sie beliebige **[!UICONTROL category]** und fügen Sie eine geplante Aktualisierung hinzu:
   * Jeder Name, jedes Anfangsdatum in der Zukunft, jedes Enddatum in der Zukunft und jede Änderung in **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Speichern Sie die Aktualisierung und überprüfen Sie die [!DNL browser developer console] auf Fehler.

<u>Erwartete Ergebnisse</u>:

Keine [!DNL JS] -Fehler und Änderungen am [!DNL staging] -Update werden erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

[!DNL JS] -Fehler werden in der Konsole angezeigt, das Formular ist fehlerhaft und die [!DNL spinner] werden nach dem Speichern nie deaktiviert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
