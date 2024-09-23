---
title: "ACSD-54887: Der Einkaufswagen des Kunden wird gelöscht, nachdem die Kundensitzung abgelaufen ist"
description: Wenden Sie den Patch ACSD-54887 an, um das Adobe Commerce-Problem zu beheben, bei dem der Warenkorb für Kunden gelöscht wird, nachdem die Kundensitzung abgelaufen ist und [!UICONTROL Persistent Shopping Cart] aktiviert ist.
feature: Shopping Cart
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---


# ACSD-54887: Der Einkaufswagen des Kunden wird nach Ablauf der Kundensitzung gelöscht

Der Patch ACSD-54887 behebt das Problem, dass der Warenkorb des Kunden gelöscht wird, nachdem die Kundensitzung abgelaufen ist und [!UICONTROL Persistent Shopping Cart] aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID lautet ACSD-54887. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7 und 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Warenkorb des Kunden wird gelöscht, nachdem die Kundensitzung abgelaufen ist und [!UICONTROL Persistent Shopping Cart] aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie [!UICONTROL Persistent Shopping Cart]. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *Ja*.

   Melden Sie sich mit aktivierter Persistenz an (Hinweis: Sie ist nicht in der Popup-Autorisierung verfügbar, sondern nur auf der direkten Seite [!UICONTROL Sign in] ).

1. Fügen Sie dem Warenkorb ein Produkt hinzu.
1. Gehen Sie zum Checkout und wählen Sie eine Zahlungsmethode aus.
1. Läuft die Sitzung ab (löschen Sie `PHPSESSID`).
1. Aktualisieren Sie die Seite. Beachten Sie, dass das Anführungszeichen sofort in ein Gastangebot konvertiert wird, da bereits eine Zahlungsmethode ausgewählt ist und das Cookie [!UICONTROL Persistent Cart] entfernt wird.
1. Läuft die Sitzung ab (löschen Sie `PHPSESSID`).
1. Aktualisieren Sie die Seite. Stellen Sie sicher, dass der Warenkorb leer ist.
1. Melden Sie sich erneut an.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb enthält das Produkt, wenn Sie sich erneut anmelden.

<u>Tatsächliche Ergebnisse</u>:

Der Warenkorb ist beim erneuten Anmelden leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.

