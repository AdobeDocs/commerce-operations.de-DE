---
title: Beta-Versionen
description: Erfahren Sie mehr über die Beta-Versionen von Adobe Commerce und wie Sie teilnehmen können.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: c523b57270370d87be0f2ab0513f7908bb0a7173
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---

# Beta-Versionen von Adobe Commerce

Adobe Commerce-Beta-Programme bieten Händlern die Möglichkeit, auf Vorabversionsfunktionen und -code zuzugreifen, Feedback zu geben und die Zukunft von Adobe Commerce zu gestalten. Es gibt zwei Arten von Beta-Programmen:

- Öffentliche Beta: Allen Adobe Commerce-Kunden und -Partnern steht ein öffentliches Beta-Programm zur Verfügung
- Private Beta: Für ein privates Beta-Programm ist möglicherweise eine Genehmigung erforderlich, die auf bestimmten Teilnahmekriterien basiert

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (über Adobe Support Services oder anderweitig). Kunden wird empfohlen, Vorsicht walten zu lassen und sich in keiner Weise auf das ordnungsgemäße Funktionieren oder die Leistung der Beta-Versionen und/oder begleitender Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Ankündigung geändert werden. Dementsprechend erfolgt jede Nutzung der Beta-Releases auf eigene Gefahr des Kunden.

## Vorteile der Teilnahme

Der frühzeitige Zugriff auf Funktionen, die Adobe Systems entwickelt, bietet Kunden und Partnern die Möglichkeit, Feedback zu geben, die Produktentwicklung zu gestalten und sich auf die Einführung neuer Funktionen vorzubereiten, bevor sie allgemein verfügbar sind.

## Aktuelle Beta Programme

In den folgenden Abschnitten finden Sie eine Liste der aktiven Beta-Programme.

### Adobe Commerce Optimizer

Adobe Commerce Optimizer verbessert Ihr E-Commerce-Erlebnis mit einer leistungsstarken Storefront, die organischen Traffic, Kundeninteraktion und Umsatz steigert.

Mit Adobe Commerce Optimizer können Sie:

- Erweitern und skalieren Sie Ihren Katalog, ohne Ihren gesamten Commerce-Stack auf eine neue Plattform umzustellen.
- Erfassen Sie Katalogdaten aus beliebigen Quellen.
- Definieren Sie Geschäftskanäle und Richtlinien.
- Personalisierte Suche und Empfehlungen mit KI und ML erstellen.
- Zeigen Sie wichtige Produktdatenverfügbarkeit an, einschließlich Synchronisierungsstatus und Storefront-Ereignisdaten für eine genaue Implementierung und Fehlerbehebung.

[Weitere Informationen](https://experienceleague.adobe.com/docs/commerce/optimizer/overview.html) über Adobe Commerce Optimizer. Wenn Sie am Early-Access-Programm von Adobe Commerce Optimizer teilnehmen möchten, senden Sie eine E-Mail-Anfrage an [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Erweiterte Suchfunktionen für die Live-Suche (Public Beta)

Diese Beta-Version unterstützt drei neue Funktionen in der [`productSearch` Abfrage](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Mehrschichtige Suche** - Suche in einem anderen Suchkontext - Mit dieser Funktion können Sie bis zu zwei Suchebenen für Ihre Suchanfragen durchführen. Beispiel:

   - **Layer 1-Suche** - Suche nach „motor“ in „product_attribute_1“.
   - **Layer 2-Suche** - Suchen Sie nach „Teilenummer 123“ in „product_attribute_2“. In diesem Beispiel wird in den Ergebnissen nach „Motor“ nach „Teilenummer 123“ gesucht.

  Die mehrschichtige Suche ist sowohl für die `startsWith` als auch für die `contains` Suchindizierung verfügbar, wie unten beschrieben:

- **startsWith suchen Indizierung** – Search mit `startsWith` Indizierung. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach Produkten, bei denen der Attributwert mit einer bestimmten Zeichenfolge beginnt.
   - Das Konfigurieren eines &quot;endet mit&quot;-suchen, damit Käufer nach Produkten suchen können, bei denen der Attributwert mit einer bestimmten Zeichenfolge endet. Um eine &quot;endet mit&quot;-suchen zu aktivieren, muss das Produktattribut umgekehrt erfasst werden, und der API-Aufruf sollte ebenfalls eine umgekehrte Zeichenfolge sein.

- **enthält Suchindizierung** - Das Suchattribut enthält die Indizierung. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach einer Abfrage innerhalb einer größeren Zeichenfolge. Beispiel: Ein Käufer sucht in der Zeichenfolge „HAPE-123“ nach der Produktnummer „PE-123“.

      - Hinweis: Dieser Suchtyp unterscheidet sich von dem vorhandenen Suchbegriff[ der eine ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) Suche durchführt. Wenn der Wert Ihres Produktattributs z. B. &quot;Outdoor-Hosen&quot; lautet, gibt ein Ausdruck suchen eine Antwort für &quot;out pan&quot;, aber keine Antwort für &quot;oor ants&quot; zurück. A enthält suchen gibt jedoch eine Antwort für &quot;oor ants&quot; zurück.

Durch diese neuen Bedingungen werden die Suchanfrage Filtermechanismen verbessert, um suchen Ergebnisse zu verfeinern. Die neuen Bedingungen betreffen nicht die Haupt Suchanfrage. Um an der Beta teilzunehmen, senden Sie eine E-Mail-Anfrage an [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Informationen zur Installation der Live Search-Betaversion finden Sie [Live Search-Handbuch](https://experienceleague.adobe.com/en/docs/commerce/live-search/install#install-the-live-search-beta).

### IBM Sterling Order Management-Systemintegration (Private Beta)

Mit diesem Integrationsbeschleuniger für IBM Sterling Order Management können Adobe Commerce-Kunden mit erweiterten Bestellverwaltungsfunktionen beginnen, die auf IBM Sterling OMS basieren. Mit dieser Integration erhalten Händler:

- Echtzeit-Einblick in die Lagerbestände und genaue Liefertermine für Ihre Kunden.
- Automatisierte Beschaffung für Bestellungen auf der Grundlage konfigurierbarer Regeln, sodass Sie Ihr Fulfillment-Netzwerk und Ihren Bestand optimieren können.
- Eine universelle Ansicht von Bestellungen über verschiedene Kanäle von einer einzigen Dashboard aus, damit Ihre Support-Teams außergewöhnlichen Service bieten und Ausnahmen schnell erkennen und beheben können.
- Ein auf Vorlagen basierender Ablauf für das Retourenmanagement zur Vereinfachung des Retourenmanagements.

Um an dieser Beta-Version teilzunehmen, senden Sie eine E-Mail-Anfrage an [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Systems Commerce Foundation (öffentliche Beta)

Jede Betaversion von Adobe Systems Commerce Foundation umfasst alle Änderungen, die bis zum geplanten Veröffentlichungsdatum am Adobe Systems Commerce-Kerncode vorgenommen wurden, einschließlich, aber nicht beschränkt auf die folgenden Funktionsbereiche:

- Neueste Sicherheitskorrekturen
- Leistungsverbesserungen
- GraphQL-Verbesserungen
- Allgemeine Qualitätsfehler-Fehlerbehebungen
- Gemeinschaftsbeiträge
- Erforderliche Änderungen zur Unterstützung der Kompatibilität mit [Adobe Systems Commerce-Diensten](https://experienceleague.adobe.com/docs/commerce/user-guides/home.html)

#### Namenskonvention und -zeitplan

Adobe veröffentlicht Beta-Patches in der Regel zweimal jährlich.

Beta-Versionspakete haben ein `-betaX` Suffix. Beispielsweise verwenden die Adobe Commerce 2.4.7 Beta-Versionspakete die folgende Namenskonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

Siehe den [Veröffentlichungszeitplan](schedule.md) für die Liste der kommenden öffentlichen Beta-Veröffentlichungstermine.

#### Zugriff auf Beta-Versionen

Adobe Commerce-Beta-Versionen werden auf die gleiche Weise wie alle anderen Adobe Commerce-Patch-Versionen verteilt: als Composer-Metapakete auf `https://repo.magento.com`. Der Quell-Code ist auf &quot;[&quot; ](https://github.com/magento/magento2).

Siehe [Schnellstart für die Composer-Installation](../installation/composer.md) für weitere Details.

#### Problem-Reporting

Adobe bietet keinen standardmäßigen Adobe-Support-Service für Beta-Versionen.

Um Feedback zu Beta-Versionen zu senden, folgen Sie unserem [Fluss für die regelmäßige Problemberichterstattung](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) auf [GitHub](https://github.com/magento/magento2).

Unsere internen Teams überwachen alle wichtig Probleme, die im Zusammenhang mit der neuesten Beta-Version gemeldet werden, und priorisieren sie, um sie vor dem GA-Veröffentlichungsdatum zu lösen.
