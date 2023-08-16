---
title: Übersicht über die Inhaltssicherheitsrichtlinie
description: Erfahren Sie, wie Sie mithilfe einer Content Security-Richtlinie die Sicherheitsstufe Ihres Adobe Commerce- oder Magento Open Source-Stores verbessern können.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Übersicht über die Inhaltssicherheitsrichtlinie

Eine Content Security Policy (CSP) kann zusätzliche Verteidigungsebenen für Adobe Commerce- und Magento Open Source-Installationen bereitstellen, indem sie dazu beiträgt, Cross-Site Scripting (XSS) und damit verbundene Angriffe auf Dateninjektionen zu erkennen und zu minimieren. Dieser häufige Angriffsvektor injiziert böswillige Inhalte, die fälschlicherweise behaupten, von der Website stammen zu wollen. Nachdem der schädliche Inhalt geladen und ausgeführt wurde, kann er die unbefugte Übertragung von Daten auslösen.

CSP bietet einen standardisierten Satz von Direktiven, die dem Browser mitteilen, welche Inhaltsressourcen vertrauenswürdig sind und welche blockiert werden sollen. Mithilfe sorgfältig definierter Richtlinien kann CSP Browser-Inhalte so einschränken, dass nur auf der Whitelist befindliche Ressourcen angezeigt werden.

## Konfiguration

Um eine Störung des Site-Betriebs zu vermeiden, kann CSP in Phasen implementiert werden. CSP verfügt über zwei grundlegende Betriebsarten: `report-only mode` und `restrict mode`. Die Veröffentlichung von Adobe Commerce 2.3.5 markiert die erste Phase unserer Implementierung und stellt CSP in der `report-only mode` Standardmäßig. In einer zukünftigen Version `restrict mode` ist standardmäßig für zusätzlichen nativen Schutz aktiviert.

**Nur-Bericht-Modus**: Der Browser wird angewiesen, Richtlinienverletzungen zu melden, aber nicht durchzusetzen. Jedes Mal, wenn eine angeforderte Ressource CSP verletzt, protokolliert der Browser die resultierenden Fehler in der Konsole. Das Konsolenprotokoll kann dann verwendet werden, um die Ursache jedes Verstoßes zu untersuchen.

Es ist wichtig, alle CSP-Fehler zu überprüfen, sobald sie auftreten, und die Richtlinien zu verfeinern, bis alle erforderlichen Ressourcen auf die Whitelist gesetzt sind. Es ist sicher, zu `restrict mode` wenn keine Fehler mehr auftreten. Andernfalls kann eine schlecht konfigurierte CSP dazu führen, dass der Browser eine leere Seite mit zahlreichen Konsolenfehlern anzeigt. Eine ordnungsgemäß konfigurierte CSP ermöglicht die Bereitstellung von Inhalten aus der Whitelist, ohne dass die Leistung beeinträchtigt wird.

**Restrict mode**: Der Browser wird angewiesen, alle Inhaltsrichtlinien durchzusetzen und die Veröffentlichung auf auf die Whitelist gesetzte Ressourcen zu beschränken. Da CSP vom Server und nicht vom Administrator konfiguriert wird, benötigen die meisten Händler die Hilfe eines Systemintegrators oder -entwicklers, um sie ordnungsgemäß zu konfigurieren. Siehe [Inhaltssicherheitsrichtlinien](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) im _Commerce-PHP-Erweiterungen_ Entwicklerhandbuch.

## Berichterstellung

Standardmäßig sendet CSP Fehler an die Browser-Konsole, kann jedoch so konfiguriert werden, dass Fehlerprotokolle über HTTP-Anforderungen erfasst werden. Darüber hinaus gibt es mehrere Drittanbieterdienste, mit denen Sie CSP-Verstöße überwachen, erfassen und melden können.

[Bericht-URI](https://report-uri.io/) ist ein Dienst, der CSP-Verstöße überwacht und die Ergebnisse in einem Dashboard anzeigt. Sowohl Händler als auch Entwickler können den Dienst verwenden, um Berichte zu erhalten, sobald CSP-Verstöße auftreten.
