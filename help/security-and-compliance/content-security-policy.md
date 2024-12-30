---
title: Übersicht über die Content Security-Richtlinie
description: Erfahren Sie, wie Sie den Sicherheitszustand Ihres Adobe Commerce Stores mithilfe einer Content Security-Richtlinie verbessern können.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Übersicht über die Content Security-Richtlinie

Eine Content Security Policy (CSP) kann zusätzliche Schutzebenen für Adobe Commerce-Installationen bieten, indem sie Cross-Site Scripting (XSS) und damit verbundene Dateninjektionsangriffe erkennt und abwehrt. Dieser häufige Angriffsvektor funktioniert durch Einschleusen von bösartigem Inhalt, der fälschlicherweise behauptet, von der Website zu stammen. Nachdem der schadhafte Inhalt geladen und ausgeführt wurde, kann er die unbefugte Übertragung von Daten auslösen.

CSP bietet einen standardisierten Satz von Anweisungen, die dem Browser mitteilen, welchen Inhaltsressourcen vertraut werden kann und welche blockiert werden sollten. Mithilfe sorgfältig definierter Richtlinien kann CSP Browser-Inhalte einschränken, sodass nur Ressourcen auf der Whitelist angezeigt werden.

## Konfiguration

Um Störungen beim Site-Betrieb zu vermeiden, kann CSP in Phasen implementiert werden. CSP verfügt über zwei grundlegende Betriebsmodi: `report-only mode` und `restrict mode`.

**Nur-Bericht-Modus**: Der Browser wird angewiesen, Richtlinienverletzungen zu melden, sie jedoch nicht durchzusetzen. Jedes Mal, wenn eine angeforderte Ressource gegen CSP verstößt, protokolliert der Browser die resultierenden Fehler in der Konsole. Das Konsolenprotokoll kann dann verwendet werden, um die Ursache jeder Verletzung zu untersuchen.

Es ist wichtig, alle auftretenden CSP-Fehler zu überprüfen und die Richtlinien zu verfeinern, bis alle erforderlichen Ressourcen auf die Whitelist gesetzt sind. Es ist sicher, zu `restrict mode` zu wechseln, wenn keine Fehler mehr auftreten. Andernfalls kann ein schlecht konfigurierter CSP dazu führen, dass der Browser eine leere Seite mit zahlreichen Konsolenfehlern anzeigt. Ein ordnungsgemäß konfiguriertes CSP ermöglicht die Bereitstellung von Inhalten auf der Whitelist ohne wahrgenommene Auswirkungen auf die Leistung.

**Beschränkungsmodus**: Der Browser wird angewiesen, alle Inhaltsrichtlinien durchzusetzen und die Veröffentlichung auf Ressourcen auf der Whitelist zu beschränken.

Die erste Phase der Adobe Commerce-CSP-Implementierung wurde mit Adobe Commerce 2.3.5 eingeführt und machte CSP standardmäßig in `report-only mode` verfügbar.  In Adobe Commerce 2.4.7 und höher ist CSP für Zahlungsseiten in den Bereichen Storefront und Admin standardmäßig in `restrict-mode` und für alle anderen Seiten im `report-only` konfiguriert. Der entsprechende CSP-Header enthält für Zahlungsseiten nicht das `unsafe-inline`-Schlüsselwort in der `script-src`-Direktive. Außerdem sind nur Inline-Skripte auf der Zulassungsliste zulässig.

Da CSP nicht vom Administrator, sondern vom Server konfiguriert wird, benötigen die meisten Händler die Unterstützung eines Systemintegrators oder Entwicklers, um es ordnungsgemäß zu konfigurieren. Siehe [Inhaltssicherheitsrichtlinien](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) im _Commerce PHP-Entwicklerhandbuch_.


## Berichterstellung

Standardmäßig sendet CSP Fehler an die Browser-Konsole, kann jedoch so konfiguriert werden, dass Fehlerprotokolle per HTTP-Anfrage erfasst werden. Darüber hinaus gibt es mehrere Drittanbieterdienste, mit denen Sie CSP-Verstöße überwachen, erfassen und melden können. CSP-Verletzungen können an einen Endpunkt zur Sammlung gemeldet werden, indem der URI von der Admin-Instanz oder, bei einem benutzerdefinierten Modul, von der `config.xml`-Datei hinzugefügt wird.  Siehe [Report URI-Konfiguration](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) im _Commerce PHP Extensions-Entwicklerhandbuch_.

[Berichts-URI](https://report-uri.io/) ist ein Service, der CSP-Verletzungen überwacht und die Ergebnisse in einem Dashboard anzeigt. Sowohl Händler als auch Entwickler können den Service verwenden, um Berichte zu erhalten, wenn CSP-Verstöße auftreten.
