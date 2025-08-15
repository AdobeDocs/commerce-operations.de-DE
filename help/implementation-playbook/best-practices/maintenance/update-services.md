---
title: Best Practices für Services aktualisieren
description: Erfahren Sie, wie Sie Ihre Adobe Commerce im Cloud-Infrastrukturtechnologie-Stack auf dem neuesten Stand halten.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 5e3289b328b51eb50354efdc1571283791175b9a
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Best Practices für Services aktualisieren

Dieser Artikel enthält Empfehlungen dazu, wie Sie Ihre Adobe Commerce im Cloud-Infrastrukturtechnologie-Stack auf dem neuesten Stand halten können, und enthält Links zu hilfreichen Ressourcen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur 2.4.x und höher

## Dienste aktualisieren

Aktualisieren Sie die von Adobe Commerce verwendeten Services und Komponenten, bevor sie das Ende ihres Lebenszyklus erreichen oder kurz davor sind. Dies hilft, mit der PCI-Compliance Schritt zu halten und Sicherheitslücken zu schließen.

Kunden mit Starter-Plänen können Service-Upgrades selbst durchführen. Einzelheiten dazu finden [ unter &quot;](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version) ändern“.

Kunden mit Pro-Plänen können Services-Upgrades nur selbst in ihrer [Integrationsumgebung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html?lang=de) bereitstellen. Für Service-Upgrades in der Produktion müssen Sie [ein Support-Ticket einreichen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=de#submit-ticket) um das Upgrade anzufordern.

>[!WARNING]
>
>Service-Upgrades können nicht in eine Produktionsumgebung verschoben werden, ohne dass das Infrastruktur-Team von Adobe innerhalb von 48 Geschäftsstunden davon in Kenntnis gesetzt wird. Dies ist erforderlich, damit Adobe sicherstellen kann, dass ein Support-Techniker für die Infrastruktur zur Verfügung steht, der Ihre Konfiguration innerhalb eines gewünschten Zeitraums mit minimalen Ausfallzeiten in Ihrer Produktionsumgebung aktualisiert. Adobe empfiehlt, Ihre Site während des Service-Upgrades in den Wartungsmodus zu versetzen.

Die Liste der Service-Versionen und der Daten zum Ende der Nutzungsdauer finden Sie in der folgenden Datei: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Diese Datei kann nicht als eine einzige Quelle der Wahrheit betrachtet werden. Im Zweifelsfall sollten diese Technologien auf den offiziellen Anbieterwebsites nachgelesen werden.

## Weitere Informationen

[Systemanforderungen](../../../installation/system-requirements.md)
