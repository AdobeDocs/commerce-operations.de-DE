---
title: Adobe Commerce-Leistungsoptimierung
description: Bereiten Sie Ihr Adobe Commerce-Projekt auf die Verwendung von Adobe Experience Manager as a CMS vor, indem Sie einige Standardeinstellungen ändern.
exl-id: 55d77af7-508c-4ef7-888b-00911cc6e920
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# Leistungsoptimierung von Adobe Commerce

## Geografischer Standort der AEM und Adobe Commerce-Infrastruktur

Um die Latenz zwischen AEM Publisher und Adobe Commerce GraphQL beim Erstellen von Seiten zu reduzieren, sollte die anfängliche Bereitstellung der beiden separaten Infrastrukturen in derselben AWS- (oder Azure-) Region gehostet werden. Der geografische Standort, der für beide Clouds ausgewählt wird, sollte auch dem Großteil Ihres Kundenstamms am nächsten sein, sodass clientseitige GraphQL-Anforderungen von einem geografisch nahen Ort an die Mehrheit Ihrer Kunden gesendet werden.

## GraphQL-Zwischenspeicherung in Adobe Commerce

Wenn der Browser oder AEM Publisher des Benutzers die GraphQL von Adobe Commerce aufruft, werden bestimmte Aufrufe zwischengespeichert
in Fastly. Bei den zwischengespeicherten Abfragen handelt es sich im Allgemeinen um Abfragen, die nicht personenbezogene Daten enthalten und sich wahrscheinlich nicht häufig ändern. Dies sind beispielsweise: Kategorien, categoryList und Produkte. Diejenigen, die explizit nicht zwischengespeichert werden, sind diejenigen, die sich regelmäßig ändern und im Cache gespeichert werden, könnten Risiken für personenbezogene Daten und Site-Vorgänge darstellen, z. B. Abfragen wie cart und customerPaymentTokens.

Mit GraphQL können Sie mehrere Abfragen in einem einzelnen Aufruf durchführen. Beachten Sie, dass Adobe Commerce den Cache für alle Abfragen im Aufruf umgeht, wenn Sie selbst eine Abfrage angeben, dass Adobe Commerce nicht mit vielen anderen zwischenspeichert, die nicht zwischenspeicherbar sind. Dies sollte von Entwicklern bei der Kombination mehrerer Abfragen berücksichtigt werden, um sicherzustellen, dass potenziell zwischenspeicherbare Abfragen nicht unbeabsichtigt übersprungen werden ‡.

>[!NOTE]
>
> Weitere Informationen zu zwischenspeicherbaren und nicht zwischenspeicherbaren Abfragen finden Sie in der Adobe Commerce [Entwicklerdokumentation](https://devdocs.magento.com/guides/v2.4/graphql/caching.html).

## Katalogflachtabelle

Die Verwendung von flachen Tabellen für Produkte und Kategorien wird nicht empfohlen. Die Verwendung dieser veralteten Funktion kann zu Leistungsbeeinträchtigungen und Indizierungsproblemen führen. Daher sollte der reduzierte Katalog über den Adobe Commerce-Administrator im Storefront-Bereich deaktiviert werden. Einige Module und Anpassungen von Drittanbietern erfordern eine korrekte Funktionsweise flacher Tabellen. Es wird empfohlen, eine Bewertung durchzuführen, um die Auswirkungen und Risiken zu verstehen, die mit der Verwendung flacher Tabellen verbunden sind, wenn diese Erweiterungen oder Anpassungen verwendet werden.

## Schutz vor fastem Ursprung

Standardmäßig ist die Fastly-Ursprungs-Abschirmung nicht aktiviert. Der Zweck der Herkunfts-Shirting von Fastly besteht darin, den Traffic direkt auf den Ursprung von Adobe Commerce zu reduzieren: Wenn eine Anforderung empfangen wird, prüft ein am schnellsten Edge-Standort (oder &quot;Punkt des Vorhandenseins&quot;/&quot;POP&quot;), ob der Inhalt im Cache gespeichert wurde, und stellt ihn bereit. Wenn er nicht zwischengespeichert wird, prüft er weiterhin, ob er dort zwischengespeichert wird (wenn der Inhalt zuvor auch von einem anderen globalen POP angefordert wurde, wird er zwischengespeichert). Wenn nicht im Schild POP zwischengespeichert, wird nur dann der Origin-Server gestartet.

Die schnelle Ursprungsabschirmung kann in Ihren Adobe Commerce-Admin-Backend-Einstellungen für die schnelle Konfiguration aktiviert werden. Sie sollten einen Schildspeicherort wählen, der Ihrem Adobe Commerce-Herkunftsdatenzentrum am nächsten ist, um die beste Leistung zu erzielen.

## Schnelle Bildoptimierung

Sobald die Fastly-Ursprungs-Shielding aktiviert ist, können Sie damit auch Fastly Image Optimizer aktivieren. Wenn Produktkatalogbilder in Adobe Commerce gespeichert werden, bietet dieser Dienst die Möglichkeit, alle ressourcenintensiven Produktkatalogbildverarbeitungen aus der Adobe Commerce-Herkunft auf Schnell und aus zu laden. Die Antwortzeiten der Endbenutzer werden auch für Seitenladezeiten verbessert, da Bilder an der Edge-Position umgewandelt werden, wodurch Latenzzeiten vermieden werden, indem die Anzahl der Anforderungen zurück an die Adobe Commerce-Herkunft reduziert wird.

Die schnelle Bildoptimierung kann durch &quot;Deep-Image-Optimierung aktivieren&quot;in der Fastly-Konfiguration in Admin aktiviert werden, allerdings erst, nachdem Ihr Ursprungsschild aktiviert wurde. Weitere Informationen zu Konfigurationen für die schnelle Bildoptimierung finden Sie in der Adobe Commerce [Entwicklerdokumentation](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html).

![Screenshot der Fastly-Bildoptimierungseinstellungen in der Adobe Commerce Admin](../assets/commerce-at-scale/image-optimization.svg)

## Nicht verwendete Module deaktivieren

Wenn Adobe Commerce Headless ausgeführt wird, nur Anforderungen über den GraphQL-Endpunkt verarbeitet werden und keine Frontend-Store-Seiten direkt von Adobe Commerce bereitgestellt werden, werden viele Module redundant und nicht verwendet. Durch die Deaktivierung nicht verwendeter Module wird die Adobe Commerce-Codebasis kleiner und weniger komplex und könnte daher Leistungsverbesserungen bieten. Die Deaktivierung von Modulen in Adobe Commerce kann mit Composer verwaltet werden. Welche Module deaktiviert werden können, hängt von den Anforderungen für Ihre Site ab. Daher kann keine empfohlene Liste angegeben werden, da sie für die Implementierung von Adobe Commerce durch jeden Kunden spezifisch ist.

## Aktivierung der MySQL- und Redis-Verbindung

Standardmäßig sind MySQL- und Redis Slave-Verbindungen in Adobe Commerce in Cloud nicht aktiviert. Dies liegt daran, dass diese Einstellungen nur für Kunden geeignet sind, die eine sehr hohe Auslastung erwarten. Die Latenz zwischen Cross-AZ (Verfügbarkeitszonen) ist höher, wenn Slave-Verbindungen aktiviert sind. Daher verringert diese Einstellung die Leistung eines Adobe Commerce in der Cloud-Instanz tatsächlich, falls die Instanz nur normale Ladestufen erhält.

Wenn die Adobe Commerce-Instanz eine extreme Auslastung erwartet, hilft die Aktivierung von Übergeordnet-Slave für MySQL und Redis bei der Performance, indem die Auslastung der MySQL-Datenbank oder von Redis über verschiedene Knoten verteilt wird.

In Umgebungen mit normaler Belastung verlangsamt die Aktivierung von Slave-Verbindungen die Leistung um 10-15 %. Bei Clustern mit hoher Auslastung und starkem Traffic wird die Leistung jedoch um etwa 10-15 % gesteigert. Daher ist es wichtig, Ihre Umgebung mit dem erwarteten Traffic-Niveau zu testen, um zu beurteilen, ob diese Einstellung für Ihre Leistungszeiten bei Belastung von Vorteil ist.

Um Slave-Verbindungen für mysql und redirect zu aktivieren/deaktivieren, sollten Sie Ihre `.magento.env.yaml`-Datei so bearbeiten, dass sie Folgendes enthält:

```
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

Für skalierte Architektur (Aufspaltungsarchitektur - siehe unten) sollten Redis-Slave-Verbindungen nicht aktiviert sein, da dadurch Fehler angezeigt werden. Im Falle einer Aufspaltungsarchitektur wird stattdessen empfohlen, die L2-Zwischenspeicherung für Redis zu implementieren.

## Wechsel zu einer Adobe Commerce in Cloud skalierter (geteilter) Architektur

Wenn nach allen oben genannten Konfigurationen die Lasttest-Ergebnisse oder die Analyse der Live-Infrastrukturleistung immer noch darauf hinweisen, dass die Auslastungsstufen zu Adobe Commerce auf einem Niveau liegen, das CPU- und andere Systemressourcen konsistent ausgleicht, sollte ein Wechsel zu einer skalierten (geteilten) Architektur in Betracht gezogen werden.

Mit einer standardmäßigen Pro-Architektur gibt es 3 Knoten, von denen jeder einen vollständigen Tech-Stapel enthält. Durch die Konvertierung in die Aufspaltungsebenen-Architektur ändert sich dies auf mindestens 6 Knoten: 3 davon Elasticsearch, MariaDB, Redis und andere Hauptdienste; die anderen 3 für die Verarbeitung von Web-Traffic enthalten phpfpm und NGINX. Es gibt größere Skalierungsmöglichkeiten für die Aufspaltungsebene: Kernknoten, die Datenbanken enthalten, können vertikal skaliert werden. Web-Knoten können horizontal und vertikal skaliert werden, was eine große Flexibilität bietet, um die Infrastruktur nach Bedarf für einen festgelegten Zeitraum mit hoher Auslastung und auf Knoten, auf denen die zusätzlichen Ressourcen benötigt werden, zu erweitern.

Wenn aufgrund hoher Auslastungserwartungen für Ihre Site entschieden wurde, zu einer geteilten Tier-Architektur zu wechseln, sollten Sie sich mit Ihrem Customer Success Manager über die Schritte zur Aktivierung dieser Option unterhalten.
