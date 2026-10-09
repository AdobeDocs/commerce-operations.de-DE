---
title: Best Practices für die Berichtskonfiguration
description: Optimieren Sie die Site-Leistung, indem Sie das Reporting-Modul entfernen, wenn Sie es nicht verwenden.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%
---
# Best Practices für die Berichtskonfiguration

Wenn Ihr Unternehmen keine Reporting- oder dynamischen Kundensegmentfunktionen benötigt, deaktivieren Sie die [Reporting-Funktionen](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/reports) um die Store-Leistung zu verbessern.

## Betroffene Produkte und Versionen

[Alle unterstützten &#x200B;](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Berichterstellung deaktivieren

Wenn Sie die Berichte oder dynamischen Kundensegmente nicht verwenden, deaktivieren Sie die Funktion Berichte .

1. Navigieren Sie vom Administrator aus zu **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Berichte**.
1. Legen **unter &quot;**&quot; **Berichte aktivieren** auf *Nein* fest.
1. Leeren Sie den Cache, indem Sie `php bin/magento cache:flush` oder im Admin unter **System** > **Tools** > **Cache-Verwaltung** ausführen.

## Weitere Informationen

- [Erstellen von Berichten in Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu)
- [Dynamische Kundensegmente](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)
