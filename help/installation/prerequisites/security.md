---
title: Hausinterne Installationssicherheit
description: Erfahren Sie mehr über Möglichkeiten, die Sicherheitsbereitschaft Ihrer Adobe Commerce- oder Magento Open Source-Installation vor Ort zu verbessern.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Hausinterne Installationssicherheit

[Security Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page) ermöglicht CentOS- und Ubuntu-Administratoren eine bessere Zugriffskontrolle über ihre Server. Wenn Sie SELinux verwenden *und* Apache muss eine Verbindung zu einem anderen Host herstellen. Sie müssen die in diesem Abschnitt beschriebenen Befehle ausführen.

>[!NOTE]
>
>Adobe hat keine Empfehlung zur Verwendung von SELinux. Sie können sie bei Bedarf für eine höhere Sicherheit verwenden. Wenn Sie SELinux verwenden, müssen Sie es ordnungsgemäß konfigurieren, oder die Adobe Commerce und Magento Open Source können unvorhersehbar funktionieren. Wenn Sie sich für die Verwendung von SELinux entscheiden, konsultieren Sie eine Ressource wie die [CentOS-Wiki](https://wiki.centos.org/HowTos/SELinux) , um Regeln für die Aktivierung der Kommunikation festzulegen.

## Vorschläge für die Installation mit Apache

Wenn Sie SELinux aktivieren, kann es bei der Ausführung des Installationsprogramms zu Problemen kommen, es sei denn, Sie ändern die *Sicherheitskontext* aus einigen Verzeichnissen wie folgt:

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

Die vorherigen Befehle funktionieren nur mit dem Apache-Webserver. Aufgrund der unterschiedlichen Konfigurationen und Sicherheitsanforderungen garantieren wir nicht, dass diese Befehle in allen Situationen funktionieren. Weitere Informationen finden Sie unter:

* [Manpage](https://linux.die.net/man/8/httpd_selinux)
* [Server-Lab](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Aktivieren der Kommunikation zwischen Servern

Wenn sich Apache und der Datenbankserver auf demselben Host befinden, verwenden Sie den folgenden Befehl, wenn Sie Integrationen verwenden möchten, die `curl` (z. B. Paypal und USPS).
So aktivieren Sie Apache, um eine Verbindung zu einem anderen Host mit aktiviertem SELinux herzustellen:

1. Verwenden Sie den folgenden Befehl, um festzustellen, ob SELinux aktiviert ist:

   ```bash
   getenforce
   ```

   `Enforcing` zeigt an, um zu bestätigen, dass SELinux ausgeführt wird.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Öffnen von Ports in Ihrer Firewall

Je nach Ihren Sicherheitsanforderungen kann es erforderlich sein, Port 80 und andere Ports in Ihrer Firewall zu öffnen. Aufgrund der Sensibilität der Netzwerksicherheit empfiehlt Adobe dringend, sich mit Ihrer IT-Abteilung in Verbindung zu setzen, bevor Sie fortfahren. Im Folgenden finden Sie einige empfohlene Verweise:

* Ubuntu: [Ubuntu-Dokumentationsseite](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS-Anleitung](https://wiki.centos.org/HowTos/Network/IPTables).
