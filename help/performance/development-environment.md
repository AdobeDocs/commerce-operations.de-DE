---
title: Entwicklungsumgebung - Recommendations
description: Erfahren Sie mehr über Leistungsempfehlungen zum Einrichten Ihrer lokalen Adobe Commerce-Entwicklungsumgebung.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Empfehlungen zur Entwicklungsumgebung

Diese Seite enthält Empfehlungen für Commerce-Entwicklungsumgebungen.

## Entfernen Sie die Zwischenspeicher, anstatt sie zu deaktivieren.

Viele Entwickler neigen dazu, alle Caches auf ihren Entwicklerinstanzen zu deaktivieren. Es wird empfohlen, nur Caches zu reinigen, ohne alle Caches zu deaktivieren. [!DNL Commerce] wird effizienter ausgeführt, wenn Sie [die Caches bereinigen](../configuration/cli/manage-cache.md#clean-and-flush-cache-types), anstatt sie vollständig zu deaktivieren. Die meisten Arten von Caches werden während der Entwicklung selten invalidiert.

Wenn Sie [die Caches deaktivieren](../configuration/cli/manage-cache.md#enable-or-disable-cache-types), wird empfohlen, die Caches von Seiten und Blöcken nur in Entwicklungsinstanzen zu deaktivieren. Denken Sie daran, alle Caches während des Tests zu aktivieren.

## Im Entwicklungsmodus zu vermeidende Befehle

Führen Sie im Entwicklungsmodus keine Befehle zur Kompilierung, Codegenerierung und statischen Inhaltsbereitstellung aus. Diese Befehle wurden nur für die Verwendung im Produktionsmodus erstellt.

**Führen Sie keine** Produktionsbefehle im Entwicklungsmodus aus:

* `setup:di:compile` generiert automatisch generierte Klassen und optimierte Konfigurations-Caches.

  ```bash
  bin/magento setup:di:compile
  ```

  Im Entwicklungsmodus führt Magento die Generierung On-Demand durch. Sie müssen sie nicht ausführen. Wenn Sie eine Signatur einer Klasse geändert haben und ihre automatisch generierte `factories/proxies/interceptors` neu generieren müssen, entfernen Sie diese Klassen oder den Ordner _generated_ .

* `setup:static-content:deploy` stellt statischen Inhalt für einen Store bereit.

  ```bash
  bin/magento setup:static-content:deploy
  ```

  Im Entwicklungsmodus führt Magento ihn bei Bedarf aus, Sie müssen ihn nicht ausführen.

## Normale Seitenladezeit auf einem virtuellen Computer

Wenn Sie auf einer VM entwickeln und das Laden einer Magento-Seite länger als 2 Sekunden dauert, überprüfen Sie Ihre Umgebungseinstellungen.
