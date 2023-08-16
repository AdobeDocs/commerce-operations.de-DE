---
title: Adobe Commerce-Überwachungstools selbst hosten
description: Erfahren Sie mehr über Ideen und Konzepte und Best Practices für die Self-Hosting-Monitoring-Tools.
landing-page-description: Lernen Sie einige Konzepte und Aspekte von Monitoring-Tools kennen, die Sie beim Hosten von Adobe Commerce selbst beachten sollten.
short-description: Erfahren Sie Strategien und Konzepte für Monitoring-Tools für das Hosting von Adobe Commerce selbst.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 728e9439-63d0-4481-b014-7ba2ce97b9d0
feature: Install, Logs, Observability
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---

# Self-Hosting von Adobe Commerce Monitoring-Telemetrie und -Tools

Die Verwendung von Monitoring-Tools bietet Möglichkeiten, Änderungen zu erkennen, ohne dass jemand dafür bezahlen muss, alles ständig zu beobachten. Mit den meisten Tools können Sie Warnhinweise und Benachrichtigungen hinzufügen, wenn ein Schwellenwert erreicht wird, z. B. eine Festplatte, auf der nicht genügend Speicherplatz zur Verfügung steht. Einige Tools bieten Ausgaben, die verfolgt und berechnet werden sollen, z. B. Lasttestergebnisse. Unabhängig vom Tool hat jedes Tool einen Zweck und kann bei konsistenter Verwendung bei der Verwaltung Ihrer Anwendung helfen. Es gibt kostenlose Optionen für jedes Tool, aber denken Sie daran, für einen Service zu bezahlen, sorgt oft für eine schnellere zuverlässige Unterstützung und kann die Investition wert sein. New Relic ist ein Beispiel für ein Tool, das eine freie Ebene und eine kostenpflichtige Version bietet, die viel mehr Strom und Funktionen freischaltet. Es gibt andere, wie z. B. DataDog oder Dynatrace. Suchen Sie eine gute Option für Sie und verwenden Sie sie konsistent.

## Infrastrukturüberwachung

Der Begriff &quot;Infrastruktur&quot;wird in diesem Zusammenhang eher lose verwendet. Für dieses Thema bedeutet dies jeden Server, Prozess oder Gerät, der zum Betrieb der Site verwendet wird. Beispiel:

* Festplatten
* CPU-Auslastung
* RAM-Nutzung
* Redis
* Durchschnittliche Auslastung pro Server
* Netzwerkverkehr

Forschungsschwellen zur Erstellung wirksamer Warnhinweise. Weisen Sie für wichtige Dinge wie Festplattenkapazität keine zu. Richten Sie ein paar ein, um verschiedene Gruppen zu benachrichtigen, wenn sich die Lage verschlechtert. Hier finden Sie beispielsweise einen Regelsatz, wenn eine Festplatte voll wird.

* 70 % Slack-Benachrichtigung für den DevOps-Kanal
* 80 % Benachrichtigen Sie den Slack Room DevOps-Kanal und eine E-Mail-Verteilungsliste von DevOps-Teams.
* 90 % Slack DevOps-Kanal und Produktionsunterstützungskanal benachrichtigen Slack, E-Mail DevOps-Verteilungsgruppe und Technikmanager
* 95% Slack DevOps und Slack-Kanäle für Produktionsunterstützung benachrichtigen, E-Mail-Verteilungsliste aller Ingenieure und Director of Engineering
* 98 % Über P1-Slack-Kanäle und DevOps und Slack-Kanäle für Produktionsunterstützung, E-Mail-Verteilungsliste von Technikern und Director of Engineering und VP of technology informieren

Es gibt viele Möglichkeiten, ein Team zu benachrichtigen. Wählen Sie also ein zuverlässiges Team aus, das nicht mit zu vielen Warnhinweisen überflutet wird. Es ist wichtig, Warnhinweise zu reservieren, wenn dies wichtig ist. Andernfalls besteht die Gefahr, dass Sie überlastet werden und Warnhinweise ignorieren.

Für die meisten Tools wie New Relic, DataDog und Dynatrace sind häufig gute Vorlagen zu beachten. Nehmen Sie sich Zeit, um gute Ideen zu finden, die für Ihre Anwendung am sinnvollsten sind. Bei Adobe Commerce zur Cloud-Infrastruktur gibt es Warnhinweise und Trigger, die bei der Bereitstellung des Projekts vorhanden sind. Dadurch kann das Adobe-Produktions-Support-Team seine Tools für die Betriebszeit- und Hochverfügbarkeitsüberwachung anwenden.

Dashboards bieten schnellen Zugriff auf die häufigen oder wichtigen Aspekte Ihrer Site. Dashboard-Elemente können aus Seitenansichten, CPU-Auslastung pro Host, Liste aller Server, Seitenladezeiten, Transaktionsdauern und sogar Ergebnissen synthetischer Überwachungstests für die letzten Tage bestehen. Diese Dashboards sollten so konzipiert sein, dass sie schnell getestet werden können, wenn etwas nicht stimmt oder verschiedene Dashboards für verschiedene Benutzererlebnisse eingerichtet sind. Hoffentlich können Sie mehrere Dashboards entwerfen und Ihre Anwendungsüberwachung in Echtzeit sehen. Es ist sehr zufrieden, insbesondere wenn Sie vom Eigentümer des Projekts oder einem Manager gefragt werden, wie die Website funktioniert, und Sie die Antwort in Sekunden finden können, nicht in Stunden.

## Protokollierung und -rotation

Protokolldateien werden auf Anwendungsservern gefunden, die Anfragen verarbeiten oder MySQL-Protokolle verarbeiten, wenn die Ausführung der Dinge zu lange dauert. Das Schwierigste an Protokollen ist, dass sie voneinander getrennt sind und alle finden, das Parsen der Informationen aus jedem Protokoll umständlich sein kann. Vor vielen Jahren wurde dieses Problem mithilfe einer Technik behoben, die _Protokollaggregation_. Dadurch werden Protokolldateien von allen Protokollspeicherorten an einen zentralen Speicherort übertragen. Sobald die verschoben wurden, kann ein Teil der Software sie lesen und Möglichkeiten bieten, die Informationen zu suchen, zu filtern und zu überprüfen. Dies kann ein schwieriger Prozess sein, um richtig zu kommen. Es gibt viele Optionen, aber wenn Sie Glück haben, können Ihre Monitoring-Tools Ihre Protokolldateien wie New Relic lesen und aggregieren. Wenn Sie ein gutes Werkzeug finden, können Sie sich in Zukunft eine unmessbare Zeit sparen. Sofern Sie nicht nur über einen einzelnen Server verfügen, der alles für die Ausführung und den Betrieb Ihrer Site tut, ist die Protokollierung von Aggregationen unerlässlich. Dies ist besonders nützlich, wenn Sie versuchen herauszufinden, ob Sie unter einem DDoS-Angriff leiden oder eine legitime Traffic-Spitze erleben oder wenn Sie untersuchen, warum eine bestimmte Anfrage fehlschlägt.

Ein weiteres wichtiges Element für Logs ist, sicherzustellen, dass eine Drehung stattfindet. Dies bezieht sich historisch auf `run-away logs` die versehentlich Ihre Festplatte füllen und dazu führen kann, dass die Website herunterfährt. Eine Protokollrotation kann auftreten, wenn eine Protokolldatei eine bestimmte Größe erreicht, z. B. 1 GB. Es gibt Tools auf Serverebene wie `logrotate` automatisch entfernen. Beispielsweise können zu große Protokolldateien entfernt werden, wenn sie größer als 1 GB sind, oder Protokolldateien, die älter als 90 Tage sind. Da Sie eine Protokollrichtlinie definieren, ist es wichtig, die Einschränkungen Ihrer Ressourcen zu verstehen.

## Malware-Scans

Viele Website-Hosting-Unternehmen, die für Adobe Commerce gewidmet sind, hätten eine Bibliothek bekannter Exploits und Malware. Sie sollten entweder automatisch oder auf Anfrage eine Prüfung anbieten. Wo diese effektiv sind, sind sie reaktionär und funktionieren nur, wenn neue Malware erkannt wird. Es kann eine gute Idee sein, ein proaktives Tool zu haben, das sich den Code und die Datenbank auf bekannte Malware ansehen kann. Es stehen einige Optionen zur Verfügung, z. B. [MageReport](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"}, or [Magento Malware Scanner](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Sie können entweder eine Remote-Prüfung von außen durchführen oder nach der Einrichtung auf den Servern installiert und proaktiv aktualisiert/überprüft/überwacht werden. Dies kann eine großartige Option sein, da ihre Bibliothek ständig aktualisiert wird, da sie Tausende von Sites installiert und überwacht werden, wenn Sie eine bereitgestellte Lösung wie Sansec wählen. Da eine neue Malware erkannt wird, profitiert jedes von ihnen überwachte Projekt von den Informationen und wird jetzt benachrichtigt, wenn sie erkannt wird.

Es gibt einige kostenlose Versionen zu beachten, aber für Malware sollten Sie wirklich eine bezahlte Lösung in Erwägung ziehen. Dies kann einen Unterschied zwischen der Infektion Ihrer Site über einige Minuten und der Infektion über einige Monate darstellen. Eine Ausbeutung auf Ihrer Website verursacht enorme Kopfschmerzen. Dies ist ein Bereich, den Sie in Erwägung ziehen sollten, für eine Dienstleistung zu bezahlen.

## Adobe Site-weites Analyse-Tool

Das Site-weite Analyse-Tool ist ein proaktives Self-Service-Tool und zentrales Repository mit detaillierten Systemeinblicken und Empfehlungen, um die Sicherheit und Bedienbarkeit Ihrer Adobe Commerce-Installation sicherzustellen. Es bietet rund um die Uhr eine Leistungsüberwachung, Berichte und Beratung in Echtzeit, um potenzielle Probleme zu identifizieren und bessere Sichtbarkeit in Bezug auf Gesundheit, Sicherheit und Anwendungskonfigurationen der Website zu erreichen. Dies trägt zur Verkürzung der Auflösungszeit und zur Verbesserung der Site-Stabilität und -Leistung bei.

Auf der Recommendations-Seite des Site-weiten Analyse-Tools werden Empfehlungen basierend auf Best Practices zur Behebung von Problemen aufgelistet, die auf Ihrer Site erkannt wurden. Die Empfehlungen werden nach Priorität PO nach P4 sortiert, wobei PO kritisch und P4 niedrig ist. Zu den Ergebnissen gehören Beschreibung, Empfehlung, Site-Auswirkung, Ursache, Szenarien/Vorbedingungen, erwartetes Ergebnis und verwendete Tools.

Erfahren Sie mehr über die Best Practices zur Verbesserung der Site-Leistung. Verfolgen und implementieren Sie die Empfehlungen, die gemäß Priorität aufgeführt sind.

Weitere Informationen zur Installation dieses Programms auf Ihrem Projekt finden Sie unter [Installationshandbuch für das Site-weite Analyse-Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## SSL-Überwachung

Eines der vergessensten Elemente für ein Projekt ist das SSL-Zertifikat. Sie brauchen nur einmal jährlich Aufmerksamkeit, also ist es sehr einfach, sie zu vergessen. Der Ablauf Ihres Sicherheitszertifikats kann dazu führen, dass moderne Browser die Seiten auf Ihrer Site warnen oder ablehnen. Kunden können mit dem Versand von E-Mails oder dem Aufruf des Support beginnen, wenn ein solches Problem vorliegt und Sie möglicherweise nicht arbeiten können, bis es behoben ist. Jede Minute zählt. Daher ist es von größter Bedeutung, den Ablauf zu erkennen und sicherzustellen, dass die Dinge erneuert werden, damit die Website betriebsbereit bleibt. Es gibt viele Möglichkeiten zur SSL-Überwachung. Erwägen Sie die Verwendung synthetischer Überwachungstools für Ihre Site, indem Sie kostenlose oder kostengünstige Tools wie Pingdom, Keychest oder Sucuri verwenden und sogar einen Dienst abonnieren, der Warnhinweise zum Ablauf von SSL-Zertifikaten anbietet. Diese einfachen Tools können sicherstellen, dass Ihre Site-Zertifikate gültig sind, und das Ausfallrisiko für Ihre Kunden reduzieren.

## Automatisierte Tests

Automatisierte Tests wie Funktionstests oder Komponententests helfen oft dabei, Probleme aus neu eingeführten Code zu erkennen. Diese Tests erfassen möglicherweise nicht alles, da Adobe Commerce- und Komponententests in der Regel weniger als 50 % abdecken. Das bedeutet nicht, dass Sie es vermeiden sollten, sie zu schreiben und zu testen. Diese Tools sind hier, um eine weitere Sicherheits- und Sicherheitsschicht hinzuzufügen, dass alles, was begangen wird, die vordefinierten und benutzerdefinierten Tests, die Ihr Entwicklungsteam erstellt, nicht negativ beeinflusst. Durch die Durchführung dieser Tests bei jeder Implementierung werden alle wichtigen Probleme frühzeitig erkannt und es wird verhindert, dass die Dinge zur Produktion gelangen.

Belastungstests können eine Herausforderung darstellen, um die richtige Lösung zu finden. Ein Großteil der Komplexität kommt aus der Verwendung und Implementierung des Frontend. Wenn Ihre Site über ein Headless-Frontend verfügt, können Sie GraphQL- und REST-APIs testen. Wie Sie am Ende die Belastungstests durchführen, liegt bei Ihnen und dem DevOps-Team. Beachten Sie, dass jeder so bald wie möglich durchgeführte Belastungstest einen Einblick in den Status des Projekts bietet. Sie bietet auch Benchmarks für künftige Tests, um festzustellen, ob sich die Belastungstest-Ergebnisse drastisch ändern. Wenn dies der Fall ist und sie negativ sind, ist dies eine gute Gelegenheit, die neuesten Code-Änderungen zu überprüfen und nach Abschnitten zu suchen, die sich auf die Leistung auswirken, um diese zu verbessern.

Adobe Commerce bietet eine gute Anleitung zum Verständnis, wie Unit-Tests ausgeführt werden, siehe [PHP-Komponententests](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} im _Handbuch zum Anwendungstest_ auf der Adobe Developer-Dokumentations-Site.

Weitere Informationen zu Funktionstests finden Sie unter [Einführung in das Funktionstests-Framework](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
