---
title: "ACSD-60584: Das Zugriffstoken, das für eine Website erstellt wurde, darf auf Informationen auf anderen Websites zugreifen."
description: Wenden Sie den Patch ACSD-60584 an, um das Problem zu beheben, dass das Zugriffstoken, das für den Benutzer auf einer Website erstellt wurde, den Zugriff auf oder die Änderung von Kundeninformationen auf anderen Websites erlaubt.
feature: Customers, GraphQL
role: Admin, Developer
source-git-commit: eba4a8fd7bbf52fbc4295feab0d5bb79e7383b66
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584: Das Zugriffstoken, das für eine Website erstellt wurde, erlaubt den Zugriff auf Informationen auf anderen Websites

Der Patch ACSD-60584 behebt das Problem, dass das Zugriffstoken, das für den Benutzer auf einer Website erstellt wurde, den Zugriff auf oder die Änderung von Kundeninformationen auf anderen Websites erlaubt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.53 installiert ist. Die Patch-ID ist ACSD-60584. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Mit dem API-Token, das für den Benutzer auf einer Website erstellt wurde, können Sie auf Kundeninformationen zugreifen, einen Warenkorb erstellen und Produkte in anderen Website-Ansichten zum Warenkorb hinzufügen.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass **[!DNL Share Customer Accounts configuration]** auf **[!UICONTROL Per Website]** gesetzt ist.
1. Erstellen Sie zusätzliche *Website*, *Store* und *storeview*.
1. Erstellen Sie zwei Kunden mit derselben E-Mail auf der Haupt-*Website* und der *Website* aus dem vorherigen Schritt.
1. Generieren Sie ein Kunden-Token über [!DNL GraphQL] auf der Haupt-Website.
1. Senden Sie mit dem generierten Token eine Kunden-Abfrage mit der zweiten Website in der Kopfzeile, um Kundeninformationen abzurufen.**[!DNL GraphQL]**
1. Beobachten Sie das zurückgegebene Ergebnis.

<u>Erwartete Ergebnisse</u>:

Kundeninformationen von der Haupt- *Website* werden zurückgegeben, da das Token von der Haupt- *Website* in der [!DNL GraphQL]-Abfrage verwendet wird.

<u>Tatsächliche Ergebnisse</u>:

Kundeninformationen von der zweiten Website werden zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
