---
title: Übersicht über die Content Security-Richtlinie
description: Erfahren Sie, wie Sie den Sicherheitszustand Ihres Adobe Commerce- oder Magento Open Source-Speichers mithilfe einer Inhaltssicherheitsrichtlinie verbessern können.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 8bb692518536f5e7403ed308328e6532c020a230
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Übersicht über die Content Security-Richtlinie

Eine Content Security Policy (CSP) kann zusätzliche Schutzebenen für Adobe Commerce- und Magento Open Source-Installationen bieten, indem sie dazu beiträgt, Cross-Site Scripting (XSS) und damit verbundene Dateninjektionsangriffe zu erkennen und abzuschwächen. Dieser häufige Angriffsvektor funktioniert durch Einschleusen bösartiger Inhalte, die fälschlicherweise behaupten, von der Website zu stammen. Nachdem der schadhafte Inhalt geladen und ausgeführt wurde, kann er die unbefugte Übertragung von Daten auslösen.

CSP bietet einen standardisierten Satz von Anweisungen, die dem Browser mitteilen, welchen Inhaltsressourcen vertraut werden kann und welche blockiert werden sollten. Mithilfe sorgfältig definierter Richtlinien kann CSP Browser-Inhalte so einschränken, dass nur Ressourcen auf der Whitelist angezeigt werden.

## Konfiguration

Um Störungen beim Site-Betrieb zu vermeiden, kann CSP in Phasen implementiert werden. CSP verfügt über zwei grundlegende Betriebsmodi: `report-only mode` und `restrict mode`.

**Nur-Bericht-Modus**: Der Browser wird angewiesen, Richtlinienverletzungen zu melden, sie jedoch nicht durchzusetzen. Jedes Mal, wenn eine angeforderte Ressource gegen CSP verstößt, protokolliert der Browser die resultierenden Fehler in der Konsole. Das Konsolenprotokoll kann dann verwendet werden, um die Ursache jeder Verletzung zu untersuchen.

Es ist wichtig, alle auftretenden CSP-Fehler zu überprüfen und die Richtlinien zu verfeinern, bis alle erforderlichen Ressourcen auf die Whitelist gesetzt sind. Es ist sicher, zu wechseln `restrict mode` Wenn keine Fehler mehr auftreten. Andernfalls kann ein schlecht konfigurierter CSP dazu führen, dass der Browser eine leere Seite mit zahlreichen Konsolenfehlern anzeigt. Ein ordnungsgemäß konfiguriertes CSP ermöglicht die Bereitstellung von Inhalten auf der Whitelist ohne wahrgenommene Auswirkungen auf die Leistung.

**Beschränkungsmodus**: Der Browser wird angewiesen, alle Inhaltsrichtlinien durchzusetzen und die Veröffentlichung auf auf die Whitelist-Ressourcen zu beschränken.

Die erste Phase der Implementierung des Adobe Commerce CSP wurde in Adobe Commerce 2.3.5 eingeführt und das CSP in verfügbar gemacht. `report-only mode` Standardmäßig.  In Adobe Commerce 2.4.7 und höher ist CSP konfiguriert in `restrict-mode` Standardmäßig für Zahlungsseiten in den Bereichen Storefront und Admin und in `report-only` Modus für alle anderen Seiten. Die entsprechende CSP-Kopfzeile enthält nicht die `unsafe-inline` Keyword innerhalb der `script-src` Richtlinie für Zahlungsseiten. Außerdem sind nur Inline-Skripte auf der Whitelist zulässig.

Da CSP nicht vom Administrator, sondern vom Server konfiguriert wird, benötigen die meisten Händler die Unterstützung eines Systemintegrators oder Entwicklers, um es ordnungsgemäß zu konfigurieren. Siehe [Inhaltssicherheitsrichtlinien](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) in der _PHP-Entwicklerhandbuch für Commerce_.


## Berichterstellung

Standardmäßig sendet CSP Fehler an die Browser-Konsole, kann jedoch so konfiguriert werden, dass Fehlerprotokolle per HTTP-Anfrage erfasst werden. Darüber hinaus gibt es mehrere Drittanbieterdienste, mit denen Sie CSP-Verstöße überwachen, erfassen und melden können. CSP-Verstöße können an einen Endpunkt zur Erfassung gemeldet werden, indem der URI vom Administrator oder vom Benutzer hinzugefügt wird `config.xml` Datei für ein benutzerdefiniertes Modul.  Siehe [Konfiguration des Berichts-URI](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) in der _Entwicklerhandbuch für Commerce PHP Extensions_.

[Berichts-URI](https://report-uri.io/) ist ein Service, der CSP-Verstöße überwacht und die Ergebnisse in einem Dashboard anzeigt. Sowohl Händler als auch Entwickler können den Service verwenden, um Berichte zu erhalten, wenn CSP-Verstöße auftreten.
