---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.76'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.76  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8eac0cdbf303e307b7734845c09c9d652d901d7b
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.76

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.76 verfügbaren Patches behoben wurden.

QPT v1.1.76 enthält die folgenden Patches:
1. **[ACSD-67091](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091.md)**: Behebt den Fehler bei der maximalen Writeset-Größe, um die Bereinigung des Produktindexes der Katalogregel sicherzustellen, indem zwei Löschstrategien basierend auf dem Datenvolumen implementiert werden.
1. **ACSD-67370**: Behebt mehrere Probleme, bei denen falsche Preise für Bundle-Produkte auf PDP/PLP und der Warenkorbseite für Geschäfte mit mehreren Währungen angezeigt wurden.
1. **[ACSD-68410](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410.md)**: Es wird ein Problem behoben, bei dem durch die Platzierung einer Bestellung für ein verhandelbares Angebot fälschlicherweise zusätzliche Warenkorbzeilen zum Angebot hinzugefügt oder zusammengeführt werden. Produkte werden jetzt korrekt zum Warenkorb hinzugefügt, nachdem der letzte Schritt des verhandelbaren Angebots-Checkouts verlassen wurde.
1. **ACSD-69086**: Es wurde ein Problem behoben, bei dem der Cron-Auftrag die Changelog-Tabellen nicht löschen konnte, was bei der Verarbeitung großer Datenmengen zu [!DNL Galera Cluster] Abstürzen führte.
1. **ACSD-69115**: Es wurde ein Problem behoben, bei dem Warenkorbfehler dem Admin-Benutzer beim Verwalten des Warenkorbs für einen Kunden, der einer nicht standardmäßigen Website zugewiesen war, nicht angezeigt wurden.
1. **[ACSD-69129](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129.md)**: Es wurde ein Problem behoben, bei dem das Löschen der standardmäßigen Basis-Website und die Verwendung der sekundären Website als Standard zu einem Fehler führte, wenn versucht wurde, den Stufenpreis für die sekundäre Website über die [!DNL REST]-API zu aktualisieren.
1. **ACSD-69203**: Es wird ein Problem behoben, bei dem das **[!UICONTROL Products List]**-Widget falsche Ergebnisse zurückgibt, wenn mehrere Kategorien in der Kategoriebedingung aufgelistet wurden.
1. **ACSD-69261**: Es wurde ein Problem behoben, bei dem ein Warenkorb-Preisregelcoupon, der für den einmaligen Gebrauch pro Kunde konfiguriert war, mehrmals wiederverwendet wurde, da das `times_used`-Attribut in Teilrechnungs- und Restmengen-Stornierungsszenarien falsch verarbeitet wurde.
1. **[ACSD-69308](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308.md)**: Es wurde ein Problem behoben, bei dem Katalogpreisregeln nicht anwendbar waren, wenn `special_price` nur auf Website-Ebene festgelegt wurde (nicht auf **[!UICONTROL All Store Views]**).
1. **ACSD-69319**: Es wurde ein Problem behoben, bei dem Bundle-Preise nicht richtig indiziert wurden, wenn untergeordnete Produkte unter benutzerdefinierten Quellen vorrätig waren.
1. **[ACSD-69325](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325.md)**: Es wurde ein Problem behoben, durch das beim Ändern des SKU-Falls das Produkt in der Storefront nicht vorrätig angezeigt wird.
1. **ACSD-69331**: Es wurde ein Problem behoben, bei dem Ersteller von Inhalten in der Mediensammlung keine Ordner mit nur der Berechtigung `create_folder` erstellen konnten. Nach der Behebung können sie wie erwartet Ordner erstellen.
1. **[ACSD-69541](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541.md)**: Es wurde ein Problem behoben, bei dem die Möglichkeit, die Produktmenge in dem Warenkorb über GraphQL zu bearbeiten, durch Reduzieren der Produktmenge im [!UICONTROL Admin] auf eine geringere als die vorherige Menge in einem Warenkorb unterbrochen wurde.
1. **[ACSD-69333](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333.md)**: Es wurde ein Problem behoben, bei dem SKU-Änderungen für Produkte mit einer aktiven geplanten Aktualisierung zulässig waren. Nach der Behebung werden SKU-Änderungen während aktiver Aktualisierungen verboten. Das Speichern schlägt mit einem eindeutigen Fehler fehl und das Feld „Admin SKU“ ist deaktiviert. Dadurch werden MSI-Inventarinkonsistenzen verhindert, die durch SKU-Änderungen während Staging-Rollbacks verursacht werden.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
