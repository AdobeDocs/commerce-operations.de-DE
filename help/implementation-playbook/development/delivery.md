---
title: Projektimplementierungsmethode
description: Machen Sie sich mit der Funktionsweise der Bereitstellung von Adobe Commerce-Software vertraut.
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
feature: Build, Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Projektimplementierungsmethode

Nachdem Sie nun eine bessere Vorstellung von den damit verbundenen Tools haben, werden wir nun unsere Versand- und Testprozesse aufschlüsseln.

## Kontinuierliche Integration (CI)

Kontinuierliche Integrationsaufträge führen automatisch die folgenden Aktionen aus:

- Erstellen Sie den Quellcode, um Kompilierungsfehler zu überprüfen.
- Führen Sie Tests aus, wenn eine Pull-Anforderung erstellt/aktualisiert wird. Derzeit werden PHP-Komponententests ausgeführt.

Der Auftrag sendet seinen Ausführungsstatus an die Pull-Anforderung. Entwickler können die Details der Auftragsausführung anzeigen, damit sie vorhandenen Code korrigieren oder verbessern können.

## Kontinuierliche Bereitstellung (CD)

Continuous Delivery (CD) stellt sofort Quellcode auf dem Server bereit, nachdem alle Tests erfolgreich bestanden wurden. Entwickler können ihre Funktionen schnell überprüfen und die Aufgabe dann dem QA-Team zur Überprüfung zuweisen.

Da der Build auf dem Build-System ausgeführt wird, minimiert er nicht nur die Bereitstellungsausfälle, sondern verringert auch die Auslastung des Servers. Dadurch sind die QS-Aktivitäten, die auf dem Server stattfinden, weniger betroffen.

![Infografik zum fortlaufenden Versand](../../assets/playbooks/cicd.svg)

Der CI/CD-Prozess im vorherigen Diagramm kann kurz wie folgt beschrieben werden:

- Bitbucket hostet das Git-Repository.
- Docker-Bilder werden aus Stapelkonfigurationen der Produktionstechnologie repliziert.
- Docker-Container werden für alle Entwicklungs- und Testumgebungen verwendet. Andere Umgebungen können diese Konfigurationen bei Bedarf nutzen.
- Entwickler führen für jede neue Aufgabe/jedes neue Ticket einen Checkout der entsprechenden Codeverzweigung durch.
- Für alle Commit-Zweige automatisch:
   - Führen Sie eine standardmäßige Codescan durch.
   - Führen Sie einen Code-Kompilierungstest aus.
   - Führen Sie eine statische Codescan durch (z. B. SonarQube).
- Alle Scan-Commits, die bestanden werden, werden mit der Zielverzweigung zusammengeführt.
- Für das Bereitstellungspaket wird ein neues veröffentlichtes Tag an AWS S3 gesendet.
- Die neue Bereitstellung wird vom Bereitstellungs-Engineering-Team ausgelöst.
   - Bei einem Bereitstellungsauftrag wird das neue Paket in der Zielumgebung bereitgestellt.
   - Datenbankstrukturaktualisierungen erfordern eine Pause, um neue Anfragen des Kunden zu übernehmen.
- Der Bereitstellungsprozess endet mit einer E-Mail-/Slack-/Teams-Benachrichtigung, die vom Server automatisch an das Bereitstellungs-Engineering-Team gesendet wird.
