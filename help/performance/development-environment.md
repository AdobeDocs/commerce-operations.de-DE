---
title: Empfehlungen für die Entwicklungsumgebung
description: Erfahren Sie mehr über die Empfehlungen für Entwicklungsumgebungen in Adobe Commerce. Erfahren Sie mehr über Implementierungsanleitungen und Optimierungsstrategien.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '238'
ht-degree: 0%
---
# Empfehlungen für die Entwicklungsumgebung

Diese Seite enthält Empfehlungen für Commerce-Entwicklungsumgebungen.

## Caches bereinigen, statt sie zu deaktivieren

Viele Entwickler neigen dazu, alle Caches in ihren Entwicklerinstanzen zu deaktivieren. Es wird empfohlen, nur Caches zu bereinigen, ohne alle Caches zu deaktivieren. [!DNL Commerce] wird effizienter ausgeführt, wenn Sie [die Caches bereinigen](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) anstatt sie vollständig zu deaktivieren. Die meisten Arten von Caches werden während der Entwicklung nur selten ungültig gemacht.

Wenn Sie [die Caches deaktivieren](../configuration/cli/manage-cache.md#enable-or-disable-cache-types) empfehlen wir nur das Deaktivieren von Seiten- und Blockcaches in Entwicklungsinstanzen. Denken Sie daran, während des Tests alle Caches zu aktivieren.

## Im Entwicklungsmodus zu vermeidende Befehle

Führen Sie im Entwicklungsmodus keine Befehle für die Kompilierung, Codegenerierung und statische Inhaltsbereitstellung aus. Diese Befehle wurden nur für die Verwendung im Produktionsmodus erstellt.

**Produktionsbefehle nicht ausführen** im Entwicklungsmodus:

* `setup:di:compile` generiert automatisch generierte Klassen und optimierte Konfigurationscaches.

  ```shell
  bin/magento setup:di:compile
  ```

  Im Entwicklungsmodus führt Magento die Generierung bei Bedarf durch; Sie müssen sie nicht ausführen. Wenn Sie eine Signatur einer Klasse geändert haben und die automatisch generierte `factories/proxies/interceptors` neu generieren müssen, entfernen Sie diese Klassen oder den _generierten_ Ordner.

* `setup:static-content:deploy` stellt statische Inhalte für einen Store bereit.

  ```shell
  bin/magento setup:static-content:deploy
  ```

  Im Entwicklungsmodus führt Magento sie bei Bedarf aus, Sie müssen sie nicht ausführen.

## Normale Seitenladezeit auf einer virtuellen Maschine

Wenn Sie eine Entwicklung auf einer VM durchführen und das Laden einer Magento-Seite länger als zwei Sekunden dauert, überprüfen Sie die Umgebungseinstellungen.
