---
title: Best Practices für Dienste aktualisieren
description: Erfahren Sie, wie Sie Ihre Adobe Commerce auf dem neuesten Stand der Cloud-Infrastruktur-Technologie halten.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Best Practices für Dienste aktualisieren

Dieser Artikel enthält Empfehlungen, wie Sie Ihren Adobe Commerce auf dem neuesten Stand der Cloud-Infrastruktur-Technologie halten können, und enthält Links zu hilfreichen Ressourcen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.x und höher

## Aktualisierungsdienste

Aktualisieren Sie die von Adobe Commerce verwendeten Dienste und Komponenten, bevor sie das Enddatum erreichen oder nahe daran liegen. Dies hilft, mit PCI-Compliance Schritt zu halten und Sicherheitslücken zu schließen.

Kunden mit Starter-Plänen können sich selbst für Service-Upgrades bedienen. Weitere Informationen dazu finden Sie unter [Dienstversion ändern](https://devdocs.magento.com/cloud/project/services.html#change-service-version) .

Kunden mit Pro-Plänen können nur Self-Service für Dienstaktualisierungen in ihrer [Integrationsumgebung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html) durchführen. Für Service-Upgrades bei der Produktion müssen Sie [ein Support-Ticket senden](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket), das die Aktualisierung anfordert.

>[!WARNING]
>
>Service-Upgrades können nicht ohne 48-Stunden-Benachrichtigung an unser Infrastrukturteam in die Produktionsumgebung gesendet werden. Dies ist erforderlich, da wir sicherstellen müssen, dass wir über einen Infrastruktur-Support-Mitarbeiter verfügen, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert.

Sie können die Liste der Dienstversionen und das Ende des Lebenszyklus in der folgenden Datei anzeigen: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Diese Datei kann nicht als eine einzige Quelle der Wahrheit betrachtet werden. Weitere Informationen zu diesen Technologien finden Sie auf den offiziellen Websites der Anbieter.

## Weitere Informationen

[Systemanforderungen](../../../installation/system-requirements.md)
