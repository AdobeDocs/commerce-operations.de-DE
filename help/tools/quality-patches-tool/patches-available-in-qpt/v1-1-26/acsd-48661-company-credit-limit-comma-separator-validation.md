---
title: 'ACSD-48661: Problem mit der Überprüfung des Kommatrennzeichens des Firmenkreditlimits'
description: Wenden Sie den Patch ACSD-48661 an, um das Adobe Commerce-Problem zu beheben, bei dem das Firmenkreditlimit größer als 999 ist und das Kommatrennzeichen aufgrund eines Validierungsfehlers das Speichern des Unternehmens verhindert.
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
exl-id: 7115226e-5942-4a8f-9dec-b1b6f665eef8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-48661: Problem mit der Überprüfung des Kommatrennzeichens des Firmenkreditlimits

Mit dem Patch ACSD-48661 wird das Problem behoben, dass das Speichern des Unternehmens aufgrund eines Validierungsfehlers verhindert wird, wenn das Kreditlimit des Unternehmens größer als 999 ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48661. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn das Kreditlimit des Unternehmens größer als 999 ist, verhindert das Kommatrennzeichen, dass das Unternehmen aufgrund eines Validierungsfehlers speichert.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die Unternehmensfunktion unter **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Erstellen Sie ein Unternehmen und fügen Sie auf der Registerkarte **[!UICONTROL Company Credit]** ein Kreditlimit von mehr als 999 hinzu.
1. Rette die Firma.
1. Bearbeiten Sie die Firma und versuchen Sie erneut, sie zu speichern.

<u>Erwartete Ergebnisse</u>:

Sie können die Firma speichern, ohne das Kreditlimit festzulegen. Kommas werden für Eingabefelder für die Beträge und Preise nicht unterstützt.

<u>Tatsächliche Ergebnisse</u>:

Sie können das Unternehmen aufgrund eines Validierungsfehlers im Feld &quot;*[!UICONTROL Credit Limit]*&quot; nicht speichern. Adobe Commerce fügt automatisch Kommatrennzeichen für Kreditlimits hinzu, auch wenn das [!UICONTROL Credit Limit] keine Kommas akzeptiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
