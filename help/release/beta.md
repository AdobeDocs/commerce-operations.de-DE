---
title: Beta-Versionen
description: Erfahren Sie mehr über die Beta-Versionen von Adobe Commerce und wie Sie teilnehmen können.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: f90279e0e152204ac976db307ca14d4418cbcba8
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 0%

---

# Beta-Versionen von Adobe Commerce

Betaprogramme von Adobe Commerce bieten Händlern die Möglichkeit, Zugriff auf Funktionen und Code einer Vorabversion zu erhalten, Feedback zu geben und die Zukunft von Adobe Commerce zu steuern. Es gibt zwei Arten von Beta-Programmen:

- Öffentliche Beta: Ein öffentliches Betaprogramm steht allen Adobe Commerce-Kunden und -Partnern zur Verfügung
- Private Beta: Ein privates Betaprogramm kann eine Genehmigung auf der Grundlage von Kriterien für die Teilnahme erfordern

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden ohne Gewährleistung jeglicher Art &quot;AS IS&quot; bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern, zu ändern oder anderweitig zu unterstützen (über Adobe Support Services oder anderweitig). Kunden wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die korrekte Funktionsweise oder Leistung der Beta-Versionen und/oder der zugehörigen Dokumentation oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Dementsprechend erfolgt die Verwendung der Beta-Versionen ausschließlich auf eigenes Risiko des Kunden.

## Vorteile der Teilnahme

Durch frühzeitigen Zugriff auf Funktionen, die Adobe entwickelt, erhalten Kunden und Partner die Möglichkeit, Feedback zu geben, die Produktentwicklung zu gestalten und sich auf die Übernahme neuer Funktionen vor der allgemeinen Verfügbarkeit vorzubereiten.

## Aktuelle Beta-Programme

In den folgenden Abschnitten finden Sie eine Liste der aktiven Betaprogramme.

### Erweiterte Suchfunktionen für die Live-Suche (Public Beta)

Diese Beta-Version unterstützt drei neue Funktionen in der [`productSearch`-Abfrage](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Ebenensuche** - Suche in einem anderen Suchkontext - Mit dieser Funktion können Sie bis zu zwei Ebenen der Suche für Ihre Suchabfragen durchführen. Beispiel:

   - **Suche auf Ebene 1** - Suchen Sie nach &quot;motor&quot;auf &quot;product_attribute_1&quot;.
   - **Suche auf Ebene 2** - Suchen Sie nach &quot;Teilenummer 123&quot;auf &quot;product_attribute_2&quot;. In diesem Beispiel wird in den Ergebnissen nach &quot;motor&quot;nach &quot;part number 123&quot;gesucht.

  Die Ebenensuche ist für die Suchindexierung `startsWith` und die Suchindexierung `contains` wie unten beschrieben verfügbar:

- **startsWith search indexation** - Suche mithilfe der `startsWith` -Indexierung. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach Produkten, bei denen der Attributwert mit einer bestimmten Zeichenfolge beginnt.
   - Konfiguration einer Suche &quot;endet mit&quot;, damit Käufer nach Produkten suchen können, bei denen der Attributwert mit einer bestimmten Zeichenfolge endet. Um die Suche &quot;endet mit&quot;zu aktivieren, muss das Produktattribut umgekehrt aufgenommen werden und der API-Aufruf sollte auch eine umgekehrte Zeichenfolge sein.

- **enthält Suchindexierung** - Suchen Sie nach einem Attribut, das die Indexierung enthält. Diese neue Funktion ermöglicht Folgendes:

   - Suchen nach einer Abfrage in einer größeren Zeichenfolge. Beispiel: Ein Käufer sucht in der Zeichenfolge &quot;HAPE-123&quot;nach der Produktnummer &quot;PE-123&quot;.

      - Hinweis: Dieser Suchtyp unterscheidet sich von der vorhandenen [Phrasensuche](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase), die eine automatische Suche durchführt. Wenn Ihr Produktattributwert beispielsweise &quot;Hosen im Freien&quot;lautet, gibt die Wortgruppensuche eine Antwort für &quot;out pan&quot;zurück, gibt jedoch keine Antwort für &quot;oor ants&quot;zurück. Eine enthält Suche gibt jedoch eine Antwort für &quot;oor ants&quot;zurück.

Diese neuen Bedingungen verbessern den Filtermechanismus für Suchabfragen, um die Suchergebnisse zu verfeinern. Diese neuen Bedingungen wirken sich nicht auf die Hauptsuchabfrage aus. Für den Beta-Zugriff senden Sie eine E-Mail an `sagonzal@adobe.com` oder `alexj@adobe.com`.

Informationen zum Installieren der Beta-Version der Live-Suche finden Sie im [Handbuch zur Live-Suche](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install#install-the-live-search-beta).

### Experience Manager Assets-Integration für Commerce (Private Beta)

Die Experience Manager Assets-Integration für Commerce ermöglicht eine effiziente Verwaltung und Bereitstellung einer großen Anzahl von Produktbildern von Experience Manager Assets nach Adobe Commerce, ohne dass ein geringer oder gar kein betrieblicher Aufwand erforderlich ist.

Wichtigste Funktionen:

- Integration von Plug and Play - Bieten Sie eine Adobe-gestützte, vordefinierte Integration zwischen Experience Manager Assets und Adobe Commerce, um Händler in die Lage zu versetzen, sich auf das Wesentliche zu konzentrieren - mit geringeren Betriebskosten und einer höheren Effizienz.

- Personalisieren Sie Produktbilder im Maßstab. Verwenden Sie Experience Manager Assets, um Millionen von Produktvarianten für personalisierte Commerce-Erlebnisse mit benutzeroberflächenbasierten Bearbeitungswerkzeugen, der generativen Inhaltserstellung mithilfe von Adobe Firefly und zugewiesenen Asset-Workflows zu generieren, um Markenkonsistenz zu gewährleisten. Sobald Sie mit den Assets zufrieden sind, stellen Sie sie mithilfe der Experience Manager Assets-Integration nahtlos an Ihre Commerce-Storefronts bereit.

- Einfaches Onboarding - Vereinfachen Sie das Onboarding von Händlern mit einem konfigurierbaren Synchronisierungsprozess, der eine vollständige Synchronisierung zwischen dem Experience Manager Assets-Repository und dem Commerce-Katalog ermöglicht.

- Flexible Übereinstimmungsstrategie - Die Integration umfasst standardmäßige Algorithmen für die Asset-Zuordnung basierend auf Produkt-SKUs, die Bilder zwischen AEM Assets und Commerce synchronisieren, und ist mit Adobe Developer App Builder erweiterbar. Arbeiten Sie mit Ihrem Lösungspartner zusammen, um zusätzlich zur Integration eine benutzerdefinierte Asset-Abgleichstrategie zu erstellen, um jede Asset-Management-Repository-Struktur aufzunehmen.

Um an der Beta-Version teilzunehmen, senden Sie eine E-Mail-Anfrage an [Shaun McCran](mailto:mccran@adobe.com).

### IBM Sterling Order Management-Systemintegration (Private Beta)

Dieser Integrationsbeschleuniger für IBM Sterling Order Management ermöglicht Adobe Commerce-Kunden den Einstieg in erweiterte Auftragsverwaltungsfunktionen, die von IBM Sterling OMS unterstützt werden. Mit dieser Integration erhalten Händler Folgendes:

- Echtzeit-Übersicht über Lagerbestände und genaue Lieferdaten für Ihre Kunden.
- Automatisierte Beschaffung für Bestellungen basierend auf konfigurierbaren Regeln, sodass Sie Ihr Fulfillment-Netzwerk und Ihren Bestand optimieren können.
- Eine universelle Ansicht von Bestellungen über verschiedene Kanäle hinweg über ein einzelnes Dashboard, sodass Ihre Support-Teams außergewöhnlichen Service bereitstellen und Ausnahmen schnell identifizieren und handhaben können.
- Vorlagenfluss zur Rückkehrverwaltung zur Vereinfachung der Rückkehrverwaltung.

Um an dieser Beta-Version teilzunehmen, senden Sie eine E-Mail-Anfrage an [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Datenverbindung und Audience Activation (Public Beta)

Die Datenfreigabe zwischen Adobe Commerce und Adobe Experience Platform wurde erweitert, um leistungsfähigere personalisierte Erlebnisse zu ermöglichen. Mit dieser Funktion können Händler:

- Commerce-Kundenprofile freigeben
- Benutzerdefinierte Attribute erstellen

Um an dieser Beta-Version teilzunehmen, senden Sie eine E-Mail-Anfrage an [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation (Public Beta)

Jede Adobe Commerce Foundation Beta-Version enthält alle Änderungen, die bis zum geplanten Veröffentlichungsdatum an den Adobe Commerce-Core-Code gesendet werden, einschließlich, aber nicht beschränkt auf die folgenden Funktionsbereiche:

- Neueste Sicherheitskorrekturen
- Leistungsverbesserungen
- Verbesserungen bei GraphQL
- Allgemeine Fehlerbehebungen für Qualität
- Gemeinschaftsbeiträge
- Erforderliche Änderungen zur Unterstützung der Kompatibilität mit [Adobe Commerce-Diensten](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Namenskonvention und -zeitplan

Adobe veröffentlicht normalerweise zweimal jährlich Beta-Patches.

Beta-Release-Pakete haben das Suffix &quot;`-betaX`&quot;. Die Beta-Release-Pakete von Adobe Commerce 2.4.7 verwenden beispielsweise die folgende Benennungskonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

Eine Liste der bevorstehenden öffentlichen Beta-Veröffentlichungstermine finden Sie im [Veröffentlichungsplan](schedule.md) .


#### Beta-Versionszugriff

Beta-Versionen von Adobe Commerce werden auf dieselbe Weise wie alle anderen Adobe Commerce Patch-Versionen verteilt: als Composer-Metapakete auf `https://repo.magento.com`. Der Quellcode ist auf [GitHub](https://github.com/magento/magento2) verfügbar.

Weitere Informationen finden Sie unter [Schnellstart für die Composer-Installation](../installation/composer.md) .

#### Problemberichterstellung

Adobe stellt den standardmäßigen Adobe-Support-Service für Beta-Versionen nicht bereit.

Um Feedback zu Beta-Versionen zu senden, folgen Sie unserem [normalen Ablauf zur Problemberichterstellung](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) auf [GitHub](https://github.com/magento/magento2).

Unsere internen Teams werden alle kritischen Probleme überwachen, die im Zusammenhang mit der neuesten Beta-Version gemeldet werden, und sie priorisieren, dass sie vor dem GA-Veröffentlichungsdatum gelöst werden.
