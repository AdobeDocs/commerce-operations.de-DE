---
title: Best Practices für die Verarbeitung und Speicherung von Zahlungen
description: Erfahren Sie, wie Sie Zahlungsdetails sicher verarbeiten und speichern können.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best Practices für die Verarbeitung und Speicherung von Zahlungen

Eines der wichtigsten Grundsätze bei der Aufrechterhaltung [PCI-Compliance](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) hat eine Strategie, Kreditkartenzahlungen ordnungsgemäß zu verarbeiten und zu speichern.

Speichern von Karteninhaberdaten in Adobe Commerce ist **streng verboten** und dies könnte einen Verstoß gegen Ihre Verpflichtungen als Händler im Rahmen des Payment Card Industry Data Security Standard (PCI-DSS) darstellen. Weitere Informationen über unser gemeinsames Verantwortungsmodell und die Richtlinien für Handelsverpflichtungen finden Sie in unserer [Handbuch zur gemeinsamen Verantwortung für Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) im Adobe Trust Center.

Wir empfehlen, die unten stehenden Best Practices zu befolgen, um sicherzustellen, dass Sie die Zahlungsinformationen auf Ihrer E-Commerce-Site ordnungsgemäß verarbeiten. Weitere Hinweise zu den allgemeinen Best Practices für die Sicherheit finden Sie in unserer [Handbuch zu Best Practices für die Sicherheit von Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) über das Adobe Trust Center

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

* Adobe Commerce auf Cloud-Infrastruktur
* Adobe Commerce vor Ort

## Schutz der Daten des Karteninhabers

Wenn die Speicherung von Karteninhaberdaten erforderlich ist, sollten die Karteninhaberdaten außerhalb von Adobe Commerce mit Speicherungsgarantien gespeichert werden. Durch die Einführung von Speichergarantien für Zahlungsdetails wie Kreditkarteninhaberdaten können Betrug und andere potenzielle Sicherheitsprobleme verhindert werden. Im Einklang mit anderen PCI-Standards ist der Schutz der ersten Verteidigungslinie. Zu den bevorzugten Methoden zur Verbesserung des Schutzes gespeicherter Daten gehören Verschlüsselung, Kürzung, Tokenisierung, unidirektionales Hashing und Maskierung.

Der Schutz kryptografischer Schlüssel ist für Datenschutzstrategien von entscheidender Bedeutung. Es ist wichtig, über qualifizierte und vertrauenswürdige Kunden zu verfügen, die diese Schlüssel überwachen.

Schließlich muss eine primäre Kontonummer (PAN) während der Speicherung unlesbar sein (z. B. maskiert wie XXX). Dazu gehören tragbare Speicher- und Sicherungsmedien wie Flash-Laufwerke, USB- und externe Festplatten sowie sogar Prüfprotokolle.

## Verschlüsseln der Übertragung von Karteninhaberdaten

Der Schutz von Daten während der Übermittlung ist der Schlüssel zum Schutz von Zahlungsinformationen, wie z.B. Daten des Karteninhabers. Wenn diese Informationen über offene Netze übermittelt werden, können sie anfälliger für Sicherheitsprobleme werden.

### Verwenden sicherer Übertragungsprotokolle

Übermittlung von Karteninhaberdaten mithilfe sicherer Übertragungsprotokolle und -praktiken, einschließlich:

* Vertrauenswürdige Schlüssel und Zertifikate
* Sichere Übertragungsprotokolle wie TLS, SSH oder VPN
* Asymmetrische Algorithmen bei der Verschlüsselung
* Tokenisierung, Maskierung und Penetrationstests mit Übertragung und Anzeige von PANs
* Zugriff auf Daten des Karteninhabers beschränken
* Der Zugang zu sensiblen Informationen sollte auf der Grundlage des Kenntnisbedarfs beschränkt und nur den autorisierten Personen mit geschäftlichen Bedürfnissen gewährt werden

Die empfohlene Methode zur Verarbeitung von Karteninhaberdaten besteht darin, die primäre Kontonummer (PAN) nicht zu speichern, sondern die Karte mit einem bestimmten Zahlungsdienstleister zu tokenisieren und das Token, den Kartentyp und das verschlüsselte Ablaufdatum zu speichern. Sie können das Token als Berechtigung für die zukünftige Verwendung in der Datei verwenden, da es nur für jeden Händler eindeutig ist. Da das Token eindeutig ist, ist bei einem Sicherheitsproblem das Token in invalidiert, was dazu beiträgt, betrügerische Aktivitäten zu verhindern

## Zusätzliche Informationen

Wenn Sie nach empfohlenen Zahlungslösungen pro Adobe suchen, beachten Sie bitte [Adobe Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
