---
title: config.php-Referenz
description: Erfahren Sie mehr über config.php-Dateiwerte und Abschnitte für die Adobe Commerce-Konfiguration. Entdecken Sie Module, Bereiche, Systemeinstellungen und Best Practices für die Bereitstellung.
exl-id: 9b355d6d-ea66-480b-ad96-0ea9e7e61844
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 1%

---

# config.php-Referenz

Die `config.php`-Datei enthält die folgenden Abschnitte:

| -Name | Beschreibung |
| --------- | -------------------|
| `i18n` | Alle Inline-Übersetzungsdaten. Das Lesen aus diesem Abschnitt wird nicht unterstützt. |
| `modules` | Die Liste der aktivierten und deaktivierten Module. |
| `scopes` | Die Liste der Stores, Store-Gruppen und Websites mit zugehörigen Informationen. |
| `system` | Die für die Bereitstellung statischer Inhalte erforderlichen Systemkonfigurationen. |
| `themes` | Die Konfiguration der installierten Designs. |

## Module

Enthält ein Array von Modulen und deren Status. Wenn das Modul aktiviert ist, ist der Wert 1. Andernfalls ist der Wert 0.

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

Weitere Informationen zu [Modulen](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html?lang=de).

## Bereiche

Enthält ein Array von Bereichskonfigurationswerten. Sie weist die folgenden Unterknoten auf:

| -Name | Beschreibung |
| ---------- | -----------------------------------|
| `websites` | Website-Konfiguration |
| `groups` | Speichert die Konfiguration |
| `stores` | Konfiguration der Store-Ansichten |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

Weitere Informationen zu [Commerce-Bereichen](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=de#scope-settings).

## System

Enthält ein Array von Systemfeldkonfigurationswerten.

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

Weitere Informationen [Systemspezifische Konfigurationen](config-reference-sens.md).

## Designs

Enthält ein Array von Werten für die Design-Konfiguration.

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

Weitere Informationen zu [Designs](https://developer.adobe.com/commerce/frontend-core/guide/themes/create-storefront/).

