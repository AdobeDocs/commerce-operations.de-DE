---
title: Best Practices zum Konfigurieren von Sites, Stores und Store-Ansichten
description: Erfahren Sie Best Practices zum Konfigurieren von Sites, Stores und Store-Ansichten, um die Site-Leistung zu maximieren.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Best Practices zum Konfigurieren von Sites, Stores und Store-Ansichten

Um eine optimale Site-Leistung zu erzielen, konfigurieren Sie maximal 50 Sites, 50 Stores und 50 Store-Ansichten für Adobe Commerce in Cloud-Infrastrukturprojekten.

>[!NOTE]
>
>Für Adobe Commerce on Cloud Infrastructure gelten die Best Practices speziell für die Produktionsumgebung (und möglicherweise für die Staging on Pro-Architektur, die Ressourcenbeschränkungen unterliegt), die über mehr Ressourcen verfügen als die Integrations- und Entwicklungsumgebungen. Für die Integration (Pro- und Starter-Umgebung) und Staging-Umgebungen (Starter) reduzieren Sie die Anzahl der Store-Ansichten auf weniger als 5 oder 10 (vorbehaltlich einer technischen Überprüfung).

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Strategien zur Leistungsverbesserung

Wenn für Ihr Projekt viele Sites, Stores oder Store-Ansichten erforderlich sind, können Sie die folgenden Strategien zur Leistungsverbesserung verwenden:

- Neustrukturierung des Katalogs durch Verlagerung der Logik in Kategorien
- Trennen Sie Preislisten von Katalogdaten durch externe Preise und ein Preismanagementsystem (PMS).
- Verwenden Sie einen alternativen noSQL-Datenspeicher wie Elasticsearch

## Mögliche Leistungseinbußen

Websites und Stores sind Multiplikatoren für Katalogdaten, sodass viele Websites und Stores die Site-Leistung auf folgende Weise beeinträchtigen können:

- Größere Indextabellen erhöhen die Zeit, die zum Ausführen von Indizierungsvorgängen erforderlich ist [Preisindex].
- Die längere Zeit zum Abrufen der Anwendungskonfiguration verringert die Wartezeit für die Storefront-Antwort für nicht zwischengespeicherte Katalogseiten.
- Die zum Abschluss von Speichervorgängen im Admin erforderliche Zeit nimmt erheblich zu, da die Daten für jede Website separat gespeichert werden.


## Zusätzliche Informationen

- [Grundlegendes zu Websites, Geschäften und Store-Ansichten](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Einrichten mehrerer Websites oder Stores](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
