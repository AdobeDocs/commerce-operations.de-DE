---
title: Best Practices für die Berichtskonfiguration
description: Optimieren Sie die Site-Leistung, indem Sie das Berichtsmodul entfernen, wenn Sie es nicht verwenden.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# Best Practices für die Berichtskonfiguration

Wenn Ihr Unternehmen keine Reporting- oder dynamische Kundensegmentfunktionalität benötigt, deaktivieren Sie die Funktion [Berichte](https://docs.magento.com/user-guide/configuration/general/reports.html) , um die Store-Leistung zu verbessern.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Reporting deaktivieren

Wenn Sie die Berichte oder dynamischen Kundensegmente nicht verwenden, deaktivieren Sie die Funktion Berichte .

1. Navigieren Sie vom Administrator zu **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Berichte**.
1. Legen Sie unter **Allgemeine Optionen** **Berichte aktivieren** auf *Nein* fest.
1. Leeren Sie den Cache, indem Sie `php bin/magento cache:flush` oder im Admin unter **System** > **Tools** > **Cache-Verwaltung** ausführen.

## Weitere Informationen

- [Erstellen von Berichten in Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Dynamische Kundensegmente](https://docs.magento.com/user-guide/marketing/customer-segments.html)
