---
title: Sicherheit bei der Installation vor Ort
description: Erfahren Sie, wie Sie den Sicherheitszustand Ihrer lokalen Adobe Commerce-Installation verbessern können.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%
---
# Sicherheit bei der Installation vor Ort

[Security Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page) ermöglicht CentOS- und Ubuntu-Administratoren eine bessere Zugriffskontrolle über ihre Server. Wenn Sie SELinux verwenden *und* muss Apache eine Verbindung zu einem anderen Host herstellen, müssen Sie die in diesem Abschnitt beschriebenen Befehle ausführen.

>[!NOTE]
>
>Adobe hat keine Empfehlung zur Verwendung von SELinux. Sie können es für erweiterte Sicherheit verwenden, wenn Sie möchten. Wenn Sie SELinux verwenden, müssen Sie es ordnungsgemäß konfigurieren, da sonst die Adobe Commerce unvorhersehbar funktionieren kann. Wenn Sie SELinux verwenden möchten, konsultieren Sie eine Ressource wie das [CentOS Wiki](https://wiki.centos.org/HowTos/SELinux), um Regeln für die Kommunikation einzurichten.

## Vorschlag für die Installation mit Apache

Wenn Sie SELinux aktivieren, können Probleme beim Ausführen des Installationsprogramms auftreten, es sei denn, Sie ändern den *Sicherheitskontext* einiger Ordner wie folgt:

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```shell
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

Die vorherigen Befehle funktionieren nur mit dem Apache-Webserver. Aufgrund der Vielzahl von Konfigurationen und Sicherheitsanforderungen können wir nicht garantieren, dass diese Befehle in allen Situationen funktionieren. Weitere Informationen finden Sie unter:

* [Manpage](https://linux.die.net/man/8/httpd_selinux)
* [Serverlabor](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Aktivieren der Kommunikation zwischen Servern

Wenn sich Apache und der Datenbank-Server auf demselben Host befinden, verwenden Sie den folgenden Befehl, wenn Sie Integrationen verwenden möchten, die `curl` verwenden (z. B. Paypal und USPS).
So aktivieren Sie Apache, um eine Verbindung zu einem anderen Host mit aktiviertem SELinux herzustellen:

1. Um festzustellen, ob SELinux aktiviert ist, verwenden Sie den folgenden Befehl:

   ```shell
   getenforce
   ```

   `Enforcing` wird angezeigt, um zu bestätigen, dass SELinux ausgeführt wird.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Ports in der Firewall öffnen

Je nach Ihren Sicherheitsanforderungen müssen Sie möglicherweise Port 80 und andere Ports in Ihrer Firewall öffnen. Aufgrund des sensiblen Charakters der Netzwerksicherheit empfiehlt Adobe dringend, sich vor dem Fortfahren mit Ihrer IT-Abteilung zu beraten. Im Folgenden finden Sie einige vorgeschlagene Verweise:

* Ubuntu: [Ubuntu-Dokumentationsseite](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [Anleitung für CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
