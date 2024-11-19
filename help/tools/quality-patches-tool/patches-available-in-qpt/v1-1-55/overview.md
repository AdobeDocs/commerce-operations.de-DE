---
title: "Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.55"
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.55 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 97b52220f3b254ee17705a22137693abc6008c72
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.55

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.55 verfügbaren Patches behoben wurden.

QPT v1.1.55 enthält die folgenden Patches:

1. **ACSD-58383**: Behebung des Problems, bei dem die Ausgabe einer Rückerstattung über die [!DNL REST API] mit zwei identischen Anforderungen, die gleichzeitig ausgeführt werden, doppelte Kreditkarten erzeugt.
1. **ACSD-58471**: Behebung des Problems, bei dem dynamische Inhalte bei der Planung der zugehörigen Katalogpreisregeln nicht auf der Produktdetailseite geladen werden können.
1. **ACSD-58566**: Behebung des Problems, bei dem [!DNL GraphQL] einen internen Server-Fehler zurückgibt, wenn das Feld `created_at` in der `addPurchaseOrderComment`-Mutation abgefragt wird.
1. **ACSD-58685**: Behebung des Problems, bei dem Verkaufs-E-Mails, die bei Deaktivierung der E-Mail-Kommunikation initiiert wurden, nach der erneuten Aktivierung der E-Mail-Kommunikation weiterhin gesendet werden.
1. **ACSD-58735**: Behebung des Problems, bei dem ein eingeschränkter Administrator die abgebrochenen Warenkörbe auf der Kundenkontoseite in der [!UICONTROL Admin] einer zugehörigen Website nicht anzeigen kann.
1. **ACSD-58828**: Behebung des Problems, bei dem die serverseitige Validierungsmeldung *Adresse erforderlich* angezeigt wird, wenn ein erforderliches Feld leer gelassen wird, neben der clientseitigen Validierungsmeldung. Bei der serverseitigen Validierung wird die Meldung für leere erforderliche Felder nicht angezeigt, und die clientseitige Validierung verarbeitet die Fehlerbenachrichtigung, in der steht, dass dies ein erforderliches Feld ist.**
1. **ACSD-60344**: Behebung des Problems, bei dem doppelte E-Mails zur Bestellbestätigung gesendet werden, wenn eine **[!UICONTROL Purchase Order]** mit automatischer Genehmigung verwendet wird.
1. **ACSD-61348**: Behebung des Problems, bei dem Wunschlisten-Elemente über [!DNL GraphQL] sichtbar sind, jedoch nicht in einer Storefront in einer Umgebung mit mehreren Websites.
1. **ACSD-61534**: Behebung des Problems, bei dem die Designkonfiguration nicht mit dem Befehl `bin/magento config:set` festgelegt werden kann und gesperrte Werte durch die Bearbeitung des Formulars geändert werden können. Jetzt können gesperrte Werte, die aus dem [!DNL CLI] mit `--lock-env` oder `--lock-conf` festgelegt wurden, nicht aktualisiert werden.
1. **ACSD-61785**: Behebung des Problems, bei dem eine Aktualisierung des `reward_warning_notification` -Attributs über [!DNL GraphQL] Mutationen und [!DNL REST API] -Aufrufe nicht möglich ist, indem sein Verhalten an `reward_update_notification` ausgerichtet wird.
1. **ACSD-62591**: Behebung des Problems, bei dem das Design bei der Konfiguration von **[!UICONTROL User Agent Rules]** nicht ordnungsgemäß wechselt.
1. **ACSD-62793**: Behebung des Problems, bei dem `datetime` -Attribute in exportierten Daten die Zeitkomponente nicht enthalten. Wenn *[!UICONTROL Fields Enclosure]* den Wert *enabled* aufweist, werden die Attributwerte in der Spalte `additional_attributes` in doppelte Anführungszeichen gesetzt.
1. **ACSD-62332**: Behebung des Problems, bei dem die Abfrage mit der Produktliste [!DNL GraphQL] auf eine `total_count` von 10.000 Produkten beschränkt ist. Behebt außerdem das Problem, bei dem [!DNL Live Search] die aktuelle Seite in den Suchkriterien auf *1* anstelle von Seite *2* setzt, wenn die Abfrage über [!DNL GraphQL] erfolgt.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
