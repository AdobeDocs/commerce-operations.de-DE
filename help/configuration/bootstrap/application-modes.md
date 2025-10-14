---
title: Anwendungsmodi
description: Die Commerce-Anwendung kann je nach Bedarf in verschiedenen Modi ausgeführt werden. Eine detaillierte Liste der verfügbaren Anwendungsmodi anzeigen.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: c415c3427f513255b9d4ebe1d24ba4024df21928
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Anwendungsmodi

Sie können die Commerce-Anwendung in einem der folgenden _ausführen_:

| Modusname | Beschreibung | Cloud-Support |
| ------------------------ | ------------------- | ------------- |
| [Standard](#default-mode) | Bereitstellen und Ausführen der Commerce-Anwendung auf einem einzelnen Server ohne Änderung der Einstellungen. _Nicht_ für die Produktion optimiert. | Nein |
| [developer](#developer-mode) | Ideal für die Entwicklung bei der Erweiterung oder Anpassung des Commerce-Programms. | Nein |
| [Produktion](#production-mode) | Stellen Sie das Commerce-Programm bereit und führen Sie es in einem Produktionssystem aus. | Ja |
| [Wartung](#maintenance-mode) | Verhindern Sie den Zugriff auf eine Site, während Sie Aktualisierungen und Konfigurationen durchführen. | Ja |

Informationen [&#x200B; manuellen Ändern der Adobe Commerce](../cli/set-mode.md)Betriebsmodi finden Sie unter „Festlegen des Betriebsmodus“.

## Cloud-Support

Aufgrund des schreibgeschützten Dateisystems gibt es eine strikte Einschränkung bezüglich des Wechsels der Modi in Remote-Cloud-Umgebungen und es kann nicht durch den Adobe Commerce-Support überschrieben werden. Versuchen Sie nicht, den Modus zu ändern, indem Sie die `app/etc/env.php` ändern, da das `ece-tools` die Datei basierend auf mehreren Konfigurationsquellen überschreibt.

Adobe Commerce in der Cloud-Infrastruktur führt die Anwendung während einer Bereitstellung automatisch _Wartungsmodus_ aus. Dadurch wird Ihre Site offline geschaltet, bis die Bereitstellung abgeschlossen ist. Andernfalls verbleibt die Anwendung im _Produktions_ Modus. Siehe [Bereitstellungsprozess](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=de#deploy-phase) im Handbuch zu _Commerce in Cloud-Infrastrukturen_.

Wenn Sie Cloud Docker für Commerce als Entwicklungs-Tool verwenden, können Sie Ihr Cloud-Infrastrukturprojekt in einer Docker-Umgebung im _Entwicklermodus_ bereitstellen, die Leistung ist jedoch aufgrund zusätzlicher Dateisynchronisierungsvorgänge langsamer. Siehe [Bereitstellen der Docker-Umgebung](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) im Handbuch _Cloud Docker for Commerce_.


## Standardmodus

Der _Standard_-Modus ermöglicht die Bereitstellung der Commerce-Anwendung auf einem einzelnen Server, ohne dass dabei Einstellungen geändert werden müssen. Der Standardmodus ist jedoch aufgrund der negativen Auswirkungen statischer Dateien nicht für die Produktion optimiert. Das Erstellen statischer Dateien und das Zwischenspeichern dieser Dateien wirkt sich stärker auf die Leistung aus als das Generieren mit dem Tool zur Erstellung statischer Dateien.

Im Standardmodus:

- Ausnahmen werden in Protokolldateien geschrieben statt angezeigt
- Statische Ansichtsdateien werden zwischengespeichert
- Blendet benutzerdefinierte `X-Magento-*`-HTTP-Anfrage- und -Antwort-Header aus

Commerce wird im Standardmodus ausgeführt, wenn kein anderer Modus angegeben ist.

## Entwicklermodus

Der _Entwicklermodus_ wird zum Erweitern und Anpassen des Commerce-Programms empfohlen. Statische Ansichtsdateien werden nicht zwischengespeichert, sondern bei Bedarf in das `pub/static`-Verzeichnis geschrieben.

Im Entwicklermodus:

- Aktiviert [automatische Code-Kompilierung](../cli/code-compiler.md) und verbessertes Debugging
- Nicht erfasste Ausnahmen werden im Browser angezeigt
- Die Systemprotokollierung in `var/report` ist ausführlich
- Eine Ausnahme wird im Fehler-Handler ausgelöst, anstatt protokolliert zu werden
- Es wird eine Ausnahme ausgelöst, wenn ein Ereignis-Abonnent nicht aufgerufen werden kann
- Zeigt benutzerdefinierte `X-Magento-*` HTTP-Anfrage- und Antwort-Header an

>[!NOTE]
>
>Dieser Modus wird in der Adobe Commerce-Cloud-Umgebung nicht unterstützt und der Adobe Commerce-Support kann das Ändern des Anwendungsmodus nicht vereinfachen.

## Produktionsmodus

Der _Produktionsmodus_ eignet sich am besten für die Bereitstellung der Commerce-Anwendung auf einem Produktionssystem. Nach der Optimierung der Serverumgebung, z. B. der Datenbank und des Webservers, sollten Sie das Bereitstellungs-Tool für [statische Ansichtsdateien](../cli/static-view-file-deployment.md) ausführen, um statische Ansichtsdateien in das `pub/static`-Verzeichnis zu schreiben. Dies verbessert die Leistung, indem alle erforderlichen statischen Dateien bei der Bereitstellung bereitgestellt werden, anstatt das Commerce-Programm zu zwingen, statische Dateien bei Bedarf während der Laufzeit dynamisch zu suchen und zu kopieren (materialisieren).

Einige Felder, wie die Systemkonfigurationsabschnitte „Erweitert“ und „Entwickler“ in „Admin“, sind im Produktionsmodus nicht verfügbar. Beispielsweise können Sie _Cache-Typen_ der Admin-Klasse nicht aktivieren oder deaktivieren. Sie können Cache-Typen (nur _)_ der [Befehlszeile) aktivieren &#x200B;](../cli/manage-cache.md#config-cli-subcommands-cache-en) deaktivieren.

Im Produktionsmodus:

- Statische Ansichtsdateien werden nur aus dem Cache bereitgestellt
- Fehler und Ausnahmen werden im Dateisystem protokolliert und dem Benutzer nie angezeigt
- Einige Konfigurationsfelder im Administrator-Ordner sind nicht verfügbar

## Wartungsmodus

Der _Wartungsmodus_ beschränkt oder verhindert den Zugriff auf eine Site während Verbesserungen, Aktualisierungen und Konfigurationsaufgaben. Standardmäßig leitet die Site Besucher zu einer standardmäßigen `Service Temporarily Unavailable` um.

Sie können eine [benutzerdefinierte Wartungsseite](../../upgrade/troubleshooting/maintenance-mode-options.md) erstellen, den Wartungsmodus manuell aktivieren und deaktivieren und den Wartungsmodus so konfigurieren, dass Besucher von autorisierten IP-Adressen den Store normal anzeigen können. Siehe [Aktivieren und Deaktivieren des &#x200B;](../../installation/tutorials/maintenance-mode.md) im _Installationshandbuch_.

Wenn Sie Commerce in der Cloud-Infrastruktur verwenden, wird die Commerce-Anwendung während der Bereitstellungsphase im Wartungsmodus ausgeführt. Wenn die Bereitstellung erfolgreich abgeschlossen wurde, kehrt die Commerce-Anwendung zur Ausführung im Produktionsmodus zurück. Siehe [Bereitstellungs-Hooks](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html?lang=de#phase-5%3A-deployment-hooks) im Handbuch zu _Commerce in Cloud-Infrastrukturen_.

Im Wartungsmodus:

- Site-Besuchende werden zu einer standardmäßigen `Service Temporarily Unavailable` umgeleitet
- Das `var/` enthält die `.maintenance.flag`
- Sie können den Besucherzugriff je nach IP-Adressen einschränken
