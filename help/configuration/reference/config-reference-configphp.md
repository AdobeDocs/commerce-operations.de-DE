---
title: config.php-Referenz
description: Eine Liste der Werte finden Sie in der Datei config.php .
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# config.php-Referenz

Die `config.php` -Datei enthält die folgenden Abschnitte:

| Name | Beschreibung |
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

Weitere Informationen [Module].

## Bereiche

Enthält ein Array von Bereichskonfigurationswerten. Sie weist die folgenden Unterknoten auf:

| Name | Beschreibung |
| ---------- | -----------------------------------|
| `websites` | Website-Konfiguration |
| `groups` | Speicherkonfiguration |
| `stores` | Konfiguration von Ansichten speichern |

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

Weitere Informationen [Commerce-Bereiche][scopes].

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

## themes

Enthält ein Array von Werten für die Designkonfiguration.

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

Weitere Informationen [Designs].

<!-- link definitions -->

[Module]: https://devdocs.magento.com/videos/fundamentals/create-a-new-module/
[scopes]: https://docs.magento.com/user-guide/configuration/scope.html
[Designs]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/theme-create.html
