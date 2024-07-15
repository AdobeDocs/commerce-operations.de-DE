---
title: Übersicht über die Inhaltssicherheitsrichtlinie
description: Erfahren Sie, wie Sie mithilfe einer Content Security-Richtlinie die Sicherheitsstufe Ihres Adobe Commerce-Stores verbessern können.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Übersicht über die Inhaltssicherheitsrichtlinie

Eine Inhaltssicherheitsrichtlinie (Content Security Policy, CSP) kann zusätzliche Verteidigungsebenen für Adobe Commerce-Installationen bereitstellen, indem sie dazu beiträgt, Cross-Site Scripting (XSS) und damit verbundene Angriffe auf Dateninjektionen zu erkennen und zu minimieren. Dieser häufige Angriffsvektor injiziert böswillige Inhalte, die fälschlicherweise behaupten, von der Website stammen zu wollen. Nachdem der schädliche Inhalt geladen und ausgeführt wurde, kann er die unbefugte Übertragung von Daten auslösen.

CSP bietet einen standardisierten Satz von Direktiven, die dem Browser mitteilen, welche Inhaltsressourcen vertrauenswürdig sind und welche blockiert werden sollen. Mithilfe sorgfältig definierter Richtlinien kann CSP Browser-Inhalte so einschränken, dass nur auf der Whitelist befindliche Ressourcen angezeigt werden.

## Konfiguration

Um eine Störung des Site-Betriebs zu vermeiden, kann CSP in Phasen implementiert werden. CSP verfügt über zwei grundlegende Betriebsmodi: `report-only mode` und `restrict mode`.

**Nur Bericht-Modus**: Der Browser wird angewiesen, Richtlinienverletzungen zu melden, aber nicht durchzusetzen. Jedes Mal, wenn eine angeforderte Ressource CSP verletzt, protokolliert der Browser die resultierenden Fehler in der Konsole. Das Konsolenprotokoll kann dann verwendet werden, um die Ursache jedes Verstoßes zu untersuchen.

Es ist wichtig, alle CSP-Fehler zu überprüfen, sobald sie auftreten, und die Richtlinien zu verfeinern, bis alle erforderlichen Ressourcen auf die Whitelist gesetzt sind. Es ist sicher, auf &quot;`restrict mode`&quot;zu wechseln, wenn keine Fehler mehr auftreten. Andernfalls kann eine schlecht konfigurierte CSP dazu führen, dass der Browser eine leere Seite mit zahlreichen Konsolenfehlern anzeigt. Eine ordnungsgemäß konfigurierte CSP ermöglicht die Bereitstellung von Inhalten aus der Whitelist, ohne dass die Leistung beeinträchtigt wird.

**Modus beschränken**: Der Browser wird angewiesen, alle Inhaltsrichtlinien zu erzwingen und die Veröffentlichung auf auf die Whitelist gesetzte Ressourcen zu beschränken.

Die erste Phase der CSP-Implementierung von Adobe Commerce wurde in Adobe Commerce 2.3.5 eingeführt und CSP standardmäßig in `report-only mode` verfügbar gemacht.  In Adobe Commerce 2.4.7 und höher ist CSP standardmäßig in `restrict-mode` für Zahlungsseiten in den Storefront- und Admin-Bereichen und im Modus `report-only` für alle anderen Seiten konfiguriert. Die entsprechende CSP-Kopfzeile enthält nicht das Schlüsselwort `unsafe-inline` innerhalb der Anweisung `script-src` für Zahlungsseiten. Außerdem sind nur Inline-Skripte auf der Whitelist zulässig.

Da CSP vom Server und nicht vom Administrator konfiguriert wird, benötigen die meisten Händler die Hilfe eines Systemintegrators oder -entwicklers, um sie ordnungsgemäß zu konfigurieren. Siehe [Inhaltssicherheitsrichtlinien](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) im _Commerce PHP Developer Guide_.


## Berichterstellung

Standardmäßig sendet CSP Fehler an die Browser-Konsole, kann jedoch so konfiguriert werden, dass Fehlerprotokolle über HTTP-Anforderungen erfasst werden. Darüber hinaus gibt es mehrere Drittanbieterdienste, mit denen Sie CSP-Verstöße überwachen, erfassen und melden können. CSP-Verstöße können zur Erfassung an einen Endpunkt gemeldet werden, indem der URI aus dem Admin oder aus der Datei `config.xml` für ein benutzerdefiniertes Modul hinzugefügt wird.  Siehe [Report URI-Konfiguration](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) im _Commerce PHP Extensions-Entwicklerhandbuch_.

[Bericht-URI](https://report-uri.io/) ist ein Dienst, der CSP-Verstöße überwacht und die Ergebnisse in einem Dashboard anzeigt. Sowohl Händler als auch Entwickler können den Dienst verwenden, um Berichte zu erhalten, sobald CSP-Verstöße auftreten.
