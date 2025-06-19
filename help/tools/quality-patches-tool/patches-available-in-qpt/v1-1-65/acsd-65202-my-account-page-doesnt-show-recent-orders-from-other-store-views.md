---
title: 'ACSD-65202: Auf der Seite Mein Konto werden keine aktuellen Bestellungen aus anderen Store-Ansichten angezeigt'
description: Wenden Sie den Patch ACSD-65202 an, um das Adobe Commerce-Problem zu beheben, bei dem auf der Seite Mein Konto keine aktuellen Bestellungen aus anderen Store-Ansichten innerhalb desselben Stores angezeigt werden.
feature: Orders, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: 031f12f2-1b70-4cbc-92a0-8eb561e34067
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-65202: Auf [!UICONTROL My Account] Seite werden keine aktuellen Bestellungen aus anderen Store-Ansichten angezeigt

Mit dem Patch ACSD-65202 wird das Problem behoben, dass auf der Seite **[!UICONTROL My Account]** keine aktuellen Bestellungen aus anderen Store-Ansichten innerhalb desselben Stores angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 installiert ist. Die Patch-ID ist ACSD-65202. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p12

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Sie die Seite „Kundenkonto“ aufrufen (Abschnitt **[!UICONTROL My Account]**), sehen Sie keine aktuellen Bestellungen, die in einer anderen Shop-Ansicht aufgegeben wurden. Wenn Sie jedoch zum Bestellverlauf (Abschnitt *[!UICONTROL My Orders]*) wechseln, sehen Sie alle Bestellungen in beiden Store-Ansichten.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce.
1. Erstellen Sie im *Admin*-Bedienfeld eine neue Store-Ansicht und geben Sie deren Code als *second* ein, um die Ansicht zu identifizieren.
1. Erstellen Sie ein einfaches Produkt und indizieren Sie es neu.
1. Erstellen Sie ein Kundenkonto und geben Sie eine Bestellung in der standardmäßigen Store-Ansicht auf, deren Code &quot;*&quot;*.
1. Gehen Sie zur Seite **[!UICONTROL My Orders]** und überprüfen Sie, ob die Reihenfolge in beiden Store-Ansichten sichtbar ist, z. B.:
1. Standard: https://localhost/pub/default/sales/order/history/
1. Zweitens: https://localhost/pub/second/sales/order/history/

1. Navigieren Sie in beiden Store-Ansichten zur Seite **[!UICONTROL My Account]** :
1. Standard: https://localhost/pub/default/customer/account/
1. Zweitens: https://localhost/pub/second/customer/account/

<u>Erwartete Ergebnisse</u>:

Auf der Seite Bestellungen können Sie Bestellungen aus beiden Store-Ansichten sehen. Es ist derselbe Laden, nur eine andere Shop-Ansicht.

<u>Tatsächliche Ergebnisse</u>:

Das Verhalten ist inkonsistent. Bestellungen werden nicht in der zweiten Shop-Ansicht angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
