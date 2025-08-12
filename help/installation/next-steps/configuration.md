---
title: Konfigurieren des Programms
description: Erfahren Sie mehr über die Konfiguration nach der Installation, die für lokale Adobe Commerce-Bereitstellungen erforderlich ist.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: a7c98879e027948fc887e28d4baa5fb04214ca95
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# Konfigurieren des Programms

Nachdem Sie die Installation von Adobe Commerce abgeschlossen haben, müssen Sie es konfigurieren. Dieses Thema enthält einige empfohlene Konfigurationseinstellungen.

## Cron einrichten

Der UNIX-Aufgabenplaner Cron ist für den täglichen Betrieb des Programms von entscheidender Bedeutung. Es werden Dinge wie Neuindizierung, Newsletter, E-Mails und Sitemaps geplant. Eine *crontab* ist eine Cron-Konfiguration.

Sie müssen Adobe Commerce-Services in der *crontab* installieren, da sonst einige Kernfunktionen (und einige Erweiterungen von Drittanbietern) nicht ordnungsgemäß funktionieren.

Weitere Informationen zu cron, einschließlich der Entfernung eines crontab und der Ausführung von cron über die Befehlszeile, finden Sie unter [Konfigurieren und Ausführen von cron](../../configuration/cli/configure-cron-jobs.md).

## Sicherheitseinstellungen und Empfehlungen

Nach der Installation empfehlen wir Folgendes:

* Stellen Sie sicher, dass Ihr Dateieigentümerstatus und Ihre Berechtigungen [ordnungsgemäß](../prerequisites/file-system/configure-permissions.md)
* Es wird dringend empfohlen[ den standardmäßigen Admin-URI ](../tutorials/admin-uri.md)`admin` zu ändern
* Stellen Sie sicher, dass der [`X-Frame-Option` HTTP](../../configuration/security/xframe-options.md)Header ordnungsgemäß festgelegt ist.
* Treffen Sie Vorkehrungen gegen Cross-Site-Scripting (XSS), indem Sie [Ihre Vorlagen schützen](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Wenn Sie durch [Klonen des GitHub-Repositorys](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) installiert haben, stellen Sie sicher, dass Sie bei der Bereitstellung des Programms nur die für die Produktionsumgebung erforderlichen Dateien und Ordner einbeziehen. Nicht erforderliche Dateien und Ordner können Sicherheitsrisiken aufweisen.

## Apache-Server-Neuschreibungen aktivieren

Wenn Sie den Apache-Webserver verwenden, müssen Sie Server-Neuschreibungen für Seiten aktivieren, damit sie ordnungsgemäß angezeigt werden. Andernfalls werden Seiten ohne Stile und andere Probleme angezeigt.

[Abschnitt zu Apache-Server-Neuschreibungen](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Zwischenspeicherung in einer Umgebung mit mehreren Webknoten

Wenn Sie über mehrere Web-Knoten verfügen *können Sie* standardmäßige Dateizwischenspeicherung der Anwendung verwenden, da es keine Synchronisierung zwischen Web-Knoten gibt. Mit anderen Worten wird die Aktivität auf einem Webknoten nur in das Dateisystem dieses Webknotens geschrieben. Eine nachfolgende Aktivität, die auf einem anderen Web-Knoten ausgeführt wird, kann dazu führen, dass unnötige Dateien geschrieben oder Fehler verursacht werden.

Verwenden Sie stattdessen [Redis](../../configuration/cache/config-redis.md) sowohl für den Standard-Cache als auch für den Seiten-Cache.

## Server-Einstellungen

In diesem Abschnitt werden kurz Einstellungen erläutert, die Sie für den Server berücksichtigen sollten, auf dem die Anwendung ausgeführt wird. Einige dieser Einstellungen beziehen sich nicht direkt auf das Programm. Sie werden nur als Vorschläge bereitgestellt.

### Rotation des Protokolls

Mit dem UNIX-`logrotate` können Sie Systeme verwalten, die eine große Anzahl von Protokolldateien generieren. Es ermöglicht die automatische Rotation, Komprimierung, Entfernung und Versendung von Protokolldateien. Jede Protokolldatei kann täglich, wöchentlich, monatlich oder dann verarbeitet werden, wenn die Protokolldatei eine bestimmte Größe überschreitet.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Vorgehensweise: Das Tutorial zum Drehen von Protokollen mit zehn Beispielen](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stapelaustausch](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` man page](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>Die folgenden Verfügbarkeitsinformationen gelten für Adobe Commerce in Cloud-Infrastrukturprojekten:
>
>* Starterumgebungen haben keine Protokollrotation.
>
>* Sie können die Protokollrotation in Pro Integration-Umgebungen nicht konfigurieren. Sie müssen eine benutzerdefinierte Lösung/ein benutzerdefiniertes Skript implementieren und [Ihren Cron konfigurieren](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property), um das Skript nach Bedarf auszuführen.

### iptables-Regeln einrichten, um verschiedenen Services die Kommunikation zu ermöglichen

Unabhängig davon, ob Sie über einen oder mehrere Server verfügen, müssen Sie Ports in der Firewall öffnen, um die Kommunikation zwischen Services zu ermöglichen. Wenn Sie beispielsweise die Solr-Suchmaschine mit Adobe Commerce verwenden, müssen Sie sie für die Kommunikation mit dem Webserver aktivieren. Wenn Sie mehrere Web-Knoten haben, müssen Sie ihnen die Kommunikation miteinander ermöglichen.

Weitere Informationen:

* Ubuntu: [Ubuntu-Dokumentationsseite](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [Anleitung für CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### Erweiterte Linux-Sicherheitsregeln (SELinux)

Wir haben keine Empfehlung, ob Sie SELinux verwenden sollten. Wenn Sie es jedoch verwenden, müssen Sie Dienste konfigurieren, die ähnlich wie iptables miteinander kommunizieren.

Weitere Informationen:

* Ubuntu: [Debian-Handbuch](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS-Wiki](https://wiki.centos.org/HowTos/SELinux)

### Einrichten eines E-Mail-Servers

Adobe Commerce benötigt einen E-Mail-Server. Wir empfehlen keinen bestimmten Server, aber Sie können einen der folgenden Schritte ausführen:

* Postfix für CentOS ([Digital Ocean Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS-Dokumentation](https://www.centos.org))
* Postfix für Ubuntu ([Digital Ocean Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu-Dokumentation](https://help.ubuntu.com/community/MailServer))

### Verfeinern Sie die Suchmaschine, um die Leistung zu verbessern:

Elasticsearch oder OpenSearch ist für alle Installationen ab Version 2.4.0 erforderlich.

* [Installieren und Konfigurieren der Suchmaschine](../../configuration/search/overview-search.md)

### Einrichten einer Nachrichtenwarteschlange

Seit Version 2.3.0 bietet Adobe Commerce Funktionen für die Nachrichtenwarteschlange. In früheren Versionen ist sie nur für Adobe Commerce verfügbar.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Einstellungen nur für Adobe Commerce

Folgendes können Sie nur konfigurieren, wenn Sie Adobe Commerce verwenden:

* [Aufspaltung von Datenbanken für Checkout, Bestellverwaltung und andere Datenbanktabellen](../../configuration/storage/multi-master.md)
