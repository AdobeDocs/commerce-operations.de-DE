---
title: Leistungsoptimierung
description: Erfahren Sie mehr über die Leistungsoptimierung und die Schritte, die zur Leistungsüberprüfung Ihrer Adobe Commerce-Implementierung durchgeführt werden müssen.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Leistungsoptimierung

Leistung ist ein großes Thema. Wenn Benutzer eine langsame oder nicht responsive Site erleben, wirkt sich dies auf die Konversion aus. Es wird empfohlen, die folgenden Schritte auszuführen, um die Leistung Ihres Adobe Commerce bei der Implementierung der Cloud-Infrastruktur zu optimieren:

- Bewertung des Problems
- Leistung messen
- Identifizieren Sie Teile des Systems, die für die Leistungsverbesserung wichtig sind.
- Systemteil ändern, um den Engpass zu entfernen
- Messen Sie die Leistung nach der Änderung.
- Nehmen Sie sie gegebenenfalls an oder setzen Sie sie zurück.

## Typische Leistungsprobleme

Die Auswirkungen eines langsamen Erlebnisses werden in der Regel durch zwei Indikatoren bestimmt, und jeder Faktor kann aus Gründen von Tonnen verursacht werden.

High Time-to-First-Byte (TTFB) wird normalerweise als Indikator betrachtet, der die Reaktionsgeschwindigkeit des Servers definiert. Die Zeit wird nicht nur durch die Ausführung des Quellcodes für die Bearbeitung der Anfrage verursacht, sondern kann auch durch die folgenden Faktoren beeinflusst werden:

- DNS-Suche
- Langsame Abfragen von der DB-Ebene
- CPU-Zeit der einzelnen Anwendungsschichten
- Speicherbegrenzung
- Die E/A-Wartezeit kann sich auf das Lesen und Schreiben von Dateien auswirken und den Verbindungsdienst über Sockets verbinden
- Softwareeinstellungen (nginx, PHP, MySQL, Redis, Varnish)
- Netzwerkbandbreite
- Ungültige Zwischenspeicherung
- Unangemessener Code
- Schlechter Integrationsansatz
- Abhängigkeit der langsamen Antwort des Drittanbieterdienstes
- Architektur ohne Skalierbarkeit

Ressourcen mit langsamem Laden werden normalerweise als Indikator betrachtet, der die statische Ressource definiert (CSS, JavaScript, Bilder, Videos, Ajax-Aufrufantwort von Drittanbietern).

Adobe Commerce kann mit seinen Funktionen skaliert werden:

![Abbildung der skalierbaren Funktionen von Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

Es gibt auch wichtige Faktoren, die den Maßstab im Handel antreiben, was sich auch auf die Gesamtleistung auswirkt.

- Komplexer und großer Produktkatalog
- Eine große Anzahl von Administratoren
- Globale Storefronts
- Traffic mit hoher Variablen
- Erweitern von Touchpoints
- Transaktionen mit hohem Volumen

Für skalierbare, übereinander liegende Architekturen können Sie dieses Diagramm als Referenz verwenden.

![Abbildung der Verwendung der Adobe Commerce GraphQL-API in einer zwischenspeicherbaren Architektur](../../../assets/playbooks/cacheable-architecture.svg)
