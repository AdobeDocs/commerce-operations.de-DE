---
title: Best Practices für das Code-Management
description: Erfahren Sie mehr über die Best Practices für die Code-Verwaltung in der Entwicklungsphase von Adobe Commerce-Projekten.
feature: Best Practices
role: Developer
exl-id: 0bff4c7a-1082-4b3e-b19c-bc8ad529b131
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 0%

---

# Best Practices für die Code-Verwaltung für Adobe Commerce

Dieses Thema soll Ihnen bei der Entscheidung helfen, ob Sie Git oder Composer zur Verteilung von benutzerdefiniertem Code verwenden möchten, unter Berücksichtigung der Versionsverwaltung, der Code-Komplexität und der Abhängigkeitsverwaltung.

>[!NOTE]
>
>Diese Best Practices eignen sich am besten für Migrationen und Implementierungen, weniger für die Entwicklung einzelner Module.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

Sie umfasst sowohl die [globale Referenzarchitektur (GRA)](../../architecture/global-reference/overview.md) als auch Installationen mit einzelnen Instanzen.

## Definitionen

{{$include /help/_includes/gra-definitions.md}}

## Verwendung von Git oder Composer

<table>
<thead>
  <tr>
    <th></th>
    <th>hauptsächlich über Git verwalteter Code</th>
    <th>Code, der hauptsächlich über Composer verwaltet wird</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Verwendung für eine Einzelinstanz</td>
    <td>
      <ul>
        <li><strong>Standardansatz für die Verwaltung von Code für eine Einzelinstanz-Einrichtung</strong></li>
        <li>Wenn die Codebasis in Zukunft nicht Teil einer Markenübergreifenden Analyse sein wird</li>
        <li>Wenn alle Marken auf einer einzigen Instanz als Websites ausgeführt werden</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Wenn die Codebasis in Zukunft Teil eines Multi-Instanz-Setups werden kann oder wird</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>Verwendung für eine Einrichtung mit mehreren Instanzen</td>
    <td>
      <ul>
        <li>Wenn fast alle Module verknüpft sind (nicht empfohlen)</li>
        <li>Wenn der Code von einem Team verwaltet wird, das nicht mit Composer vertraut ist</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>Standardansatz für die Verwaltung von Code für eine Einrichtung mit mehreren Instanzen</strong></li>
        <li>Wenn Adobe die Codebasis verwaltet oder das Wartungsteam mit Composer vertraut ist</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Funktionsmatrix

| Funktion | Git | Verfasser |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Hauptcode-Repository | Der gesamte Code befindet sich in einem oder mehreren Git-Repositorys | Der gesamte Code befindet sich in den Paketen in einem Composer-Repository<br>Jedes einzelne Composer-Paket wird durch ein Git-Repository dargestellt |
| Code-Speicherort | Die Entwicklung erfolgt im Verzeichnis `app/` . | Die Entwicklung erfolgt im Verzeichnis `vendor/` . |
| Verwaltung von Core-Upgrades | Adobe Commerce Core wird mit Composer installiert und aktualisiert. Das Ergebnis wird in Git übernommen | Adobe Commerce Core wird mithilfe von Composer installiert und aktualisiert. Das Ergebnis wird in Git übernommen |
| Verwaltung von Drittanbietermodulen | Drittanbietermodule werden in `vendor/` installiert, wenn sie über den Marketplace oder packagist.org installiert werden. Andernfalls werden sie in `app/` installiert | Alle Module von Drittanbietern werden im Verzeichnis `vendor/` installiert. |
| Versionen | Die Freigabe ist durch die Befehle `git merge` und `git pull` oder `git checkout` gekennzeichnet | Die Freigabe ist durch die Befehle `composer update` und `git pull` oder `git checkout` gekennzeichnet |
| Anzahl der Git-Repositorys | Wenig | Viele |
| Entwicklungskomplexität | Einfach | Komplex |
| Komplexität der Pull-Anforderungen | Einfach | Komplex |
| Komplexität der Codeüberprüfung | Einfach | Einfach |
| Komplexität der Aktualisierung der Entwicklungs-/QA-/UAT-Umgebung | Einfach | Komplex |
| GRA-Unterstützung | ![Ja-Symbol](../../../assets/yes.svg) | ![Ja-Symbol](../../../assets/yes.svg) |
| Module können externe Bibliotheken automatisch installieren | ![Symbol &quot;Nein&quot;](../../../assets/no.svg) | ![Ja-Symbol](../../../assets/yes.svg) |
| Flexibilität bei der GRA-Zusammensetzung | ![Symbol &quot;Nein&quot;](../../../assets/no.svg) | ![Ja-Symbol](../../../assets/yes.svg) |
| Modulabhängigkeitsverwaltung | ![Ja-Symbol](../../../assets/yes.svg) Nur durch `module.xml`, eingeschränkte Funktionalität | ![Ja-Symbol](../../../assets/yes.svg) Vollständige Abhängigkeitsverwaltung durch `composer.json` |
| Modulversionierung | ![Ja-Symbol](../../../assets/yes.svg) Sie können eine Version definieren, eine bestimmte Version kann jedoch nicht installiert werden | ![Ja-Symbol](../../../assets/yes.svg) Unterstützung der Vollversion |
| Benötigte gebührenpflichtige Dienstleistungen | Git-Repository | Git-Repository, Private Packagist (± 600 EUR pro Jahr) |
| Bitbucket-Integration mit Jira möglich | ![Ja-Symbol](../../../assets/yes.svg) | ![Ja-Symbol](../../../assets/yes.svg) |
| Änderungen an Code, der sofort für die Installation verfügbar ist | ![Ja-Symbol](../../../assets/yes.svg) | ![Ja-Symbol](../../../assets/yes.svg) |

## Lösungen zur Vermeidung

1. **Kombinieren von Composer und `app/code` für Ihre Module**

   Dies führt dazu, dass alle Nachteile beider Code-Management-Stile in Ihrem Projekt kombiniert werden. Es erhöht unnötige Komplexität, Instabilität und mangelnde Flexibilität.

   Beispiel:
   - Erklären Sie dem Entwicklungsteam sowohl Git- als auch Composer-Workflows (anstelle von nur einem davon).
   - Installieren Sie inkompatible Module in &quot;`app/code`&quot;, da nichts vorhanden ist, um zu verhindern, dass dies passiert.
   - Das Verschieben eines Moduls von `app/code` in den Composer (oder umgekehrt) ist umständlich, insbesondere bei laufender Entwicklung.

1. **satis package manager**

   Private Packagisten kosten ± 600 € pro Jahr. Diese Kosten sind für die gesamte GRA kombiniert, nicht pro Marke. Versuchen Sie nicht, diese Kosten mit der kostenlosen Lösung Satis zu vermeiden. Satis aktualisiert Ihre Pakete nicht automatisch, wenn Sie Commits zu Git pushen. Auch Satis hat keine eingebaute Autorisierung. Sie müssen einen Webserver unterhalten, um Satis auszuführen. Am Ende verbringen Sie eine Vielzahl von privaten Packagisten Abonnementgebühren für Satis.

1. **Mit Git beginnen und dann zu Composer wechseln**

   Entscheiden Sie sich zu Beginn Ihres Projekts für einen Code-Management-Ansatz. Der Wechsel von Git zu Composer oder umgekehrt mit laufender Entwicklung ist umständlich und könnte zu Code-Verlust und/oder Verlust des Revisionsverlaufs führen.
