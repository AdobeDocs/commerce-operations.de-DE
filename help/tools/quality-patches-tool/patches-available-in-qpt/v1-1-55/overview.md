---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.55'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.55  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: a4895d1b-e8d0-458e-81c8-4b892c116de6
source-git-commit: 29845fd4a8c1c744aa780e60bb4154dfc3c1a02c
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.55

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.55 verfügbaren Patches behoben wurden.

QPT v1.1.55 enthält die folgenden Patches:

1. **ACSD-58383**: Es wird ein Problem behoben, bei dem die Ausstellung einer Rückerstattung über die [!DNL REST API] mit zwei identischen Anfragen, die gleichzeitig ausgeführt werden, zu doppelten Gutschriften führt.
1. **ACSD-58471**: Es wird ein Problem behoben, bei dem dynamische Inhalte nicht auf der Produktdetailseite geladen werden, wenn die zugehörigen Katalogpreisregeln geplant sind.
1. **ACSD-58566**: Es wird ein Problem behoben, bei dem [!DNL GraphQL] bei der Abfrage des `created_at` in der `addPurchaseOrderComment` einen internen Server-Fehler zurückgibt.
1. **ACSD-58685**: Es wird ein Problem behoben, bei dem Verkaufs-E-Mails, die initiiert werden, während die E-Mail-Kommunikation deaktiviert ist, weiterhin gesendet werden, sobald die E-Mail-Kommunikation erneut aktiviert wurde.
1. **ACSD-58735**: Es wurde ein Problem behoben, durch das ein Admin mit Zugriffsbeschränkung die Transaktionsabbrüche auf der Seite „Kundenkonto“ im [!UICONTROL Admin] für eine zugehörige Website nicht anzeigen konnte.
1. **ACSD-58828**: Es wird ein Problem behoben, bei dem die Server-seitige Validierungsmeldung *Adresse ist erforderlich* angezeigt wird, wenn ein erforderliches Feld leer gelassen wird, zusammen mit der Client-seitigen Validierungsmeldung. Bei der Server-seitigen Validierung wird die Meldung für leere erforderliche Felder nicht angezeigt, und die Client-seitige Validierung verarbeitet die Fehlerbenachrichtigung mit dem Hinweis: *Dies ist ein erforderliches Feld.*
1. **ACSD-60344**: Es wird ein Problem behoben, bei dem doppelte E-Mails zur Bestellbestätigung gesendet werden, wenn ein **[!UICONTROL Purchase Order]** mit automatischer Genehmigung verwendet wird.
1. **ACSD-61348**: Es wird das Problem behoben, dass Wunschlistenelemente in einer Umgebung mit mehreren Websites über [!DNL GraphQL], aber nicht in der Storefront sichtbar sind.
1. **ACSD-61534**: Es wird das Problem behoben, dass die Design-Konfiguration nicht mit dem Befehl `bin/magento config:set` festgelegt werden kann und gesperrte Werte durch Formularbearbeitung geändert werden können. Jetzt können gesperrte Werte, die aus dem [!DNL CLI] mit `--lock-env` oder `--lock-conf` festgelegt wurden, nicht aktualisiert werden.
1. **ACSD-61785**: Es wird ein Problem behoben, bei dem die Aktualisierung des `reward_warning_notification`-Attributs nicht über [!DNL GraphQL] Mutations- und [!DNL REST API]-Aufrufe möglich ist, wodurch das Verhalten an `reward_update_notification` angepasst wird.
1. **ACSD-62591**: Es wird das Problem behoben, dass das Design nicht richtig wechselt, wenn die **[!UICONTROL User Agent Rules]** konfiguriert sind.
1. **ACSD-62793**: Es wird das Problem behoben, bei dem `datetime` Attribute in exportierten Daten die Zeitkomponente nicht enthalten. Wenn *[!UICONTROL Fields Enclosure]* *aktiviert* ist, werden Attributwerte in der `additional_attributes` Spalte außerdem in doppelte Anführungszeichen gesetzt.
1. **ACSD-62332**: Es wurde das Problem behoben, dass die Produktliste [!DNL GraphQL] die Abfrage auf eine `total_count` von 10.000 Produkten beschränkt ist. Außerdem wird das Problem behoben, bei dem [!DNL Live Search] die aktuelle Seite bei der Abfrage über [!DNL GraphQL] in den *auf* 1 *anstelle* 2 setzt.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
