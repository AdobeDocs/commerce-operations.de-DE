---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.82'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.82  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-24T20:44:59.025Z'
TQID: 'https://experienceleague.adobe.com/Qoz-3w1ddXeHyDsyfsM0gD1kwi-Z6dc-C6P9Q-nYrUo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: b5b0f88fa2b7c168ab51f457994e4ed0578794a2
workflow-type: tm+mt
source-wordcount: 488
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.82

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.82 verfügbaren Patches behoben wurden.

QPT v1.1.82 enthält die folgenden Patches:

1. **ACP2E-4815**: Behebt mehrere GraphQL-Probleme, die PHP-Ausnahmen in Protokollen verursacht haben, die korrekte Zuordnung von Bestellungen zu Kundenkonten, die nach der Bestellung über GraphQL erstellt wurden, und die Abstimmung von Antworten mit GraphQL über HTTP-Spezifikationen.
1. **ACP2E-4194**: Behebt das Problem, dass GraphQL-Antworten falsche HTTP-Status-Codes für ungültige, nicht autorisierte oder falsch formatierte Anfragen zurückgeben.
1. **[ACP2E-4682](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4682.md)**: Es wird ein Problem behoben, dass beim Besuch einer Storefront-Seite, die den Status „Angebot ist aktiv“ prüft, bei jedem Laden der Seite leere Anführungszeichen erstellt.
1. **[ACP2E-4547](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547.md)**: Es wird ein Problem behoben, bei dem ein Admin-Benutzer **[!UICONTROL Add Products By SKU]** im Admin-Bereich nicht verwenden kann, um Produkte aus dem Standardkatalog einer Bestellung für eine Firma hinzuzufügen, die einer Kundengruppe zugewiesen wurde, die nicht mit einem freigegebenen Katalog verknüpft ist.
1. **[ACP2E-4593](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4593.md)**: Es wird das Problem behoben, dass die für Website-Einschränkungen angezeigte CMS-Seite auf sekundären Websites in Bereitstellungen mit mehreren Websites falsch sein kann.
1. **ACP2E-4695**: Behebt das Problem, dass der Katalogregel-Indexer zu viel Speicher verbraucht und nicht abgeschlossen werden kann, was zu Instabilität und Speicherfehlern führt.
1. **ACP2E-4698**: Es wird das Problem behoben, dass bei der erneuten Bearbeitung eines Bildes in Page Builder-Textinhalten eine absolute Medien-URL gespeichert wird, anstatt eine portable Medienanweisung beizubehalten.
1. **[ACP2E-4797](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4797.md)**: Es wird ein Problem behoben, bei dem die Eingabe von 4-Byte-Unicode-Zeichen in den WYSIWYG-Editor oder Page Builder-Inhalt in der Admin fälschlicherweise blockiert wird, selbst wenn die Datenbank für die Unterstützung von utf8mb4 konfiguriert ist.
1. **[ACP2E-4748](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748.md)**: Behebt das Problem, dass der Ablauf von Belohnungspunkten in Geschäften mit einem großen Belohnungspunktverlauf langsam abläuft, was zu Verzögerungen bei ablaufenden Belohnungspunkten führt.
1. **[ACP2E-4799](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4799.md)**: Es wird ein Problem behoben, bei dem die `requisition_lists GraphQL` Abfrage einen `total_count` zurückgibt, der nur die Anzahl der Elemente auf der aktuellen Seite anstelle der Gesamtzahl der Anforderungslisten widerspiegelt, die den Abfragekriterien entsprechen.
1. **[ACP2E-4805](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805.md)**: Es wird das Problem behoben, dass Checkout-API-Anfragen für konfigurierbare Produkte mit vielen untergeordneten Produkten erheblich langsamer werden, wenn das erste verkaufbare untergeordnete Produkt spät in der Liste angezeigt wird.
1. **ACP2E-4840**: Es wird das Problem behoben, bei dem der in der `products` GraphQL-Abfrage angeforderte Mengenwert &quot;*&quot;*.
1. **[ACP2E-4870](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4870.md)**: Behebt das Problem, dass E-Mail-Benachrichtigungen zu Produktanzeigen die E-Mail-Einstellungen der Store-Ansicht ignorieren.
1. **[ACP2E-4875](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875.md)**: Es wurde ein Problem behoben, durch das beim Anzeigen von Kundenkonten mit großen Adressbüchern im Admin unerwartet Admin-Benutzer abgemeldet wurden.
1. **ACP2E-4894**: Es wird das Problem behoben, dass neue Bestellungen verzögert in den Auftragsverwaltungsrastern von Admin angezeigt werden, wenn **[!UICONTROL Asynchronous Indexing]** in Stores mit hohem Volumen aktiviert ist.
1. **ACP2E-4981**: Behebt das Problem, dass in Page Builder-Produktkarussells Produkte in einer Reihenfolge angezeigt werden, die nicht der in der Admin festgelegten Position entspricht, und konfigurierbare Produkte einbezogen werden, wenn übereinstimmende untergeordnete Produkte einzeln sichtbar sind.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
