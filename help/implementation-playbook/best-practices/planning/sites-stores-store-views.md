---
title: Best Practices für die Konfiguration von Sites, Stores und Store-Ansichten
description: Erfahren Sie mehr über Best Practices für die Konfiguration von Sites, Stores und Store-Ansicht, um die Site-Leistung zu maximieren.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Best Practices für die Konfiguration von Sites, Stores und Store-Ansicht

Bei Adobe Commerce auf Cloud-Infrastrukturen gelten die Best Practices speziell für die Produktionsumgebung (und möglicherweise die Staging- auf Pro-Architektur, je nach Ressourcenbeschränkungen), die mehr Ressourcen hätte als die Integrations- und Entwicklungsumgebungen.

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Strategien zur Leistungsverbesserung

Wenn für Ihr Projekt viele Sites, Stores oder Store-Ansichten erforderlich sind, können Sie die folgenden Strategien verwenden, um die Leistung zu verbessern:

- Katalog durch Verlagerung der Logik auf Kategorien umstrukturieren
- Trennen Sie Preislisten von Katalogdaten mithilfe von externen Preislisten und einem Preismanagementsystem (PMS).
- Verwenden eines alternativen NoSQL-Datenspeichers wie Elasticsearch

## Mögliche Auswirkungen auf die Leistung

Websites und Stores sind Multiplikatoren für Katalogdaten, sodass sich eine große Anzahl von Websites und Stores negativ auf die Site-Leistung auswirken kann:

- Größere Indextabellen erhöhen den Zeitaufwand für den Abschluss von Indizierungsvorgängen [Preisindex].
- Die längere Zeit zum Abrufen der Anwendungskonfiguration verringert die Antwortzeit der Storefront für nicht zwischengespeicherte Katalogseiten.
- Erhebliche Zeiterhöhungen für den Abschluss von Speichervorgängen im Administrator, da die Daten für jede Website separat gespeichert werden.


## Weitere Informationen

- [Grundlegendes zu Websites, Stores und Store-Ansichten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Einrichten mehrerer Websites oder Stores](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)
