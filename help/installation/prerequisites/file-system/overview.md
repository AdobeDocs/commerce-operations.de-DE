---
title: Dateieigentum und -berechtigungen
description: Erfahren Sie mehr über die Bedeutung von Dateisystemberechtigungen bei der Arbeit mit lokalen Installationen von Adobe Commerce.
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Dateieigentum und -berechtigungen

Es ist wichtig, die Adobe Commerce-Installation in einer Entwicklungsumgebung zu sichern, um Probleme im Zusammenhang mit dem Zugriff unberechtigter Personen oder Prozesse auf Ihr System und dessen potenzielle Beschädigung zu verhindern. Verwenden Sie die folgenden Richtlinien für Dateisystemeigentum und -berechtigungen, um Ihre Installation zu schützen.

## Dateisystembesitzer

Der Dateisystembesitzer ist ein Benutzer, der Schreibberechtigungen für Dateien im Dateisystem besitzt und besitzt.

Es gibt zwei Arten von Dateisystembesitzern:

- **Gemeinsames Hosting mit einem einzelnen Benutzer**

  Mit Anbietern freigegebener Hosts können Sie sich als ein Benutzer beim Anwendungsserver anmelden. Als einzelner Benutzer können Sie sich anmelden, Dateien über FTP übertragen und den Webserver ausführen. Sie haben die Möglichkeit, eine [`umask`](#restrict-access-with-a-umask) festzulegen, um den Zugriff weiter einzuschränken, insbesondere in einer Produktionsumgebung.

- **Privates Hosting mit zwei Benutzern**

  Privates Hosting ist nützlich, wenn Sie einen Anwendungsserver verwalten. Jeder Benutzer hat eine bestimmte Verantwortung:

   - Der _Webserver-Benutzer_ führt die Admin- und Storefront aus.

   - Der _Befehlszeilenbenutzer_ führt Cron-Aufträge und Befehlszeilen-Dienstprogramme aus.

  Beide Benutzer benötigen dieselben Berechtigungen für das Dateisystem. Daher ist es am besten, eine [freigegebene Gruppe“ zu verwenden ](configure-permissions.md#set-ownership-and-permissions-for-two-users) eine [`umask`](#restrict-access-with-a-umask) festzulegen.

### Beschränken des Zugriffs mit einer Maske

Um die Sicherheit zu erhöhen, insbesondere in einer Produktionsumgebung auf einem freigegebenen Hosting-System, können Sie `umask` verwenden, um den Zugriff einzuschränken. Ein `umask` - auch als _Dateisystem-Erstellungsmaske“ bezeichnet_ ist ein Satz von Bits, die steuern, wie die Dateiberechtigungen für neu erstellte Dateien festgelegt werden.

>[!WARNING]
>
>Dateisystemsicherheit ist komplex und wichtig. Es wird dringend empfohlen, sich an einen erfahrenen System- oder Netzwerkadministrator zu wenden, bevor Sie die Berechtigungsstufe festlegen. Wir bieten einen Mechanismus, den Sie verwenden können. Sie sind jedoch dafür verantwortlich, eine Berechtigungsstrategie zu erstellen.

Adobe Commerce verwendet eine Standardmaske mit drei Bit: `002`. Subtrahieren Sie die Standardmaske von den UNIX-Standardwerten 666 für Dateien und 777 für Verzeichnisse.

Beispiel:

- **775 für Verzeichnisse** - Vollständige Kontrolle durch den Benutzer, volle Kontrolle durch die Gruppe und ermöglicht es jedem, das Verzeichnis zu durchlaufen. Diese Berechtigungen werden normalerweise von Anbietern für freigegebene Hosts benötigt.

- **664 für Dateien** - Schreibzugriff für den Benutzer, Schreibzugriff für die Gruppe und Schreibzugriff für alle anderen Benutzer.

Weitere Informationen zum Erstellen einer `magento_umask` finden Sie unter [Festlegen einer Umask](../../next-steps/set-umask.md).

## Berechtigungen, Eigentümer und Anwendungsmodi

Bei Verwendung der verschiedenen Adobe Commerce-Anwendungsmodi werden unterschiedliche Berechtigungen und Eigentümerrechte empfohlen:

- Standard
- Entwickler
- Produktion

Siehe [Über ](../../../configuration/bootstrap/application-modes.md)) im _Konfigurationshandbuch_.

Weitere Informationen zu Berechtigungsempfehlungen finden Sie unter [Zugriffsberechtigungen für Dateisysteme](../../../configuration/deployment/file-system-permissions.md) im _Konfigurationshandbuch_.

>[!TIP]
>
>Lesen Sie vor der Installation von Adobe Commerce [Konfigurieren von Dateieigentum und Berechtigungen](configure-permissions.md).
