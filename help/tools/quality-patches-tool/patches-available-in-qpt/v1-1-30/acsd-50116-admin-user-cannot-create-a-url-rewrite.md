---
title: 'ACSD-50116: Ein Administrator kann keine URL-Umschreibung für die Unterkategorien der Ebene drei oder niedriger erstellen'
description: Wenden Sie den Patch ACSD-50116 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Administrator bzw. eine Administratorin keine URL-Umschreibung für die Unterkategorien der Ebene drei oder niedriger erstellen kann.
feature: Admin Workspace, Categories
role: Admin
exl-id: b2a248eb-a6c4-4596-acac-04a52c5c2a61
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-50116: Ein Administrator kann keine URL-Umschreibung für die Unterkategorien der Ebene drei oder niedriger erstellen

Mit dem Patch ACSD-50116 wird das Problem behoben, dass ein Admin-Benutzer keine URL-Umschreibung für die Unterkategorien der Ebene drei oder niedriger erstellen kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-50116. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Administrator bzw. eine Administratorin kann keine URL-Umschreibung für die Unterkategorien der Ebene drei oder niedriger erstellen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Kategoriestruktur mit mehr als drei Ebenen für Unterkategorien.
1. Versuchen Sie, eine *[!UICONTROL URL Rewrite]* für die Kategorie Ebene vier mit den Optionen *[!UICONTROL For Product]* und *[!UICONTROL For Category]* zu erstellen.

<u>Erwartete Ergebnisse</u>:

Der Kategoriestruktur zeigt die Unterkategorien bis Ebene vier oder darunter an.

<u>Tatsächliche Ergebnisse</u>:

Die Kategoriestruktur zeigt nur bis zu drei Unterkategorien der Ebene an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
