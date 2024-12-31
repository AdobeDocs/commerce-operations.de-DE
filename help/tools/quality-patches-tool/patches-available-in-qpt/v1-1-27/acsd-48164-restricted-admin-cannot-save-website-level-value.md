---
title: 'ACSD-48164: Der eingeschränkte Administrator kann den Wert auf Website-Ebene nicht speichern'
description: Wenden Sie den Patch „ACSD-48164“ an, um das Adobe Commerce-Problem zu beheben, bei dem ein Admin mit Zugriffsbeschränkungen einen Wert auf Website-Ebene nicht speichern kann.
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48164: Der eingeschränkte Administrator kann den Wert auf Website-Ebene nicht speichern

Mit dem Patch „ACSD-48164“ wird das Problem behoben, dass ein eingeschränkter Administrator einen Wert auf Website-Ebene nicht speichern kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID ist ACSD-48164. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein eingeschränkter Administrator kann einen Wert auf Website-Ebene nicht speichern.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Website-, Store- und Store-Ansicht in [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Erstellen Sie eine neue Administratorrolle unter [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Gehen Sie zu **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, wählen Sie die neue Website aus und weisen Sie diese Rolle einem beliebigen Administrator zu.

1. Wählen Sie ein Produkt aus und weisen Sie nur die neue Website zu. Wählen Sie nicht die Standard-Website aus.
1. Melden Sie sich als in Schritt 2 zugewiesener Administrator an und bearbeiten Sie das Produkt unter **[!UICONTROL All Store View]** Umfang, indem Sie beliebige Attribute auf Website-Ebene wie *[!UICONTROL Status]*, *[!UICONTROL Tax Class]* ändern und das Produkt als neu festlegen.
1. Speichern Sie das Produkt.

<u>Erwartete Ergebnisse</u>:

Ein Admin-Benutzer, der mit dem Rollenbereich auf einer Website verknüpft ist, kann Produktattribute auf Website-Ebene mithilfe des *[!UICONTROL All Store View]* speichern.

<u>Tatsächliche Ergebnisse</u>:

Die Erfolgsmeldung, dass das Produkt gespeichert wurde, wird angezeigt, aber die Produktattributwerte bleiben unverändert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
