---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.61'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.61  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 0800285df83eb3e3ffcfb003bf984248b750db32
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.61

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.61 verfügbaren Patches behoben wurden.

QPT v1.1.61 enthält die folgenden Patches:

1. **ACP2E-3689**: Behebt mehrere Probleme mit der Anzeige der Kategoriestruktur auf tieferen Ebenen und spiegelt Anker-/Nicht-Anker-Beziehungen wider.
1. **ACP2E-3705**: Behebt ein Problem, bei dem die `indexer_update_all_views` Cron-Ausführung fehlschlägt, wenn `MAGE_INDEXER_THREADS_COUNT` festgelegt wird.
1. **ACSD-63883**: Es wird das Problem behoben, bei dem der [!UICONTROL Requisition List] eine falsche `items_count` in der [!DNL GraphQL] Antwort zurückgibt.
1. **ACSD-63974**: Behebt das Problem, dass das Laden der [!UICONTROL Requisition List]-Seite zu viel Zeit in Anspruch nimmt, wenn zu viele Elemente vorhanden sind, indem dem [!UICONTROL Requisition List] Raster in der Storefront eine Paginierungsfunktion hinzugefügt wird, die nur Teile von Datensätzen anzeigt, die auf die Anzahl der Datensätze pro Seite beschränkt sind, anstatt alle Datensätze auf einmal.
1. **ACSD-64178**: Es wird das Problem behoben, dass die [!UICONTROL Attribute Set] Bearbeitungsseite langsam geladen wird, wenn Tausende von Produktattributen vorhanden sind.
1. **ACSD-64209**: Es wird das Problem behoben, dass der Cron-Scheduler alle verhandelbaren Anführungszeichen abruft, ohne diejenigen mit dem Status &quot;**[!UICONTROL ordered]**&quot; auszuschließen, wodurch eine E-Mail oder E-Mails ausgelöst werden.
1. **ACSD-64431**: Die `placeOrder` Mutation, die die Couponcode-Informationen in der Anfrage enthält, löst keinen internen Fehler mehr aus, sondern zeigt stattdessen an, dass die Bestellung erfolgreich aufgegeben wurde.
1. **ACSD-64467**: Es wird ein Problem behoben, bei dem der WYSIWYG-Editor nach dem Speichern einer Kategoriebeschreibung auf Store-Ansichtsebene leer erscheint.
1. **ACSD-64546**: Es wird das Problem behoben, bei dem eine allgemeine Fehlermeldung in der Benutzeroberfläche auftritt und eine *Array-in-String-Konvertierung*-Ausnahme während der Erstellung der UPS-Versandkennzeichnung in den Protokollen gespeichert wird, sodass sichergestellt ist, dass der tatsächliche Fehler in der Benutzeroberfläche angezeigt und die richtige Fehlermeldung in den Protokollen gespeichert wird.
1. **ACSD-64684**: Es wird ein Problem behoben, bei dem beim Bearbeiten und Speichern einer Geschenkkarte mit einem Wert größer als *999* aufgrund eines Kommas (Tausendertrennzeichen) in der Zahl *1000) ein Validierungsfehler auftritt*.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
