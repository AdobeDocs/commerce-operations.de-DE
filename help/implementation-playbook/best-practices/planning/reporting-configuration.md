---
title: Best Practices für die Berichtskonfiguration
description: Optimieren Sie die Site-Leistung, indem Sie das Berichtsmodul entfernen, wenn Sie es nicht verwenden.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Best Practices für die Berichtskonfiguration

Wenn Ihr Unternehmen keine Reporting- oder dynamische Kundensegmentfunktionalität benötigt, deaktivieren Sie die [Berichtsfunktionen](https://docs.magento.com/user-guide/configuration/general/reports.html) zur Verbesserung der Store-Leistung.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Reporting deaktivieren

Wenn Sie die Berichte oder dynamischen Kundensegmente nicht verwenden, deaktivieren Sie die Funktion Berichte .

1. Navigieren Sie vom Administrator zu **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Berichte**.
1. under **Allgemeine Optionen**, set **Berichte aktivieren** nach *Nein*.
1. Cache leeren durch Ausführen `php bin/magento cache:flush` oder im Admin unter **System** > **Instrumente** > **Cacheverwaltung**.

## Zusätzliche Informationen

- [Erstellen von Berichten in Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Dynamische Segmente des Kunden](https://docs.magento.com/user-guide/marketing/customer-segments.html)