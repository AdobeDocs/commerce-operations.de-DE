---
title: 'ACSD-54887: Der Warenkorb des Kunden wird gelöscht, nachdem die Kundensitzung abgelaufen ist'
description: Wenden Sie den Patch ACSD-54887 an, um das Adobe Commerce-Problem zu beheben, bei dem der Warenkorb des Kunden geleert wird, nachdem die Kundensitzung mit aktiviertem [!UICONTROL Persistent Shopping Cart] abgelaufen ist.
feature: Shopping Cart
role: Admin, Developer
exl-id: de2a96b2-48ce-4b9b-93bc-f7b64c37463a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-54887: Der Warenkorb des Kunden wird gelöscht, nachdem die Kundensitzung abgelaufen ist

Mit dem Patch ACSD-54887 wird das Problem behoben, dass der Warenkorb des Kunden geleert wird, nachdem die Kundensitzung mit aktiviertem [!UICONTROL Persistent Shopping Cart] abgelaufen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-54887. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7 und 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Warenkorb des Kunden wird geleert, nachdem die Kundensitzung mit aktiviertem [!UICONTROL Persistent Shopping Cart] abgelaufen ist.

<u>Schritte zur Reproduktion</u>:

1. [!UICONTROL Persistent Shopping Cart] aktivieren. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *Ja*.

   Melden Sie sich mit aktivierter Persistenz an (Hinweis: Sie ist nicht in der Popup-Autorisierung verfügbar, sondern nur auf der Seite „Direkte [!UICONTROL Sign in]„).

1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Wechseln Sie zur Kasse und wählen Sie eine Zahlungsmethode aus.
1. Läuft die Sitzung ab (`PHPSESSID` löschen)
1. Aktualisieren Sie die Seite. Beachten Sie, dass das Angebot sofort in ein Gastangebot konvertiert wird, da bereits eine Zahlungsmethode ausgewählt ist und das [!UICONTROL Persistent Cart]-Cookie entfernt wird.
1. Läuft die Sitzung ab (`PHPSESSID` löschen)
1. Aktualisieren Sie die Seite. Beachten Sie, dass der Warenkorb leer ist.
1. Melden Sie sich erneut an.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb enthält das Produkt, wenn Sie sich erneut anmelden.

<u>Tatsächliche Ergebnisse</u>:

Der Warenkorb ist bei der erneuten Anmeldung leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
