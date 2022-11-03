---
title: Best Practices für Dienste aktualisieren
description: Erfahren Sie, wie Sie Ihre Adobe Commerce auf dem neuesten Stand der Cloud-Infrastruktur-Technologie halten.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Best Practices für Dienste aktualisieren

Dieser Artikel enthält Empfehlungen, wie Sie Ihren Adobe Commerce auf dem neuesten Stand der Cloud-Infrastruktur-Technologie halten können, und enthält Links zu hilfreichen Ressourcen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.x und höher

## Aktualisierungsdienste

Aktualisieren Sie die von Adobe Commerce verwendeten Dienste und Komponenten, bevor sie das Enddatum erreichen oder nahe daran liegen. Dies hilft, mit PCI-Compliance Schritt zu halten und Sicherheitslücken zu schließen.

Kunden mit Starter-Plänen können sich selbst für Service-Upgrades bedienen. Siehe [Dienstversion ändern](https://devdocs.magento.com/cloud/project/services.html#change-service-version) für weitere Informationen.

Kunden mit Pro-Plänen können sich nur selbst für Service-Upgrades in ihrer [Integrationsumgebung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md). Für Service-Upgrades in der Produktion müssen Sie [Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) das Upgrade anfordern.

>[!WARNING]
>
>Service-Upgrades können nicht ohne 48-Stunden-Benachrichtigung an unser Infrastrukturteam in die Produktionsumgebung gesendet werden. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert.

Sie können die Liste der Dienstversionen und das Ende der Lebensdauer in der folgenden Datei anzeigen: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Diese Datei kann nicht als eine einzige Quelle der Wahrheit betrachtet werden. Weitere Informationen zu diesen Technologien finden Sie auf den offiziellen Websites der Anbieter.

## Zusätzliche Informationen

[Systemanforderungen](../../../installation/system-requirements.md)
