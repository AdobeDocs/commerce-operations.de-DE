---
title: Beta-Versionen
description: Erfahren Sie mehr über die Beta-Versionen von Adobe Commerce und wie Sie teilnehmen können.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 1c0dd720df944a5784c850a3f4ea63b8984069f1
workflow-type: tm+mt
source-wordcount: '963'
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

### Adobe Commerce Optimizer

Adobe Commerce Optimizer verbessert Ihr E-Commerce-Erlebnis mit einer leistungsstarken Storefront, die organischen Traffic, Kundeninteraktion und Umsatz steigert.

Mit Adobe Commerce Optimizer können Sie:

- Erweitern und skalieren Sie Ihren Katalog, ohne den gesamten Commerce-Stack neu zu platzieren.
- Nehmen Sie Katalogdaten aus einer beliebigen Quelle auf.
- Definieren Sie Geschäftskanäle und Richtlinien.
- Personalisierte Suche und Empfehlungen mit KI und ML erstellen.
- Zeigen Sie wichtige Produktdatenverfügbarkeit an, einschließlich Synchronisierungsstatus und Storefront-Ereignisdaten für eine genaue Implementierung und Fehlerbehebung.

[Weitere Informationen](https://experienceleague.adobe.com/docs/commerce/optimizer/overview.html?lang=de) über Adobe Commerce Optimizer. Wenn Sie mehr über das [!DNL Adobe Commerce Optimizer] Early Access-Programm erfahren möchten, füllen Sie das [Early Access-Anfrage-Formular](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4WOxhjY2doZPikS2hIbfmL5UMlhTMTYzVDhPQVFNTUFYUjJHNlRKTE5TWS4u) aus.

### Erweiterte Suchfunktionen für die Live-Suche (Public Beta)

Diese Beta-Version unterstützt drei neue Funktionen in der [`productSearch` Abfrage](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Mehrschichtige Suche** - Suche in einem anderen Suchkontext - Mit dieser Funktion können Sie bis zu zwei Suchebenen für Ihre Suchanfragen durchführen. Beispiel:

   - **Layer 1-Suche** - Suche nach „motor“ in „product_attribute_1“.
   - **Layer 2-Suche** - Suchen Sie nach „Teilenummer 123“ in „product_attribute_2“. In diesem Beispiel wird in den Ergebnissen nach „Motor“ nach „Teilenummer 123“ gesucht.

  Die mehrschichtige Suche ist sowohl für die `startsWith` als auch für die `contains` Suchindizierung verfügbar, wie unten beschrieben:

- **startsWith search indexation** - Suche mit `startsWith`. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach Produkten, bei denen der Attributwert mit einer bestimmten Zeichenfolge beginnt.
   - Konfigurieren der Suche „endet mit“, damit Käufer nach Produkten suchen können, bei denen der Attributwert mit einer bestimmten Zeichenfolge endet. Um eine Suche „endet mit“ zu aktivieren, muss das Produktattribut in umgekehrter Reihenfolge aufgenommen werden und der API-Aufruf sollte auch eine umgekehrte Zeichenfolge sein.

- **enthält Suchindizierung** - Das Suchattribut enthält die Indizierung. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach einer Abfrage innerhalb einer größeren Zeichenfolge. Beispiel: Ein Käufer sucht in der Zeichenfolge „HAPE-123“ nach der Produktnummer „PE-123“.

      - Hinweis: Dieser Suchtyp unterscheidet sich von dem vorhandenen Suchbegriff[ der eine ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) Suche durchführt. Wenn Ihr Produktattributwert beispielsweise „Outdoor Pants“ ist, gibt eine Suchphrase eine Antwort für „out pan“ zurück, aber keine Antwort für „or ants“. Eine Suche enthält jedoch eine Antwort für „oder Ameisen“.

Diese neuen Bedingungen verbessern den Filtermechanismus für Suchanfragen, um Suchergebnisse zu verfeinern. Diese neuen Bedingungen wirken sich nicht auf die Hauptsuchabfrage aus. Um an der Beta teilzunehmen, senden Sie eine E-Mail-Anfrage an [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Informationen zur Installation der Live Search-Betaversion finden Sie [Live Search-Handbuch](https://experienceleague.adobe.com/de/docs/commerce/live-search/install#install-the-live-search-beta).

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
- Zur Unterstützung der Kompatibilität mit [Adobe Commerce-Services erforderliche Änderungen](https://experienceleague.adobe.com/de/docs/commerce/user-guides/home)

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
