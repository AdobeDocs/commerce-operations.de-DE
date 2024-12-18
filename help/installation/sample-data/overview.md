---
title: Übersicht über Beispieldaten
description: Erfahren Sie mehr über die Verwendung von Beispieldaten für Adobe Commerce-Projekte.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Übersicht über Beispieldaten

Beispieldaten bieten eine Storefront, die auf dem Luma-Design basiert und mit Produkten, Kategorien, Kundenregistrierung usw. ausgestattet ist. Es funktioniert wie eine Commerce-Storefront, und Sie können Preise, Inventar und Preisregeln für Werbeaktionen mit dem Admin-Team manipulieren.

>[!NOTE]
>
>Um die Datenbank und verschiedene -Funktionen zu überprüfen und zu analysieren, sollten Sie echte Daten anstelle von Beispieldaten verwenden. Beispieldaten werden als vorgenerierte Speichersimulation entworfen, um Design-Design und grundlegendes Verhalten der Storefront zu demonstrieren. Alle Beispieldatenentitäten werden direkt in die Datenbanktabellen geschrieben, während Beispieldaten installiert werden.

Sie können Beispieldaten entweder vor oder nach der Installation der Commerce-Software installieren. Wenn Sie mit den Beispieldaten fertig sind, können Sie sie entweder entfernen oder neu installieren, wie in [Entfernen von Beispieldatenmodulen oder Aktualisieren von Beispieldaten](remove-or-update.md) beschrieben.

>[!WARNING]
>
>Beispieldaten können nicht deinstalliert werden. Verwenden Sie Beispieldaten nur, um mehr über die Funktionsweise von Adobe Commerce zu erfahren. Vermeiden Sie Entwicklungsarbeiten in einem System, in dem Sie Beispieldaten installiert haben.

Sie können optionale Beispieldaten auf eine der folgenden Arten installieren:

| Installationsmethode | Beschreibung | Erforderliche Qualifikationsstufe |
|--- |--- |--- |
| Verwenden von Composer | [Führen Sie `magento sampledata:deploy` aus, um die `composer.json`](composer-packages.md) der Anwendung zu ändern und Beispieldatenmodule zu aktivieren. | Erfordert Composer-Kenntnisse und Zugriff auf das Commerce-Dateisystem. |
| Klonen von Repositorys | [Klonen Sie das GitHub](git-repositories.md)Repository und das Beispieldaten-Repository und verknüpfen Sie sie dann miteinander. | Nur für mitwirkende Entwickler. Alle anderen sollten eine der oben genannten Methoden verwenden. |
