---
title: Best Practices
description: Verwenden Sie die von Adobe empfohlenen Best Practices, um den Aktualisierungsprozess für Ihre Adobe Commerce-Projekte zu verwalten.
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# Best Practices für die Aktualisierung

In diesem Thema werden die Aktionen aufgelistet, die Sie durchführen sollten, um die Komplexität der Aktualisierung von Adobe Commerce-Projekten zu verwalten. Ihr Team sollte über Upgrades nachdenken, sobald Ihre Projektentwicklung beginnt und mit jeder Version fortgesetzt wird. Durch die Befolgung dieser Best Practices wird der Aktualisierungsprozess viel einfacher, schneller und billiger.

>[!TIP]
>
>Diese Empfehlungen basieren auf Best Practices, die durch Beweise für ihre Wirkung und Wirksamkeit von Partnern, Händlern, Adobe-Experten und der Community unterstützt werden.

## Welche Auswirkungen hat ein Upgrade?

Es ist wichtig, die Variablen zu verstehen, die die Komplexität eines Upgrades bestimmen. Sie müssen diese Variablen zu Beginn jedes Projekts berücksichtigen - nicht nur, wann die Aktualisierung Zeit ist. Die Entwicklung eines Projekts ist entscheidend, um sicherzustellen, dass zukünftige Upgrades reibungslos ablaufen und dass Sie die erforderlichen Anstrengungen zur Durchführung dieser Aktualisierungen steuern können.

Der Aufwand für die Aktualisierung Ihrer Adobe Commerce-Instanz hängt von folgenden Faktoren ab:

- **Wie haben Sie Ihre Site erstellt?** Der Umfang der benutzerdefinierten Arbeit und die Anzahl der installierten Module von Drittanbietern wirken sich stark auf die Komplexität eines Upgrades aus. Die Qualität der benutzerdefinierten Arbeit und der Module kann bestimmen, ob eine Aktualisierung reibungslos verläuft.

- **Überspringen Sie mehrere Versionen?** Wenn Sie Versionen überspringen, wird das nächste Upgrade komplexer. Ein Upgrade von aufeinander folgenden Versionen macht den Prozess einfacher und billiger.

- **Welche Art von Aktualisierung führen Sie durch?** Ein Upgrade auf eine Nebenversion (z. B. von 2.3.x auf 2.4.0) ist umfangreicher als ein Upgrade zwischen Patch-Versionen (z. B. von 2.4.2 auf 2.4.3). Sicherheitsupdates sind der einfachste zu implementierende Typ.

## Best Practices für die Planung von Upgrades

Wenn Sie an einem Projekt arbeiten, das bereits in Produktion ist, bieten Upgrades Ihnen die Möglichkeit, die Qualität Ihres Codes und Ihrer Anpassungen zu verbessern und zukünftige Upgrades zu optimieren. Die Zeit, die Sie heute investieren, wird langfristig eingespart.

Wenn Sie mehrere Sites für verschiedene Händler verwalten, besteht der beste Ansatz darin, eine Basisinstanz mit den Hauptfunktionen und Anpassungen zu haben, die Sie normalerweise verwenden. Verwenden Sie diese Basisinstanz als Ihre Test-Site zum Abschluss eines Upgrades und führen Sie sie dann für andere durch. Dadurch erhalten Sie die Flexibilität, benutzerdefinierte Module für verschiedene Kunden wiederzuverwenden und Upgrades projektübergreifend zu vereinfachen.

Wenn Ihr Projekt live ist, empfehlen wir Ihnen, eine Prüfung durchzuführen, um die Qualität zu ermitteln und zu verstehen, wie Sie es verbessern können, um Upgrades effizienter zu gestalten.

### Entwickeln mit Upgrades unter Berücksichtigung

Ab dem Moment, in dem Sie mit der Arbeit an einem Projekt beginnen, sollten Sie überlegen, wie sich zukünftige Upgrades durch Ihre aktuelle Arbeit auswirken werden. Befolgen Sie stets die Best Practices für die Entwicklung von Adobe Commerce, wie hier beschrieben:

- [Best Practices für die Entwicklung](https://developer.adobe.com/commerce/php/best-practices/)
- [Kodierungsstandards](https://developer.adobe.com/commerce/php/coding-standards/)

Beginnen Sie mit der Übernahme der Adobe Commerce Extensibility-Plattform, falls noch nicht geschehen. Die Plattform ermöglicht es Ihnen, Prozesse effizient anzupassen, Systeme zu integrieren und neue Funktionen bereitzustellen und gleichzeitig eine SaaS-ähnliche Upgrade-Funktion zu erhalten. Zu den Funktionen gehören:

- **Erweiterbarkeit der Benutzeroberfläche**. Erweitern und entwickeln Sie Ihre Storefront unabhängig von Backend und Middleware mit [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **API-Erweiterbarkeit**. Verwenden Sie [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/index.html), um die Web-API-Ebene zu erweitern, indem Sie das Diagrammdatenmodell entwickeln und Lambda-Funktionen direkt aus der Diagrammebene ausführen.

- **Adobe I/O Middleware und Dienste**. Verbinden Sie Ihre Systeme mit Adobe Commerce über Adobe Middleware und eine Suite mit App-Verbindungen, die auf [Adobe I/O](https://www.adobe.io/) basieren. Darüber hinaus können Sie die Kernplattformfunktionen erweitern, indem Sie das Standardverhalten mit Ihrer eigenen Geschäftslogik überschreiben, die auf Adobe I/O ausgeführt wird.

### Planen von Upgrades

Da wir die Funktionen von Adobe Commerce kontinuierlich erweitern, ist es wichtig, dass Sie die neueste Version entwickeln und eine Upgrade-Strategie in Ihre Projektpläne aufnehmen. Auf diese Weise können Sie sicher, konform und auf dem neuesten Stand der neuesten Verbesserungen bleiben, mit denen Sie Ihre Umsätze schneller steigern, effizienter arbeiten und Ihrem Wettbewerb jetzt und in die Zukunft voraus bleiben können.

Um Ihnen bei der Planung und dem Budget für Upgrades zu helfen, sollten Sie unseren [Veröffentlichungsplan](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) überwachen. Planen Sie die Aktualisierungsaufgaben im Rückstand Ihres Teams vor der Zeit. Ziel ist es, diese Arbeit mit GA abzuschließen.

- Verwenden Sie die Vorabversion, um mehr über jede neue Version zu erfahren. Die Vorabversion ist der allgemeine Verfügbarkeitscode, der zwei Wochen vor der allgemeinen Verfügbarkeit für Adobe Commerce-Händler und alle Partner verfügbar ist. Wenn Sie über mehrere Stores verfügen, verwenden Sie die Vorabversion in Ihrem Basisspeicher und stellen Sie sicher, dass Ihre benutzerdefinierten Module und Designs mit ihr kompatibel sind.

- Überprüfen Sie die Checkliste für den [Aktualisierungsplan](https://support.magento.com/hc/en-us/articles/360057968951) für Adobe Commerce, um Sie bei der Planung der Aktualisierung zu unterstützen.

- Planung von Upgrades zu Beginn des Jahres. Sie müssen ein Budget und Ressourcen für jedes Upgrade buchen. Beachten Sie, dass der Aktualisierungsaufwand von Projekt zu Projekt erheblich variieren kann. Nutzen Sie Ihre Erfahrungen und Ihr Wissen, um einen Plan so präzise wie möglich zu gestalten.

- Wenn Ihre Upgrades mehr als den hier beschriebenen Aufwand erfordern, empfehlen wir Ihnen, Ihr Projekt zu prüfen und Anpassungen an Ihrer Umgebung vorzunehmen, um die langfristige Wartung zu reduzieren.

### Durchführen von Upgrades

Aktualisierungen sollten regelmäßig und unter einem vordefinierten Budget erfolgen. Es wird empfohlen, vorab genehmigte Upgrades zu Beginn des Jahres zu planen, um sicherzustellen, dass Aktualisierungen rechtzeitig geplant und abgeschlossen werden.

Prüfen Sie die für die Aktualisierung erforderliche Arbeit:

- Lesen Sie die [Versionshinweise](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) , um den Umfang und die Auswirkungen der neuen Version zu verstehen.

- Verwenden Sie den [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) , um potenzielle Probleme zu identifizieren, die in Ihrem benutzerspezifischen Code behoben werden müssen, bevor Sie versuchen, auf eine neuere Version zu aktualisieren.

- Wenn Sie Erweiterungen von Drittanbietern verwenden, überprüfen Sie deren Kompatibilität mit der Zielversion, auf die Sie ein Upgrade durchführen möchten.

### Tests nach der Aktualisierung

Beim Testen handelt es sich um die Phase eines Upgrades, für die die meiste Zeit benötigt wird. Daher sollte dieser Prozess so automatisiert wie möglich sein. Sie können von der Verwendung der Kerntestwerkzeuge profitieren. Das [Handbuch zum Testen von Anwendungen](https://developer.adobe.com/commerce/testing/guide/) enthält Details.

Verwenden Sie eine Staging-Umgebung, um Ihre Aktualisierung zu testen und zu validieren, bevor Sie zur Produktion wechseln.

Verwenden Sie eine **Wartungsseite**. Wenn Sie diese Seite vorab vorbereiten, können Sie mit Ihren Kunden kommunizieren und ihnen mitteilen, dass die Arbeit im Hintergrund stattfindet. Diese Seite sollte einige Minuten lang sichtbar sein. Wenn jedoch ein Problem auftritt, müssen Sie sie möglicherweise länger verwenden. Wenn Sie über die entsprechenden Inhalte und Designs für Ihre Wartungsseite verfügen, erhalten Ihre Benutzer ein gutes Erlebnis, selbst wenn Ihr Store nicht verfügbar ist.
