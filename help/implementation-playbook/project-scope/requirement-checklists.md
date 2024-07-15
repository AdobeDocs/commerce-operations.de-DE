---
title: Checklisten für Anforderungen
description: Verwenden Sie diese Liste umfassender Fragen, um Sie bei der Vorbereitung auf eine Adobe Commerce-Implementierung zu unterstützen.
exl-id: 9ac485c5-d491-4022-9366-5e3a382513b6
feature: Best Practices
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 0%

---

# Checklisten für Anforderungen

Die folgenden Fragen können als Ausgangspunkt dienen, um zu sehen, welche Informationen dokumentiert werden sollten, um die organisatorische Abwehrbereitschaft zu bestätigen. Sie können auch bei der Entwicklung eines RFP helfen.

## Unternehmen

- Welche Geschäftsziele verfolgt die neue E-Commerce-Plattform?

- Aus welchen Gründen ändern Sie Ihre aktuelle E-Commerce-Plattform?

- Welche Ziele verfolgt die Website-Infrastruktur?

- Wie lange dauert die Bereitstellung der neuen E-Commerce-Plattform?

- Wie viele Ihrer IT-Projektmanager werden diesem Projekt zugewiesen?

- Wie viele Ihrer Geschäftsanalysten werden diesem Projekt zugewiesen?

- Wie viele Ihrer technischen Analysten werden diesem Projekt zugewiesen?

- Wie viele Ihrer HTML-Entwickler werden diesem Projekt zugewiesen?

- Welche Dokumentation gibt es für aktuelle Geschäftsprozesse?

- Welche Dokumentation gibt es für aktuelle Systemintegrationen?

- Welche Dokumentation gibt es für aktuelle Prozessflüsse?

- Welche Dokumentation gibt es für aktuelle Datenflüsse?

- Wer wird die Fortbildung anbieten?

- Welche Ausbildung wird vor dem Live-Besuch abgeschlossen?

- Welche Ausbildung wird nach dem Aufleben abgeschlossen?

- Welche Adobe Commerce-Unterstützung ist nach der Live-Schaltung erforderlich?

- Ist dieses Projekt von anderen Projekten zur Systementwicklung abhängig?

- Wie sehen Sie, dass Ihr Umsatz in den nächsten 12 bis 24 Monaten wächst?

- Wer sind Ihre Hauptkonkurrenten? Bitte geben Sie Links zu ihren Websites an. Wie wollen Sie Ihr Online-Erlebnis von Ihren Konkurrenten unterscheiden?

- Wo sehen Sie das zukünftige Wachstum in Ihrem Unternehmen?

- Welche Rolle spielt der digitale Handel in Ihrer Geschäftsstrategie? Welches sind Ihre Hauptziele für die Einrichtung dieser E-Commerce-Plattform?

- Haben Sie Marken/Unternehmen, die Sie als Referenz für Ihr Omnichannel-Geschäft nehmen?

- Welche Teams oder Einzelpersonen sind für die E-Commerce-Strategie verantwortlich? Beschreiben Sie die relevanten Positionen.

## Aktuelle Plattform

- Wie wird die aktuelle Plattform gehostet: intern, Hosting-Anbieter, private Cloud-Server oder gehostete Cloud-Server?

- Welche Umgebungen hat die aktuelle Plattform: Entwicklung, Qualitätssicherung, Vorproduktion, Produktion?

- Wie viele Web- und Datenbankserver befinden sich in der Entwicklungsumgebung?

- Wie viele Web- und Datenbankserver befinden sich in der QS-Umgebung?

- Wie viele Web- und Datenbankserver befinden sich in der Staging- (Pre-Production-)Umgebung?

- Wie viele Web- und Datenbankserver befinden sich in der Produktionsumgebung?

- Ist es eine Multi-Server-Architektur mit Lastenausgleich?

- Ist es eine Systemarchitektur mit hoher Verfügbarkeit?

- Welche Probleme haben Sie mit Ihren aktuellen Websites?

- Aktuelle Kataloggröße (Anzahl der SKUs)?

- Durchschnittliche Besucher pro Tag?

- Durchschnittliche gleichzeitige Sitzungen pro Stunde

- Durchschnittliche Seitenansichten pro Tag?

- Durchschnittliche Bestellungen pro Stunde und Tag?

## Erwartete Plattformanforderungen

- Welche Adobe Commerce-Version werden Sie verwenden?

- Wie wird die künftige Plattform gehostet: intern, Hosting-Anbieter, private Cloud-Server oder gehostete Cloud-Server?

- Welche Umgebungen werden die künftige Plattform haben: Entwicklung, Qualitätssicherung, Vorproduktion, Produktion?

- Wie viele Web- und Datenbankserver werden sich in der Entwicklungsumgebung befinden?

- Wird es sich um eine Systemarchitektur mit hoher Verfügbarkeit handeln?

- Wie viele Adobe Commerce-Administratoren haben Sie?

- Erwartete Kataloggröße (Anzahl der SKUs)?

- Erwartete durchschnittliche Besucher pro Tag?

- Erwartete durchschnittliche gleichzeitige Sitzungen pro Stunde?

- Erwartete durchschnittliche Seitenansichten pro Tag?

- Welche Daten sollten von der alten Site auf die neue Site importiert werden? (Beispiel: Produkt, Kunde, Auftragsverlauf)

## Websites

- Wie viele inländische Websites werden implementiert?

- Welche Sprachen werden implementiert?

- Wie viele internationale Websites werden implementiert?

- Welche Regionen werden von den Websites unterstützt?

- Welche Sprachen werden implementiert?

- Welche Währungen werden eingeführt?

- Verfügen Sie über Vereinbarungen auf Ebene der Zustelldienste für jedes Land?

- Wer sind Ihre Zustellungsanbieter für jedes Land?

- Wer sind Ihre Steuerzahler für jedes Land?

- Benötigen Sie ein benutzerdefiniertes internationales Website-Design?

- Ist dies in erster Linie eine B2C- oder B2B-Site? Gibt es ein B2B2B- oder B2B2C-Element?

- Gibt es ein vorhandenes Design, das angepasst wird oder wird die Plattform von Grund auf neu entworfen?

- Gibt es eine Anforderung an Headless Commerce (separate Frontend- und Backend-Ebenen)?

- Was sind die Haltepunkte (Tablet/Mobilgerät) für das responsive Design?

- Gibt es eine Anforderung für eine mobile App? Sollte PWA für das mobile Frontend genutzt werden?

- Welche spezifischen Browser sollten getestet werden (mit Ausnahme der Standardbrowser IE9+, Firefox, Chrome, Safari)?

- Welche Sprache(n) haben die einzelnen Frontend? Sind die übersetzten Inhalte verfügbar oder wird Unterstützung benötigt?

- Gibt es mehrere Websites? Wenn ja, können Kunden ihre Anmeldeinformationen auf allen Sites verwenden?

- Werden Produktdaten über alle Sites hinweg freigegeben?

- Gibt es Änderungen am Design von Site zu Site?

- Gibt es Abonnementoptionen und wie werden Abonnenten verwaltet?

- Gibt es bestimmte SEO-Anforderungen? Wie wird Suchmaschinen-Marketing verwaltet?

## Integrationen

- Welches CMS-System wird in Adobe Commerce integriert? (Beispiele: WordPress, Drupal, Conkret5)

Gibt es vorhandene APIs, die verwendet werden können?

- Wurde die Systemfehlerbehandlung für diese Integration mit Drittanbietersystemen entwickelt und entwickelt?

- Welches ERP-System wird in Adobe Commerce integriert? (Beispiele: SAP, MS Dynamics NAV)

- Welche Reedereisysteme werden in Adobe Commerce integriert?

- Welches Steuersoftwaresystem wird in Adobe Commerce integriert? (Beispiel: Taxware)

- Von welchem System werden Produktdaten in Adobe Commerce importiert?

- Häufigkeit des Ladens importierter Produktdaten?

- In welches System exportiert Adobe Commerce Produktdaten?

- Häufigkeit der Ladevorgänge von exportierten Produktdaten?

- Von welchem System werden Daten in Adobe Commerce importiert?

- Häufigkeit des Ladens importierter Bestelldaten?

- In welches System exportiert Adobe Commerce Bestelldaten?

- Häufigkeit des Ladens exportierter Bestelldaten?

- Welche Analyseplattform wird verwendet? (Beispiele: Adobe Analytics, Google Analytics)

- Wird es ein Single Sign-on und die Freigabe sozialer Netzwerke geben? Wenn ja, welche sozialen Netzwerke?

- Gibt es Belohnungen oder Treueprogramme? Gibt es eine Integration mit POS-Systemen für Belohnungen?

- Wie werden Produktanweisungen verarbeitet? Wird vom Kunden erwartet, dass er eine Rückkehranfrage online protokolliert?

- Ist ein Online-Chat-Tool erforderlich? Ist ein Chatbot erforderlich?

- Welches Zahlungsportal möchten Sie für Ihre Site haben?

- Welches Auftragsverwaltungssystem wird in Adobe Commerce integriert? (Beispiele: Microsoft Dynamics, SAP, Retail Pro)

- Welches Produktinformationsmanagementsystem wird in Adobe Commerce integriert? (Beispiele: Akeneo, InRiver, Bluestone)

- Welches Customer Relationship Management-System wird in Adobe Commerce integriert? (Beispiele: Hubspot, Salesforce, Klaviyo)

## Adobe Commerce-spezifische Funktionen

- Benötigen Sie irgendeine Art von A/B-Tests?

- Wie viele gleichzeitige Administratoren können im System arbeiten?

- Erlauben Sie einem Kunden, auf der Website erworbene Artikel in einem Laden abzurufen?

- Haben Sie Werbeseiten?

- Haben Sie Marketingbanner?

- Möchten Sie Videos auf einer CMS-Seite abspielen lassen?

- Wie oft werden Inhalte geändert oder aktualisiert?

- Welche Art von Inhalt wird geladen?

- Werden Inhaltsaktualisierungen geplant?

- Benötigen Sie eine Content-Staging-Website?

- Sollen Kunden die Möglichkeit erhalten, ein Website-Konto zu erstellen?

- Verwenden Sie eindeutige Rabattgutscheine für Promotions?

- Haben Sie Werbe-Preise?

- Haben Sie flexible Gutscheine (Möglichkeit, diese pro Website, Kundengruppe, Zeit, Kategorien oder Produkten festzulegen)?

- Werden prozentuale Rabatte für einzelne Artikel angeboten?

- Welche Geschenkfunktionalität ist erforderlich?

- Wird die Funktionalität des Prämienprogramms benötigt?

- Wird die Newsletter-Funktion benötigt?

- Ermöglicht es einem Kunden, frühere Bestellungen anzuzeigen und auszuwählen, welche Artikel umgetauscht werden sollen?

- Erlauben Sie einem Kunden, die Stornierung einer Bestellung von der Website aus zu veranlassen?

- Erlauben Sie einem Kunden, den Austausch von Artikeln von der Website aus zu starten?

- Benötigen Sie eine Echtzeitadressenvalidierung?

- Erlauben Sie einem Kunden, die Rückgabe von Artikeln von der Website zu initiieren?

- Wird Adobe Commerce eine Rückgabe-RMA ausstellen?

- Erfassen von Erstattungsinformationen in Adobe Commerce?

- Benötigen Sie ein Online-Bestelltracking für einen registrierten Kunden?

- Benötigen Sie ein Online-Bestelltracking für einen Gastkunden?

- Führen Sie die Online-Autorisierung durch und erfassen Sie sie während der Bestellplatzierung?

- Autorisierung mit Betrugsfilter während der Auftragserteilung mit verzögerter Erfassung

- Anzahl der Tage, die die volle Zahlung erhalten (nicht autorisiert)?

- Erfassung und Ausführung vor Ablauf der Autorisierung?

- Authorize.net

- Braintree

- PayPal Express

- Store-Gutschrift

- Kunststoffgeschenkkarten

- Prämienpunkte

- &quot;Bill Me Later&quot;- häufiger als &quot;Buy Now, Pay Later&quot;, da er sofort in Rechnung gestellt, aber noch nicht bezahlt wurde

- Wird es auf verschiedenen Websites unterschiedliche Produktpreise geben?

- Werden Funktionen zum Vergleichen verschiedener Produkte benötigt?

- Welche Arten von Produkten werden Sie verkaufen?

- Wie oft werden neue Produkte hinzugefügt?

- Wie oft werden Produkte aktualisiert?

- Wie oft werden neue Kategorien oder Unterkategorien erstellt?

- Wird die Funktion &quot;Bewertungen und Überprüfungen&quot;benötigt?

- Ermöglicht es Ihnen Kunden, ein Produkt zu empfehlen?

- Verkauf: Bestellungen, Steuern, Fakturiert, Versand, Erstattungen, Gutscheine, PayPal-Vergleichsberichte

- Warenkorb: Produkte in Warenkorb, verlassene Kunst

- Produkte: Bestseller, bestellte, am häufigsten angezeigte Produkte, niedriger Bestand, Downloads

- Kunden: Neue Konten, Kunden nach Gesamtbestellungen, Kunden nach Anzahl der Bestellungen, Kundensegmente, Kundenbewertungen

- Produktprüfungen

- Tags: Kunden, Produkte, beliebt

- Suchbegriffe

- Einladungen: Allgemein, Kunden, Bestellkonversionsrate

- Benötigen Sie Adobe Commerce, Berichte basierend auf Couponbenutzungsdaten zu erstellen?

- Benötigen Sie Adobe Commerce, um Berichte auf der Grundlage von Verkaufsdaten zu erstellen?

- Benötigen Sie benutzerdefinierte Adobe Commerce-Berichte?

- Wie lautet Ihre aktuelle SEO-Strategie?

- Wie wird Ihre neue SEO-Strategie aussehen?

- Welche Voraussetzungen müssen für die SEO-Migration erfüllt sein?

- Store Festpreise in Adobe Commerce?

- Teillieferungen zulassen?

- Müssen Versandverfolgungsinformationen in Adobe Commerce gespeichert werden?

- Werden Sie Steuerberechnungsregeln für Ihre eigenen Regionen benötigen?

- Werden Sie Steuerberechnungsregeln für Ihre internationalen Regionen benötigen?
