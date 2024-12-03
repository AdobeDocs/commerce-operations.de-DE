---
title: 'ACSD-51890: [!UICONTROL Submit review] -Schaltfläche kann mehrmals angeklickt werden'
description: Wenden Sie den Patch ACSD-51890 an, um das Adobe Commerce-Problem zu beheben, bei dem die Schaltfläche [!UICONTROL Submit Review] mehrmals ohne Validierung von  [!DNL Google reCAPTCHA v3] angeklickt werden kann.
feature: Products
role: Admin
exl-id: db69ccdc-c66e-4bdb-9783-772f2af0d33f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51890: **[!UICONTROL Submit Review]** -Schaltfläche kann mehrmals ohne **[!DNL Google reCAPTCHA v3]** Validierung angeklickt werden

>[!NOTE]
>
>Dieser Patch wird durch [ACSD-55112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md) ersetzt.

Der Patch ACSD-51890 behebt das Problem, dass die Schaltfläche **[!UICONTROL Submit Review]** mehrmals ohne Validierung von **[!DNL Google reCAPTCHA v3]** angeklickt werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51890. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Schaltfläche **[!UICONTROL Submit Review]** kann mehrmals ohne die Validierung **[!DNL Google reCAPTCHA v3]** angeklickt werden.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **[!DNL Google reCAPTCHA v3]** für die Produktüberprüfung.
1. Öffnen Sie die Produktseite, navigieren Sie zum Abschnitt &quot;**[!UICONTROL Review]**&quot; und stellen Sie sicher, dass der Abschnitt &quot;[!DNL reCAPTCHA]&quot;sichtbar ist.
1. Füllen Sie das Überprüfungsformular aus und klicken Sie so schnell wie möglich mehrmals auf die Schaltfläche **[!UICONTROL Submit Review]** .
1. Öffnen Sie den Abschnitt &quot;**[!UICONTROL Review]**&quot;über &quot;Admin&quot;.

<u>Erwartete Ergebnisse</u>

Doppelte Überprüfungen werden nicht erstellt.

<u>Tatsächliche Ergebnisse</u>

Es werden doppelte Überprüfungen erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](</help/tools/quality-patches-tool/usage.md>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
