---
title: Best Practices für die Konfiguration des Redis-Dienstes
description: Erfahren Sie, wie Sie die Zwischenspeicherleistung verbessern können, indem Sie die erweiterte Redis-Cache-Implementierung für Adobe Commerce 2.3.5 verwenden.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# Best Practices für die Konfiguration des Redis-Dienstes

- Für Adobe Commerce 2.3.3 und höher, die in der Cloud-Infrastruktur bereitgestellt werden, aktualisieren Sie auf Redis Version 5.0.
- Verwenden Sie für Adobe Commerce Version 2.3.5 oder höher die erweiterte Redis-Cache-Implementierung. Diese Implementierung umfasst die folgenden Optimierungen, um die Anzahl der Redis-Abfragen zu minimieren, die für jede Adobe Commerce-Anfrage ausgeführt werden:
   - Reduzierung der Netzwerkdatenübertragung zwischen Redis und Adobe Commerce
   - Geringerer Verbrauch von CPU-Zyklen durch Verbesserung der Fähigkeit des Adapters, automatisch zu bestimmen, was geladen werden muss
   - Race-Bedingungen bei Redis-Schreibvorgängen reduzieren

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur mit Version 2.3.3 oder neuer.
Adobe Commerce (alle Bereitstellungsmethoden), Version 2.3.5 und höher

## Aktualisieren der Redis-Version für Cloud-Bereitstellungen

Für Adobe Commerce-Implementierungen in Cloud-Infrastrukturen mit Adobe Commerce 2.3.3 oder höher aktualisieren Sie den Redis-Dienst auf Redis Version 5.0. Anweisungen finden Sie in den folgenden Themen in der Dokumentation zur Cloud-Infrastruktur in Adobe Commerce:

- [Redis-Dienst einrichten](https://devdocs.magento.com/cloud/project/services-redis.html)
- [Dienstversion ändern](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## Erweiterte Redis-Cache-Implementierung konfigurieren

Aktualisieren Sie Ihre Konfiguration für Adobe Commerce 2.3.5 und höher, um die erweiterte Redis-Cache-Implementierung zu verwenden. `\Magento\Framework\Cache\Backend\Redis`.

### Konfiguration für Cloud-Bereitstellungen

Mit `ece-tools` 2002.1.1 oder höher, konfigurieren Sie den erweiterten Redis-Cache, indem Sie die `REDIS_BACKEND` Bereitstellungsvariable in der Umgebungskonfigurationsdatei, `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Weitere Informationen finden Sie unter [Bereitstellen von Variablen > `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) in der Dokumentation für Adobe Commerce zur Cloud-Infrastruktur.

>[!NOTE]
>
> Überprüfen Sie die in Ihrer lokalen Cloud-Umgebung installierte Version der ece-Tools über die Befehlszeile mit dem `composer show magento/ece-tools` Befehl. Falls erforderlich, [Aktualisieren der ece-tools-Version](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

### Konfiguration für lokale Bereitstellungen

Für lokale Adobe Commerce-Bereitstellungen konfigurieren Sie die neue Redis-Cache-Implementierung mit dem `bin/magento:setup` Befehle. Anweisungen finden Sie unter [Verwenden von Redizes für den Standard-Cache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Zusätzliche Informationen

- [Adobe Commerce-Version 2.3.5 - Leistungssteigerungen](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)


