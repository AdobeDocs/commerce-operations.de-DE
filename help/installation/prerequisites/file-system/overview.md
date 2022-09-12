---
title: Dateieigentum und -berechtigungen
description: Erfahren Sie mehr über die Bedeutung von Dateisystemberechtigungen für die Arbeit mit lokalen Installationen von Adobe Commerce und Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Dateieigentum und -berechtigungen

Es ist wichtig, Ihre Adobe Commerce- oder Magento Open Source-Installation in einer Entwicklungsumgebung zu sichern, um Probleme im Zusammenhang mit nicht autorisierten Personen oder Prozessen zu verhindern, die auf Ihr System zugreifen und möglicherweise Ihr System schädigen. Verwenden Sie zum Schutz Ihrer Installation die folgenden Richtlinien zur Eigentümerschaft des Dateisystems und zu Berechtigungen.

## Dateisysteminhaber

Der Dateisysteminhaber ist ein Benutzer, der Schreibberechtigungen für Dateien im Dateisystem besitzt und besitzt.

Es gibt zwei Arten von Dateisysteminhabern:

- **Freigegebenes Hosting für einen einzelnen Benutzer**

   Mit freigegebenen Hosting-Anbietern können Sie sich als ein Benutzer beim Anwendungsserver anmelden. Als einzelner Benutzer können Sie sich anmelden, Dateien über FTP übertragen und den Webserver ausführen. Sie haben die Möglichkeit, eine [`umask`](#restrict-access-with-a-umask) weitere Einschränkung des Zugangs, insbesondere in einem Produktionsumfeld.

- **Privates Hosting mit zwei Benutzern**

   Private Hosting ist nützlich, wenn Sie einen Anwendungsserver verwalten. Jeder Benutzer hat eine spezifische Verantwortung:

   - Die _Webserver-Benutzer_ führt die Admin- und Storefront aus.

   - Die _Befehlszeilenbenutzer_ führt Cron-Aufträge und Befehlszeilen-Dienstprogramme aus.
   Beide Benutzer benötigen dieselben Berechtigungen für das Dateisystem. Daher ist es am besten, eine [freigegebene Gruppe](configure-permissions.md#set-ownership-and-permissions-for-two-users) und legen Sie eine [`umask`](#restrict-access-with-a-umask).

### Zugriff auf eine Umfrage beschränken

Um die Sicherheit insbesondere in einer Produktionsumgebung auf einem gemeinsamen Hosting-System zu erhöhen, können Sie `umask` , um den Zugriff zu beschränken. A `umask`—auch als _Erstellungsmaske des Dateisystems_—ist ein Satz von Bit, der steuert, wie die Dateiberechtigungen für neu erstellte Dateien festgelegt werden.

>[!WARNING]
>
>Die Sicherheit des Dateisystems ist komplex und wichtig. Es wird dringend empfohlen, sich an einen erfahrenen Systemadministrator oder Netzwerkadministrator zu wenden, bevor Sie die festzulegenden Berechtigungen festlegen. Wir bieten Ihnen einen Mechanismus, den Sie verwenden können, aber die Erstellung einer Berechtigungsstrategie liegt in Ihrer Verantwortung.

Adobe Commerce und Magento Open Source verwenden eine 3-Bit-Standardmaske: `002`. Ziehen Sie die Standardmaske von den UNIX-Standardeinstellungen von 666 für Dateien und 777 für Ordner ab.

Beispiel:

- **775 für Verzeichnisse**—Vollständige Kontrolle durch den Benutzer, vollständige Kontrolle durch die Gruppe und ermöglicht jedem, das Verzeichnis zu durchlaufen. Diese Berechtigungen sind normalerweise für freigegebene Hosting-Anbieter erforderlich.

- **664 für Dateien**—Schreibbar durch den Benutzer, schreibbar durch die Gruppe und schreibgeschützt für alle anderen.

Weitere Informationen zum Erstellen eines `magento_umask` -Datei, siehe [Umfrage setzen](../../next-steps/set-umask.md).

## Berechtigungen, Eigentümer und Anwendungsmodi

Wir empfehlen verschiedene Berechtigungen und Eigentumsrechte, wenn Sie die verschiedenen Anwendungsmodi von Adobe Commerce und Magento Open Source verwenden:

- Standard
- Entwickler
- Produktion

Siehe [Über Modi](../../../configuration/bootstrap/application-modes.md) im _Konfigurationshandbuch_.

Weitere Informationen zu Berechtigungsempfehlungen finden Sie unter [Zugriffsberechtigungen für Dateisysteme](../../../configuration/deployment/file-system-permissions.md) im _Konfigurationshandbuch_.

>[!TIP]
>
>Lesen Sie vor der Installation von Adobe Commerce oder Magento Open Source den Abschnitt [Konfigurieren des Eigentums an Dateien und der Berechtigungen](configure-permissions.md).
