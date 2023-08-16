---
title: Leistungs-Benchmarks
description: Überprüfen Sie die Performance-Benchmark-Ergebnisse für Adobe Commerce-Implementierungen, die auf der Adobe-Cloud-Infrastruktur gehostet werden.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# Benchmark-Zusammenfassung

Die Leistungs-Benchmark-Ergebnisse von Adobe Commerce 2.4.5 spiegeln die Leistung wider, die auf einer Adobe Commerce-Instanz gemessen wird, die mit der folgenden Infrastruktur und zusätzlichen Komponenten bereitgestellt wird.
- [Pro Cloud-Umgebung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) mit [skalierte Architektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B für Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

Es gibt keine weiteren Anpassungen.

Die folgenden Informationen fassen die Benchmark-Ergebnisse zusammen und liefern Informationen über die Umgebung und die während des Tests verwendeten Daten.

## Wichtige Leistungsmetriken

Die folgende Abbildung zeigt die Commerce-Store-Konfiguration für den Leistungs-Benchmark und die wichtigsten Leistungsmetriken aus den Testergebnissen.

![Performance Benchmark JMeter und Produktionsinfrastruktur](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

Basierend auf Testkriterien, die eine B2C-Organisation eines Unternehmens imitieren, kann das System angeforderte Traffic- und Bestellzahlen während Spitzenzeiten bei einem Standardlastfluss verarbeiten.

### Leistungsmerkmale

- **Bestellungen**—Es wurden 3.481 Bestellungen pro Minute verarbeitet, wobei die Antwortzeiten für das 99. Perzentil weniger als 2 Sekunden betragen (99 % der Anfragen wurden mit einer Antwortzeit von weniger als 2 Sekunden bearbeitet).
- **Seitenansichten**—Es wurden über 2 Millionen Seitenansichten pro Stunde verarbeitet, während die Antwortzeiten für das 99. Perzentil weniger als 2 Sekunden blieben.
- **Effektive SKUs**—Das Kundenprofil umfasste 242 Millionen verschiedene Preisvarianten (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKUs</a>) für 250.000 Produkte.
- **GraphQL-Anforderungen**—Das System wurde auf 10.500 nicht zwischengespeicherte Anfragen pro Minute skaliert, wobei die Antwortzeiten für das 99. Perzentil weniger als 2 Sekunden betragen.
- **Gleichzeitige Administratoren**—Das System wurde skaliert, um 500 gleichzeitige Admin-Benutzer zu unterstützen, während die Antwortzeiten für das 99. Perzentil weniger als 2 Sekunden betragen.

## Testumgebung

Leistungs-Benchmark-Ergebnisse wurden durch Tests mit einer Adobe Commerce 2.4.5-Instanz erzielt, die in einer Pro-Cloud-Umgebung mit skalierter Architektur bereitgestellt wurde. Für die Instanz wurden auch die Adobe Commerce-Integrationsmodule B2B, Inventory management und Adobe Stock installiert, konfiguriert und aktiviert.

Leistungstestdaten für das Testprofil wurden mit der <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Leistungs-Toolkit</a>.

Leistungsmessungen basieren auf simulierten täglichen Store-Aktivitäten für Kunden und Geschäftsbenutzer. Die Werte spiegeln für jeden Fall einen nahezu maximalen Durchsatz wider, spiegeln jedoch keine einzigartigen Geschäftsmodelle wie private Verkäufe oder Flash-Verkäufe wider.

- **LUMA-Storefront**
   - 3000 gleichzeitige Benutzer auf der Storefront
   - Auf CDN-Cache-Trefferrate von 30 % festlegen

     Die effektive Nutzung der Cache-Ebene erhöht die Anzahl der Seitenansichten pro Stunde.

- **GraphQL-API**
   - 250 gleichzeitige Threads
   - Setzen Sie die CDN-Cache-Trefferrate auf 0 %

     Die Reaktionszeiten werden durch eine Zwischenspeicherschicht vor GraphQL erheblich verbessert.

- **Admin Web**
   - 500 gleichzeitige Benutzer
   - Setzen Sie die CDN-Cache-Trefferrate auf 0 %

## Spezifikationen der Testumgebung

Der Lasttest wurde mit JMeter-Lastprofilen abgeschlossen, die für die Adobe Commerce-Instanz ausgeführt wurden. Während des Tests wurden drei Webknoten und drei Dienstknoten verwendet. Die folgende Abbildung zeigt den Einstiegspunkt der JMeter- und Produktionsinfrastruktur.

![Performance Benchmark JMeter und Produktionsinfrastruktur](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Anwendung

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> wird in der Cloud-Infrastruktur mit Pro-Architektur bereitgestellt.

### Infrastruktur

Für den Performance-Benchmark wurde Adobe Commerce 2.4.5 auf einer [skalierbare Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) mit der folgenden Kapazität.

- **Webknotenspezifikationen**
   - vCPU 216 (72 x 3 Knoten)
   - Speicher 432 GiB (144 x 3 Knoten)
   - Netzwerkbandbreite 768 Gbit/s (256 x 3 Knoten)
   - EBS-Bandbreite 57000 MBit/s (19000 x 3 Knoten)
   - Bereitgestellter Speicher - 100 GB

- **Dienstknotenspezifikationen**
   - vCPU 192 (64 x 3 Knoten)
   - Speicher 768 GiB (256 x 3 Knoten)
   - Netzwerkbandbreite 60 Gbit/s (20 x 3 Knoten)
   - EBS-Bandbreite 40800 MBit/s (13600 x 3 Knoten)
   - Bereitgestellter Speicher 1100 GB
