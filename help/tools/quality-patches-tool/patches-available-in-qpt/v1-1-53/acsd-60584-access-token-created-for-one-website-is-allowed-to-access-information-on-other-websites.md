---
title: 'ACSD-60584: Ein für eine Website erstelltes Zugriffstoken darf auf Informationen auf anderen Websites zugreifen'
description: Wenden Sie den Patch ACSD-60584 an, um das Problem zu beheben, dass das für den Benutzer auf einer Website erstellte Zugriffstoken auf Kundeninformationen auf anderen Websites zugreifen oder diese ändern darf.
feature: Customers, GraphQL
role: Admin, Developer
exl-id: ea30ba92-4b7b-44f9-a1b1-97946061d9e6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584: Ein für eine Website erstelltes Zugriffstoken darf auf Informationen auf anderen Websites zugreifen

Mit dem Patch ACSD-60584 wird das Problem behoben, dass das für den Benutzer auf einer Website erstellte Zugriffstoken auf Kundeninformationen auf anderen Websites zugreifen oder diese ändern darf. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) 1.1.53 installiert ist. Die Patch-ID ist ACSD-60584. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das für den Benutzer auf einer Website erstellte API-Token ermöglicht es Ihnen, auf Kundeninformationen zuzugreifen, einen Warenkorb zu erstellen und Produkte auf anderen Website-Ansichten zum Warenkorb hinzuzufügen.

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie sicher, dass **[!DNL Share Customer Accounts configuration]** auf **[!UICONTROL Per Website]** eingestellt ist.
1. Erstellen Sie zusätzliche *Website*, *store* und *storeview*.
1. Erstellen Sie zwei Kunden mit derselben E-Mail auf der Haupt *Website* und der *Website* aus dem vorherigen Schritt.
1. Generieren Sie ein Kunden-Token über [!DNL GraphQL] auf der Haupt-Website.
1. Senden Sie unter Verwendung des generierten Tokens eine **[!DNL GraphQL]** mit der zweiten Website in der Kopfzeile, um Kundeninformationen abzurufen.
1. Beobachten Sie das zurückgegebene Ergebnis.

<u>Erwartete Ergebnisse</u>:

Kundeninformationen von der Haupt *Website* werden zurückgegeben, da das Token von der Haupt-*Website* in [!DNL GraphQL] Abfrage verwendet wird.

<u>Tatsächliche Ergebnisse</u>:

Kundeninformationen von der zweiten Website werden zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
