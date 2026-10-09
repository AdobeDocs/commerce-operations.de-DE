---
title: Optimieren von Bildern für eine reaktionsschnellere Site
description: Erfahren Sie, wie Sie Bilder optimieren und die Reaktionszeit auf Ihren Adobe Commerce-Sites mit Fastly Image Optimization optimieren können.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
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

Nachdem Sie den Fastly-Service für Ihr Adobe Commerce-Cloud-Projekt eingerichtet haben, finden Sie unter [Fastly-](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly-image-optimization)) Anweisungen zum Aktivieren und Konfigurieren der Bildoptimierung.

## Weitere Informationen

- [Schnell einrichten](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)
- [Schlecht optimierte Bilder können zu Leistungsproblemen führen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow)
