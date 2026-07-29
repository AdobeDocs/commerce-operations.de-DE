---
title: 'Sicherheitsdurchsetzungsrichtlinie: Erforderliche Aktionen und Fristen'
description: Erfahren Sie mehr über die Durchsetzung der Sicherheit für nicht unterstützte Adobe Commerce in Bezug auf Cloud-Versionen und Softwareabhängigkeiten, einschließlich Fristen, erforderlicher Maßnahmen und Risiken.
TQID: 'https://experienceleague.adobe.com/0JX-Z-dRjsiQk5jO-LLRi-J4GWdylTh4pOfXRPOabxs'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c32adafa-ed01-4b31-997e-2413013911b0id: cc250cf1-34eb-4863-80d0-d170d45ea067id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2: id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Nur Adobe Commerce in Cloud" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce in Cloud-Projekten."
hide: true
source-git-commit: 93446d5be993e53e94f714a592d519a945dfbebd
workflow-type: tm+mt
source-wordcount: 1915
ht-degree: 0%

---

# Sicherheitsdurchsetzungsrichtlinie: Erforderliche Aktionen und Fristen

Adobe erzwingt Sicherheitsanforderungen für Adobe Commerce in Cloud-Umgebungen, einschließlich unterstützter Softwareabhängigkeitsversionen und unterstützter Adobe Commerce-Versionen. Auf dieser Seite wird beschrieben, was erforderlich ist, welche Erzwingungstermine gelten und was passiert, wenn die Anforderungen nicht erfüllt werden.

## Was ist los?

Die Adobe Corporate Security Policy erfordert, dass alle von Adobe gehosteten Umgebungen für Adobe Commerce on Cloud mit sicherer und konformer Software ausgeführt werden.

1. Unterstützte Versionen aller Drittanbieter-Softwareabhängigkeiten (PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ)

1. Adobe Commerce on Cloud (Version 2.4.8, 2.4.9 oder neueste Version)

Dadurch sollen Sicherheitsrisiken in Ihren E-Commerce-Umgebungen gemindert werden. Bei Umgebungen, die diese Anforderungen nicht innerhalb der in [Tabelle 1) angegebenen Fristen erfüllen](#determine-your-required-actions) wird der eingehende Traffic ausgesetzt, wodurch die Storefront offline geschaltet wird. Beachten Sie diese Mitteilung als Sicherheits- und Compliance-Anforderung mit den Durchsetzungsdaten.

Möglicherweise müssen Sie zwei Aktionen ausführen.

1. Überprüfen Sie, ob die Softwareabhängigkeiten von Drittanbietern unterstützt werden. Falls nicht, aktualisieren Sie auf eine unterstützte Version.

1. Überprüfen Sie, ob Sie Ihre Adobe Commerce on Cloud-Version auf eine unterstützte Version aktualisieren müssen.

### Bestimmen der erforderlichen Aktionen

Suchen Sie in der folgenden Tabelle nach Ihrer Adobe Commerce on Cloud-Version, um zu sehen, was für Sie erforderlich ist.

**Tabelle 1: Erforderliche Maßnahmen und Fristen nach Version**

| **Ihre Version** | **[Aktion 1<br>Upgrade von Softwareabhängigkeiten von Drittanbietern](#action-1-upgrade-third-party-software-dependencies)** | **Aktion 2:<br>[Aktualisieren oder migrieren Sie Ihre Adobe Commerce-Version](#action-2-upgrade-to-a-supported-adobe-commerce-version)** |
| --- | --- | --- |
| 2.4.4 oder 2.4.5 | Erforderliche Maßnahmen bis zum 30. Oktober 2026. | Erforderliche Maßnahmen bis zum 1. Juni 2027 |
| 2.4.6 oder 2.4.7 | Erforderliche Aktion bis zum 30. Oktober 2026 oder 31. Mai 2027, je nach Software. | Erforderliche Maßnahmen bis zum 1. Juni 2028 |
| 2.4.8 oder 2.4.9 | Erforderliche Aktion bis zum 30. Oktober 2026 oder 31. Mai 2027, je nach Software. | Derzeit keine Aktion erforderlich |

## Wer muss nicht handeln?

Diese Mitteilung gilt nicht für:

* Kunden, die [!DNL Adobe Commerce as a Cloud Service] verwenden
* Kunden, die Adobe Commerce in der Cloud-Version 2.4.8 oder 2.4.9 mit unterstützten Softwareabhängigkeiten in allen Umgebungen verwenden

### Aktuelle Versionen überprüfen

Sie benötigen Hilfe von Ihrem E-Commerce-Administrator, um die folgenden Schritte durchzuführen und zu überprüfen, welche Version Sie in jeder Ihrer Adobe Commerce on Cloud-Umgebungen ausführen.

#### Schritt 1: Adobe Commerce auf Cloud-Version überprüfen

1. Melden Sie sich bei Ihrem Adobe Commerce Admin Panel an.

   Die aktuelle Version sollte in der rechten unteren Ecke einer beliebigen Admin-Seite angezeigt werden.

1. Wenn die Version nicht in Admin angezeigt wird, verwenden Sie das Befehlszeilen-Tool [Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli){target="_blank"} um den Versionsbefehl auszuführen:

   ```shell
   bin/magento --version
   ```

#### Schritt 2: Software-Abhängigkeitsversionen überprüfen

1. Melden Sie sich bei der [Cloud-Konsole](https://console.adobecommerce.com/) an.
1. Öffnen Sie das entsprechende Projekt und wählen Sie dann die Umgebung aus, die Sie überprüfen möchten.
1. Überprüfen Sie die Service-Konfiguration für diese Umgebung in der `.magento/services.yaml`-Datei, die die unterstützten Service-Namen und -Versionen definiert, die von Adobe Commerce in der Cloud-Infrastruktur verwendet werden.
Detaillierte Anweisungen finden Sie in der Dokumentation [Konfigurieren von Services](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/services/config-services){target="_blank"}.

## Warum dieses Sicherheitsmandat wichtig ist

Software, die das Ende der Unterstützung des Anbieters überschritten hat, erhält keine Sicherheits-Patches mehr, sodass bekannte Sicherheitsprobleme in dieser Software nicht behoben werden können. Darüber hinaus gilt gemäß der [Adobe-Lebenszyklusrichtlinie](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy):

* Die **Adobe Commerce-Versionen 2.4.4 und 2.4.5** erhalten jetzt bis zum 31. Mai 2027 nur begrenzte, isolierte Sicherheitskorrekturen für das Kernprogramm. Diese eingeschränkte Unterstützung umfasst keine Qualitätskorrekturen, Kompatibilitätsunterstützung für Anwendungsabhängigkeiten (z. B. PHP) oder Plattformabhängigkeits-Updates

* **Adobe Commerce 2.4.6** wird bis zum 30. August 2027 unterstützt und erhält nur begrenzte, isolierte Sicherheitskorrekturen für die Kernanwendung bis zum 31. Mai 2028

* **Adobe Commerce Version 2.4.7** erhält bis zum 31. Mai 2027 Standard-Support und bis zum 31. Mai 2028 erweiterten Support

* **Adobe Commerce in Cloud-Versionen 2.4.8 und 2.4.9** werden weiterhin unterstützt und erfordern derzeit kein Versions-Upgrade.

Wenn Sie Ihre E-Commerce-Storefront weiterhin mit nicht unterstützter Software betreiben, entsteht ein echtes und wachsendes Sicherheitsrisiko für Ihr Unternehmen, einschließlich Ihrer Fähigkeit, die PCI-Compliance zu wahren und die Daten Ihrer Kunden zu schützen.

>[!WARNING]
>
>Wenn Ihre Umgebung die Anforderungen nicht innerhalb der in der Tabelle [Erforderliche Aktionen und Fristen](#determine-your-required-actions) beschriebenen Fristen erfüllt, ist Adobe gezwungen, den eingehenden Traffic an die betroffene Umgebung auszusetzen. Ihre E-Commerce-Storefront wird offline geschaltet und beliefert keine Käufer.

## Was für jede Aktion erforderlich ist

### Aktion 1: Aktualisieren von Softwareabhängigkeiten von Drittanbietern

Abhängig von der -Software müssen alle nicht unterstützten Softwareabhängigkeiten auf der Grundlage der in der folgenden Tabelle freigegebenen Zeitleisten aktualisiert werden. Sie können Ihre Umgebungen in der [Cloud-Konsole](https://console.adobecommerce.com/) anzeigen. Informationen zum Überprüfen der in den einzelnen Umgebungen ausgeführten Abhängigkeitsversionen finden Sie unter [Software-Abhängigkeitsversionen überprüfen](#check-software-dependency-versions). Softwareabhängigkeits-Upgrades gelten für alle Adobe Commerce on Cloud-Versionen 2.4.4 bis 2.4.9.

**Tabelle 2: Anforderungen an Software-Abhängigkeiten-Upgrades**

| Abhängigkeit | Version | Muss aktualisiert werden auf | Erzwingungsdatum |
| --- | --- | --- | --- |
| PHP | 8.1 und darunter | 8.2 oder höher | &#x200B;31. Mai 2027 |
| MariaDB/Galera | 10.5 und darunter | 10.6 oder höher | &#x200B;30. Oktober 2026 |
| MariaDB/Galera | Größer als 10,5, aber kleiner als 10,11 | 10.11 oder höher | &#x200B;31. Mai 2027 |
| Elasticsearch | Beliebige Version | OpenSearch:<br><br>- Version 2.19 für Kunden mit 2.4.4 und 2.4.5<br>- Version 3 für Kunden mit 2.4.6 und höher. | &#x200B;30. Oktober 2026 |
| OpenSearch | 1.x | Version 2.19 für Kunden mit 2.4.4 und 2.4.5.<br>Version 3 für Kunden mit 2.4.6 und höher. | &#x200B;31. Mai 2027 |
| Redis | 5 und darunter | Tal 8 oder höher | &#x200B;31. Mai 2027 |
| RabbitMQ | 3.9 und darunter | 3.13 oder höher | &#x200B;30. Oktober 2026 |
| RabbitMQ | Größer als 3,9, aber kleiner als 3,13 | 4.3 oder höher | &#x200B;31. Mai 2027 |

#### Vorbereiten eines Software-Abhängigkeits-Upgrades von Drittanbietern

Adobe unterstützt Sie beim direkten Upgrade dieser Softwareabhängigkeiten.

* **Erste Schritte:** Öffnen Sie ein Support-Ticket, in dem die Umgebungen, die Sie aktualisieren müssen, und die zugehörigen Abhängigkeiten aufgelistet sind. Öffnen Sie Ihr Ticket mindestens 30 Tage vor dem Erzwingungsdatum, damit unser Team die Arbeit planen kann.

* **Ausfallzeit:** Adobe wird das erwartete Fenster bei der Planung mit Ihnen bestätigen.

* **Testen** Aktualisieren und validieren Sie eine produktionsfremde Umgebung vor der Produktion. Überprüfen Sie mindestens Checkout, Suche, Warenkorb und alle benutzerdefinierten Integrationen. Die Anforderungen gelten für alle Ihre Umgebungen. Planen Sie daher ein Upgrade für jede Umgebung und nicht nur für die Produktion.

* **Kompatibilität:** Die meisten dieser Änderungen sind Versionsaktualisierungen innerhalb derselben Software und bergen ein geringes Risiko. Die folgenden Punkte verdienen besondere Aufmerksamkeit:

  * **Elasticsearch zu OpenSearch** und **Redis zu Valkey** sind Migrationen zu anderer Software und keine Versionsaktualisierungen. Benutzerdefinierter Code, Erweiterungen oder Konfigurationen, die auf den ursprünglichen Service verweisen, müssen möglicherweise aktualisiert werden.
  * **PHP 8.1 bis 8.2** kann veraltete Versionen in benutzerdefiniertem Code und Erweiterungen von Drittanbietern anzeigen.

Wenn Sie Erweiterungen von Drittanbietern verwenden, sollten Sie sich bei Ihren Erweiterungsanbietern vergewissern, dass ihre aktuellen Versionen Ihre Zielversionen unterstützen. Wenn Sie mit einem Lösungsintegrator zusammenarbeiten, beziehen Sie ihn in die Planung und Validierung ein.

### Aktion 2: Aktualisieren auf eine unterstützte Adobe Commerce-Version

Wenn Sie Ihre Adobe Commerce on Cloud-Version aktualisieren müssen, haben Sie zwei Möglichkeiten:

1. [Aktualisieren auf eine unterstützte Adobe Commerce on Cloud-Version](#upgrade-to-adobe-commerce-on-cloud-version-249)
1. [Migrieren zu Adobe Commerce as a Cloud Service (SaaS-Plattform)](#migrate-to-adobe-commerce-as-a-cloud-service)

Das Erzwingungsdatum für Ihre aktuelle Version gilt unabhängig davon, welche Option Sie auswählen.

**Tabelle 3: Richtlinien und Fristen für die Aktualisierung auf eine unterstützte Adobe Commerce on Cloud-Version**

| Aktuelle Version | Aktion | Erzwingungsdatum |
| --- | --- | --- |
| Verwenden von Adobe Commerce in Cloud-Version 2.4.4 oder 2.4.5 | Aktualisieren Sie auf Adobe Commerce auf Cloud-Version 2.4.9 (oder die neueste Version) oder migrieren Sie zu Adobe Commerce as a Cloud Service | &#x200B;1. Juni 2027 |
| Verwenden von Adobe Commerce in Cloud-Version 2.4.6 oder 2.4.7 | Aktualisieren Sie auf Adobe Commerce auf Cloud-Version 2.4.9 (oder die neueste Version) oder migrieren Sie zu Adobe Commerce as a Cloud Service | &#x200B;1. Juni 2028 |
| Verwenden von Adobe Commerce in Cloud-Versionen 2.4.8 oder 2.4.9 | Derzeit ist keine Aktion zum Aktualisieren der Adobe Commerce auf der Cloud-Version erforderlich. Die in Aktion 1 genannten Fristen für die Softwareabhängigkeit gelten weiterhin. | Nicht zutreffend |

## Optionen vergleichen

Um zu entscheiden, welche Option Ihren Anforderungen entspricht, sehen Sie sich die folgende Tabelle an, in der Adobe Commerce in Cloud Version 2.4.9 mit Adobe Commerce as a Cloud Service verglichen wird.

**Tabelle 4: Adobe Commerce on Cloud vs. Adobe Commerce as a Cloud Service**

| | Adobe Commerce auf Cloud-Version 2.4.9 | Adobe Commerce as a Cloud Service |
| --- | --- | --- |
| Was es ist | Die neueste Adobe Commerce-Version mit vollständiger Sicherheitsabdeckung, Qualitätskorrekturen und Plattformabhängigkeits-Updates. | Adobes vollständig verwaltete Commerce-Plattform, die für kontinuierliche Innovation ohne den Upgrade-Overhead entwickelt wurde. [Weitere Informationen](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview). |
| Am besten für Sie, wenn | Sie möchten vorerst weiterhin Ihre eigene Infrastruktur, Upgrades und Patches verwalten. Sie können zu Adobe Commerce as a Cloud Service migrieren, sobald Sie bereit sind. | Sie möchten die Upgrade-Zyklen endgültig hinter sich lassen, Ihre Gesamtbetriebskosten senken und die neuesten Funktionen von Adobe ohne zusätzlichen Aufwand automatisch nutzen. |
| Hauptvorteil | Erfüllt jetzt die Sicherheitsanforderungen, wobei das vorhandene Setup beibehalten wird. | Eine blitzschnelle Storefront mit Edge-Bereitstellung, ein hochgradig skalierbarer Katalog, native Digital-Asset-Verwaltung und integrierte generative KI - alles auf einer von Adobe verwalteten Infrastruktur. |

## Was passiert, wenn Sie nichts unternehmen?

Wenn eine Umgebung diese Anforderungen nicht bis zu den Erzwingungsterminen in [Bestimmen der erforderlichen Aktionen](#determine-your-required-actions) erfüllt, ergreift Adobe die entsprechenden Maßnahmen. Dazu gehört auch, den Traffic an die betroffene Infrastruktur zu unterbrechen, sodass Ihre E-Commerce-Storefront offline geht.

Wenn eine Umgebung nach der Traffic-Aussetzung weiterhin nicht konform ist, kann Adobe Cloud-Services beenden und den Stilllegungsprozess starten. Als Ergebnis der Stilllegung werden alle Daten und Assets in der gehosteten E-Commerce-Umgebung, einschließlich aller Instanzen, Umgebungen und Zweige, dauerhaft gelöscht und können nicht wiederhergestellt werden.

## So hilft Ihnen Adobe

Adobe bietet Tools und Support, um Ihren Übergang so reibungslos wie möglich zu gestalten, unabhängig davon, ob Sie ein Upgrade durchführen oder migrieren.

### Aktualisieren auf Adobe Commerce auf Cloud-Version 2.4.9

* **Upgrade-Kompatibilitätsbericht:** Adobe bietet einen detaillierten Bericht, der genau aufzeigt, was für ein Upgrade auf Adobe Commerce Version 2.4.9 erforderlich ist, einschließlich Zeit und Kostenumfang. [Generieren Sie Ihren Upgrade-Kompatibilitätsbericht](https://supportinsights.adobe.com/commerce/tab/main).

* **Software-Abhängigkeits-Upgrade:** Da Sie die Softwareabhängigkeiten nicht direkt aktualisieren können, [öffnen Sie ein Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket){target="_blank"}, damit Adobe das Upgrade für Sie übernimmt. Weitere Informationen finden Sie unter [Konfigurieren von Services](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/configuration/overview){target="_blank"}.

### Migrieren zu Adobe Commerce as a Cloud Service

Adobe bietet Tools, die die Kosten und den Zeitaufwand für die Migration auf Adobe Commerce as a Cloud Service reduzieren. Diese Tools gelten nur für die Migration. Sie werden nicht für ein Versions-Upgrade auf Adobe Commerce on Cloud verwendet. Das vollständige Migrationshandbuch, einschließlich [ Migrationspfade und -phasen, finden Sie ](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview) „Migrationsübersicht“.

* **Migrationsbewertung:** Bewertung der Migrationskomplexität Ihrer Anpassungen. Siehe [Übersicht über das Migrationsbewertungs-Tool](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Datenmigration:** Das Tool [Massenmigration und inkrementelle Datenmigration](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data) verschiebt Ihre Daten in Ihre neue Adobe Commerce as a Cloud Service-Umgebung.

* **Migration von Storefronts und Erweiterungen:** Die [KI-gestützten Migrations- und ](https://developer.adobe.com/commerce/extensibility/developer-agent/) von Adobe, einschließlich [!DNL Adobe Developer App Builder] und [!DNL Commerce Storefront powered by Edge Delivery Services], beschleunigen die Modernisierung von Storefronts und die Neuplattform von Erweiterungen.

Bei Fragen wenden Sie sich bitte an Ihr Account-Team, Ihren Solution Account Manager, einen Verlängerungsspezialisten oder wenden Sie sich an [Support Services](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).
