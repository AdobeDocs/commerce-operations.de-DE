---
title: Anwendungsmodi
description: Die Commerce-Anwendung kann je nach Bedarf in verschiedenen Modi eingesetzt werden. Zeigen Sie eine detaillierte Liste der verfügbaren Anwendungsmodi an.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# Anwendungsmodi

Sie können die Commerce-Anwendung in einem der folgenden _Modi_:

| Modusname | Beschreibung | Cloud-Unterstützung |
| ------------------------ | ------------------- | ------------- |
| [default](#default-mode) | Stellen Sie die Commerce-Anwendung auf einem einzigen Server bereit und führen Sie sie aus, ohne die Einstellungen zu ändern. _not_ für die Produktion optimiert. | no |
| [Entwickler](#developer-mode) | Ideal für die Entwicklung beim Erweitern oder Anpassen der Commerce-Anwendung. | no |
| [production](#production-mode) | Stellen Sie die Commerce-Anwendung bereit und führen Sie sie in einem Produktionssystem aus. | Ja |
| [Wartung](#maintenance-mode) | Verhindern Sie den Zugriff auf eine Site bei der Durchführung von Aktualisierungen und Konfigurationen. | Ja |

Siehe [Betriebsmodus festlegen](../cli/set-mode.md) , um zu erfahren, wie Sie die Adobe Commerce-Betriebsmodi manuell ändern.

## Cloud-Unterstützung

Die Anwendungsmodi für ein Cloud-Infrastrukturprojekt müssen nicht verwaltet werden. Aufgrund des schreibgeschützten Dateisystems können Sie die Modi in den Remote-Cloud-Umgebungen nicht ändern. Adobe Commerce in der Cloud-Infrastruktur führt die Anwendung automatisch in aus _Wartung_ -Modus während einer Bereitstellung verwenden, wodurch Ihre Site offline geschaltet wird, bis die Bereitstellung abgeschlossen ist. Andernfalls bleibt die Anwendung in _production_ -Modus. Siehe [Bereitstellungsprozess](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) im _Leitfaden zu Commerce on Cloud Infrastructure_.

Wenn Sie Cloud Docker für Commerce als Entwicklungstool verwenden, können Sie Ihr Cloud-Infrastrukturprojekt in einer Docker-Umgebung in _Entwickler_ Modus, aber die Leistung ist aufgrund zusätzlicher Dateisynchronisierungsvorgänge langsamer. Siehe [Docker-Umgebung bereitstellen](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) im _Handbuch zu Cloud Docker für Commerce_.

## Standardmodus

Die _default_ -Modus ermöglicht die Bereitstellung der Commerce-Anwendung auf einem einzelnen Server, ohne die Einstellungen zu ändern. Der Standardmodus ist jedoch aufgrund der Leistungsbeeinträchtigung statischer Dateien nicht für die Produktion optimiert. Das Erstellen statischer Dateien und das Zwischenspeichern dieser Dateien hat eine höhere Leistung als das Erstellen statischer Dateien mit dem Erstellungswerkzeug für statische Dateien.

Im Standardmodus:

- Ausnahmen werden in Protokolldateien statt in die Anzeige geschrieben
- Statische Ansichtsdateien werden zwischengespeichert
- Blendet benutzerspezifische `X-Magento-*` HTTP-Anfrage- und Antwortheader

Commerce arbeitet im Standardmodus, wenn kein anderer Modus angegeben ist.

## Entwicklermodus

Die _Entwickler_ wird zum Erweitern und Anpassen der Commerce-Anwendung empfohlen. Statische Ansichtsdateien werden nicht zwischengespeichert, sondern in die `pub/static` Verzeichnis auf Anfrage.

Im Entwicklermodus:

- Aktiviert [automatische Codekompilierung](../cli/code-compiler.md) und verbessertes Debugging
- Nicht erfasste Ausnahmen werden im Browser angezeigt
- Systemanmeldung `var/report` is verbose
- Im Fehler-Handler wird eine Ausnahme ausgelöst, anstatt protokolliert zu werden
- Eine Ausnahme wird ausgelöst, wenn ein Ereignisabonnent nicht aufgerufen werden kann
- Zeigt benutzerdefinierte `X-Magento-*` HTTP-Anfrage- und Antwortheader

## Produktionsmodus

Die _production_ Der -Modus eignet sich am besten für die Bereitstellung der Commerce-Anwendung in einem Produktionssystem. Nach der Optimierung der Serverumgebung, z. B. der Datenbank und des Webservers, sollten Sie die [Bereitstellungswerkzeug für statische Ansichtsdateien](../cli/static-view-file-deployment.md) , um statische Ansichtsdateien in die `pub/static` Verzeichnis. Dies verbessert die Leistung, indem alle erforderlichen statischen Dateien bei der Bereitstellung bereitgestellt werden, anstatt die Commerce-Anwendung zu zwingen, statische Dateien während der Laufzeit dynamisch zu lokalisieren und zu kopieren (materialisieren).

Einige Felder, wie z. B. die Abschnitte Erweiterte Systemkonfiguration und Entwicklerkonfiguration im Admin, sind nicht im Produktionsmodus verfügbar. Beispiel: Sie _cannot_ Aktivieren oder deaktivieren Sie die Cache-Typen mit dem Admin. Sie können Cache-Typen aktivieren und deaktivieren _only_ mithilfe der [Befehlszeile](../cli/manage-cache.md#config-cli-subcommands-cache-en).

Im Produktionsmodus:

- Statische Ansichtsdateien werden nur aus dem Cache bereitgestellt
- Fehler und Ausnahmen werden im Dateisystem protokolliert und dem Benutzer nie angezeigt
- Einige Konfigurationsfelder in Admin sind nicht verfügbar

## Wartungsmodus

Die _Wartung_ -Modus den Zugriff auf eine Site während Verbesserungen, Aktualisierungen und Konfigurationsaufgaben einschränkt oder verhindert. Standardmäßig leitet die Site Besucher zu einer standardmäßigen `Service Temporarily Unavailable` Seite.

Sie können eine [benutzerspezifische Wartungsseite](../../upgrade/troubleshooting/maintenance-mode-options.md), aktivieren und deaktivieren Sie den Wartungsmodus manuell und konfigurieren Sie den Wartungsmodus, damit Besucher von autorisierten IP-Adressen den Speicher normal anzeigen können. Siehe [Aktivieren und Deaktivieren des Wartungsmodus](../../installation/tutorials/maintenance-mode.md) im _Installationsanleitung_.

Wenn Sie Commerce in der Cloud-Infrastruktur verwenden, wird die Commerce-Anwendung während der Bereitstellungsphase im Wartungsmodus ausgeführt. Nach erfolgreichem Abschluss der Bereitstellung kehrt die Commerce-Anwendung im Produktionsmodus zur Ausführung zurück. Siehe [Bereitstellungshinweise](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) im _Leitfaden zu Commerce on Cloud Infrastructure_.

Im Wartungsmodus:

- Site-Besucher werden zu einer Standardeinstellung umgeleitet. `Service Temporarily Unavailable` page
- Die `var/` Verzeichnis enthält `.maintenance.flag` file
- Sie können den Besucherzugriff anhand von IP-Adressen einschränken
