---
title: "ACSD-50858: Verbesserte Leistung beim Laden von Bannerinhalten"
description: Wenden Sie den Patch ACSD-50858 an, um das Adobe Commerce-Problem zu beheben, bei dem die Bannerleistung auf der Einkaufswagen-/Checkout-Seite aufgrund übermäßiger DB-Abfragen und erhöhter Seitenladezeit beeinträchtigt wird.
feature: Page Content
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-50858: Verbesserte Leistung beim Laden von Bannerinhalten

Der Patch ACSD-50858 behebt ein Banner-Leistungsproblem auf der Einkaufswagen-/Checkout-Seite: *übermäßige DB-Abfragen und längere Ladezeiten von Seiten*. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.31 installiert ist. Die Patch-ID lautet ACSD-50858. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Bannerleistung wird auf der Warenkorb-/Checkout-Seite aufgrund von *übermäßigen DB-Abfragen und erhöhter Seitenladezeit* beeinträchtigt.

Dieses Problem wurde behoben, indem die Art und Weise, wie Bannerinhalte geladen werden, umgestaltet wurde. Dadurch wurden die Anzahl der DB-Abfragen um 99,99 % und die Seitenladezeit um ca. 99 % reduziert.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin an und erstellen Sie ein einfaches Produkt.
1. Erstellen Sie einen Kunden entweder vom Administrator oder vom Frontend und fügen Sie eine Versandadresse hinzu.
1. Verschieben Sie banners.php in den Ordner `magento_root/pub/` .
1. Generieren Sie Banner mit dem Befehl `php pub/banners.php` . Es werden 10.000 einfache Banner und 1.000 Banner mit Verkaufsregeln generiert.
1. Melden Sie sich beim Kunden an, der zuvor auf der Vorderseite erstellt wurde.
1. Fügen Sie das zuvor erstellte Produkt zum Warenkorb hinzu.
1. Gehen Sie zur Checkout-Seite (Checkout/Warenkorb).
1. Überwachen Sie die Ladezeit der `banner/ajax/load` -Anfrage:

   * Ohne `bin/magento dev:query-log:enable`
   * Mit `bin/magento dev:query-log:enable`

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>Erwartete Ergebnisse</u>:

Verringern Sie die Anzahl der DB-Abfragen für `magento_banner_content` und die Ladezeit der Warenkorb-/Checkout-Seite.

<u>Tatsächliche Ergebnisse</u>:

Erhöhen Sie die Anzahl der DB-Abfragen für `magento_banner_content` und die Ladezeit der Warenkorb-/Checkout-Seite.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Weitere Informationen

<u>banners.php content</u>:

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

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
