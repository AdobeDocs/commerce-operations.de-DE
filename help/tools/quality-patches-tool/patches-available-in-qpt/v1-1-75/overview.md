---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.75'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.75  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: d952deb1c82ce0d99c3e13909cfc18b7a48034c3
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.75

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.75 verfügbaren Patches behoben wurden.

QPT v1.1.75 enthält die folgenden Patches:
1. **ACSD-68289**: Es wird ein Problem behoben, bei dem die Volltextsuche jetzt übereinstimmende Produkte zurückgibt, wenn die Mindestbedingung für die Übereinstimmung für alle durchsuchbaren Felder gemeinsam erfüllt ist, anstatt dass die Bedingung für ein einzelnes Feld erfüllt sein muss.
1. **ACSD-68359**: Es wurde ein Problem behoben, bei dem die Auswahl eines Shops während des Checkouts mit **[!UICONTROL Pick in Store]** aufgrund langer URLs nicht mehr fehlschlug, wenn sich viele Produkte im Warenkorb befinden. Zuvor wurde ein 414-Fehler ausgelöst, der durch zu lange URLs verursacht wurde, die während eines Store-Verkaufs generiert wurden.
1. **ACSD-68451**: Es wird ein Problem bei mehreren Websites behoben, bei denen sich ein Unternehmensadministrator auf einer Website anmeldet, auf einer anderen Website ein nicht verbundenes Unternehmen erstellt, aber fälschlicherweise mit diesem nicht verbundenen Unternehmen verknüpft ist.
1. **ACSD-68490**: **[!UICONTROL Add New Attribute]** Schaltfläche, die bei der konfigurierbaren Produkterstellung für Administratoren mit eingeschränkter Zugriffsberechtigung sichtbar ist.
1. **ACSD-68517**: Behebt einen Fehler bei der erneuten Übermittlung von Formularen auf Katalogseiten und Katalogsuchseiten.
1. **ACSD-68573**: Es wurde das Problem behoben, dass Kategorieberechtigungen nicht ordnungsgemäß auf Elemente der Kunden-Wunschliste angewendet wurden. Nach der Fehlerbehebung werden Elemente der Wunschliste sowohl im Web als auch in GraphQL ordnungsgemäß angezeigt und paginiert.
1. **ACSD-68615**: Es wurde ein Problem behoben, bei dem die CLI für die Ausgleichszahlung für Lagerreservierungen eine Ausnahme anzeigte, wenn die verarbeitete Kombination eine fehlende Auftrags-ID hatte.
1. **ACSD-68793**: Es wurde ein Problem behoben, bei dem gültige Produkte fälschlicherweise zurückgewiesen wurden, wenn sie einem freigegebenen Katalog zugewiesen wurden.
1. **ACSD-68925**: Es wurde ein Problem behoben, bei dem die Antworten für GraphQL-Anfragen jetzt mit den GraphQL over HTTP-Spezifikationen übereinstimmen. Ein 4XX-Antwort-Code wird zurückgegeben, wenn die Anfrage nicht geparst werden kann, nicht autorisiert ist oder ein allgemeines Problem auftritt, wenn die Anfrage geparst wird.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
