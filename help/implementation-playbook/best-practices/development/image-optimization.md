---
title: Optimieren von Bildern für eine reaktionsschnellere Site
description: Erfahren Sie, wie Sie Bilder optimieren und die Reaktionszeit auf Ihren Adobe Commerce-Sites mit Fastly Image Optimization optimieren können.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# Optimieren von Bildern für eine reaktionsschnellere Site

Verbessern Sie bei Adobe Commerce in Cloud-Infrastrukturbereitstellungen die Reaktionszeit der Site, indem Sie Bilder optimieren, bevor Sie sie hochladen. Verwenden Sie dann Fastly Image Optimization, um die Bildbereitstellung zu beschleunigen und die Wartung von Bildquellensätzen zu vereinfachen.

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

Adobe Commerce auf Cloud-Infrastruktur


## Bilder optimieren und komprimieren

Optimieren und komprimieren Sie Bilder vor dem Hochladen auf Ihre Commerce-Sites, um Leistung und Anzeigequalität miteinander in Einklang zu bringen. Dies erhöht den Speicherplatz und reduziert die Seitenladezeiten.

- Das PNG-Format liefert kleinere Bilder für Bilder mit großen einfarbigen Bereichen.

- Das JPEG-Format liefert kleinere Bilder für alle anderen Bildtypen. Verwenden Sie die höchste Komprimierung (ohne merkliche Beeinträchtigung). Das sind normalerweise 60 bis 80 Prozent.

## Schnelle Bildoptimierung aktivieren und konfigurieren

Nachdem Sie den Fastly-Service für Ihr Adobe Commerce-Cloud-Projekt eingerichtet haben, finden Sie unter [Fastly-](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization)) Anweisungen zum Aktivieren und Konfigurieren der Bildoptimierung.

## Weitere Informationen

- [Schnell einrichten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration)
- [Schlecht optimierte Bilder können zu Leistungsproblemen führen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
