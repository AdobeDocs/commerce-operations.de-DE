---
title: Adobe Commerce-Lebenszyklusrichtlinie
description: Erfahren Sie mehr über Adobe Commerce-Support-Zeiträume, das Ende der Unterstützung und Cloud-Durchsetzungsdaten, Übergangsbestimmungen und Pfade zu einer unterstützten Version.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 620523021580a9dba44e0e2041d8100761b8bce1
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 0%

---


# Adobe Commerce-Lebenszyklusrichtlinie

Adobe Commerce folgt einer definierten Software-Lebenszyklusrichtlinie, um sicherzustellen, dass Kunden mit sicheren, unterstützten Versionen arbeiten. Wenn Sie eine ältere Version verwenden, ist es wichtig zu verstehen, wo in diesem Lebenszyklus Sie hinfallen - und vor den Erzwingungsfristen zu handeln. Dieses Thema behandelt Definitionen der Support-Stufe, Termine für das Ende der Unterstützung und die Durchsetzung, Übergangsbestimmungen für Versionen, die sich dem Ende ihrer Lebensdauer nähern, und Pfade, auf denen weiterhin eine unterstützte Version verfügbar ist.

>[!IMPORTANT]
>
>Adobe führt eine Richtlinie zur erzwungenen Versionsaktualisierung für Adobe Commerce on Cloud (PaaS) ein. Ab **1. Juni 2027** Adobe keine Cloud-Umgebungen mehr, in denen nicht unterstützte Commerce-Versionen ausgeführt werden, und behält sich das Recht vor, sie zu deaktivieren. Wenn Sie in der Cloud (PaaS) ausführen, müssen Sie zu einer unterstützten Adobe Commerce-Version wechseln oder vor dem Veröffentlichungsdatum [Ende der erweiterten Unterstützung](lifecycle-policy.md#end-of-support-dates) für Ihre Release-Zeile zu [!DNL Adobe Commerce as a Cloud Service] migrieren. Unter [Richtlinie zur Durchsetzung des Cloud-](version-upgrade-enforcement-policy.md)-Upgrades) finden Sie Erzwingungsdaten, betroffene Versionen und was passiert, wenn Sie auf einer nicht unterstützten Version bleiben.

## Grundlagen zu Support-Ebenen

Adobe Commerce definiert drei Support-Ebenen für Versionsinformationen. In den folgenden Abschnitten werden die einzelnen Ebenen beschrieben.

### Regelmäßige Unterstützung

Der standardmäßige dreijährige Support-Zeitraum ab dem Datum der allgemeinen Verfügbarkeit. Der reguläre Support umfasst Qualitätskorrekturen, Sicherheits-Patches und vollständigen Adobe Commerce-Support auf Abruf.

- **Qualitätskorrekturen** - Kunden können auf Qualitätskorrekturen zugreifen, indem sie sich an den [Adobe Commerce Support ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) oder über die Self-Service-[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) wenden.

- **Sicherheitskorrekturen** - Adobe bietet Sicherheitskorrekturen durch kumulative Sicherheits-Patches und nicht kumulative [isolierte Sicherheits-Patch-Dateien](versioning-policy.md#isolated-security-patch-file) für den dreijährigen Support-Zeitraum.

- **Hotfixes** - Für kritische Sicherheitsprobleme, z. B. Zero-Day-Sicherheitslücken, stellt Adobe [Hotfixes](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) für alle Kundinnen und Kunden mit einer unterstützten Version bereit, auch wenn sie nicht über das neueste Patch oder die neueste Sicherheits-Patch-Version verfügen. Beachten Sie, dass ein Hotfix nicht vollständig ist und nicht alle Sicherheitsprobleme behebt, die durch eine Aktualisierung auf die neueste Version behoben würden.

### Erweiterte Unterstützung

Eine einjährige Support-Verlängerung, die über den regulären Support hinaus für bestimmte Versionshinweise verfügbar ist. Enthält Qualitäts- und Sicherheits-Patches. Nur für Adobe Commerce-Kunden verfügbar — nicht für Magento Open Source verfügbar.

### Übergangszeitraum nur für Sicherheitsleistungen

Für bestimmte Versionen, deren erweiterte Unterstützung 2025 oder 2026 endete, ist eine einmalige, zeitlich begrenzte Übergangszeit verfügbar. Die Übergangszeit, in der nur die Sicherheit verfügbar ist, bietet nur begrenzte, isolierte Sicherheitskorrekturen. Adobe Commerce On-Call-Support ist nicht enthalten. Dieser Zeitraum entspricht weder einer regelmäßigen noch einer verlängerten Unterstützung und wird nicht weiter verlängert. Behandeln Sie sie als Migrationszeitraum, nicht als langfristige Support-Stufe. Siehe [Übergangsbestimmungen nur für die Sicherheit](#security-only-transitional-provisions).

## Ende der Support-Termine

In der folgenden Tabelle wird der gesamte Lebenszyklus für jede Adobe Commerce-Version angezeigt, einschließlich der Erzwingungstermine für die Aktualisierung der neuen Version für Adobe Commerce in Cloud (PaaS)-Umgebungen.

| -Version | Allgemeine Verfügbarkeit | Ende der regulären Unterstützung | Ende der erweiterten Unterstützung | Ende des reinen Sicherheitszeitraums | [Erzwingungsdatum für das Versions-Upgrade (nur Cloud)](version-upgrade-enforcement-policy.md) |
|---------|----------------------|------------------------|-------------------------|-----------------------------|-----------------------------------------------|
| Adobe Commerce 2.4.9 | &#x200B;12. Mai 2026 | &#x200B;31. Mai 2029 | TBD | Nicht zutreffend | TBD |
| Adobe Commerce 2.4.8 | &#x200B;8. April 2025 | &#x200B;31. Mai 2028 | TBD | Nicht zutreffend | TBD |
| Adobe Commerce 2.4.7 | &#x200B;9. April 2024 | &#x200B;31. Mai 2027 | &#x200B;31. Mai 2028 | Nicht zutreffend | &#x200B;1. Juni 2028 |
| Adobe Commerce 2.4.6 | &#x200B;14. März 2023 | &#x200B;11. August 2026 | &#x200B;30. August 2027 | &#x200B;31. Mai 2028 | &#x200B;1. Juni 2028 |
| Adobe Commerce 2.4.5 | &#x200B;9. August 2022 | &#x200B;12. August 2025 | &#x200B;12. August 2026 | &#x200B;31. Mai 2027 | &#x200B;1. Juni 2027 |
| Adobe Commerce 2.4.4 | &#x200B;12. April 2022 | &#x200B;12. April 2025 | &#x200B;14. April 2026 | &#x200B;31. Mai 2027 | &#x200B;1. Juni 2027 |

{style="table-layout:auto"}

Wenn sich Ihre Release-Reihe diesen Terminen nähert oder überschritten wird, finden Sie weitere Informationen unter [Upgrade- und Migrationsoptionen](#upgrade-and-migration-options). Details zur Cloud-Durchsetzung finden Sie unter [Richtlinie zur Durchsetzung der Cloud-Version](version-upgrade-enforcement-policy.md).

### Support-Zeitleiste nach Quartal

In diesem Diagramm können Sie sich überschneidende Support-Fenster in allen Versionshinweisen anzeigen. Die genauen Enddaten sind den Tabellen oben zu entnehmen. Die erweiterte Unterstützung für 2.4.8 und 2.4.9 ist noch bekannt und wird nicht angezeigt.

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
    <th colspan="4">2029</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.9</td>
    <td colspan="17"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**key**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>Regelmäßige Unterstützung</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Erweiterte Unterstützung</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Übergangszeitraum nur für Sicherheitsleistungen</td>
  </tr>
 </tbody>
</table>

## Übergangsbestimmungen nur für die Sicherheit {#security-only-transitional-provisions}

Als einmalige Maßnahme für die Versionen 2.4.4, 2.4.5 und 2.4.6 mit erweiterter Unterstützung, die bereits 2025 und 2026 endete, bietet Adobe die folgenden Übergangsbestimmungen, um Ihnen zusätzliche Zeit für die Planung und Ausführung Ihrer Migration oder Aktualisierung zu geben. Diese Bestimmungen ersetzen nicht die [Durchsetzung der Cloud-Version](version-upgrade-enforcement-policy.md) für PaaS-Umgebungen. Sie müssen vor dem veröffentlichten Erzwingungsdatum weiterhin ein Upgrade durchführen oder migrieren.

| Version | Übergangsbestimmung | Zeitraum | Was enthalten ist | Was nicht enthalten ist |
|---------|------------------------|--------|------------------|----------------------|
| 2.4.4 und 2.4.5 | Übergangszeitraum nur für Sicherheitsleistungen | Bis zum 31. Mai 2027 | Eingeschränkte, isolierte Sicherheitskorrekturen von Fall zu Fall | Adobe Commerce-Support auf Abruf, Qualitätskorrekturen, Plattformabhängigkeits-Updates |
| 2.4.6 | Verlängerter Support + Übergangszeitraum nur für Sicherheitszwecke | Verlängerung der Unterstützung bis zum 30. August 2027. Nur-Sicherheit-Zeitraum bis zum 31. Mai 2028. | Verlängerter Support-Zeitraum: Qualitäts- und Sicherheits-Patches Nur-Sicherheit-Zeitraum: begrenzte isolierte Sicherheitskorrekturen. | Während des Nur-Sicherheit-Zeitraums: Adobe Commerce-Bereitschaftsdienst, Qualitätskorrekturen, Plattformabhängigkeits-Updates |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>Die Übergangszeit, die ausschließlich für die Sicherheit gilt, ist eine einmalige Ausnahme. Sie wird nicht über die veröffentlichten Daten hinaus verlängert. Behandeln Sie den Zeitraum „Nur Sicherheit“ als Migrationszeit, nicht als langfristige Support-Stufe.

## Platform-Abhängigkeiten

Um auf einer unterstützten Commerce-Version zu bleiben, sind auch unterstützte Plattformabhängigkeiten erforderlich. Adobe bietet keine Sicherheits- und Qualitätskorrekturen für Services und Softwareabhängigkeiten von Drittanbietern - wie z. B. PHP, MariaDB, OpenSearch, Redis, Valkey, RabbitMQ und andere -, die möglicherweise das Ende des Lebenszyklus erreichen, während Sie die dreijährige oder verlängerte Support-Periode für Adobe Commerce durchlaufen.

Sie sind für die Pflege aller Drittanbieterabhängigkeiten und Plattformdienste für Versionen verantwortlich, die aktiv unterstützt werden. Unter [Systemanforderungen](../installation/system-requirements.md) finden Sie eine vollständige Liste der getesteten und unterstützten Technologien von Drittanbietern.

Adobe bietet keine Sicherheitsunterstützung oder Hilfe für Bereitstellungen, auf denen nicht unterstützte Abhängigkeitsversionen ausgeführt werden. Siehe [Sicherheitsmodell und Betriebsmodell mit geteilter Verantwortung](../security-and-compliance/shared-responsibility.md) für Details.

>[!IMPORTANT]
>
>Das Ausführen nicht unterstützter Abhängigkeitsversionen kann zu einer Sicherheitslücke in Ihrer Cloud-Instanz führen, die Adobe nicht beheben kann. In solchen Fällen behält sich Adobe das Recht vor, ein Upgrade der betroffenen Software-Abhängigkeit durchzusetzen oder den Service zu deaktivieren, wenn ein Upgrade nicht möglich ist - unabhängig von Ihrem Adobe Commerce-Versionssupport-Status.

## PHP End of Life und PCI-Compliance

Sie sind dafür verantwortlich, den Support-Status der in Ihren Umgebungen verwendeten PHP-Versionen zu überwachen.

Die folgenden PHP-Versionen, die von älteren Commerce-Versionen verwendet werden, haben das Ende des Lebenszyklus erreicht oder werden es erreichen, was direkte Auswirkungen auf die PCI-Compliance hat.

| PHP-Version | Ende der Nutzungsdauer | Betroffene Commerce-Versionen | Auswirkungen auf die PCI-Compliance |
|-------------|------------------|----------------------------|------------------------|
| PHP 8.1 | &#x200B;31. Dezember 2025 | 2.4.4, 2.4.5 und 2.4.6 (wenn PHP 8.1 verwendet wird) | PCI-Compliance in Gefahr — Die Ausführung von PHP 8.1 nach dem Ende des Lebenszyklus bedeutet, dass Sicherheitslücken in PHP möglicherweise keine Fehlerbehebungen erhalten, was die PCI-Compliance gefährdet. Bewertung des Compliance-Status und Priorisierung von Upgrades |
| PHP 8.2 | &#x200B;31. Dezember 2026 | 2.4.6 (wenn PHP 8.2 verwendet wird) | PCI-Compliance ab Ende 2026 gefährdet — Planen Sie ein Upgrade oder eine Migration vor Ende 2026, um die PCI-Compliance aufrechtzuerhalten. |

{style="table-layout:auto"}

### PCI-Compliance-Hinweis

PCI-Compliance liegt in der Verantwortung des Händlers, zu bewerten. Adobe empfiehlt den Händlern dringend, sich mit ihrem qualifizierten Sicherheitsexperten in Verbindung zu setzen und so bald wie möglich den Umstieg auf eine unterstützte Commerce-Version und eine unterstützte PHP-Version zu priorisieren. Informationen zu den Zeitplänen für die PHP-Unterstützung [ Sie unter ](https://www.php.net/supported-versions.php)PHP-unterstützte Versionen[ und „PHP End of Life](https://www.php.net/eol.php).

## Upgrade- und Migrationsoptionen

Wenn Sie eine Version verwenden, die das Ende des Support-Zeitraums naht oder überschritten hat, ergreifen Sie jetzt die erforderlichen Maßnahmen. Wenn Sie auf einer nicht unterstützten Version bleiben, riskieren Sie für Ihren Store Sicherheitslücken, Compliance-Probleme und den Verlust von Support. Adobe bietet die folgenden Pfade zum Wechsel zu einer unterstützten Version.

### Empfohlener Pfad: Migrieren zu Adobe Commerce as a Cloud Service (ACCS)

[!DNL Adobe Commerce as a Cloud Service] ist die gehostete Commerce-Plattform der nächsten Generation von Adobe und Adobes empfohlenes langfristiges Ziel für alle Kunden von Adobe Commerce on Cloud.

- Adobe verwaltet alle Infrastrukturen, Patches und Upgrades automatisch.
- Sie sind immer auf unterstützter, konformer Infrastruktur - die Situation nach dem Ende der Nutzungsdauer tritt nicht wieder auf.
- Sie erhalten Zugriff auf die neuesten Funktionen von Adobe: KI-gestütztes Merchandising, zusammensetzbare Storefront-Architektur und native Adobe Experience Cloud-Integrationen.
- Sie können wiederkehrende Upgrade-Zyklen vermeiden.

Wenden Sie sich an Ihr Adobe-Account-Team, um eine Migrationsbewertung durchzuführen. Siehe [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview) für eine Produktübersicht.

### Alternativpfad: Upgrade auf eine unterstützte Adobe Commerce-On-Cloud- oder -On-Premise-Version

Wenn Sie nicht sofort zu [!DNL Adobe Commerce as a Cloud Service] migrieren können, können Sie auf die neueste derzeit unterstützte lokale Adobe Commerce- oder Cloud-Version aktualisieren. Dadurch gelangen Sie zu einem vollständig unterstützten, modernen Infrastrukturstapel, während Ihr vorhandenes PaaS-Bereitstellungsmodell beibehalten wird.

Beachten Sie, dass durch diesen Pfad zukünftige Upgrade-Verpflichtungen nicht entfallen. PaaS-Kunden müssen mit dem Upgrade fortfahren, wenn die Versionszeilen das Erzwingungsdatum für das Versions-Upgrade erreichen.
