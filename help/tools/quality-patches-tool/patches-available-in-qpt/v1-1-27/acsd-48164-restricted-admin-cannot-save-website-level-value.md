---
title: 'ACSD-48164: Eingeschränkter Administrator kann Wert auf Website-Ebene nicht speichern'
description: Wenden Sie den Patch ACSD-48164 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Administrator keinen Wert auf Website-Ebene speichern kann.
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48164: Eingeschränkter Administrator kann Wert auf Website-Ebene nicht speichern

Der Patch ACSD-48164 behebt das Problem, dass ein eingeschränkter Administrator keinen Wert auf Website-Ebene speichern kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID lautet ACSD-48164. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eingeschränkte Administratoren können keinen Wert auf Website-Ebene speichern.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website-, Store- und Store-Ansicht unter [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Erstellen Sie eine neue Administratorrolle unter [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Gehen Sie zu **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, wählen Sie die neue Website aus und weisen Sie diese Rolle jedem Administrator zu.

1. Wählen Sie ein beliebiges Produkt aus und weisen Sie nur die neue Website zu. Wählen Sie nicht die Standardwebsite aus.
1. Melden Sie sich als in Schritt 2 zugewiesener Admin-Benutzer an und bearbeiten Sie das Produkt unter dem Bereich **[!UICONTROL All Store View]** , indem Sie ein beliebiges Attribut auf Website-Ebene wie *[!UICONTROL Status]* und *[!UICONTROL Tax Class]* ändern und das Produkt als neu festlegen.
1. Speichern Sie das Produkt.

<u>Erwartete Ergebnisse</u>:

Der mit dem Rollenbereich einer Website verknüpfte Admin-Benutzer kann Produktattribute auf Website-Ebene mithilfe des Bereichs *[!UICONTROL All Store View]* speichern.

<u>Tatsächliche Ergebnisse</u>:

Die Erfolgsmeldung, dass das Produkt gespeichert wurde, wird angezeigt, aber die Produktattributwerte bleiben unverändert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
