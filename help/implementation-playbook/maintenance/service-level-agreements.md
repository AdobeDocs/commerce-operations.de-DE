---
title: Service Level Agreements
description: Erfahren Sie mehr über Service-Level-Vereinbarungen und deren Verwendung zur Unterstützung Ihrer Adobe Commerce-Implementierung.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---


# Service Level Agreements (SLAs)

Die Service-Level Agreement (SLA) definiert das von einem Kunden vom Dienstleister erwartete Dienstleistungsniveau mit einfachen Metriken, anhand derer dieser Dienst gemessen wird, sowie gegebenenfalls die Abhilfemaßnahmen oder Sanktionen, falls die vereinbarten Service-Level nicht erreicht werden.

Die SLAs für verschiedene Arten von Störungskritiken können vertraglich festgelegt, aufrechterhalten und gemessen werden. Darüber hinaus kann der Antworttyp mehrere Standards (Gold, Platin) aufweisen, die auf dem vom Kunden benötigten Serviceniveau basieren.

In der folgenden Tabelle wird eine typische Aufschlüsselung der SLA-Metrik mit mehreren Service-Levels beschrieben:

<table>
<thead>
  <tr>
    <th>Problemtyp</th>
    <th>Auswirkung</th>
    <th>Beispiel</th>
    <th colspan="2">Antwort-/Wiederherstellungszeit während unterstützter Geschäftszeiten</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>Gold</td>
    <td>Platinum</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>Kritische Auswirkungen</td>
    <td>Service down oder unbrauchbar</td>
    <td>1 Stunde / 4 Stunden</td>
    <td>1 Stunde / 4 Stunden</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Dienst ist nicht verfügbar</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Der Dienst ist für Endbenutzer nicht verwendbar.</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>Hohe Auswirkung</td>
    <td>Service schwer beeinträchtigt</td>
    <td>2 Stunden / 12 Stunden</td>
    <td>2 Stunden / 8 Stunden</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Die Dienstleistung ist beeinträchtigt</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Dienst verfügbar, aber erzeugt signifikante Fehlermeldungen</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P3</td>
    <td>Mittlere Auswirkung</td>
    <td>Service teilweise beeinträchtigt</td>
    <td>8 Stunden / 16 Stunden</td>
    <td>8 Stunden / 12 Stunden</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Erstellte Fehlermeldungen, keine spürbaren Auswirkungen auf den Endbenutzer</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Fragen zu Funktionen, die beim Kundenstart verwendet werden</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## Deckungsoptionen

Die Deckungsoptionen für zugewiesene SLAs variieren je nach Angebotstyp. Normalerweise sieht der Umfang der Gold- und Platinum-Support-Services wie folgt aus:

![Infografik mit SLA-Deckungsoptionen](../../assets/playbooks/sla-coverage-options.svg)
