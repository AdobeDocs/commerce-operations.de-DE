---
title: 'ACSD-55628: Datei wird auf dem Unternehmensregistrierungsformular hochgeladen; Datei für Kundenattribut in Storefront wird ersetzt'
description: Wenden Sie den Patch ACSD-55628 an, um das Problem zu beheben, dass Adobe Commerce eine -Datei in das Unternehmensregistrierungsformular hochlädt und eine -Datei durch ein Kundenattribut in der Storefront ersetzt.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: a008a205-ec1d-4a1d-9cd2-75f10a937057
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-55628: Datei wird auf dem Unternehmensregistrierungsformular hochgeladen; Datei für Kundenattribut in Storefront wird ersetzt

>[!NOTE]
>
>Dieser Patch ersetzt [ACSD-51240](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

Mit dem Patch ACSD-55628 wird das Problem behoben, dass eine Datei auf das Unternehmensregistrierungsformular hochgeladen und eine Datei durch ein Kundenattribut in der Storefront ersetzt wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-55628. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2 &lt; 2.4.5 und 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Datei für ein Kundenattribut in der Storefront kann nicht ersetzt werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein neues Kundenattribut mit den folgenden Werten:

   * *[!UICONTROL Input Type]*: *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*: *Ja*
   * *[!UICONTROL Forms to Use In]*: *Alle verfügbaren Optionen*

1. Melden Sie sich als Kunde an der Storefront an und öffnen Sie **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**.
1. Ein neues Bild hochladen und speichern.
1. Aktualisieren Sie die Seite. Löschen Sie das alte Bild und laden Sie ein neues hoch. Speichern Sie die Änderungen.

<u>Erwartete Ergebnisse</u>:

Das neue Bild wird gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Das alte Bild wird weiterhin angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
