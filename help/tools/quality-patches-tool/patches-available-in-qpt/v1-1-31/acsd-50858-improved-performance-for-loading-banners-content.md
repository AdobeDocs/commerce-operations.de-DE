---
title: 'ACSD-50858: Verbesserte Leistung beim Laden des Bannerinhalts'
description: Wenden Sie den ACSD-50858-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Bannerleistung auf der Warenkorb-/Kassenseite aufgrund übermäßiger DB-Abfragen und verlängerter Seitenladezeit beeinträchtigt ist.
feature: Page Content
role: Admin
exl-id: 1b46e51f-70ad-4450-b3a8-173c2e4b7925
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# ACSD-50858: Verbesserte Leistung beim Laden des Bannerinhalts

Der Patch ACSD-50858 behebt ein Leistungsproblem des Banners auf der Warenkorb-/Kaufbestätigungsseite: *Übermäßige DB-Abfragen und verlängerte Seitenladezeit*. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.31 installiert ist. Die Patch-ID ist ACSD-50858. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bannerleistung auf der Warenkorb-/Kassenseite ist aufgrund von (*DB-Abfragen und verlängerter Seitenladezeit)*.

Dieses Problem wurde behoben, indem die Art und Weise, wie Bannerinhalte geladen werden, überarbeitet wurde, wodurch die Anzahl der DB-Abfragen um 99,99 % und die Seitenladezeit um ~99 % reduziert wurde.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Admin an und erstellen Sie ein einfaches Produkt.
1. Erstellen Sie einen Kunden entweder über Admin oder das Frontend und fügen Sie eine Versandadresse hinzu.
1. Verschieben Sie banners.php in den Ordner `magento_root/pub/`.
1. Erzeugen Sie Banner mit dem Befehl `php pub/banners.php` . Es wird 10.000 einfache Banner und 1.000 Banner mit Verkaufsregeln generieren.
1. Melden Sie sich bei dem zuvor im Frontend erstellten Kunden an.
1. Fügen Sie das zuvor erstellte Produkt zum Warenkorb hinzu.
1. Navigieren Sie zur Kasse (Kasse/Warenkorb).
1. Überwachen Sie die Ladezeit der `banner/ajax/load`:

   * Ohne `bin/magento dev:query-log:enable`
   * Mit `bin/magento dev:query-log:enable`

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>Erwartete Ergebnisse</u>:

Verringern der Anzahl von DB-Abfragen für die Ladezeit von `magento_banner_content` und Warenkorb-/Kaufbestätigungsseite.

<u>Tatsächliche Ergebnisse</u>:

Erhöhung der Anzahl der DB-Abfragen für die Ladezeit von `magento_banner_content` und Warenkorb-/Kaufbestätigungsseiten.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Weitere Informationen

<u>banners.php Inhalt</u>:

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
