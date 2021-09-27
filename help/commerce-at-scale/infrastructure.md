---
title: Ausrichtung von Adobe Commerce und Adobe Experience Manager-Infrastruktur
description: Stellen Sie in Ihrer Adobe Commerce- und Adobe Experience Manager-Infrastruktur akzeptable Timeouts und Verbindungsgrenzen ein.
source-git-commit: 1cff7359ddb4caeca6773ff74b92048c89676f12
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---


# Infrastrukturausrichtungen (Zeitüberschreitungen und Verbindungsbeschränkungen)

Es gibt Einstellungen für AEM und Adobe Commerce und die umliegende Infrastruktur, wie z. B. Lastenausgleichsmodule, die ausgerichtet werden müssen. Diese beziehen sich auf Verbindungsbeschränkungen und Timeout-Einstellungen.

Eine Fehlausrichtung zwischen diesen Beschränkungen würde bedeuten, dass Verbindungen auf AEM Seite gedrosselt werden könnten, während Adobe Commerce in der Lage ist, mehr Verbindungen zu handhaben. Gleichermaßen kann eine Fehlausrichtung bei den Timeout-Einstellungen dazu führen, dass auf AEM Seite Zeitüberschreitungsfehler auftreten, während Adobe Commerce weiterhin eine Anforderung verarbeitet.

Für die Timeout-Einstellungen sollten die Einstellungen überprüft und angepasst werden, um zu verhindern, dass beim Laden 503 Timeout-Fehler auftreten. Es gibt mehrere Einstellungen für Infrastruktur- und Anwendungstimeout, die überprüft werden müssen:

![Nummeriertes Diagramm, das Timeouts und Verbindungsbeschränkungen für AEM beschreibt](../assets/commerce-at-scale/timeout-settings.svg)

## AEM Lastenausgleich

Wenn es in der Infrastruktur einen AWS-Anwendungs-Lastenausgleich und mehrere Dispatcher/Publisher gibt, sollten die folgenden Einstellungen für den Lastenausgleich berücksichtigt werden:

1. Die Konsistenzprüfungen des Herausgebers sollten überprüft werden, um zu verhindern, dass Dispatcher unnötig früh aus dem Dienst aussteigen. Die Timeout-Einstellungen der Konsistenzprüfung des Lastenausgleichs sollten mit den Timeout-Einstellungen des Herausgebers übereinstimmen.

   ![Screenshot mit Konsistenzprüfungen AEM Lastenausgleichs](../assets/commerce-at-scale/health-checks.svg)

1. Die Treue der Dispatcher-Zielgruppe kann deaktiviert werden und der Round Robin-Lastenausgleich-Algorithmus kann verwendet werden. Dies setzt voraus, dass keine AEM spezifischen Funktionen oder AEM Benutzersitzungen verwendet werden, für die die Sitzungsstickigkeit festgelegt werden muss. Es wird davon ausgegangen, dass die Benutzeranmeldung und Sitzungsverwaltung nur über GraphQL in Adobe Commerce erfolgt.

   ![Screenshot mit AEM Sitzungs-Stickiness-Attributen](../assets/commerce-at-scale/session-stickiness.svg)

1. Beachten Sie bitte, wenn Sie die Sitzungsstickigkeit aktivieren, dies kann dazu führen, dass Anforderungen an Schnell nicht zwischengespeichert werden, da standardmäßig keine Seiten mit dem Set-Cookies-Header zwischengespeichert werden. Adobe Commerce setzt Cookies auch auf zwischenspeicherbaren Seiten (TTL > 0), aber der standardmäßige Fastly VCL entfernt diese Cookies auf zwischenspeicherbaren Seiten, damit das schnelle Zwischenspeichern funktioniert. Wenn die Seiten nicht zwischengespeichert werden, überprüfen Sie die möglicherweise von Ihnen verwendeten benutzerdefinierten Cookies, laden Sie auch den Fastly VCL hoch und überprüfen Sie erneut die Site.

## Dispatcher-Timeout-Einstellungen

Die /timeout in den Dispatcher-Optionen &quot;renders&quot;(rendert) gibt das Verbindungstimeout für den Zugriff auf die AEM Veröffentlichungsinstanz in Millisekunden an. Dies sollte überprüft werden und die Standardeinstellung &quot;0&quot;(unbestimmte Zeitüberschreitung) sollte verwendet werden, wenn ein separater Lastenausgleich vorhanden ist, um die Timeout-Einstellungen zu verarbeiten.

Wenn in der Infrastruktur kein Lastenausgleich vorhanden ist, sollten die Timeout-Einstellungen stattdessen in den Dispatcher-/Timeout-Einstellungen angegeben werden, wobei ein Wert vorhanden ist, der mit den GraphQL-Timeout-Einstellungen im Publisher übereinstimmt.

## Herausgeber

Verbindungsbeschränkungen und -zeitüberschreitungen für Publisher GraphQL: Zunächst sollten die Max-HTTP-Verbindungen in den OSGi-Einstellungen der Adobe Commerce CIF GraphQL Client Configuration Factory auf den Standardwert Fastly maximum connections limit gesetzt werden, der derzeit auf 200 festgelegt ist. Selbst wenn sich in der AEM-Farm mehrere Herausgeber befinden, sollte die Beschränkung für jeden Herausgeber gleich sein und mit der Einstellung Schnell übereinstimmen. Der Grund dafür ist, dass in einigen Fällen ein Herausgeber mehr Traffic verarbeiten könnte als die anderen Herausgeber, wenn beispielsweise ein zugehöriger Dispatcher aus der Farm genommen wird. Dies würde bedeuten, dass der gesamte Traffic über den einzigen verbleibenden Dispatcher und Herausgeber geleitet wird. In diesem Fall benötigt der einzelne Herausgeber dann alle HTTP-Verbindungen.

Die &quot;Standard-HTTP-Methode&quot;sollte von POST auf GET festgelegt werden. Im Commerce-GraphQL-Cache von Adobe werden nur GET-Anforderungen zwischengespeichert. Daher sollte die Standardmethode immer auf GET festgelegt werden.

Der Wert für HTTP-Verbindungs-Timeout und HTTP-Socket-Timeout sollte auf einen Wert festgelegt werden, der dem Fastly-Timeout entspricht.

Die folgende Abbildung zeigt das Magento CIF GraphQL Client Configuration Factory. Die hier gezeigten Einstellungen sind nur Beispiele und müssen von Fall zu Fall angepasst werden:

![Screenshot der Konfigurationseinstellungen des Commerce-Integrations-Frameworks](../assets/commerce-at-scale/cif-config.svg)

Die folgenden Abbildungen zeigen die Fastly-Backend-Konfigurationen. Die hier gezeigten Einstellungen sind nur Beispiele und müssen von Fall zu Fall angepasst werden:

![Screenshot der Commerce Admin-Konfigurationseinstellungen für Fastly](../assets/commerce-at-scale/cif-config-advanced.svg)
