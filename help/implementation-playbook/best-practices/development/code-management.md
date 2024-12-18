---
title: Best Practices für die Code-Verwaltung
description: Erfahren Sie mehr über Best Practices für die Code-Verwaltung in der Entwicklungsphase von Adobe Commerce-Projekten.
feature: Best Practices
role: Developer
exl-id: 0bff4c7a-1082-4b3e-b19c-bc8ad529b131
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Best Practices für die Code-Verwaltung in Adobe Commerce

Dieses Thema soll Ihnen bei der Entscheidung helfen, ob Sie Git oder Composer verwenden möchten, um benutzerdefinierten Code zu verteilen. Dabei sind die Versionsverwaltung, die Code-Komplexität und die Abhängigkeitsverwaltung zu berücksichtigen.

>[!NOTE]
>
>Diese Best Practices eignen sich am besten für Migrationen und Implementierungen, weniger für die Entwicklung einzelner Module.

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Definitionen

{{$include /help/_includes/gra-definitions.md}}

## Verwendung von Git oder Composer

<table>
<thead>
  <tr>
    <th></th>
    <th>Code, der hauptsächlich über Git verwaltet wird</th>
    <th>Code wird hauptsächlich durch Composer verwaltet</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Verwendung für die Einrichtung einer einzelnen Instanz</td>
    <td>
      <ul>
        <li><strong>Standardansatz für die Verwaltung von Code für eine Einzelinstanz-Einrichtung</strong></li>
        <li>Wann die Code-Basis künftig nicht mehr Teil einer Mehrmarken-GRA sein wird</li>
        <li>Wenn alle Marken auf einer einzigen Instanz als Websites ausgeführt werden</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Wann die Code-Basis Teil einer Multi-Instanz-Einrichtung werden kann oder wird</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>Verwendung für die Einrichtung mehrerer Instanzen</td>
    <td>
      <ul>
        <li>Wenn fast alle Module miteinander verknüpft sind (nicht empfohlen)</li>
        <li>Wenn der Code von einem Team verwaltet wird, das nicht mit Composer vertraut ist</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>Standardansatz für die Code-Verwaltung bei einem Setup mit mehreren Instanzen</strong></li>
        <li>Wenn Adobe die Code-Basis verwaltet oder das Wartungsteam mit Composer vertraut ist</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Funktionsmatrix

| Funktion | Git | Komponist |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Haupt-Code-Repository | Der gesamte Code befindet sich in einem oder mehreren Git-Repositorys | Der gesamte Code befindet sich in den Paketen in einem Composer<br>Repository. Jedes einzelne Composer-Paket wird durch ein Git-Repository dargestellt |
| Code-Speicherort | Die Entwicklung erfolgt im `app/` | Die Entwicklung erfolgt im `vendor/` |
| Zentrale Upgrade-Verwaltung | Adobe Commerce Core wird mit Composer installiert und aktualisiert, das Ergebnis wird in Git übertragen | Adobe Commerce Core wird mit Composer installiert und aktualisiert. Das Ergebnis wird in Git übertragen |
| Verwaltung von Drittanbietermodulen | Module von Drittanbietern werden in `vendor/` installiert, wenn sie über den Marketplace oder packagist.org installiert werden. Andernfalls werden sie in `app/` installiert | Alle Module von Drittanbietern werden im `vendor/` installiert |
| Versionen | Die Freigabe ist durch `git merge` und `git pull` oder `git checkout` gekennzeichnet | Die Freigabe ist durch `composer update` und `git pull` oder `git checkout` gekennzeichnet |
| Anzahl der Git-Repositorys | wenige | Viele |
| Komplexität der Entwicklung | Einfach | Komplex |
| Komplexität der Pull-Anfrage | Einfach | Komplex |
| Komplexität der Code-Überprüfung | Einfach | Einfach |
| Komplexität der Aktualisierung der Entwicklungs-/QA-/UAT-Umgebung | Einfach | Komplex |
| GRA-Unterstützung | ![Ja-Symbol](../../../assets/yes.svg) | ![Ja-Symbol](../../../assets/yes.svg) |
| Module können externe Bibliotheken automatisch installieren | ![Kein Symbol](../../../assets/no.svg) | ![Ja-Symbol](../../../assets/yes.svg) |
| Flexibilität bei der GRA-Zusammensetzung | ![Kein Symbol](../../../assets/no.svg) | ![Ja-Symbol](../../../assets/yes.svg) |
| Abhängigkeitsverwaltung für Module | ![Ja-Symbol](../../../assets/yes.svg) Nur durch `module.xml`, eingeschränkte Funktionalität | ![Ja-Symbol](../../../assets/yes.svg) Vollständige Abhängigkeitsverwaltung über `composer.json` |
| Modulversionierung | ![Ja-Symbol](../../../assets/yes.svg) Sie können eine Version definieren, aber Sie können eine bestimmte Version nicht installieren | ![Ja-Symbol](../../../assets/yes.svg) Unterstützung der Vollversion |
| Bezahlte Services erforderlich | Git-Repository | Git-Repository, Private Packagist (± 600 € pro Jahr) |
| Bitbucket-Integration mit Jira möglich | ![Ja-Symbol](../../../assets/yes.svg) | ![Ja-Symbol](../../../assets/yes.svg) |
| Änderungen am Code sofort zur Installation verfügbar | ![Ja-Symbol](../../../assets/yes.svg) | ![Ja-Symbol](../../../assets/yes.svg) |

## Zu vermeidende Lösungen

1. **Kombinieren von Composer und `app/code` für Ihre Module**

   Dadurch werden alle Nachteile beider Code-Management-Stile in Ihrem Projekt kombiniert. Sie sorgt für unnötige Komplexität, Instabilität und mangelnde Flexibilität.

   Beispiel:
   - Erklären Sie dem Entwicklungs-Team die beiden Workflows Git und Composer (anstelle von nur einem).
   - Installieren Sie inkompatible Module in `app/code`, da es nichts gibt, was dies verhindern könnte.
   - Das Verschieben eines Moduls von `app/code` zu Composer (oder umgekehrt) ist umständlich, insbesondere bei laufender Entwicklung.

1. **SATIS Package Manager**

   Private Packagist kostet ± € 600 pro Jahr. Diese Kosten gelten für die gesamte GRA zusammen, nicht pro Marke. Versuchen Sie nicht, diese Kosten zu vermeiden, indem Sie die kostenlose Lösung Satis verwenden. Satis aktualisiert Ihre Pakete nicht automatisch, wenn Sie Commits an Git senden. Auch Satis hat keine integrierte Autorisierung. Sie müssen einen Webserver verwalten, um Satis ausführen zu können. Am Ende gibt man eine Vielzahl der Abonnementgebühren für Privatpakete aus, um Satis zu erhalten.

1. **Beginnen Sie mit Git und wechseln Sie dann zu Composer**

   Entscheiden Sie sich zu Beginn Ihres Projekts für einen Code-Management-Ansatz. Der Wechsel von Git zu Composer oder umgekehrt ist bei fortlaufender Entwicklung umständlich und kann zu Codeverlust und/oder Verlust des Revisionsverlaufs führen.
