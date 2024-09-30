---
title: "ACSD-55628: Datei im Registrierungsformular des Unternehmens hochladen; Datei für Kundenattribut in Storefront ersetzen"
description: Wenden Sie den Patch ACSD-55628 an, um das Adobe Commerce-Problem zu beheben, indem Sie eine Datei auf das Registrierungsformular für das Unternehmen hochladen und eine Datei für ein Kundenattribut auf der Storefront ersetzen.
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-55628: Datei im Registrierungsformular des Unternehmens hochladen; Datei für Kundenattribut in Storefront ersetzen

>[!NOTE]
>
>Dieser Patch ersetzt [ACSD-51240](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md).

Der Patch ACSD-55628 behebt das Problem beim Hochladen einer Datei in das Registrierungsformular des Unternehmens und beim Ersetzen einer Datei für ein Kundenattribut auf der Storefront. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-55628. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2 &lt; 2.4.5 und 2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Datei für ein Kundenattribut auf der Storefront kann nicht ersetzt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Kundenattribut mit den folgenden Werten:

   * *[!UICONTROL Input Type]*: *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*: *Ja*
   * *[!UICONTROL Forms to Use In]*: *alle verfügbaren Optionen*

1. Melden Sie sich als Kunde an der Storefront an und öffnen Sie **[!UICONTROL My Account]** > **[!UICONTROL Account Information]**.
1. Laden Sie ein neues Bild hoch und speichern Sie.
1. Aktualisieren Sie die Seite. Löschen Sie das alte Bild und laden Sie ein neues hoch. Speichern Sie die Änderungen.

<u>Erwartete Ergebnisse</u>:

Das neue Bild wird gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Das alte Bild wird weiterhin angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
