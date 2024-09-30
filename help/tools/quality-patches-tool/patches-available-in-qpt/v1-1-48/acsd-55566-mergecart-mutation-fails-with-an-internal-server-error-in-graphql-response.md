---
title: '''ACSD-55566: [!UICONTROL mergeCart] Mutation schlägt mit internem Server-Fehler in der  [!DNL GraphQL] Antwort fehl'
description: Wenden Sie den Patch ACSD-55566 an, um das Adobe Commerce-Problem zu beheben, bei dem die Mutation "mergeCart"mit einem internen Serverfehler in der Antwort [!DNL GraphQL] fehlschlägt, wenn die Quelle und der Zielcart, die dieselben Bundle-Elemente aufweisen, zusammengeführt werden.
feature: GraphQL, Shopping Cart
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-55566: `mergeCart` Mutation schlägt mit internem Server-Fehler in [!DNL GraphQL] Antwort fehl

Der Patch ACSD-55566 behebt das Problem, bei dem die `mergeCart`-Mutation mit einem internen Server-Fehler in der [!DNL GraphQL]-Antwort fehlschlägt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 installiert ist. Die Patch-ID ist ACSD-55566. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`mergeCart` Mutation schlägt mit einem internen Server-Fehler in der [!DNL GraphQL] -Antwort fehl, wenn die Quelle und der Ziel-Warenkorb, die dieselben Bundle-Elemente aufweisen, zusammengeführt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine benutzerdefinierte Quelle und ein benutzerdefiniertes Lager.
1. Weisen Sie den erstellten Bestand der Haupt-Website zu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie ihm die erstellte Quelle zu (qty=2).
1. Erstellen Sie ein Bundle-Produkt mit einer Option und einem untergeordneten Produkt (Produkt erstellt in Schritt 3).
1. Erstellen Sie einen Warenkorb mit [!DNL GraphQL].
1. Fügen Sie ein Bundle-Produkt mit beiden ausgewählten Optionen hinzu.
1. Speichern Sie die *cartID*.
1. Erstellen Sie einen Kunden und generieren Sie ein Kunden-Token.
1. Erstellen Sie einen Warenkorb.
1. Fügen Sie dasselbe Paket-Produkt mit derselben Konfiguration zum Warenkorb hinzu.
1. Versuchen Sie, den Warenkorb mit dem Warenkorb des Kunden zusammenzuführen.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb enthält Produkte aus beiden Warenkorb.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten einen internen Fehler.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
