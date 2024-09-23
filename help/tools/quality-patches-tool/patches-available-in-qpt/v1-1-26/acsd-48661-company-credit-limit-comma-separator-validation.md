---
title: "ACSD-48661: Validierungsproblem für das Unternehmenskreditlimit für ein gemeinsames Trennzeichen"
description: Wenden Sie den Patch ACSD-48661 an, um das Adobe Commerce-Problem zu beheben. Wenn die Firmenkreditbeschränkung größer als 999 ist, verhindert das Kommatrennzeichen die Speicherung des Unternehmens aufgrund eines Validierungsfehlers.
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-48661: Problem mit der Validierung eines Unternehmenskreditlimits für ein gemeinsames Trennzeichen

Der Patch ACSD-48661 behebt das Problem, bei dem das Firmenkreditlimit größer als 999 ist, das Kommatrennzeichen die Speicherung des Unternehmens aufgrund eines Validierungsfehlers verhindert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48661. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn das Firmenkreditlimit größer als 999 ist, verhindert das Kommatrennzeichen, dass das Unternehmen aufgrund eines Validierungsfehlers gespeichert wird.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Unternehmensfunktion unter **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Erstellen Sie ein Unternehmen und fügen Sie auf der Registerkarte **[!UICONTROL Company Credit]** eine Kreditbeschränkung von über 999 hinzu.
1. Speichern Sie das Unternehmen.
1. Bearbeiten Sie das Unternehmen und versuchen Sie erneut, es zu speichern.

<u>Erwartete Ergebnisse</u>:

Sie können das Unternehmen speichern, ohne die Kreditgrenze festzulegen. Komma wird nicht für Eingabefelder für die Beträge und Preise unterstützt.

<u>Tatsächliche Ergebnisse</u>:

Das Unternehmen kann aufgrund eines Validierungsfehlers im Feld *[!UICONTROL Credit Limit]* nicht gespeichert werden. Adobe Commerce fügt für Kreditbeschränkungen automatisch Kommatratoren hinzu, auch wenn das Feld [!UICONTROL Credit Limit] keine Kommas akzeptiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
