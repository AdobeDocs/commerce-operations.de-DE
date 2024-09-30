---
title: "ACSD-51230: Gift-Kartenkonto wird gelöscht"
description: Wenden Sie den Patch ACSD-51230 an, um das Adobe Commerce-Problem zu beheben, bei dem das Konto für die Geschenkkarte gelöscht wird, wenn die teilweise Rückerstattung eines einfachen Produkts aus einer Bestellung verarbeitet wird.
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-51230: Gift-Kartenkonto wird gelöscht

Der Patch ACSD-51230 behebt das Problem, dass das Geschenkkartenkonto gelöscht wird, wenn die teilweise Rückerstattung eines einfachen Produkts aus einer Bestellung verarbeitet wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51230. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Geschenkkartenkonto wird gelöscht, wenn die teilweise Rückerstattung eines einfachen Erzeugnisses aus einer Bestellung verarbeitet wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Bestellung mit einer *Geschenkkarte* und einem *einfachen Produkt* (z. B. *fügen Sie Folgendes hinzu: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (beliebige Zahlungs- und Versandmethoden funktionieren).
1. Rechnungsstellung.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Für die Geschenkkarte wird ein Konto erstellt.
1. Gehen Sie nun zu **[!UICONTROL Order]** und erstellen Sie eine **[!UICONTROL Credit Memo]**.
1. Ändern Sie die Menge für die *Geschenkkarte* in 0 und aktualisieren Sie sie. Dies führt zu einer teilweisen Rückerstattung für das *einfache Produkt*.
1. Klicken Sie auf **[!UICONTROL Refund]**.
1. Aktualisieren Sie nun die **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Das neu erstellte Konto wird gelöscht.

<u>Erwartete Ergebnisse</u>

Das Geschenkgutschein-Konto ist zur Verwendung verfügbar, da die Rückerstattung nicht für die Geschenkkarte erstellt wurde.

<u>Tatsächliche Ergebnisse</u>

Das Geschenkgutschein-Konto wird gelöscht und die Geschenkkarte wird nicht zurückerstattet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
