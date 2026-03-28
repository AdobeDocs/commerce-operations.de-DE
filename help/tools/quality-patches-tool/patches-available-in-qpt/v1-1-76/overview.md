---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.76'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.76  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 33361f8de36b1d3f346d216244efb413835d88ef
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.76

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.76 verfügbaren Patches behoben wurden.

QPT v1.1.76 enthält die folgenden Patches:
1. **[ACSD-67091](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091.md)**: Behebt den Fehler bei der maximalen Writeset-Größe, um die Bereinigung des Produktindexes der Katalogregel sicherzustellen, indem zwei Löschstrategien basierend auf dem Datenvolumen implementiert werden.
1. **[ACSD-67370](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67370.md)**: Behebt mehrere Probleme, bei denen falsche Preise für Bundle-Produkte auf PDP/PLP und der Warenkorbseite für Geschäfte mit mehreren Währungen angezeigt wurden.
1. **[ACSD-68410](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410.md)**: Es wird ein Problem behoben, bei dem durch die Platzierung einer Bestellung für ein verhandelbares Angebot fälschlicherweise zusätzliche Warenkorbzeilen zum Angebot hinzugefügt oder zusammengeführt werden. Produkte werden jetzt korrekt zum Warenkorb hinzugefügt, nachdem der letzte Schritt des verhandelbaren Angebots-Checkouts verlassen wurde.
1. **[ACSD-69086](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69086.md)**: Es wurde ein Problem behoben, bei dem der Cron-Auftrag keine Changelog-Tabellen löschen konnte, was bei der Verarbeitung großer Datenmengen zu [!DNL Galera Cluster] Abstürzen führte.
1. **[ACSD-69115](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69115.md)**: Es wurde ein Problem behoben, bei dem Warenkorbfehler dem Admin-Benutzer beim Verwalten des Warenkorbs für einen Kunden, der einer nicht standardmäßigen Website zugewiesen war, nicht angezeigt wurden.
1. **[ACSD-69129](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129.md)**: Es wurde ein Problem behoben, bei dem das Löschen der standardmäßigen Basis-Website und die Verwendung der sekundären Website als Standard zu einem Fehler führte, wenn versucht wurde, den Stufenpreis für die sekundäre Website über die [!DNL REST]-API zu aktualisieren.
1. **[ACSD-69203](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69203.md)**: Es wurde ein Problem behoben, bei dem das **[!UICONTROL Products List]**-Widget falsche Ergebnisse zurückgab, wenn mehrere Kategorien in der Kategoriebedingung aufgelistet waren.
1. **[ACSD-69261](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69261.md)**: Es wurde ein Problem behoben, bei dem ein Warenkorb-Preisregelcoupon, der für den einmaligen Gebrauch pro Kunde konfiguriert war, mehrmals wiederverwendet wurde, da das `times_used`-Attribut in Teilrechnungs- und Restmengen-Stornierungsszenarien falsch verarbeitet wurde.
1. **[ACSD-69308](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308.md)**: Es wurde ein Problem behoben, bei dem Katalogpreisregeln nicht anwendbar waren, wenn `special_price` nur auf Website-Ebene festgelegt wurde (nicht auf **[!UICONTROL All Store Views]**). Nach der Fehlerbehebung gelten die Katalogpreisregeln korrekt, indem zunächst der Standardspeicher der Website überprüft wird.
1. **[ACSD-69319](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69319.md)**: Es wurde ein Problem behoben, bei dem Bundle-Preise nicht richtig indiziert wurden, wenn untergeordnete Produkte unter benutzerdefinierten Quellen vorrätig waren.
1. **[ACSD-69325](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325.md)**: Es wurde ein Problem behoben, durch das beim Ändern des SKU-Falls das Produkt in der Storefront als nicht vorrätig angezeigt wurde.
1. **[ACSD-69331](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69331.md)**: Es wurde ein Problem behoben, bei dem Ersteller von Inhalten in der Mediensammlung keine Ordner mit nur der Berechtigung `create_folder` erstellen konnten. Nach der Behebung können sie wie erwartet Ordner erstellen.
1. **[ACSD-69333](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333.md)**: Es wurde ein Problem behoben, bei dem SKU-Änderungen für Produkte mit einer aktiven geplanten Aktualisierung zulässig waren. Nach der Behebung werden SKU-Änderungen während aktiver Aktualisierungen verboten. Das Speichern schlägt mit einem eindeutigen Fehler fehl und das Feld „Admin SKU“ ist deaktiviert. Dadurch werden MSI-Inventarinkonsistenzen verhindert, die durch SKU-Änderungen während Staging-Rollbacks verursacht werden.
1. **[ACSD-69541](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541.md)**: Es wurde ein Problem behoben, durch das bei einer Reduzierung der Produktmenge im [!UICONTROL Admin] auf eine geringere Menge als die bereits im Warenkorb vorhandene Produktmenge die Bearbeitung der Produktmenge in diesem Warenkorb über GraphQL nicht möglich war.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
