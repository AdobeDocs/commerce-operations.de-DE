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

Beispieldaten bieten eine Storefront basierend auf dem Luma-Design, das mit Produkten, Kategorien, Kundenregistrierung usw. ausgestattet ist. Es funktioniert genauso wie eine Commerce-Storefront und Sie können mithilfe des Administrators Preise, Inventar und Preisregeln für Werbeaktionen ändern.

>[!NOTE]
>
>Um Datenbank und verschiedene Funktionen zu überprüfen und zu analysieren, sollten Sie anstelle von Beispieldaten echte Daten verwenden. Beispieldaten werden als vorgenerierte Store-Simulation konzipiert, um Designdesign und grundlegendes Storefront-Verhalten zu demonstrieren. Alle Beispieldatenentitäten werden direkt in die Datenbanktabellen geschrieben, während Beispieldaten installiert sind.

Sie können Beispieldaten entweder vor oder nach der Installation der Commerce-Software installieren. Wenn Sie mit den Beispieldaten fertig sind, können Sie sie entweder entfernen oder neu installieren, wie unter [Beispieldatenmodule entfernen oder Beispieldaten aktualisieren](remove-or-update.md).

>[!WARNING]
>
>Beispieldaten können nicht deinstalliert werden. Verwenden Sie nur Beispieldaten, um mehr über die Funktionsweise von Adobe Commerce zu erfahren. Vermeiden Sie die Entwicklung in einem System, in dem Sie Beispieldaten installiert haben.

Sie können optionale Beispieldaten auf eine der folgenden Arten installieren:

| Installationsmethode | Beschreibung | Erforderliche Kompetenz-stufe |
|--- |--- |--- |
| Verwenden von Composer | [Ausführen `magento sampledata:deploy` zum Ändern des Stammverzeichnisses der Anwendung `composer.json`](composer-packages.md) um Beispieldatenmodule zu aktivieren. | Erfordert Kenntnisse von Composer und Zugriff auf das Commerce-Dateisystem. |
| Klonen von Repositorys | [GitHub-Repository klonen](git-repositories.md) und dem Beispieldaten-Repository verknüpfen. | Nur für beitragende Entwickler. Alle anderen sollten eine der vorhergehenden Methoden verwenden. |
