---
title: Beta-Versionen
description: Erfahren Sie mehr über die Beta-Versionen von Adobe Commerce und wie Sie teilnehmen können.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."
source-git-commit: 41e4aa725848fd7fa4910eaea09a802326fa3995
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---

# Beta-Versionen von Adobe Commerce

Beta-Programme für [Adobe Commerce-Produktlösungen](https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions) bieten Händlern die Möglichkeit, auf Vorabversionsfunktionen und -code zuzugreifen, Feedback zu geben und die Zukunft von Adobe Commerce zu gestalten. Es gibt zwei Arten von Beta-Programmen:

- Öffentliche Beta: Allen Adobe Commerce-Kunden und -Partnern steht ein öffentliches Beta-Programm zur Verfügung
- Private Beta: Für ein privates Beta-Programm ist möglicherweise eine Genehmigung erforderlich, die auf bestimmten Teilnahmekriterien basiert

>[!IMPORTANT]
>
>**Haftungsausschluss**<br/>
>Beta-Versionen enthalten Vorabversionsfunktionen und -code, der möglicherweise Mängel enthält und ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt wird. Adobe hat das alleinige Ermessen, Beta-Versionen allgemein verfügbar zu machen. Adobe ist nicht verpflichtet, diese Beta-Versionen bis zu einem bestimmten Datum zu pflegen, zu korrigieren, zu aktualisieren, zu ändern, zu unterstützen (über Adobe Support Services oder anderweitig) oder bereitzustellen. Sollte eine Beta-Version allgemein verfügbar werden, kann sie zusätzlichen Bedingungen unterliegen, einschließlich anwendbarer Gebühren. Beta-Versionen können ohne Vorankündigung geändert werden, einschließlich der Einstellung. Kunden wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die unterbrechungsfreie oder fehlerfreie Funktion oder Leistung der Beta-Versionen zu verlassen.  Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

## Vorteile der Teilnahme

Wenn Sie frühzeitig auf von Adobe entwickelte Funktionen zugreifen können, erhalten Kunden und Partner die Möglichkeit, Feedback zu geben, die Produktentwicklung zu gestalten und sich auf die Übernahme neuer Funktionen vorzubereiten, bevor diese allgemein verfügbar sind.

## Aktuelle Beta-Programme

In den folgenden Abschnitten finden Sie eine Liste der aktiven Beta-Programme.

### Abgleich und Rangfolge suchen (Private Beta)

[!BADGE nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."}

[!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."}

Adobe verbessert die Sortierung der Suchergebnisse für [!DNL Live Search] nach [!DNL Adobe Commerce] und [!DNL Adobe Commerce Optimizer] durch die Produktsuche. Die Aktualisierung priorisiert **exakte und Beinahe-Phrasenübereinstimmung**, dann Übereinstimmungen, wobei **alle Abfragebegriffe im selben durchsuchbaren Attribut erscheinen** und schließlich **feldübergreifende** Übereinstimmungen (einschließlich des Verhaltens, das Vorschläge mit automatischer Vervollständigung unterstützt). Mit diesem mehrschichtigen Modell können Abfragen mit hohem Intent die relevantesten Produkte zuerst aufdecken und gleichzeitig nützliche Alternativen zurückgeben.

Dasselbe Relevanzmodell interagiert mit **Suchgewichten**, **Intelligent Ranking**, **Synonymen** und **Merchandising-Regeln** (Pin, Boost, Bury). Deutsche Storefronts können **Dekompoundierung** für zusammengesetzte Wörter mit demselben allgemeinen Priorisierungsansatz verwenden.

**Die wichtigsten Vorteile**

- Stärkere Verstärkungen für exakte und Beinahe-Phrasenübereinstimmungen (einschließlich normalisierter Formulare wie Singular und Plural).
- Höheres Ranking, wenn alle Abfragewörter gemeinsam in einem durchsuchbaren Feld angezeigt werden.
- Klarere Erwartungen an die Kombination von Gewichtungen, intelligentem Ranking und manuellen Regeln zur Abfragezeit.
- Anleitungen für die Validierung von Abfragen mit hohem Wert und für Optimierungsregeln nach der Änderung.

Erfahren Sie mehr über Suchabgleich und Rangfolgestrategie in [Adobe Commerce Optimizer (SaaS)](https://experienceleague.adobe.com/en/docs/commerce/optimizer/search-relevance-matching) und [Live Search (PaaS)](https://experienceleague.adobe.com/en/docs/commerce/live-search/search-relevance-matching).

Um eine Einladung zu dieser privaten Beta-Version anzufordern, senden Sie eine E-Mail an [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com). Das Adobe-Team wird mit den nächsten Schritten und Eignungsanforderungen antworten.

### Preisfilter für Empfehlungen (Public Beta) {#recommendation-price-filters-public-beta}

[!BADGE nur SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce as a Cloud Service- und Adobe Commerce Optimizer-Projekte (von Adobe verwaltete SaaS-Infrastruktur)."}

[!DNL Adobe Commerce Optimizer] fügt **Preisfilter** zu Produktempfehlungen hinzu, damit Sie empfohlene Produkte basierend auf dem Preis ein- oder ausschließen können, wenn Sie eine Empfehlungseinheit erstellen oder bearbeiten. Die Filter verwenden den **endgültigen berechneten Preis** des &quot;**Preisbuchs“ des jeweiligen Produkts,** Rabatte und Sonderangebote aus diesem Preisbuch (nicht nur Listenpreis). Preisregeln verfeinern die Kandidatenmenge; sie sehen keine Neubewertung von Produkten vor.

Sie können **statische** Bereiche mit festen Mindest- und Höchstwerten in der Basiswährung Ihres Geschäfts oder **dynamische** Regeln auf Produktdetailseiten definieren, die empfohlene Produkte mit dem **aktuell angezeigten Produkt** vergleichen, indem Sie Operatoren wie kleiner oder gleich, größer oder gleich oder innerhalb eines Wert- oder Prozentbereichs des Ankerpreises verwenden. Dynamische Filter sind für SKU-bezogene Empfehlungstypen verfügbar, die im Produktkontext ausgeführt werden (z. B *„Anzeigen dieser, Anzeigen dieser* und *Ähnliche*).

**Die wichtigsten Vorteile**

- Ein- oder Ausschließen von Empfehlungskandidaten anhand des Preises mithilfe von Ein- und Ausschlussregeln im Schritt **Produkte**.
- Verwenden Sie statische Preisbänder für feste Merchandising-Ziele (z. B. budgetfreundliche Add-ons oder Premium-Upsells).
- Verwenden Sie dynamische Preisregeln auf der Produktdetailseite, um Alternativen innerhalb einer vergleichbaren Preisspanne relativ zum angezeigten Produkt anzuzeigen.
- Passen Sie die Filterung an den Preis an, den Käufer sehen. Dies ist derselbe Endpreis aus dem aktiven Preisbuch, der für die Filterung und Anzeige verwendet wird.

Weitere Informationen finden Sie unter [Empfehlungsfilter — Preis](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/recommendations/filters#price) im Handbuch für Händler und [Produktempfehlungen einrichten](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/content-customizations/product-recommendations/) im Dropdown-Handbuch für Storefronts.

Um Ihr Feedback bei der Verwendung dieser Beta-Funktion zu geben, senden Sie eine E-Mail an [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Cloud Automation Patching Service (Private Beta)

[!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."}

Der [Cloud Automation Patching Service](../tools/caps-tool/intro.md) automatisiert das Anwenden isolierter Sicherheits-Patches auf Ihre [Adobe Commerce in Cloud-](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview)-Umgebungen.

Im Oktober 2025 wird die Beta-Version des Cloud Automation Patching Service zum Dashboard des [Site-Wide Analysis Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard) hinzugefügt. Dieser Service unterstützt Commerce-Projektadministratoren mit einem optimierten Patch-Workflow, der Folgendes umfasst:

- Automatisierte Patch-Installation
- Rollback-Wiederherstellung
- Verifizierung nach der Bereitstellung.

Der Service stellt sicher, dass Sie sichere, stabile und aktualisierte Umgebungen mit minimalem manuellen Aufwand und Risiko pflegen können.

Die Beta-Version umfasst die folgenden Funktionen:

- **Automatische Patch-Installation**: Vereinfachen und automatisieren Sie das Patchen kritischer Schwachstellen in Umgebungen.
- **Minimieren des Risikos**: Vermeiden Sie Standortausfälle mit Konsistenzprüfungs- und Rollback-Funktionen nach der Bereitstellung.

>[!NOTE]
>
>Da der Cloud Automation-Patching-Service isolierte Sicherheits-Patches automatisch anwendet, benötigen Sie [ Rolle „Mitwirkender“ oder &quot;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access)&quot;, um sie verwenden zu können.

Um an dieser Beta-Version teilzunehmen, füllen Sie das Anmeldeformular [Cloud Automation Patching Service - Beta aus](https://forms.office.com/r/3Wfxj5nPdB) aus.

### Assistent für Merchant Productivity AI (Public Beta)

Der Merchant Productivity AI Assistant ist eine in Adobe Commerce Admin eingebettete Gesprächsoberfläche, die Händlern bei der Durchführung von Routineaufgaben und dem bedarfsorientierten Zugriff auf Geschäftserkenntnisse mithilfe natürlicher Sprache hilft. Sie ermöglicht Händlern die Verwaltung von Promotions, die Aktualisierung von Produktkataloginformationen und den Abruf von Betriebsdaten - wie z. B. kürzliche Bestellungen oder aktive Promotions - direkt innerhalb ihrer bestehenden Workflows. Der Assistent bietet auch kontextbezogene Anleitungen, die Händlern dabei helfen, effizienter zu navigieren und den Admin zu verwenden.

**Die wichtigsten Vorteile**

- Automatisieren Sie gängige Merchandising-Aufgaben, einschließlich der Erstellung von Promotions und Aktualisierungen von Katalogmetadaten, mithilfe von Anweisungen in natürlicher Sprache.
- Direkter Zugriff auf kontextuelle Hilfe und Anleitungen innerhalb des Admin-Workflows.
- Abfragen von Live Store-Daten nach Bedarf, z. B. Abrufen der letzten 10 Bestellungen, Anzeigen aktuell aktiver Promotions oder Überprüfen des Inventarstatus.
- Verringern Sie den Zeitaufwand für sich wiederholende Verwaltungsaufgaben, sodass sich die Händler auf Strategie und Wachstum konzentrieren können.

Um an dieser Beta teilzunehmen, senden Sie eine E-Mail an [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Adobe Commerce Foundation (Public Alpha/Beta)

[!BADGE Nur PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten (von Adobe verwaltete PaaS-Infrastruktur) und lokale Projekte."}

Jede Adobe Commerce Foundation-Alpha- und -Beta-Version enthält alle Änderungen, die bis zum geplanten Veröffentlichungsdatum an Adobe Commerce Core Code bereitgestellt wurden, einschließlich, aber nicht beschränkt auf die folgenden Funktionsbereiche:

- Neueste Sicherheitskorrekturen
- Leistungsverbesserungen
- GraphQL-Verbesserungen
- Allgemeine Qualitätsfehler-Fehlerbehebungen
- Gemeinschaftsbeiträge
- Zur Unterstützung der Kompatibilität mit [Adobe Commerce-Services erforderliche Änderungen](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)

#### Namenskonvention und -zeitplan

Adobe veröffentlicht in der Regel mehrmals im Jahr Alpha- und Beta-Patches.

Alpha-Versionspakete haben ein `-alphaX` Suffix. Beispielsweise verwenden die Alpha-Release-Pakete von Adobe Commerce 2.4.7 die folgende Namenskonvention:

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta-Versionspakete haben ein `-betaX` Suffix. Beispielsweise verwenden die Adobe Commerce 2.4.7 Beta-Versionspakete die folgende Namenskonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

Siehe [Veröffentlichungszeitplan](schedule.md) für die Liste der kommenden öffentlichen Alpha- und Beta-Veröffentlichungstermine.

#### Freigabezugang

Adobe Commerce Alpha- und Beta-Versionen werden auf die gleiche Weise wie alle anderen Adobe Commerce Patch-Versionen verteilt: als Composer-Metapakete auf `https://repo.magento.com`. Der Quell-Code ist auf &quot;[&quot; ](https://github.com/magento/magento2).

Siehe [Schnellstart für die Composer-Installation](../installation/composer.md) für weitere Details.

#### Problem-Reporting

Adobe bietet keinen standardmäßigen Adobe-Support-Service für Alpha- und Beta-Versionen.

Um Feedback zu Alpha- und Beta-Versionen zu senden, folgen Sie dem [Ablauf für regelmäßige Problemberichte](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) auf [GitHub](https://github.com/magento/magento2).

Adobe überwacht alle wichtigen Probleme, die in Bezug auf die neueste Alpha- oder Beta-Version gemeldet werden, und priorisiert, dass diese vor dem GA-Veröffentlichungsdatum behoben werden müssen.
