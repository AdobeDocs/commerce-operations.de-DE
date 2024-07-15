---
title: Hausinterne Installationssicherheit
description: Erfahren Sie, wie Sie die Sicherheitsbereitschaft Ihrer Adobe Commerce-Installation vor Ort verbessern können.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Hausinterne Installationssicherheit

[Security Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page) ermöglicht CentOS- und Ubuntu-Administratoren eine bessere Zugriffskontrolle über ihre Server. Wenn Sie SELinux *und* Apache verwenden, müssen Sie eine Verbindung zu einem anderen Host herstellen, müssen Sie die in diesem Abschnitt beschriebenen Befehle ausführen.

>[!NOTE]
>
>Adobe hat keine Empfehlung zur Verwendung von SELinux; Sie können es für eine höhere Sicherheit verwenden, wenn Sie möchten. Wenn Sie SELinux verwenden, müssen Sie es ordnungsgemäß konfigurieren oder die Adobe Commerce kann unvorhersehbar funktionieren. Wenn Sie SELinux verwenden möchten, wenden Sie sich an eine Ressource wie das [CentOS-Wiki](https://wiki.centos.org/HowTos/SELinux) , um Regeln zur Aktivierung der Kommunikation einzurichten.

## Vorschläge für die Installation mit Apache

Wenn Sie SELinux aktivieren, kann es bei der Ausführung des Installationsprogramms zu Problemen kommen, es sei denn, Sie ändern den *Sicherheitskontext* einiger Verzeichnisse wie folgt:

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

Die vorherigen Befehle funktionieren nur mit dem Apache-Webserver. Aufgrund der unterschiedlichen Konfigurationen und Sicherheitsanforderungen garantieren wir nicht, dass diese Befehle in allen Situationen funktionieren. Weitere Informationen finden Sie unter

* [man page](https://linux.die.net/man/8/httpd_selinux)
* [Server-Lab](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Aktivieren der Kommunikation zwischen Servern

Wenn sich Apache und der Datenbankserver auf demselben Host befinden, verwenden Sie den folgenden Befehl, wenn Sie Integrationen verwenden möchten, die `curl` (z. B. Paypal und USPS).
So aktivieren Sie Apache, um eine Verbindung zu einem anderen Host mit aktiviertem SELinux herzustellen:

1. Verwenden Sie den folgenden Befehl, um festzustellen, ob SELinux aktiviert ist:

   ```bash
   getenforce
   ```

   `Enforcing` wird angezeigt, um zu bestätigen, dass SELinux ausgeführt wird.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Öffnen von Ports in Ihrer Firewall

Je nach Ihren Sicherheitsanforderungen kann es erforderlich sein, Port 80 und andere Ports in Ihrer Firewall zu öffnen. Aufgrund der sensiblen Eigenschaften der Netzwerksicherheit empfiehlt Adobe dringend, sich mit Ihrer IT-Abteilung in Verbindung zu setzen, bevor Sie fortfahren. Im Folgenden finden Sie einige empfohlene Verweise:

* Ubuntu: [Ubuntu-Dokumentationsseite](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS-Anleitung](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
