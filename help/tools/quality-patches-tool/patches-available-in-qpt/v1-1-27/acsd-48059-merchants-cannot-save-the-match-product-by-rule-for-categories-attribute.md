---
title: 'ACSD-48059: Händler können [!UICONTROL Match product by rule] nicht für das Kategorienattribut speichern.'
description: Wenden Sie den Patch ACSD-48059 an, um das Adobe Commerce-Problem zu beheben, bei dem Händler die [!UICONTROL Match product by rule] für das Kategorienattribut nicht speichern können.
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
exl-id: e156a752-81b3-4404-81e2-af7ed29f2b1d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-48059: Händler können den *[!UICONTROL Match product by rule]* für das Kategorienattribut nicht speichern

Der Patch ACSD-48059 behebt das Problem, dass Händler die *[!UICONTROL Match product by rule]* für das categories-Attribut in [!DNL Visual Merchandiser] nicht speichern können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID ist ACSD-48059. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Händler können das Attribut *[!UICONTROL Match product by rule]* für Kategorien nicht in [!DNL Visual Merchandiser] speichern.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]** und fügen Sie Kategorien hinzu.
1. Navigieren Sie zu Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
   * Wechseln Sie zum Abschnitt &quot;[!UICONTROL Products in Category]&quot;.
   * Fügen Sie eine neue *[!UICONTROL Match products by rule]* -Bedingung mit dem Kategorienattribut hinzu.

<u>Erwartete Ergebnisse</u>:

Die Kategorie wurde erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

* Sie können die Kategorie nicht mit der neuen Regel und Bedingung speichern.
* *Beim Speichern des Kategorie* -Fehlers ist etwas schiefgelaufen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
