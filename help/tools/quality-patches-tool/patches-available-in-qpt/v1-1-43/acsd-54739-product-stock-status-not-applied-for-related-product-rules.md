---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* Status wurde nicht für *[!UICONTROL Related Product Rules]* angewendet'
description: Wenden Sie den Patch ACSD-54739 an, um das Adobe Commerce-Problem zu beheben, bei dem der Status *[!UICONTROL Product Stock]* nicht für *[!UICONTROL Related Product Rules]* angewendet wird.
feature: Products
role: Admin, Developer
exl-id: d6d3b25d-b10e-4ccb-a9c4-b5c1c7773eb6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-54739: *[!UICONTROL Product stock]* Status wird nicht auf *[!UICONTROL Related Product Rules]* angewendet

Der Patch ACSD-54739 behebt das Problem, bei dem der Status *[!UICONTROL Product stock]* nicht für *[!UICONTROL Related Product Rules]* angewendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-54739. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Status *[!UICONTROL Product stock]* wird nicht auf *[!UICONTROL Related Product Rules]* angewendet.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie die **[!UICONTROL Display Out of Stock Products]** -Konfiguration auf *Ja* ein.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** und legen Sie *Ja* für die Bedingung der Angebotsregel fest.
1. Erstellen Sie die zugehörige Produktregel. Gehen Sie zu **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Fügen Sie eine Bedingung mit der Attributmenge hinzu (wählen Sie auf Lager/nicht vorrätig aus).
1. Überprüfen Sie die Produkte am Frontend.

<u>Erwartete Ergebnisse</u>:

Das Produkt &quot;Vorrätig/nicht vorrätig&quot;entspricht *[!UICONTROL Related Product Rules]*.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt auf Lager/nicht vorrätig stimmt nicht mit dem Wert *[!UICONTROL Related Product Rules]* überein.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
