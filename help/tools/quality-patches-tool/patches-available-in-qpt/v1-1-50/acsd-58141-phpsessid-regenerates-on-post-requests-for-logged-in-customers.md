---
title: 'ACSD-58141: PHPSESSID wird bei POST-Anfragen für angemeldete Kunden mit aktiviertem L2-Redis-Cache neu generiert'
description: Wenden Sie den Patch ACSD-58141 an, um das Adobe Commerce-Problem zu beheben, bei dem „PHPSESSID“ bei POST-Anfragen im Storefront-Bereich für einen angemeldeten Kunden mit aktiviertem L2-Redis-Cache neu generiert und der Kunde von „Admin“ aktualisiert wird.
feature: Customers, Cache
role: Admin, Developer
exl-id: c188c215-204c-489f-8703-4c81ca8703b7
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%
---
# ACSD-58141: PHPSESSID wird bei [!DNL POST]-Anfragen für angemeldete Kunden neu generiert, wenn der L2-Redis-Cache aktiviert ist

Mit dem Patch „ACSD-58141“ wird das Problem behoben, dass `PHPSESSID` bei [!DNL POST] Anfragen für einen angemeldeten Kunden neu generiert, wenn der L2-Redis-Cache aktiviert ist und der Kunde von „Admin“ aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-58141. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce- und Magento Open Source-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
