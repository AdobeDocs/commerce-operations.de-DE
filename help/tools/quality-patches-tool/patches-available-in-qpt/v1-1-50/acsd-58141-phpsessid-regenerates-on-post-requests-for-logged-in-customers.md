---
title: "ACSD-58141: PHPSESSID wird bei POST-Anforderungen für angemeldete Kunden mit aktiviertem L2 Redis-Cache neu generiert."
description: Wenden Sie den Patch ACSD-58141 an, um das Adobe Commerce-Problem zu beheben, bei dem "PHPSESSID"bei POST-Anforderungen im Storefront-Bereich für einen angemeldeten Kunden mit L2 Redis-Cache neu generiert und der Kunde von Admin aktualisiert wird.
feature: Customers, Cache
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# ACSD-58141: PHPSESSID wird bei [!DNL POST] -Anforderungen für angemeldete Kunden neu generiert, wenn der L2 Redis-Cache aktiviert ist

Der Patch ACSD-58141 behebt das Problem, bei dem `PHPSESSID` für [!DNL POST] -Anforderungen eines angemeldeten Kunden neu generiert, wenn der L2 Redis-Cache aktiviert ist und der Kunde von Admin aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID lautet ACSD-58141. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce- und Magento Open Source-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`PHPSESSID` wird bei [!DNL POST] -Anforderungen für einen angemeldeten Kunden neu generiert, wobei der L2 Redis-Cache aktiviert ist.

<u>Voraussetzungen</u>

Die Umgebung muss mit Redis mit mindestens 3 Knoten konfiguriert werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie einen Kunden und melden Sie sich bei der Storefront an.
1. Überprüfen Sie den Wert von `PHPSESSID`.
1. Senden Sie einige [!DNL POST] -Anforderungen (z. B. das Hinzufügen eines Produkts zum Warenkorb) und stellen Sie sicher, dass `PHPSESSID` gleich bleibt.)
1. Melden Sie sich beim Bedienfeld **[!UICONTROL Admin]** an und ändern Sie den Vornamen des Kunden.
1. Wenn der Vorname gespeichert wird, ändern Sie ihn und speichern Sie ihn einige Male erneut.
1. Senden Sie im Storefront eine [!DNL POST] -Anfrage. `PHPSESSID` hätte aktualisiert werden sollen.
1. Senden Sie eine weitere [!DNL POST] -Anfrage an die Storefront und aktivieren Sie `PHPSESSID`.
1. Wiederholen Sie den vorherigen Schritt einige Male.

<u>Erwartete Ergebnisse</u>

`PHPSESSID` wird nur einmal nach Änderung der Kundendaten neu generiert.

<u>Tatsächliche Ergebnisse</u>:

`PHPSESSID` wird jedes Mal neu generiert, wenn die [!DNL POST] -Anfragen gesendet werden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
