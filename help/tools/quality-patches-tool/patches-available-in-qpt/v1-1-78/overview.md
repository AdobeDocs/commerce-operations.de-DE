---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.78'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.78  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: cc3bd15a0c11762812e4e51e4c01bfa64756421a
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.78

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.78 verfügbaren Patches behoben wurden.

QPT v1.1.78 enthält die folgenden Patches:
1. **ACP2E-4416**: Es wurde das Problem behoben, dass Kundenbelohnungspunkte nicht initialisiert wurden, wenn sie in der Admin erstellt wurden.
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**: Behebt das Problem, dass Geschenkkarten nach erfolgreicher Validierung von reCAPTCHA v2 („Ich bin kein Roboter„) in der Storefront beim Checkout nicht korrekt angewendet werden.
1. **ACP2E-4431**: Behebt das Problem, dass verwandte Produkte, die von den Zielregeln abgeglichen werden, während des Neuindizierungsprozesses gelöscht werden.
1. **ACP2E-4448**: Es wird das Problem behoben, dass Konfigurationsänderungen, die während Redis-Ausfällen vorgenommen wurden, nach der Redis-Wiederherstellung nicht widergespiegelt werden, was dazu führt, dass veraltete Werte bestehen bleiben.
1. **ACP2E-4452**: Behebt das Problem, dass Produktpreise auf der Schnellbestellseite Steuern enthalten, unabhängig von der Konfiguration der Steueranzeige.
1. **ACP2E-4456**: Es wird ein Problem behoben, bei dem durch Stornieren einer Bestellung mit einer GraphQL-Mutation eine Bestellung, die vollständig mit Geschenkkarten bezahlt wurde, nicht in den Status „Geschlossen“ wechselt.
1. **ACP2E-4507**: Es wurde das Problem behoben, dass die Kennwortoptionskonfiguration für Anfragen zum Zurücksetzen des Kundenkennworts, die durch GraphQL-Mutationen vorgenommen wurden, nicht angewendet wurde.
1. **ACP2E-4513**: Behebt das Problem, dass abgelaufene CAPTCHA-Bilder nicht aus dem System gelöscht werden.
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**: Fehlerkorrektur - In der Tabelle quote_coupons tritt jetzt kein Fehler mehr auf, wenn mehrere Anfragen zum Zusammenführen des Warenkorbs oder zum Speichern von Angeboten gleichzeitig ausgeführt werden.
1. **ACP2E-4528**: Behebt das Problem der Stadtvalidierung in Kundenadressen, das jetzt einen Schrägstrich (/) zulässt und ungültige Zeichen wie !, &quot;, # und ? zurückweist.
1. **ACP2E-4535**: Es wurde ein Problem behoben, bei dem das Senden des Formulars bei vergessenem Kennwort dazu führte, dass die Sitzung zerstört oder neu generiert wurde (PHPSESSID-Änderungen) und der Gastkorb gelöscht wurde.
1. **ACP2E-4540**: Es wurde ein Problem behoben, bei dem die Fotorama-Bibliothek nicht korrekt geladen wurde, sodass nur das erste angehängte Bild sichtbar wurde.
1. **ACP2E-4555**: Behebt das Problem, dass moderne Telefonnummern &quot;.“ enthalten. oder &quot;/&quot; werden nicht ordnungsgemäß validiert.
1. **ACP2E-4565**: Behebt das Problem, dass die Abfrage von Company GraphQL „Der aktuelle Kunde ist nicht autorisiert“ zurückgibt, wenn der Header X-Adobe-Company verwendet wird.
1. **ACP2E-4591**: Es wurde das Problem behoben, dass Kundensegmente, die auf der Bestellanzahl basieren, wie z. B. „Erstkäufer“, nicht aktualisiert haben, wenn Bestellungen über die REST-API aufgegeben wurden.
1. **ACP2E-4609**: Es wird das Problem behoben, dass auf der Seite Meine Anführungszeichen keine Anführungszeichen anzeigt, wenn einige Anführungszeichen gelöschte Produkte enthalten.
1. **ACP2E-4613**: Es wurde das Problem behoben, dass große Medienverzeichnisstrukturen zu langsamen gettree-Antworten führten, was zu verlängerten Ladezeiten der Verzeichnisstruktur der Media Gallery führte.
1. **ACP2E-4628**: Es wird das Problem behoben, dass der Import von Kunden mit E-Mail-Adressen in Großbuchstaben zu dem Fehler „Nicht definierter Array-Schlüssel“ führt, wenn die Kontofreigabe auf „Global“ festgelegt ist.
1. **ACP2E-4665**: Es wird das Problem behoben, dass untergeordnete Produkte von konfigurierbaren Produkten, die Videos in den Produktgalerien enthalten, nicht aufgelistet werden, wenn sie über die REST-API angefordert werden.
1. **ACP2E-4732**: Es wurde ein Problem behoben, bei dem die partielle Indizierung für Kunden mit einer großen Anzahl von Aktualisierungen angehalten wurde, wenn die Spalte version_id in der Changelog-Tabelle den Höchstwert erreichte.
1. **ACP2E-4763**: Es wurde ein Problem behoben, bei dem die Abfrage &quot;GraphQL customerOrders“ überhöhte Werte für „original_price_include_tax“ und „original_row_total_include_tax“ zurückgibt, wenn Katalogpreise auf „Einschließlich Steuer“ festgelegt wurden, da die Steuer zweimal angewendet wurde.
1. **ACSD-60989**: Es wird das Problem behoben, dass das Ändern einer Spalte mit einem Fremdschlüssel über ein deklaratives Schema zu Fehlern in MariaDB führt.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
