---
title: Beta-Versionen
description: Erfahren Sie mehr über die Beta-Versionen von Adobe Commerce und wie Sie teilnehmen können.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 1dd4b44c6aa685795e16dccebfaf073dcc0062f2
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Beta-Versionen von Adobe Commerce

Betaprogramme von Adobe Commerce bieten Händlern die Möglichkeit, Zugriff auf Funktionen und Code einer Vorabversion zu erhalten, Feedback zu geben und die Zukunft von Adobe Commerce zu steuern. Es gibt zwei Arten von Beta-Programmen:

- Öffentliche Betaversion: Ein öffentliches Betaprogramm steht allen Adobe Commerce-Kunden und -Partnern zur Verfügung
- Private Beta: Ein privates Beta-Programm kann eine Genehmigung auf der Grundlage von Qualifikationskriterien erfordern, um teilzunehmen

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden ohne Gewährleistung jeglicher Art &quot;AS IS&quot; bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern, zu ändern oder anderweitig zu unterstützen (über Adobe Support Services oder anderweitig). Kunden wird empfohlen, Vorsicht walten zu lassen und sich nicht auf die korrekte Funktionsweise oder Leistung der Beta-Versionen und/oder der zugehörigen Dokumentation oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Dementsprechend erfolgt die Verwendung der Beta-Versionen ausschließlich auf eigenes Risiko des Kunden.

## Vorteile der Teilnahme

Durch frühzeitigen Zugriff auf Funktionen, die Adobe entwickelt, erhalten Kunden und Partner die Möglichkeit, Feedback zu geben, die Produktentwicklung zu gestalten und sich auf die Übernahme neuer Funktionen vor der allgemeinen Verfügbarkeit vorzubereiten.

## Aktuelle Beta-Programme

In den folgenden Abschnitten finden Sie eine Liste der aktiven Betaprogramme.

### IBM Sterling Order Management System-Integration (private Beta-Version)

Dieser Integrationsbeschleuniger für die IBM Sterling Order Management ermöglicht Adobe Commerce-Kunden den Einstieg in erweiterte Auftragsverwaltungsfunktionen, die auf IBM Sterling OMS basieren. Mit dieser Integration erhalten Händler Folgendes:
- Echtzeit-Übersicht über Lagerbestände und genaue Lieferdaten für Ihre Kunden.
- Automatisierte Beschaffung für Bestellungen basierend auf konfigurierbaren Regeln, sodass Sie Ihr Fulfillment-Netzwerk und Ihren Bestand optimieren können.
- Eine universelle Ansicht von Bestellungen über verschiedene Kanäle hinweg über ein einzelnes Dashboard, sodass Ihre Support-Teams außergewöhnlichen Service bereitstellen und Ausnahmen schnell identifizieren und handhaben können.
- Vorlagenfluss zur Rückkehrverwaltung zur Vereinfachung der Rückkehrverwaltung.

Um an dieser Beta-Version teilzunehmen, senden Sie eine E-Mail-Anfrage an [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Datenverbindung und Audience Activation (öffentliche Betaversion)

Die Datenfreigabe zwischen Adobe Commerce und Adobe Experience Platform wurde erweitert, um leistungsfähigere personalisierte Erlebnisse zu ermöglichen. Mit dieser Funktion können Händler:
- Commerce-Kundenprofile freigeben
- Benutzerdefinierte Attribute erstellen
- Commerce-Einblicke in Real-Time CDP und Adobe Journey Optimizer
- Unterstützung mehrerer Datensätze und Datastreams

Um an dieser Beta-Version teilzunehmen, senden Sie eine E-Mail-Anfrage an [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Backoffice Integration Starter Kit (private Beta-Version)

Backoffice [Integrationsstartkit](https://developer-stage.adobe.com/commerce/extensibility/app-development/starter-kit/) bietet Entwicklern einen Beschleuniger zum Erstellen ereignisgesteuerter Integrationen mit Systemen wie ERPs, CRMs und OMSs. Mit dem Starter-Kit können Sie die Entwicklungskosten um bis zu 50% senken. Das Starter-Kit folgt auch den Best Practices von Adobe Commerce, die die Wartungskosten erheblich senken. Starter-Kit-Highlights:
- Datensynchronisation für häufig verwendete Objekte wie Produkt, Bestellung, Kunde, Lager und Versand
- Architektonische Blueprints nach Best Practices
- Onboarding von Skripten zur Beschleunigung der Entwicklung

Um an dieser Beta-Version teilzunehmen, müssen Sie die [Registrierungsformular](https://forms.office.com/r/YbYArqE3DT).

### Adobe Commerce Foundation (öffentliche Betaversion)

Jede Adobe Commerce Foundation Beta-Version enthält alle Änderungen, die bis zum geplanten Veröffentlichungsdatum an den Adobe Commerce-Core-Code gesendet werden, einschließlich, aber nicht beschränkt auf die folgenden Funktionsbereiche:

- Neueste Sicherheitskorrekturen
- Leistungsverbesserungen
- Verbesserungen bei GraphQL
- Allgemeine Fehlerbehebungen für Qualität
- Gemeinschaftsbeiträge
- Erforderliche Änderungen zur Unterstützung der Kompatibilität mit [Adobe Commerce-Dienste](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Namenskonvention und -zeitplan

Adobe veröffentlicht normalerweise zweimal jährlich Beta-Patches.

Beta-Release-Pakete haben eine `-betaX` Suffix. Die Beta-Release-Pakete von Adobe Commerce 2.4.7 verwenden beispielsweise die folgende Benennungskonvention:

- `2.4.7-beta1`
- `2.4.7-beta2`

Siehe [Veröffentlichungszeitplan](schedule.md) für die Liste der anstehenden öffentlichen Beta-Veröffentlichungstermine.


#### Beta-Release-Zugriff

Beta-Versionen von Adobe Commerce werden auf dieselbe Weise wie andere Adobe Commerce Patch-Versionen verteilt: als Composer-Metapakete auf `https://repo.magento.com`. Der Quellcode ist verfügbar unter [GitHub](https://github.com/magento/magento2).

Siehe [Schnellstart für die Installation von Composer](../installation/composer.md) für weitere Details.

#### Problemberichterstellung

Adobe stellt den standardmäßigen Adobe-Support-Service für Beta-Versionen nicht bereit.

Um Feedback zu Beta-Versionen einzureichen, folgen Sie unserem [regelmäßig auftretender Berichtsfluss](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) on [GitHub](https://github.com/magento/magento2).

Unsere internen Teams werden alle kritischen Probleme überwachen, die im Zusammenhang mit der neuesten Beta-Version gemeldet werden, und sie priorisieren, dass sie vor dem GA-Veröffentlichungsdatum gelöst werden.
