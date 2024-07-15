---
title: Anwendungsmodi
description: Die Commerce-Anwendung kann je nach Bedarf in verschiedenen Modi verwendet werden. Zeigen Sie eine detaillierte Liste der verfügbaren Anwendungsmodi an.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 5003e8dcbb3736201ea19ebe30d5e56775096157
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---

# Anwendungsmodi

Sie können die Commerce-Anwendung in einem der folgenden _Modi_ ausführen:

| Modusname | Beschreibung | Cloud-Unterstützung |
| ------------------------ | ------------------- | ------------- |
| [default](#default-mode) | Stellen Sie die Commerce-Anwendung auf einem einzigen Server bereit und führen Sie sie aus, ohne die Einstellungen zu ändern. _Not_ wurde für die Produktion optimiert. | no |
| [developer](#developer-mode) | Ideal für die Entwicklung beim Erweitern oder Anpassen der Commerce-Anwendung. | no |
| [production](#production-mode) | Stellen Sie die Commerce-Anwendung bereit und führen Sie sie in einem Produktionssystem aus. | Ja |
| [maintenance](#maintenance-mode) | Verhindern Sie den Zugriff auf eine Site bei der Durchführung von Aktualisierungen und Konfigurationen. | Ja |

Informationen zum manuellen Ändern der Adobe Commerce-Betriebsmodi finden Sie unter [Festlegen des Betriebsmodus](../cli/set-mode.md) .

## Cloud-Unterstützung

Aufgrund des schreibgeschützten Dateisystems können Sie die Modi in den Remote-Cloud-Umgebungen nicht ändern. Versuchen Sie nicht, die Modi durch Änderung der Datei `app/etc/env.php` zu ändern, da das Paket `ece-tools` die Datei basierend auf mehreren Konfigurationsquellen überschreibt.

Adobe Commerce in der Cloud-Infrastruktur führt die Anwendung während einer Bereitstellung automatisch im _Wartungsmodus_ aus, wodurch Ihre Site offline geschaltet wird, bis die Bereitstellung abgeschlossen ist. Andernfalls bleibt die Anwendung im Modus _Produktion_. Siehe [Bereitstellungsprozess](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) im Handbuch _Commerce on Cloud Infrastructure_.

Wenn Sie Cloud Docker für Commerce als Entwicklungstool verwenden, können Sie Ihr Cloud-Infrastrukturprojekt in einer Docker-Umgebung im _Entwickler_ -Modus bereitstellen, aber die Leistung ist aufgrund zusätzlicher Dateisynchronisierungsvorgänge langsamer. Siehe [Bereitstellen der Docker-Umgebung](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) im Handbuch _Cloud Docker für Commerce_.

## Standardmodus

Mit dem Modus _default_ können Sie die Commerce-Anwendung auf einem einzigen Server bereitstellen, ohne Einstellungen zu ändern. Der Standardmodus ist jedoch aufgrund der Leistungsbeeinträchtigung statischer Dateien nicht für die Produktion optimiert. Das Erstellen statischer Dateien und das Zwischenspeichern dieser Dateien hat eine höhere Leistung als das Erstellen statischer Dateien mit dem Erstellungswerkzeug für statische Dateien.

Im Standardmodus:

- Ausnahmen werden in Protokolldateien statt in die Anzeige geschrieben
- Statische Ansichtsdateien werden zwischengespeichert
- Blendet benutzerdefinierte HTTP-Anforderungs- und Antwortheader `X-Magento-*` aus

Commerce arbeitet im Standardmodus, wenn kein anderer Modus angegeben ist.

## Entwicklermodus

Der Modus _Entwickler_ wird zum Erweitern und Anpassen der Commerce-Anwendung empfohlen. Statische Ansichtsdateien werden nicht zwischengespeichert, sondern bei Bedarf in das Verzeichnis `pub/static` geschrieben.

Im Entwicklermodus:

- Aktiviert die [automatische Codekompilierung](../cli/code-compiler.md) und das erweiterte Debugging
- Nicht erfasste Ausnahmen werden im Browser angezeigt
- Die Systemprotokollierung in `var/report` ist ausführlich
- Im Fehler-Handler wird eine Ausnahme ausgelöst, anstatt protokolliert zu werden
- Eine Ausnahme wird ausgelöst, wenn ein Ereignisabonnent nicht aufgerufen werden kann
- Zeigt benutzerdefinierte HTTP-Anforderungs- und Antwortheader vom Typ `X-Magento-*` an

## Produktionsmodus

Der Modus _Produktion_ eignet sich am besten für die Bereitstellung der Commerce-Anwendung in einem Produktionssystem. Nach der Optimierung der Serverumgebung, z. B. der Datenbank und des Webservers, sollten Sie das Bereitstellungswerkzeug für statische Ansichtsdateien ](../cli/static-view-file-deployment.md) ausführen, um statische Ansichtsdateien in den Ordner `pub/static` zu schreiben. [ Dies verbessert die Leistung, indem alle erforderlichen statischen Dateien bei der Bereitstellung bereitgestellt werden, anstatt die Commerce-Anwendung zu zwingen, statische Dateien während der Laufzeit dynamisch zu lokalisieren und zu kopieren (materialisieren).

Einige Felder, wie z. B. die Abschnitte Erweiterte Systemkonfiguration und Entwicklerkonfiguration im Admin, sind nicht im Produktionsmodus verfügbar. Beispielsweise können Sie _nicht_ Cache-Typen mit dem Admin aktivieren oder deaktivieren. Sie können die Cache-Typen _nur_ über die [Befehlszeile](../cli/manage-cache.md#config-cli-subcommands-cache-en) aktivieren und deaktivieren.

Im Produktionsmodus:

- Statische Ansichtsdateien werden nur aus dem Cache bereitgestellt
- Fehler und Ausnahmen werden im Dateisystem protokolliert und dem Benutzer nie angezeigt
- Einige Konfigurationsfelder in Admin sind nicht verfügbar

## Wartungsmodus

Der Modus _wartung_ schränkt den Zugriff auf eine Site während Verbesserungen, Aktualisierungen und Konfigurationsaufgaben ein oder verhindert ihn. Standardmäßig leitet die Site Besucher auf eine standardmäßige `Service Temporarily Unavailable` -Seite um.

Sie können eine [benutzerdefinierte Wartungsseite](../../upgrade/troubleshooting/maintenance-mode-options.md) erstellen, den Wartungsmodus manuell aktivieren und deaktivieren und den Wartungsmodus konfigurieren, damit Besucher von autorisierten IP-Adressen den Speicher normal anzeigen können. Siehe [Aktivieren und Deaktivieren des Wartungsmodus](../../installation/tutorials/maintenance-mode.md) im _Installationshandbuch_.

Wenn Sie Commerce in der Cloud-Infrastruktur verwenden, wird die Commerce-Anwendung während der Bereitstellungsphase im Wartungsmodus ausgeführt. Nach erfolgreichem Abschluss der Bereitstellung kehrt die Commerce-Anwendung im Produktionsmodus zur Ausführung zurück. Siehe [Bereitstellungs-Hooks](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) im Handbuch _Commerce on Cloud Infrastructure_.

Im Wartungsmodus:

- Site-Besucher werden zu einer standardmäßigen `Service Temporarily Unavailable` Seite umgeleitet.
- Das Verzeichnis &quot;`var/`&quot; enthält die Datei &quot;`.maintenance.flag`&quot;
- Sie können den Besucherzugriff anhand von IP-Adressen einschränken
