---
title: Qualitätskontrolle
description: Erfahren Sie mehr über Adobe Commerce-Qualitätskontrollprozesse im Zusammenhang mit Implementierungsprojekten.
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
feature: Build
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# Qualitätskontrollprozess und -werkzeuge

![Prozessdiagramm zur Qualitätskontrolle](../../assets/playbooks/quality-control-diagram.svg)

Der im vorangehenden Diagramm beschriebene Qualitätskontrollprozess kann kurz wie folgt beschrieben werden:

<table>
<thead>
  <tr>
    <th>Software-Entwicklungsprozess</th>
    <th>QC-Workflow</th>
    <th>QC</th>
    <th>QC Leader</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Entwicklung</td>
    <td>Planung</td>
    <td></td>
    <td>Überprüfen und Beiträge zu Testplänen</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Erstellen von Testspezifikationen (Testfälle/Testszenarien)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Testdaten vorbereiten und erfassen</td>
  </tr>
  <tr>
    <td></td>
    <td>Testanalyse und -design</td>
    <td>Überprüfen und Beiträge zu Testplänen</td>
    <td>Vorbereitung, Spezifikationen</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Erstellen von Testspezifikationen (Testfälle/Testszenarien)</td>
    <td>Eine Teststrategie für das Projekt schreiben oder überprüfen</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Testdaten vorbereiten und erfassen</td>
    <td> Leitung, Leitung und Überwachung der Analyse, des Designs</td>
  </tr>
  <tr>
    <td>Interne Tests</td>
    <td>Implementierung und Ausführung von Tests</td>
    <td>Implementiert Tests, führt sie aus und protokolliert sie.</td>
    <td>Überwachung der Implementierung und Durchführung der Tests</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Leistung überprüfen und Sicherheit überprüfen - Bewerten Sie die Ergebnisse und die Abweichungen von den erwarteten Ergebnissen.</td>
    <td>Sicherstellen der Rückverfolgbarkeit der Tests auf Testbasis und Behalten der Fehler im Fehlerverfolgungssystem im Auge</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Posten von Fehlern in das Fehlerverfolgungssystem (Jira/Redmine/Trello)</td>
    <td>Priorisieren/Planen von Tests zur Anpassung an die vom PM definierte Projektplanung</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Neutest (Bestätigungstest) nach Fehlerbehebung</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Bewertung und Berichterstellung</td>
    <td>Berichtstest-Fortschritt für QC-Lead und PM</td>
    <td>Bewerten von Testergebnissen und Fortschritt</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Schreiben Sie Testzusammenfassungsberichte anhand der während des Tests gesammelten Informationen.</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>Überprüfen von Kunden-Feedbacks oder Änderungsanfragen (CRs)</td>
    <td>Folgemaßnahmen</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Wiederholungstests und Regressionstests nach Änderung des Quellcodes durchführen</td>
    <td>Steuern</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Aktualisierung der Testspezifikationen</td>
    <td></td>
  </tr>
  <tr>
    <td>Wartung</td>
    <td>Wartung</td>
    <td>Aufgaben überprüfen und dazu beitragen</td>
    <td>Zeit für Aufgaben überprüfen und schätzen</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Erstellen/Aktualisieren von Testspezifikationen</td>
    <td>Fortschritt der Folgetests</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Ausführen von Tests für diese Aufgaben</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Regressionstests durchführen</td>
    <td></td>
  </tr>
</tbody>
</table>

Ähnlich wie bei [tools](project-management-tools.md) Wir haben für den Entwicklungsprozess eine Handvoll von Auswahllösungen und Plattformen ausgewählt, die wir oft für Qualitätskontrolltests verwenden.

| Zweck | Tool |
|---------------------------|---------------------------------------------------|
| Website-Leistungsindex | Google PageSpeed, WebpageTest, JMeter |
| Sicherheit | Adobe Commerce Security Scan Tool, SonarQube, ZAP |
| Problemverwaltungssystem | JIRA |
| UI-Tests | Perfect Pixel, BrowserStack |
| API-Tests | Postman, SoapUI |
| Automatisierungstests | Selenium |


## Website-Leistungsindex

GooglePageSpeed berichtet über die Leistung einer Seite auf Mobilgeräten und Desktop-Geräten und gibt Vorschläge zur Verbesserung dieser Seite.

WebPageTest ist ein Webleistungswerkzeug, das mithilfe echter Browser auf Webseiten zugreift und Zeitmetriken erfasst.

JMeter ist ein Apache-Projekt, das als Lasttestwerkzeug für die Analyse und Messung der Leistung einer Vielzahl von Diensten mit Schwerpunkt auf Webanwendungen verwendet werden kann.

## Sicherheit

SonarQube und ZAP wurden im Entwicklungsprozess vorgestellt, aber wir nehmen auch hier weitere Informationen dazu auf, wie sie am QC-Prozess beteiligt sind.

SonarQube wird auch für die kontinuierliche Überprüfung der Code-Qualität verwendet, um automatische Überprüfungen mit statischer Analyse von Code durchzuführen, um Fehler, Code-Gerüche und Sicherheitslücken zu erkennen.

OWASPZAP (Zed Attack Proxy) soll sowohl von den neuen Anwendungssicherheitsexperten als auch von professionellen Penetrationstests verwendet werden. Zu den integrierten Funktionen gehören das Abfangen des Proxy-Servers, herkömmliche und AJAX Webcrawler, automatisierter Scanner, passiver Scanner, erzwungenes Durchsuchen, Fuzzier, WebSocket-Unterstützung, Skriptsprachen und Plug-in-Hack-Unterstützung.

## UI-Tests

Perfect Pixel ermöglicht es Entwicklern und Markup-Designern, eine halbtransparente Bildüberlagerung über die entwickelte HTML zu platzieren und einen pixelgenauen Vergleich vorzunehmen.

BrowserStack ist eine Cloud-Web- und mobile Testplattform, mit der Entwickler ihre Websites und mobilen Anwendungen über On-Demand-Browser, Betriebssysteme und reale Mobilgeräte hinweg testen können.

## API-Tests

Postman ist die Kooperationsplattform für die API-Entwicklung. Postman vereinfacht die Erstellung von APIs und optimiert die Zusammenarbeit, sodass Sie bessere APIs erstellen können.

SoapUI ist eine Open-Source-Webdienst-Testanwendung für Simple Object Access Protocol (SOAP) und Repräsentationsstatusübertragungen (REST). Die Funktionen umfassen Webdienstabnahme, Aufrufen, Entwicklung, Simulation und Modellierung, Funktionstests, Belastungs- und Compliance-Tests.

## Automatisierungstests

Selenium besteht aus mehreren Komponenten (Selenium Client API, Selenium WebDriver), von denen jede eine bestimmte Rolle bei der Entwicklung der Webanwendungstest-Automatisierung übernimmt.
