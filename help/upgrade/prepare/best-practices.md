---
title: Best Practices
description: Verwenden Sie von Adobe empfohlene Best Practices, um den Upgrade-Prozess für Ihre Adobe Commerce-Projekte zu verwalten.
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# Best Practices für Upgrades

In diesem Abschnitt werden die Maßnahmen aufgelistet, die Sie ergreifen sollten, um die Komplexität eines Upgrades von Adobe Commerce-Projekten zu bewältigen. Ihr Team sollte ab dem Zeitpunkt, zu dem Ihre Projektentwicklung beginnt, über Upgrades nachdenken und diese für jede Version fortsetzen. Wenn Sie diese Best Practices befolgen, wird der Upgrade-Prozess viel einfacher, schneller und billiger.

>[!TIP]
>
>Diese Empfehlungen basieren auf Best Practices, die durch Nachweise von Partnern, Händlern, Adobe-Experten und der Community für ihre Wirkung und Effektivität untermauert werden.

## Welche Auswirkungen hat ein Upgrade?

Es ist wichtig, die Variablen zu verstehen, die die Komplexität eines Upgrades bestimmen. Sie müssen diese Variablen zu Beginn jedes Projekts berücksichtigen - nicht nur, wann die Zeit für ein Upgrade gekommen ist. Die Entwicklung eines Projekts ist von entscheidender Bedeutung, um sicherzustellen, dass zukünftige Upgrades reibungslos verlaufen und Sie den erforderlichen Aufwand für ihren Abschluss kontrollieren können.

Der Aufwand für das Upgrade Ihrer Adobe Commerce-Instanz hängt von folgenden Faktoren ab:

- **Wie haben Sie Ihre Site erstellt?** Der Umfang der benutzerdefinierten Arbeit und die Anzahl der installierten Module von Drittanbietern wirken sich stark auf die Komplexität eines Upgrades aus. Die Qualität der benutzerdefinierten Arbeiten und Module kann bestimmen, ob ein Upgrade reibungslos verläuft.

- **Werden mehrere Versionen übersprungen?** das Überspringen von Versionen macht das nächste Upgrade komplexer, das Upgrade von nachfolgenden Versionen macht den Prozess einfacher und billiger.

- **Welche Art von Upgrade nehmen Sie vor?** Ein Upgrade auf eine Nebenversion (beispielsweise von 2.3.x auf 2.4.0) ist umfangreicher als ein Upgrade zwischen Patch-Versionen (beispielsweise von 2.4.2 auf 2.4.3). Sicherheitsupdates sind am einfachsten zu implementieren.

## Best Practices für die Planung von Upgrades

Wenn Sie an einem Projekt arbeiten, das sich bereits in der Produktion befindet, bieten Upgrades eine Möglichkeit, die Qualität Ihres Codes und Ihrer Anpassungen zu verbessern und für zukünftige Upgrades zu optimieren. Die Zeit, die Sie heute investieren, wird langfristig eingespart.

Wenn Sie mehrere Sites für verschiedene Händler verwalten, ist der beste Ansatz eine Basisinstanz mit den wichtigsten Funktionen und Anpassungen, die Sie normalerweise verwenden. Verwenden Sie diese Basisinstanz als Test-Site, um ein Upgrade abzuschließen, und führen Sie es dann auf anderen Sites durch. Diese Vorgehensweise bietet Ihnen die Flexibilität, benutzerdefinierte Module für verschiedene Kunden wiederzuverwenden und Upgrades projektübergreifend zu vereinfachen.

Wenn Ihr Projekt live ist, empfehlen wir Ihnen, eine Prüfung durchzuführen, um seine Qualität zu bestimmen und zu verstehen, wie Sie es verbessern können, um Upgrades effizienter zu gestalten.

### Entwickeln mit Blick auf Upgrades

Von dem Moment an, in dem Sie mit der Arbeit an einem Projekt beginnen, sollten Sie überlegen, wie sich Ihre aktuellen Arbeiten auf zukünftige Upgrades auswirken werden. Befolgen Sie immer die Best Practices für die Adobe Commerce-Entwicklung, wie hier beschrieben:

- [Best Practices für die Entwicklung](https://developer.adobe.com/commerce/php/best-practices/)
- [Kodierungsstandards](https://developer.adobe.com/commerce/php/coding-standards/)

Beginnen Sie mit der Übernahme der Adobe Commerce-Erweiterbarkeitsplattform, falls noch nicht geschehen. Die Plattform ermöglicht die effiziente Anpassung von Prozessen, die Integration von Systemen und die Bereitstellung neuer Funktionen bei gleichzeitiger Beibehaltung der SaaS-ähnlichen Aktualisierbarkeit. Zu den Merkmalen gehören:

- **Erweiterbarkeit der**. Erweitern und entwickeln Sie Ihre Storefront unabhängig von Ihrem Backend und Ihrer Middleware mit [PWA Studio ](https://developer.adobe.com/commerce/pwa-studio/).

- **API-**. Verwenden Sie [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/index.html), um die Web-API-Ebene zu erweitern, indem Sie das Diagrammdatenmodell weiterentwickeln und Lambda-Funktionen direkt von der Diagrammebene aus ausführen.

- **Adobe I/O-Middleware und -Services**. Verbinden Sie Ihre Systeme mit Adobe Commerce mithilfe der Adobe-Middleware und einer Suite von App-Verbindungen, die auf [Adobe I/O](https://www.adobe.io/) erstellt wurden. Darüber hinaus können Sie die Kernfunktionen der Plattform erweitern, indem Sie das Standardverhalten mit Ihrer eigenen Geschäftslogik überschreiben, die auf Adobe I/O ausgeführt wird.

### Planung von Upgrades

Da wir die Funktionen von Adobe Commerce kontinuierlich erweitern, ist es wichtig, dass Sie mit der neuesten verfügbaren Version entwickeln und in Ihren Projektplänen eine Upgrade-Strategie definieren. Auf diese Weise bleiben Sie sicher, konform und auf dem neuesten Stand der neuesten Verbesserungen, mit denen Sie Ihre Umsätze schneller steigern, effektiver arbeiten und Ihren Mitbewerbern jetzt und in Zukunft einen Schritt voraus sein können.

Um Upgrades planen und budgetieren zu können, sollten Sie unseren [Veröffentlichungszeitplan](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) überwachen. Planen Sie Upgrade-Aufgaben im Rückstand Ihres Teams im Voraus. Ziel ist es, diese Arbeit mit GA abzuschließen.

- Verwenden Sie die Vorabversion , um mehr über jede neue Version zu erfahren. Eine Vorabversion ist ein allgemeiner Verfügbarkeits-Code, der Adobe Commerce-Händlern und allen Partnern zwei Wochen vor der allgemeinen Verfügbarkeit zur Verfügung steht. Wenn Sie über mehrere Stores verfügen, verwenden Sie die Vorabversion in Ihrem Basis-Store und überprüfen Sie, ob Ihre benutzerdefinierten Module und Designs damit kompatibel sind.

- Lesen Sie die [Checkliste für den Upgrade](https://support.magento.com/hc/en-us/articles/360057968951), um Adobe Commerce bei der Planung des Upgrades zu unterstützen.

- Planen Sie Upgrades Anfang des Jahres ein. Für jedes Upgrade müssen ein Budget und Ressourcen reserviert werden. Beachten Sie, dass der Upgrade-Aufwand von Projekt zu Projekt erheblich variieren kann. Nutzen Sie Ihre Erfahrungen und Kenntnisse, um einen Plan so genau wie möglich zu machen.

- Wenn Ihre Upgrades mehr Aufwand erfordern als hier beschrieben, empfehlen wir Ihnen, Ihr Projekt zu überprüfen und Anpassungen an Ihrer Umgebung vorzunehmen, um die langfristige Wartung zu reduzieren.

### Durchführen von Upgrades

Upgrades sollten regelmäßig und mit einem vordefinierten Budget durchgeführt werden. Es wird empfohlen, vorab genehmigte Upgrades zu Beginn des Jahres zu planen, um sicherzustellen, dass Upgrades rechtzeitig geplant und abgeschlossen werden.

Bewerten Sie die für das Upgrade erforderlichen Arbeiten:

- Lesen Sie die [Versionshinweise](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) um den Umfang und die Auswirkungen der neuen Version zu verstehen.

- Verwenden Sie den [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md), um potenzielle Probleme zu identifizieren, die in Ihrem benutzerdefinierten Code behoben werden müssen, bevor Sie versuchen, auf eine neuere Version zu aktualisieren.

- Wenn Sie Erweiterungen von Drittanbietern verwenden, überprüfen Sie deren Kompatibilität mit der Zielversion, auf die Sie ein Upgrade planen.

### Tests nach einem Upgrade

Beim Testen handelt es sich um die Phase eines Upgrades, die die meiste Zeit in Anspruch nimmt. Daher sollte dieser Prozess so weit wie möglich automatisiert werden. Sie können von der Verwendung der wichtigsten Test-Tools profitieren. Weitere Informationen finden [ im ](https://developer.adobe.com/commerce/testing/guide/) „Anwendungstestleitfaden“.

Verwenden Sie eine Staging-Umgebung, um Ihr Upgrade zu testen und zu validieren, bevor Sie zur Produktion wechseln.

Verwenden Sie eine **Wartungsseite**. Wenn Sie diese Seite im Voraus vorbereiten, können Sie mit Ihren Kunden kommunizieren und sie darüber informieren, dass im Hintergrund Arbeiten durchgeführt werden. Diese Seite sollte einige Minuten lang sichtbar sein. Wenn jedoch ein Problem auftritt, müssen Sie sie möglicherweise länger verwenden. Die Verwendung des entsprechenden Inhalts und Designs für Ihre Wartungsseite bietet Ihren Benutzern ein gutes Erlebnis, auch wenn Ihr Store nicht verfügbar ist.
