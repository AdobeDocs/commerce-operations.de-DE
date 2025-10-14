---
title: Beta-Versionen
description: Erfahren Sie mehr über die Beta-Versionen von Adobe Commerce und wie Sie teilnehmen können.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: d467ada97a81d64dff358bc83acd489f69ba0677
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 0%

---

# Beta-Versionen von Adobe Commerce

Adobe Commerce-Beta-Programme bieten Händlern die Möglichkeit, auf Vorabversionsfunktionen und -code zuzugreifen, Feedback zu geben und die Zukunft von Adobe Commerce zu gestalten. Es gibt zwei Arten von Beta-Programmen:

- Öffentliche Beta: Allen Adobe Commerce-Kunden und -Partnern steht ein öffentliches Beta-Programm zur Verfügung
- Private Beta: Für ein privates Beta-Programm ist möglicherweise eine Genehmigung erforderlich, die auf bestimmten Teilnahmekriterien basiert

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (über Adobe Support Services oder anderweitig). Kunden wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die korrekte Funktionsweise oder Leistung der Beta-Versionen und/oder der zugehörigen Dokumentation oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

## Vorteile der Teilnahme

Wenn Sie frühzeitig auf von Adobe entwickelte Funktionen zugreifen können, erhalten Kunden und Partner die Möglichkeit, Feedback zu geben, die Produktentwicklung zu gestalten und sich auf die Übernahme neuer Funktionen vorzubereiten, bevor diese allgemein verfügbar sind.

## Aktuelle Beta-Programme

In den folgenden Abschnitten finden Sie eine Liste der aktiven Beta-Programme.

### Cloud Automation Patching Service (Private Beta)

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

### Erweiterte Suchfunktionen für die Live-Suche (Public Beta)

Diese Beta-Version unterstützt drei neue Funktionen in der [`productSearch` Abfrage](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/):

- **Mehrschichtige Suche** - Suche in einem anderen Suchkontext - Mit dieser Funktion können Sie bis zu zwei Suchebenen für Ihre Suchanfragen durchführen. Beispiel:

   - **Layer 1-Suche** - Suche nach „motor“ in „product_attribute_1“.
   - **Layer 2-Suche** - Suchen Sie nach „Teilenummer 123“ in „product_attribute_2“. In diesem Beispiel wird in den Ergebnissen nach „Motor“ nach „Teilenummer 123“ gesucht.

  Die mehrschichtige Suche ist sowohl für die `startsWith` als auch für die `contains` Suchindizierung verfügbar, wie unten beschrieben:

- **startsWith search indexation** - Suche mit `startsWith`. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach Produkten, bei denen der Attributwert mit einer bestimmten Zeichenfolge beginnt.
   - Konfigurieren der Suche „endet mit“, damit Käufer nach Produkten suchen können, bei denen der Attributwert mit einer bestimmten Zeichenfolge endet. Um eine Suche „endet mit“ zu aktivieren, muss das Produktattribut in umgekehrter Reihenfolge aufgenommen werden und der API-Aufruf sollte auch eine umgekehrte Zeichenfolge sein.

- **enthält Suchindizierung** - Das Suchattribut enthält die Indizierung. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach einer Abfrage innerhalb einer größeren Zeichenfolge. Beispiel: Ein Käufer sucht in der Zeichenfolge „HAPE-123“ nach der Produktnummer „PE-123“.

     >[!NOTE]
     >
     >Dieser Suchtyp unterscheidet sich von dem vorhandenen Suchbegriff[ der eine ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) Suche durchführt. Wenn Ihr Produktattributwert beispielsweise „Outdoor Pants“ ist, gibt eine Suchphrase eine Antwort für „out pan“ zurück, aber keine Antwort für „or ants“. Eine Suche enthält jedoch eine Antwort für „oder Ameisen“.

Diese neuen Bedingungen verbessern den Filtermechanismus für Suchanfragen, um Suchergebnisse zu verfeinern. Diese neuen Bedingungen wirken sich nicht auf die Hauptsuchabfrage aus. Um an der Beta teilzunehmen, senden Sie eine E-Mail-Anfrage an [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Informationen zur Installation der Live Search-Betaversion finden Sie [Live Search-Handbuch](https://experienceleague.adobe.com/en/docs/commerce/live-search/install#install-the-live-search-beta).

### IBM Sterling Order Management-Systemintegration (Private Beta)

Mit diesem Integrationsbeschleuniger für IBM Sterling Order Management können Adobe Commerce-Kunden mit erweiterten Bestellverwaltungsfunktionen beginnen, die auf IBM Sterling OMS basieren. Mit dieser Integration erhalten Händler:

- Echtzeit-Einblick in die Lagerbestände und genaue Liefertermine für Ihre Kunden.
- Automatisierte Beschaffung für Bestellungen auf der Grundlage konfigurierbarer Regeln, sodass Sie Ihr Fulfillment-Netzwerk und Ihren Bestand optimieren können.
- Eine einheitliche Ansicht von Bestellungen über verschiedene Kanäle hinweg von einem einzigen Dashboard aus, sodass Ihre Support-Teams außergewöhnlichen Service bieten und Ausnahmen schnell identifizieren und behandeln können.
- Ein vorlagenbasierter Fluss für die Rückgabe-Verwaltung zur Vereinfachung der Rückgabe-Verwaltung.

Um an dieser Beta teilzunehmen, senden Sie eine E-Mail-Anfrage an [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Commerce Foundation (Public Alpha/Beta)

Jede Alpha- und Beta-Version von Adobe Commerce Foundation enthält alle Änderungen, die bis zum geplanten Veröffentlichungsdatum an Adobe Commerce-Code bereitgestellt wurden, einschließlich, aber nicht beschränkt auf die folgenden Funktionsbereiche:

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
