---
title: 'ACSD-58141: PHPSESSID wird bei POST-Anfragen für angemeldete Kunden mit aktiviertem L2-Redis-Cache neu generiert'
description: Wenden Sie den Patch ACSD-58141 an, um das Adobe Commerce-Problem zu beheben, bei dem „PHPSESSID“ bei Anfragen zur POST im Storefront-Bereich für einen angemeldeten Kunden mit aktiviertem L2-Redis-Cache neu generiert und der Kunde von „Admin“ aktualisiert wird.
feature: Customers, Cache
role: Admin, Developer
exl-id: c188c215-204c-489f-8703-4c81ca8703b7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-58141: PHPSESSID wird bei [!DNL POST]-Anfragen für angemeldete Kunden neu generiert, wenn der L2-Redis-Cache aktiviert ist

Mit dem Patch „ACSD-58141“ wird das Problem behoben, dass `PHPSESSID` bei [!DNL POST] Anfragen für einen angemeldeten Kunden neu generiert, wenn der L2-Redis-Cache aktiviert ist und der Kunde von „Admin“ aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-58141. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce und Magento Open Source-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

`PHPSESSID` regeneriert bei [!DNL POST] Anfragen für einen angemeldeten Kunden mit aktiviertem L2-Redis-Cache.

<u>Voraussetzungen</u>

Die Umgebung muss mit Redis mit mindestens 3 Knoten konfiguriert werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie einen Kunden und melden Sie sich bei der Storefront an.
1. Überprüfen Sie den Wert von `PHPSESSID`.
1. Senden Sie einige [!DNL POST] Anfragen (z. B. zum Hinzufügen eines Produkts zum Warenkorb) und stellen Sie sicher, dass die `PHPSESSID` unverändert bleibt.
1. Melden Sie sich beim **[!UICONTROL Admin]** Panel an und ändern Sie den zweiten Vornamen des Kunden.
1. Wenn der zweite Vorname gespeichert wird, ändern Sie ihn und speichern Sie ihn einige Male erneut.
1. Senden Sie in der Storefront eine [!DNL POST]. `PHPSESSID` sollte aktualisiert worden sein.
1. Senden Sie in der Storefront eine weitere [!DNL POST]-Anfrage und überprüfen Sie `PHPSESSID`.
1. Wiederholen Sie den vorherigen Schritt einige Male.

<u>Erwartete Ergebnisse</u>

`PHPSESSID` wird nur einmal nach Änderung der Kundendaten neu generiert.

<u>Tatsächliche Ergebnisse</u>:

`PHPSESSID` wird jedes Mal neu generiert, wenn die [!DNL POST] gesendet werden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
