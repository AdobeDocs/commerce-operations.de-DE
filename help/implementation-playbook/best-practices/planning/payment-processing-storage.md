---
title: Best Practices für die Zahlungsverarbeitung und -speicherung
description: Erfahren Sie, wie Sie Zahlungsdetails sicher verarbeiten und speichern
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: db0fce79b22d409e8d639b959dc5a04693e72659
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Best Practices für Zahlungsverarbeitung und Speicherung

Eines der Schlüsselprinzipien für die Aufrechterhaltung der [PCI-Compliance](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) ist eine Strategie zur ordnungsgemäßen Verarbeitung und Speicherung von Kreditkartenzahlungen.

Das Speichern von Karteninhaberdaten in Adobe Commerce ist **streng verboten** und könnte einen Verstoß gegen Ihre Verpflichtungen als Händler gemäß dem Payment Card Industry Data Security Standard (PCI-DSS) darstellen. Weitere Informationen zum Modell der gemeinsamen Verantwortung und zu den Richtlinien für Händlerpflichten finden Sie im Handbuch für das Modell der gemeinsamen Verantwortung von Adobe Commerce [](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) auf Adobe Trust Center.

Befolgen Sie die folgenden Best Practices, um sicherzustellen, dass Sie Zahlungsinformationen auf Ihrer eCommerce-Site ordnungsgemäß verarbeiten. Weitere Anleitungen zu Best Practices für die Sicherheit finden Sie unter [Sichern Ihrer Site und Infrastruktur](../launch/security-best-practices.md).

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

* Adobe Commerce auf Cloud-Infrastruktur
* Adobe Commerce On-Premises

## Schutz der Daten des Karteninhabers

Wenn die Speicherung von Karteninhaberdaten erforderlich ist, sollten Karteninhaberdaten außerhalb von Adobe Commerce mit Speicherungsgarantien gespeichert werden. Die Speicherung von Zahlungsdaten, wie z. B. Daten von Kreditkarteninhabern, trägt dazu bei, Betrug und andere potenzielle Sicherheitsprobleme zu verhindern. Im Einklang mit anderen PCI-Standards ist die Einführung von Schutzmaßnahmen die erste Verteidigungslinie. Zu den bevorzugten Methoden zur Verbesserung des Schutzes gespeicherter Daten gehören Verschlüsselung, Abschneiden, Tokenisierung, Einweg-Hashing und Maskierung.

Schutz für kryptografische Schlüssel ist für Datenschutzstrategien von entscheidender Bedeutung. Es ist wichtig, über qualifizierte und vertrauenswürdige Depotbanken zu verfügen, die diese Schlüssel überwachen.

Schließlich muss eine primäre Kontonummer (PAN) während der Speicherung unlesbar sein, z. B. mit `XXX` maskiert. Dazu gehören tragbare Speicher- und Sicherungsmedien wie Flash-Laufwerke, USB und externe Festplatten sowie Prüfprotokolle.

## Verschlüsseln der Übertragung von Karteninhaberdaten

Die Sicherung von Daten während der Übertragung ist der Schlüssel zum Schutz von Zahlungsinformationen, wie z. B. von Karteninhaberdaten. Wenn diese Informationen über offene Netzwerke übertragen werden, können sie anfälliger für Sicherheitsprobleme werden.

### Verwendung sicherer Übertragungsprotokolle

Übermittlung von Karteninhaberdaten unter Verwendung sicherer Übertragungsprotokolle und -verfahren, einschließlich:

* Vertrauenswürdige Schlüssel und Zertifikate
* Sichere Übertragungsprotokolle wie TLS, SSH oder VPN
* Asymmetrische Algorithmen bei der Verschlüsselung
* Tokenisierung, Maskierung und Penetrationstests mit Senden und Anzeigen von PANs
* Zugriff auf Daten des Karteninhabers beschränken
* Der Zugang zu sensiblen Informationen sollte auf der Grundlage des „Need-to-Know“-Prinzips beschränkt und nur autorisierten Personen mit geschäftlichem Bedarf gewährt werden

Die empfohlene Methode zur Verarbeitung von Karteninhaberdaten besteht darin, die Daten zu Token zu versehen, anstatt sie zu speichern. Token der Karte bei einem bestimmten Zahlungsverarbeitungsanbieter und Speichern des Tokens, des Kartentyps und des verschlüsselten Ablaufdatums. Sie können das Token als Anmeldedaten in der -Datei für die zukünftige Verwendung verwenden, da es nur für jeden Händler eindeutig ist. Da das Token eindeutig ist und ein Sicherheitsproblem vorliegt, wird das Token ungültig gemacht, was dazu beiträgt, betrügerische Aktivitäten zu verhindern.

## Weitere Informationen

Wenn Sie nach empfohlenen Zahlungslösungen per Adobe suchen, sollten Sie [Adobe Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html) in Betracht ziehen.
