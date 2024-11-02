---
title: Bilder für eine reaktionsfähigere Site optimieren
description: Erfahren Sie mehr über die Schritte zur Bildoptimierung und zur Verwendung der Fastly-Bildoptimierung zur Optimierung der Reaktionszeit auf Ihren Adobe Commerce-Sites.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# Bilder für eine reaktionsfähigere Site optimieren

Für Adobe Commerce in Cloud-Infrastrukturbereitstellungen sollten Sie die Reaktionszeit der Site verbessern, indem Sie Bilder optimieren, bevor Sie sie hochladen. Verwenden Sie dann die Fastly-Bildoptimierung, um die Bildbereitstellung zu beschleunigen und die Wartung von Bildquellensätzen zu vereinfachen.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

Adobe Commerce auf Cloud-Infrastruktur


## Bilder optimieren und komprimieren

Optimieren und komprimieren Sie Bilder, bevor Sie sie auf Ihre Commerce-Sites hochladen, um ein Gleichgewicht zwischen Leistung und Anzeigequalität herzustellen. Dadurch wird der Speicherplatz erhöht und die Seitenladezeiten verkürzt.

- Das PNG-Format liefert Bilder mit kleinerer Größe für Bilder mit großen einfarbigen Bereichen.

- Das JPEG-Format liefert kleinere Bilder für alle anderen Bildtypen. Verwenden Sie die höchste Komprimierung (ohne spürbaren Abbau). Das sind in der Regel 60 bis 80 Prozent.

## Fastly-Bildoptimierung aktivieren und konfigurieren

Nachdem Sie den Fastly-Dienst für Ihr Adobe Commerce Cloud-Projekt eingerichtet haben, finden Sie unter [Fastly image optimization](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization) Anweisungen zum Aktivieren und Konfigurieren der Bildoptimierung.

## Weitere Informationen

- [Schnelles Einrichten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration)
- [Schlecht optimierte Bilder können Leistungsprobleme verursachen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
