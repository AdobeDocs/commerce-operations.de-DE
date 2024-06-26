---
title: Dateieigentum und Berechtigungen
description: Erfahren Sie mehr über die Bedeutung von Dateisystemberechtigungen für die Arbeit mit lokalen Installationen von Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Dateieigentum und Berechtigungen

Es ist wichtig, Ihre Adobe Commerce-Installation in einer Entwicklungsumgebung zu sichern, um Probleme im Zusammenhang mit nicht autorisierten Personen oder Prozessen zu verhindern, die auf Ihr System zugreifen und möglicherweise Ihr System schädigen. Verwenden Sie zum Schutz Ihrer Installation die folgenden Richtlinien zur Eigentümerschaft des Dateisystems und zu Berechtigungen.

## Dateisysteminhaber

Der Dateisysteminhaber ist ein Benutzer, der über Schreibberechtigungen für Dateien im Dateisystem verfügt und diese besitzt.

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

Adobe Commerce verwendet eine 3-Bit-Standardmaske: `002`. Ziehen Sie die Standardmaske von den UNIX-Standardeinstellungen von 666 für Dateien und 777 für Ordner ab.

Beispiel:

- **775 für Verzeichnisse**—Vollständige Kontrolle durch den Benutzer, vollständige Kontrolle durch die Gruppe und ermöglicht jedem, das Verzeichnis zu durchlaufen. Diese Berechtigungen sind normalerweise von freigegebenen Hosting-Anbietern erforderlich.

- **664 für Dateien**—Schreibbar durch den Benutzer, schreibbar durch die Gruppe und schreibgeschützt für alle anderen.

Weitere Informationen zum Erstellen eines `magento_umask` -Datei, siehe [Setzen einer Umfrage](../../next-steps/set-umask.md).

## Berechtigungen, Eigentümer und Anwendungsmodi

Wir empfehlen verschiedene Berechtigungen und Eigentumsrechte, wenn Sie die verschiedenen Adobe Commerce-Anwendungsmodi verwenden:

- Standard
- Entwickler
- Produktion

Siehe [Über Modi](../../../configuration/bootstrap/application-modes.md) im _Konfigurationshandbuch_.

Weitere Informationen zu Berechtigungen finden Sie in [Zugriffsberechtigungen für Dateisysteme](../../../configuration/deployment/file-system-permissions.md) im _Konfigurationshandbuch_.

>[!TIP]
>
>Lesen Sie vor der Installation von Adobe Commerce den Abschnitt [Konfigurieren von Dateieigentum und Berechtigungen](configure-permissions.md).
