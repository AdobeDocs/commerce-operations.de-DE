---
title: Bilder für eine reaktionsfähigere Site optimieren
description: Erfahren Sie mehr über die Schritte zur Bildoptimierung und zur Verwendung der Fastly-Bildoptimierung zur Optimierung der Reaktionszeit auf Ihren Adobe Commerce-Sites.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Bilder für eine reaktionsfähigere Site optimieren

Für Adobe Commerce in Cloud-Infrastrukturbereitstellungen sollten Sie die Reaktionszeit der Site verbessern, indem Sie Bilder optimieren, bevor Sie sie hochladen. Verwenden Sie dann die Fastly-Bildoptimierung, um die Bildbereitstellung zu beschleunigen und die Wartung von Bildquellensätzen zu vereinfachen.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

Adobe Commerce auf Cloud-Infrastruktur


## Bilder optimieren und komprimieren

Bevor Sie Bilder auf Ihre Commerce-Sites hochladen, optimieren und komprimieren Sie sie, um die Leistung mit der Anzeigequalität in Einklang zu bringen. Dadurch wird der Speicherplatz erhöht und die Seitenladezeiten verkürzt.

- Das PNG-Format liefert Bilder mit kleinerer Größe für Bilder mit großen einfarbigen Bereichen.

- Das JPEG-Format liefert kleinere Bilder für alle anderen Bildtypen. Verwenden Sie die höchste Komprimierung (ohne spürbaren Abbau). Das sind in der Regel 60 bis 80 Prozent.

## Fastly-Bildoptimierung aktivieren und konfigurieren

Nachdem Sie den Fastly-Dienst für Ihr Adobe Commerce Cloud-Projekt eingerichtet haben, lesen Sie [Schnelle Bildoptimierung](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) für Anweisungen zum Aktivieren und Konfigurieren der Bildoptimierung.

## Zusätzliche Informationen

- [Schnelles Einrichten](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [Schlecht optimierte Bilder können zu Leistungsproblemen führen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
