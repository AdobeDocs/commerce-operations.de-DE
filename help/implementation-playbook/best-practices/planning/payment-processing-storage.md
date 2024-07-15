---
title: Best Practices für die Verarbeitung und Speicherung von Zahlungen
description: Erfahren Sie, wie Sie Zahlungsdetails sicher verarbeiten und speichern können
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: db0fce79b22d409e8d639b959dc5a04693e72659
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Best Practices für die Verarbeitung und Speicherung von Zahlungen

Eines der wichtigsten Grundsätze bei der Aufrechterhaltung der [PCI compliance](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) ist die Strategie, Kreditkartenzahlungen ordnungsgemäß zu verarbeiten und zu speichern.

Das Speichern von Karteninhaberdaten in Adobe Commerce ist **streng verboten** und dies könnte einen Verstoß gegen Ihre Pflichten als Händler gemäß dem Payment Card Industry Data Security Standard (PCI-DSS) darstellen. Weitere Informationen zum Modell der gemeinsamen Verantwortung und zu den Richtlinien für Handelsverpflichtungen finden Sie im [Leitfaden für freigegebene Verantwortung für Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) im Adobe Trust Center.

Befolgen Sie die unten stehenden Best Practices, um sicherzustellen, dass Sie die Zahlungsinformationen auf Ihrer E-Commerce-Site ordnungsgemäß verarbeiten. Weitere Anleitungen zu Best Practices für die Sicherheit finden Sie unter [Sichern Ihrer Site und Infrastruktur](../launch/security-best-practices.md).

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

* Adobe Commerce auf Cloud-Infrastruktur
* Adobe Commerce vor Ort

## Schutz der Daten des Karteninhabers

Wenn die Speicherung von Karteninhaberdaten erforderlich ist, sollten die Karteninhaberdaten außerhalb von Adobe Commerce mit Speicherungsgarantien gespeichert werden. Durch die Einführung von Speichergarantien für Zahlungsdetails wie Kreditkarteninhaberdaten können Betrug und andere potenzielle Sicherheitsprobleme verhindert werden. Im Einklang mit anderen PCI-Standards ist der Schutz der ersten Verteidigungslinie. Zu den bevorzugten Methoden zur Verbesserung des Schutzes gespeicherter Daten gehören Verschlüsselung, Kürzung, Tokenisierung, unidirektionales Hashing und Maskierung.

Der Schutz kryptografischer Schlüssel ist für Datenschutzstrategien von entscheidender Bedeutung. Es ist wichtig, über qualifizierte und vertrauenswürdige Kunden zu verfügen, die diese Schlüssel überwachen.

Schließlich muss eine primäre Kontonummer (PAN) während der Speicherung unlesbar sein, z. B. mit `XXX` maskiert. Dazu gehören tragbare Speicher- und Sicherungsmedien wie Flash-Laufwerke, USB- und externe Festplatten sowie sogar Prüfprotokolle.

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

Die empfohlene Methode für die Verarbeitung von Karteninhaberdaten besteht darin, die Daten per Token zu versehen, anstatt sie zu speichern. Token Sie die Karte mit einem bestimmten Zahlungsdienstleister und speichern Sie das Token, den Kartentyp und das verschlüsselte Ablaufdatum. Sie können das Token als Berechtigung für die zukünftige Verwendung in der Datei verwenden, da es nur für jeden Händler eindeutig ist. Da das Token eindeutig ist, kann bei einem Sicherheitsproblem das ungültige Token dazu beitragen, betrügerische Aktivitäten zu verhindern.

## Weitere Informationen

Wenn Sie nach empfohlenen Zahlungslösungen durch Adobe suchen, beachten Sie [Adobe Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
