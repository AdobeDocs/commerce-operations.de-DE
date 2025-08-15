---
title: 'ACSD-64627: Benutzerdefinierte Kundenattribute können nicht in [!UICONTROL Company Structure] gespeichert werden'
description: Wenden Sie den Patch ACSD-64627 an, um das Adobe Commerce-Problem zu beheben, bei dem benutzerdefinierte Kundenattribute beim Hinzufügen oder Bearbeiten von Benutzenden in [!UICONTROL Company Structure] nicht gespeichert werden können.
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-64627: Benutzerdefinierte Kundenattribute können nicht in [!UICONTROL Company Structure] gespeichert werden

Der Patch ACSD-64627 behebt das Problem, dass benutzerdefinierte Kundenattribute beim Hinzufügen oder Bearbeiten von Benutzern auf der **[!UICONTROL Company Structure]** nicht gespeichert werden können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 installiert ist. Die Patch-ID ist ACSD-64627. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.9 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3, 2.4.7-p4, 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p8, 2.4.7-p3, 2.4.7-p4, 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzerdefinierte Kundenattribute werden beim Hinzufügen oder Bearbeiten von Benutzern auf der **[!UICONTROL Company Structure]** nicht gespeichert.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine Adobe Commerce-Instanz mit aktivierten B2B-Funktionen.
1. Erstellen Sie ein neues Kundenattribut mit dem Namen *custom_upload* und der **[!UICONTROL Input Type]** auf *[!UICONTROL File (attachment)]* festgelegt.
1. Erstellen Sie ein weiteres Kundenattribut mit dem Namen *image_attachment*, dessen **[!UICONTROL Input Type]** auf *[!UICONTROL Image File]* festgelegt ist.
1. Legen Sie **[!UICONTROL Show on Storefront]** auf *Ja* fest, damit beide Attribute in der Storefront sichtbar sind. Alle Formulare auswählen:
   * Kundenregistrierung
   * Kundenkonto bearbeiten
   * Admin-Checkout
1. Neue Firma erstellen und aktivieren.
1. Melden Sie sich bei der Storefront als Unternehmensadministrator an.
1. Navigieren Sie zu **[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]** oder **[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**.
1. Klicken Sie auf **[!UICONTROL Add New User]**.
1. Klicken Sie für das Attribut **[!UICONTROL Upload]** custom_upload *auf* .
1. Klicken Sie **[!UICONTROL Select file]** für das Attribut *image_attachment* .

<u>Erwartete Ergebnisse</u>:

Der Datei-Explorer wird für beide Attribute geöffnet. Beim Speichern werden Werte gespeichert und Dateien erfolgreich hochgeladen.

<u>Tatsächliche Ergebnisse</u>:

Schaltflächen reagieren nicht. Es wird kein Datei-Explorer geöffnet oder Daten werden gespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
