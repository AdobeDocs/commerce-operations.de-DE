---
title: Anwendung konfigurieren
description: Erfahren Sie mehr über die Konfiguration nach der Installation, die für lokale Adobe Commerce-Implementierungen erforderlich ist.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 0%

---

# Anwendung konfigurieren

Nachdem Sie die Installation von Adobe Commerce abgeschlossen haben, müssen Sie es konfigurieren. Dieses Thema enthält einige empfohlene Konfigurationseinstellungen.

## Einrichten von Cron

Der UNIX-Task Scheduler (Cron) ist für die laufenden Vorgänge der Anwendung von entscheidender Bedeutung. Er plant Dinge wie Neuindizierung, Newsletter, E-Mails und Sitemaps. Eine *crontab* ist eine Cron-Konfiguration.

Sie müssen die Adobe Commerce-Dienste in der Registerkarte *crontab* installieren, oder einige Kernfunktionen (und einige Erweiterungen von Drittanbietern) funktionieren nicht ordnungsgemäß.

Weitere Informationen zu Cron, einschließlich der Möglichkeit, eine Crontab zu entfernen und Cron über die Befehlszeile auszuführen, finden Sie unter [Konfigurieren und Ausführen von cron](../../configuration/cli/configure-cron-jobs.md).

## Sicherheitseinstellungen und Empfehlungen

Nach der Installation wird Folgendes empfohlen:

* Stellen Sie sicher, dass Ihr Dateieigentum und Ihre Berechtigungen ordnungsgemäß festgelegt sind.
* Es wird dringend empfohlen, [den standardmäßigen Administrator-URI](../tutorials/admin-uri.md) von `admin` in etwas Anderes zu ändern.
* Stellen Sie sicher, dass der [`X-Frame-Option` HTTP-Header](../../configuration/security/xframe-options.md) richtig eingerichtet ist.
* Vorsichtsmaßnahmen gegen Cross-Site-Scripting (XSS) durch [Schützen Ihrer Vorlagen](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Wenn Sie das GitHub-Repository durch [Klonen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) installiert haben, stellen Sie sicher, dass Sie bei der Bereitstellung der Anwendung nur Dateien und Ordner einschließen, die für die Produktionsumgebung erforderlich sind. Nicht benötigte Dateien und Ordner können Sicherheitsrisiken darstellen.

## Aktivieren von Neuschreibungen des Apache-Servers

Wenn Sie den Apache-Webserver verwenden, müssen Sie Serverumschreibungen aktivieren, damit Seiten ordnungsgemäß angezeigt werden. Andernfalls werden Seiten ohne Stile und andere Probleme angezeigt.

[Abschnitt auf Apache-Server-Neuschreibungen](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Zwischenspeicherung in einer Umgebung mit mehreren Webknoten

Wenn Sie mehrere Webknoten haben, können Sie *nicht* die standardmäßige Dateizwischenspeicherung der Anwendung verwenden, da keine Synchronisierung zwischen Webknoten erfolgt. Anders ausgedrückt: Die Aktivität auf einem Webknoten wird nur in das Dateisystem dieses Webknotens geschrieben. Eine nachfolgende Aktivität, die auf einem anderen Webknoten ausgeführt wird, kann dazu führen, dass unnötige Dateien geschrieben werden, oder zu Fehlern führen.

Verwenden Sie stattdessen [Redis](../../configuration/cache/config-redis.md) sowohl für den Standard-Cache als auch für den Seiten-Cache.

## Servereinstellungen

In diesem Abschnitt werden kurz die Einstellungen erläutert, die Sie für den Server berücksichtigen sollten, auf dem die Anwendung ausgeführt wird. Einige dieser Einstellungen beziehen sich nicht direkt auf die Anwendung. Sie werden nur als Vorschläge bereitgestellt.

### Protokollrotation

Mit dem Dienstprogramm UNIX `logrotate` können Sie Systeme verwalten, die eine große Anzahl von Protokolldateien generieren. Dies ermöglicht das automatische Rotieren, Komprimieren, Entfernen und Versenden von Protokolldateien. Jede Protokolldatei kann täglich, wöchentlich, monatlich oder dann verarbeitet werden, wenn die Protokolldatei eine bestimmte Größe überschreitet.

Weitere Informationen finden Sie unter einer der folgenden Themen:

* [HowTo: Das ultimative Tutorial zum Rotieren von Protokollbefehlen mit zehn Beispielen](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stack Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` man page](https://linuxconfig.org/logrotate-8-manual-page)

### Richten Sie iptrules ein, um die Kommunikation verschiedener Dienste zu ermöglichen

Unabhängig davon, ob Sie einen oder mehrere Server haben, müssen Sie Ports in der Firewall öffnen, um die Kommunikation zwischen Diensten zu ermöglichen. Wenn Sie beispielsweise die Solr-Suchmaschine mit Adobe Commerce verwenden, müssen Sie sie für die Kommunikation mit dem Webserver aktivieren. Wenn Sie über mehrere Webknoten verfügen, müssen Sie diese für die Kommunikation untereinander aktivieren.

Weitere Informationen:

* Ubuntu: [Ubuntu-Dokumentationsseite](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [CentOS-Anleitung](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### Verbesserte Sicherheitsregeln für Linux (SELinux)

Wir haben keine Empfehlung dafür, ob Sie SELinux verwenden. Wenn Sie es jedoch verwenden, müssen Sie Dienste so konfigurieren, dass sie miteinander kommunizieren, ähnlich wie beim Konfigurieren von iptables.

Weitere Informationen:

* Ubuntu: [Debian-Handbuch](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS-Wiki](https://wiki.centos.org/HowTos/SELinux)

### E-Mail-Server einrichten

Adobe Commerce benötigt einen E-Mail-Server. Wir empfehlen keinen bestimmten Server, Sie können jedoch Folgendes versuchen:

* Postfix für CentOS ([Digital Ocean-Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS-Dokumentation](https://www.centos.org))
* Postfix für Ubuntu ([Digital Ocean-Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu-Dokumentation](https://help.ubuntu.com/community/MailServer))

### Verfeinern Sie die Suchmaschine auf eine höhere Leistung:

Elasticsearch oder OpenSearch ist ab 2.4.0 für alle Installationen erforderlich.

* [Installieren und Konfigurieren der Suchmaschine](../../configuration/search/overview-search.md)

### Nachrichtenwarteschlange einrichten

Seit Version 2.3.0 bietet Adobe Commerce Funktionen für die Nachrichtenwarteschlange. In früheren Versionen ist er nur für Adobe Commerce verfügbar.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Nur Einstellungen für Adobe Commerce

Sie können Folgendes nur konfigurieren, wenn Sie Adobe Commerce verwenden:

* [Aufteilen von Datenbanken für den Checkout, die Auftragsverwaltung und andere Datenbanktabellen](../../configuration/storage/multi-master.md)
