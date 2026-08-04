---
title: 'Sicherheit und Compliance: Erforderliche Maßnahmen und Fristen'
description: Erfahren Sie mehr über die Durchsetzung der Sicherheit für nicht unterstützte Adobe Commerce in Bezug auf Cloud-Versionen und Softwareabhängigkeiten, einschließlich Fristen, erforderlicher Maßnahmen und Risiken.
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c32adafa-ed01-4b31-997e-2413013911b0id: cc250cf1-34eb-4863-80d0-d170d45ea067id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2: id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Nur Adobe Commerce in Cloud" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Versionen 2.4.4 bis 2.4.9"
color: blue
source-git-commit: 79afa4fa95c425dfd4bc0fd894abc24db2d1b33b
workflow-type: tm+mt
source-wordcount: 2040
ht-degree: 0%

---


# Sicherheits- und Compliance-Hinweis: Erforderliche Maßnahmen und Fristen

>[!NOTE]
>
> **Gilt für:** Adobe Commerce on Cloud (PaaS)-Umgebungen, auf denen Adobe Commerce-Versionen 2.4.4 bis 2.4.9 ausgeführt werden.
>
> Diese Anleitung gilt nicht für [!DNL Adobe Commerce as a Cloud Service] (SaaS)-Umgebungen oder lokale Adobe Commerce-Bereitstellungen.

Die Cybersicherheitslandschaft verändert sich grundlegend, und die bestehenden Abwehrmechanismen müssen sich rasch weiterentwickeln. Sicherheit ist für E-Commerce-Unternehmen von entscheidender Bedeutung, da sie bei Online-Transaktionen mit sensiblen personenbezogenen und geschäftlichen Daten umgehen müssen und diese im Falle eines Verstoßes finanziellen und Identitätsrisiken ausgesetzt sind. PaaS-E-Commerce-Umgebungen verfügen über ein gemeinsames Sicherheits-Verantwortungsmodell zwischen Adobe und unseren Kunden, bei dem Kunden für die Pflege von Abhängigkeiten auf Anwendungsebene, Integrationen mit Software von Drittanbietern und Bereitstellungs-Pipelines verantwortlich sind.

Bei Adobe gehen wir proaktiv auf die sich entwickelnden Risiken ein und stellen sicher, dass wir unsere Adobe Commerce on Cloud-Kunden auf die höchsten Sicherheitsstandards einrichten. Dazu gehören:

* Monatliche und isolierte Sicherheitskorrekturen für schnelleren und vorhersehbaren Schutz vor kritischen Schwachstellen
* Jährliche Patch-Versionen mit langfristigem Support
* Optimierte Lebenszyklusrichtlinien für jede Version mit einem Support-Fenster von drei Jahren

Adobe unternimmt zwar die erforderlichen Schritte, um die Sicherheit unserer Kunden zu gewährleisten, doch das [Shared Responsibility Model](../security-and-compliance/shared-responsibility.md) für Adobe Commerce on Cloud erfordert, dass unsere Kunden immer eine unterstützte Version von Adobe Commerce on Cloud und Software von Drittanbietern verwenden, Anwendungs-Patches anwenden, Erweiterungen von Drittanbietern prüfen und benutzerdefinierten Code schützen. Software, die das Ende der Unterstützung des Anbieters überschritten hat, erhält keine Sicherheits-Patches mehr, sodass Sicherheitsprobleme in der Software nicht behoben werden. Wenn Sie Ihre E-Commerce-Storefront weiterhin mit nicht unterstützter Software betreiben, entsteht ein echtes und wachsendes Sicherheitsrisiko.

Auf dieser Seite werden die Maßnahmen beschrieben, die alle Kundinnen und Kunden in Adobe Commerce on Cloud (Version 2.4.4 bis 2.4.9) ergreifen müssen, um sicherzustellen, dass ihre E-Commerce-Umgebungen sicher bleiben. Außerdem werden die Erzwingungsdaten sowie die Maßnahmen beschrieben, die zu erwarten sind, wenn die Sicherheitsanforderungen nicht erfüllt werden.

## Maßnahmen, die für die Aufrechterhaltung einer sicheren, konformen Umgebung erforderlich sind

Damit Ihre E-Commerce-Umgebung sicher und konform bleibt, müssen alle Kunden in Adobe Commerce on Cloud Services Folgendes verwenden:

1. Unterstützte Versionen aller Drittanbieter-Softwareabhängigkeiten: PHP, MariaDB, Elasticsearch/OpenSearch, Redis und RabbitMQ

1. Eine sichere und unterstützte Version von Adobe Commerce on Cloud Service

Befolgen Sie die folgenden Richtlinien, um zu überprüfen, ob Sie Maßnahmen ergreifen müssen, um Ihre Adobe Commerce in Cloud-Umgebungen zu schützen. Bei Umgebungen, die die Sicherheitsanforderungen nicht innerhalb der in Tabelle 1 unten angegebenen Fristen erfüllen, wird der eingehende Traffic ausgesetzt, wodurch die Storefront offline geschaltet wird. Wenn Sie Bedenken hinsichtlich der Fristverlängerung haben und eine kurze Verlängerung benötigen, wenden Sie sich an Ihr Account-Team oder den Adobe [Support](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case).

**Tabelle 1: Sicherheitsanforderungen und -fristen**

| Ihre Adobe Commerce on Cloud-Version | Upgrade auf unterstützte Softwareabhängigkeiten von Drittanbietern | Führen Sie ein Upgrade auf die neueste Adobe Commerce on Cloud-Version durch oder migrieren Sie zu [!DNL Adobe Commerce as a Cloud Service] |
| --- | --- | --- |
| 2.4.4 oder 2.4.5 | Erforderlich bis zum 30. Oktober 2026. | Erforderlich bis zum 1. Juni 2027 |
| 2.4.6 oder 2.4.7 | Erforderlich bis zum 30. Oktober 2026 oder 31. Mai 2027, je nach Software. | Erforderlich bis zum 1. Juni 2028 |
| 2.4.8 oder 2.4.9 | Erforderlich bis zum 30. Oktober 2026 oder 31. Mai 2027, je nach Software. | Derzeit nicht erforderlich |

## Detaillierte Schritte zum Schutz Ihrer Umgebung

### Aktion 1: Überprüfen und Aktualisieren von Softwareabhängigkeiten von Drittanbietern

Stellen Sie sicher, dass in Ihrer Umgebung vom Anbieter unterstützte Versionen der folgenden Drittanbieter-Softwareabhängigkeiten ausgeführt werden: PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ. Falls nicht, aktualisieren Sie die Softwareabhängigkeit auf eine unterstützte Version.

#### Schritt 1: Überprüfen Sie die Abhängigkeitsversionen der Software von Drittanbietern

1. Melden Sie sich bei der [Cloud-Konsole](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/start/cloud-console) an.
2. Öffnen Sie das entsprechende Projekt und wählen Sie dann die Umgebung aus, die Sie überprüfen möchten.
3. Überprüfen Sie die Service-Konfiguration für diese Umgebung in der `.magento/services.yaml`-Datei, in der die unterstützten Service-Namen und -Versionen definiert sind, die von Adobe Commerce in Cloud Manager verwendet werden.

Detaillierte Anweisungen finden Sie unter [Konfigurieren von Services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml).

Alle nicht unterstützten Softwareabhängigkeiten müssen auf die Versionen aktualisiert werden, die durch die Timelines in Tabelle 2 unten beschrieben sind.

**Tabelle 2: Erforderliche Abhängigkeits-Upgrades**

| Abhängigkeit | Version | Muss aktualisiert werden auf | Deadline |
| --- | --- | --- | --- |
| PHP | 8.1 und darunter | 8.2 oder höher | &#x200B;31. Mai 2027 |
| MariaDB/Galera | 10.5 und darunter | 10.6 oder höher | &#x200B;30. Oktober 2026 |
| MariaDB/Galera | Größer als 10,5, aber kleiner als 10,11 | Version 10.11 oder höher | &#x200B;31. Mai 2027 |
| Elasticsearch | Beliebige Version | OpenSearch: Version 2.19 für Kunden von 2.4.4 und 2.4.5. Version 3 für Kunden ab Version 2.4.6. | &#x200B;30. Oktober 2026 |
| OpenSearch | 1.x | Version 2.19 für Kunden von 2.4.4 und 2.4.5. Version 3 für Kunden ab Version 2.4.6. | &#x200B;31. Mai 2027 |
| Redis | 5 und darunter | Valkey Version 8 oder höher | &#x200B;31. Mai 2027 |
| RabbitMQ | 3.9 und darunter | Version 3.13 oder höher | &#x200B;30. Oktober 2026 |
| RabbitMQ | Größer als 3,9, aber kleiner als 3,13 | 4.3 oder höher | &#x200B;31. Mai 2027 |

#### Schritt 2: Vorbereiten eines Software-Abhängigkeits-Upgrades von Drittanbietern

Adobe unterstützt Sie beim direkten Upgrade dieser Softwareabhängigkeiten.

* **Erste Schritte:** Öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) in dem Sie die Umgebungen, die Sie aktualisieren müssen, und die zugehörigen Abhängigkeiten auflisten. Öffnen Sie Ihr Ticket mindestens 30 Tage vor dem Erzwingungsdatum, damit Adobe die Arbeit planen kann.

* **Ausfallzeit:** Adobe bestätigt beim Planen das erwartete Zeitfenster.

* **Testen** Aktualisieren und validieren Sie eine produktionsfremde Umgebung vor der Produktion. Überprüfen Sie mindestens Checkout, Suche, Warenkorb und alle benutzerdefinierten Integrationen. Die Anforderungen gelten für alle Ihre Umgebungen. Planen Sie daher ein Upgrade für jede Umgebung und nicht nur für die Produktion.

* **Kompatibilität:** Die meisten dieser Änderungen sind Versionsaktualisierungen innerhalb derselben Software und bergen ein geringes Risiko. Die folgenden Änderungen verdienen mehr Aufmerksamkeit:

  * **Elasticsearch zu OpenSearch** und **Redis zu Valkey** sind Migrationen zu anderer Software und keine Versionsaktualisierungen. Benutzerdefinierter Code, Erweiterungen oder Konfigurationen, die auf den ursprünglichen Service verweisen, müssen möglicherweise aktualisiert werden.
  * Ein Upgrade von **PHP 8.1 auf 8.2** kann Veraltungswarnungen in benutzerdefiniertem Code und Erweiterungen von Drittanbietern anzeigen.

Wenn Sie Erweiterungen von Drittanbietern verwenden, sollten Sie sich bei Ihren Anbietern vergewissern, dass ihre aktuellen Versionen Ihre Zielsoftwareversionen unterstützen. Wenn Sie mit einem Lösungsintegrator zusammenarbeiten, beziehen Sie ihn frühzeitig in die Planung, Prüfung und Validierung von Upgrades ein.

### Aktion 2: Überprüfen Sie die Commerce on Cloud-Version und aktualisieren Sie auf eine unterstützte Version.

Überprüfen Sie, welche Adobe Commerce in der Cloud-Version Ihrer Umgebungen ausgeführt wird. Wenn eine Umgebung nicht auf einer unterstützten Version basiert, können Sie auf Version 2.4.9 oder die neueste unterstützte Version aktualisieren oder zu [!DNL Adobe Commerce as a Cloud Service] migrieren.

#### Schritt 1: Überprüfen Sie Ihre Adobe Commerce on Cloud-Version und die erforderlichen Maßnahmen.

1. Melden Sie sich bei Ihrem Adobe Commerce Admin Panel an.

   Die aktuelle Version wird in der rechten unteren Ecke einer beliebigen Admin-Seite angezeigt.

1. Wenn die Version im Admin-Bedienfeld ausgeblendet ist:

   * Stellen Sie eine Verbindung zur [Remote-Umgebung](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/secure-connections#connect-to-a-remote-environment) her.
   * Verwenden Sie das [-Tool von Adobe Commerce](../configuration/cli/config-cli.md) um die Version zu überprüfen.

     ```shell
     bin/magento --version
     ```

Überprüfen Sie die erforderlichen Aktionen für Ihre Adobe Commerce-Version in der folgenden Tabelle.

**Tabelle 3: Anforderungen an die Aktualisierung der Adobe Commerce auf Cloud-Versionen**

| Aktuelle Version von Adobe Commerce in Cloud Manager | Erforderliche Aktion | Deadline |
|---|---|---|
| Version 2.4.4 oder 2.4.5 | Führen Sie ein Upgrade auf Adobe Commerce auf Cloud-Version 2.4.9 durch (oder auf die neueste Version) oder migrieren Sie auf [!DNL Adobe Commerce as a Cloud Service].<br>Grund: v2.4.4 und 2.4.5 erhalten bis zum 31. Mai 2027 nur begrenzte, isolierte Sicherheitskorrekturen für das Kernprogramm. Dazu gehören keine Qualitätskorrekturen, Kompatibilitätsunterstützung für Anwendungsabhängigkeiten (z. B. PHP) oder Plattformabhängigkeits-Updates. Siehe Adobe [Lebenszyklusrichtlinie](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy). | &#x200B;1. Juni 2027 |
| Version 2.4.6 oder 2.4.7 | Aktualisieren Sie auf Adobe Commerce auf Cloud-Version 2.4.9 (oder die neueste Version) oder migrieren Sie auf [!DNL Adobe Commerce as a Cloud Service].<br>Grund: Version 2.4.6 wird bis zum 30. August 2027 erweitert unterstützt und erhält nur begrenzte, isolierte Sicherheitskorrekturen für die Kernanwendung bis zum 31. Mai 2028. Version 2.4.7 wird bis zum 31. Mai 2027 standardmäßig unterstützt und bis zum 31. Mai 2028 erweitert. Siehe Adobe [Lebenszyklusrichtlinie](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy). | &#x200B;1. Juni 2028 |
| Version 2.4.8 oder 2.4.9 | Es ist keine Aktion zum Aktualisieren der Adobe Commerce auf der Cloud-Version erforderlich. Die Fristen für die Abhängigkeit von Software von Drittanbietern in Aktion 1 gelten weiterhin.<br>Grund: Es wurde keine Frist festgelegt. | Derzeit nicht erforderlich |

#### Schritt 2: Bestimmen des Upgrade- oder Migrationspfads

Wenn Sie Ihre Adobe Commerce on Cloud-Version aktualisieren müssen, haben Sie zwei Möglichkeiten:

1. Aktualisieren auf eine unterstützte Adobe Commerce on Cloud-Version
1. Migrieren nach [!DNL Adobe Commerce as a Cloud Service] (SaaS)

Verwenden Sie die folgende Tabelle, um Ihre Optionen zu vergleichen, um den besten Pfad zu ermitteln:

**Tabelle 4: Adobe Commerce on Cloud im Vergleich zu[!DNL Adobe Commerce as a Cloud Service]**

| | Adobe Commerce auf Cloud-Version 2.4.9 | [!DNL Adobe Commerce as a Cloud Service] |
|---|---|---|
| **Was ist es** | Die neueste Adobe Commerce-Version mit vollständiger Sicherheitsabdeckung, Qualitätskorrekturen und Plattformabhängigkeits-Updates. | Adobes vollständig verwaltete Commerce-Plattform, die für kontinuierliche Innovation ohne den Upgrade-Overhead entwickelt wurde. [Weitere Informationen](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview). |
| **Am besten für Sie, wenn** | Sie möchten weiterhin Ihre eigene Infrastruktur, Upgrades und Patches verwalten. | Sie möchten die Upgrade-Zyklen endgültig hinter sich lassen, Ihre Gesamtbetriebskosten senken und die neuesten Funktionen von Adobe ohne zusätzlichen Aufwand automatisch nutzen. |
| **Hauptvorteil** | Erfüllt die Sicherheitsanforderungen und behält gleichzeitig Ihr bestehendes Setup bei. | Eine blitzschnelle Storefront mit Edge-Bereitstellung, ein hochgradig skalierbarer Katalog, native Digital-Asset-Verwaltung und integrierte generative KI - alles auf einer von Adobe verwalteten Infrastruktur. |

## Was passiert, wenn bis zum Ablauf der Frist keine Maßnahmen ergriffen werden?

Adobe unterstützt Sie weiterhin bei den erforderlichen Schritten, um auf unterstützte Versionen von Adobe Commerce on Cloud und Software von Drittanbietern zu aktualisieren.

Wenn eine Umgebung die Sicherheitsanforderungen bis zu den oben genannten Erzwingungsdaten nicht erfüllt hat, ist Adobe gezwungen, geeignete Maßnahmen zu ergreifen, um die Sicherheit für die größere Installationsbasis zu gewährleisten. Dazu gehört auch, den Traffic an die betroffene Infrastruktur zu unterbrechen, sodass Ihre E-Commerce-Storefront offline geht.

Wenn eine Umgebung nach der Traffic-Aussetzung weiterhin nicht konform ist, kann Adobe Cloud-Services beenden und den Stilllegungsprozess starten. Als Ergebnis der Stilllegung werden alle Daten und Assets in der gehosteten E-Commerce-Umgebung, einschließlich aller Instanzen, Umgebungen und Zweige, dauerhaft gelöscht und können nicht wiederhergestellt werden.

## Ressourcen zur Unterstützung von Upgrade oder Migration

**Wenn Sie sich für ein Upgrade auf Adobe Commerce auf Cloud Version 2.4.9 entscheiden:**

* **Upgrade-Kompatibilitätsbericht:** Adobe bietet einen detaillierten Bericht, der genau aufzeigt, was Ihr Upgrade auf Adobe Commerce Version 2.4.9 erfordert, einschließlich des Kostenumfangs. [Generieren Sie Ihren Upgrade-Kompatibilitätsbericht](https://supportinsights.adobe.com/commerce/tab/main).

* **Software-Abhängigkeits-Upgrade:** Da Sie die Softwareabhängigkeiten nicht direkt aktualisieren können, öffnen Sie ein [Support-Ticket](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case), damit Adobe das Upgrade für Sie übernimmt. Weitere Informationen finden Sie unter [Konfigurieren von Services](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml).

**Wenn Sie sich für die Migration zu [!DNL Adobe Commerce as a Cloud Service] entscheiden:**

Adobe bietet Tools, die die Kosten und den Zeitaufwand für die Migration auf [!DNL Adobe Commerce as a Cloud Service] reduzieren. Sie stehen Ihnen kostenlos zur Verfügung. Diese Tools gelten nur für die Migration. Sie werden nicht für Adobe Commerce on Cloud-Versions-Upgrades verwendet. Das vollständige Migrationshandbuch, einschließlich [ Migrationspfade und -phasen, finden Sie ](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview) „Migrationsübersicht“.

* **Migrationsbewertung:** Bewertung der Migrationskomplexität Ihrer Anpassungen. Siehe [Übersicht über das Migrationsbewertungs-Tool](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Datenmigration:** Das Tool [Massenmigration und inkrementelle Datenmigration](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool) verschiebt Ihre Daten in Ihre neue [!DNL Adobe Commerce as a Cloud Service].

* **KI-gestützte Migrations- und Entwicklungs-Tools:** Adobe Developer App Builder und Commerce Storefront powered by Edge Delivery Services beschleunigen die Modernisierung von Storefronts und die Neuplattform von Erweiterungen.

Bei Fragen wenden Sie sich an Ihr Account-Team oder kontaktieren Sie [Support Services](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).

>[!MORELIKETHIS]
>
>* [Lebenszyklusrichtlinie](lifecycle-policy.md)
>* [Richtlinie zur Durchsetzung des Versions-Upgrades für Adobe Commerce on Cloud](version-upgrade-enforcement-policy.md)
>* [Sicherheitsmodell und Betriebsmodell mit gemeinsamer Verantwortung](../security-and-compliance/shared-responsibility.md)
