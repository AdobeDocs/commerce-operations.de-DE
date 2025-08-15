---
title: Best Practices für die Berichtskonfiguration
description: Optimieren Sie die Site-Leistung, indem Sie das Reporting-Modul entfernen, wenn Sie es nicht verwenden.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# Best Practices für die Berichtskonfiguration

Wenn Ihr Unternehmen keine Reporting- oder dynamischen Kundensegmentfunktionen benötigt, deaktivieren Sie die [Reporting-Funktionen](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/reports) um die Store-Leistung zu verbessern.

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

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
