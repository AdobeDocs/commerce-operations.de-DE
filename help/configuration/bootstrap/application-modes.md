---
title: Anwendungsmodi
description: Die Commerce-Anwendung kann je nach Bedarf in verschiedenen Modi eingesetzt werden. Zeigen Sie eine detaillierte Liste der verfügbaren Anwendungsmodi an.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Anwendungsmodi

Sie können die Commerce-Anwendung in einem der folgenden _Modi_:

| Modulname | Beschreibung |
| ----------- | ----------- |
| default | Ermöglicht die Bereitstellung der Commerce-Anwendung auf einem einzelnen Server, ohne Einstellungen zu ändern. Der Standardmodus ist jedoch nicht für die Produktion optimiert.<br>Um die Commerce-Anwendung auf mehr als einem Server bereitzustellen oder für die Produktion zu optimieren, wechseln Sie zu einem der anderen Modi.<ul><li>Die Zwischenspeicherung von statischen Ansichtsdateien ist aktiviert.</li><li>Dem Benutzer werden keine Ausnahmen angezeigt. Stattdessen werden Ausnahmen in Protokolldateien geschrieben.</li><li>Blendet benutzerspezifische `X-Magento-*` HTTP-Anfrage- und Antwortheader</li></ul> |
| Entwickler | Dieser Modus ist nur für die Entwicklung vorgesehen:<ul><li>Deaktiviert die Zwischenspeicherung von statischen Ansichtsdateien</li><li>Bietet ausführliche Protokollierung</li><li>Aktiviert [automatische Codekompilierung](../cli/code-compiler.md)</li><li>Aktiviert das erweiterte Debugging</li><li>Zeigt benutzerdefinierte `X-Magento-*` HTTP-Anfrage- und Antwortheader</li><li>Das führt zur langsamsten Leistung</li><li>Zeigt Fehler im Frontend an</li></ul> |
| production | Dieser Modus ist für die Bereitstellung auf einem Produktionssystem vorgesehen:<ul><li>Zeigt keine Ausnahmen für den Benutzer an (Ausnahmen werden nur in Protokolle geschrieben).</li><li>Stellt statische Ansichtsdateien nur aus dem Cache bereit.</li><li>Verhindert die automatische Kompilierung von Code-Dateien. Neue oder aktualisierte Dateien werden nicht in das Dateisystem geschrieben.</li><li>**Sie können keine Cache-Typen in Admin aktivieren oder deaktivieren.** Siehe [Cache aktivieren und deaktivieren](../cli/manage-cache.md#enable-or-disable-cache-types).</li><li>Einige Felder, wie z. B. die Abschnitte Erweiterte Systemkonfiguration und Entwicklerkonfiguration im Admin, sind nicht im Produktionsmodus verfügbar.</li></ul> |
| Wartung | Dieser Modus soll den Zugriff auf eine Site während der Aktualisierung oder Neukonfiguration verhindern:<ul><li>Leitet Site-Besucher auf einen Standard um `Service Temporarily Unavailable` Seite.</li><li>Wenn sich die Site im Wartungsmodus befindet, wird die `var/` enthält `.maintenance.flag` -Datei.</li><li>Sie können den Wartungsmodus so konfigurieren, dass Besuchern von einer festgelegten IP-Adressenliste aus der Zugriff gewährt wird.</li></ul> |

>[!INFO]
>
>[Adobe Commerce auf Cloud-Infrastruktur](https://devdocs.magento.com/cloud/bk-cloud.html) unterstützt nur die Produktions- und Wartungsmodi.

## Standardmodus

Wie der Name schon sagt, funktioniert der Standardmodus wie Commerce, wenn kein anderer Modus angegeben ist. Im Standardmodus können Sie die Commerce-Anwendung auf einem einzelnen Server bereitstellen, ohne Einstellungen zu ändern. Der Standardmodus ist jedoch nicht so für die Produktion optimiert wie der Produktionsmodus.

Um die Commerce-Anwendung auf mehr als einem Server bereitzustellen oder für die Produktion zu optimieren, wechseln Sie zu einem der anderen Modi.

Im Standardmodus:

- Fehler werden in den Dateiberichten auf dem Server protokolliert und einem Benutzer nie angezeigt
- Statische Ansichtsdateien werden zwischengespeichert
- Der Standardmodus ist nicht für eine Produktionsumgebung optimiert, hauptsächlich aufgrund der negativen Leistungsauswirkungen von [statische Dateien](https://glossary.magento.com/static-files) dynamisch generiert statt materialisiert werden. Das heißt, das Erstellen statischer Dateien und das Zwischenspeichern dieser Dateien hat eine größere Auswirkung auf die Leistung als das Erstellen statischer Dateien mit dem Erstellungswerkzeug für statische Dateien.

Siehe [Betriebsmodus festlegen](../cli/set-mode.md).

## Entwicklermodus

Führen Sie die Commerce-Anwendung im Entwicklermodus aus, wenn Sie sie erweitern oder anpassen.

Im Entwicklermodus:

- Statische Ansichtsdateien werden nicht zwischengespeichert. sie in die `pub/static` jedes Mal, wenn sie aufgerufen werden
- Nicht erfasste Ausnahmen werden im Browser angezeigt
- Systemanmeldung `var/report` is verbose
- Ein [Ausnahme](https://glossary.magento.com/exception) wird im Fehler-Handler ausgegeben, anstatt protokolliert zu werden
- Eine Ausnahme wird ausgelöst, wenn eine [event](https://glossary.magento.com/event) Abonnenten können nicht aufgerufen werden

Siehe [Betriebsmodus festlegen](../cli/set-mode.md).

## Produktionsmodus

Führen Sie Commerce im Produktionsmodus aus, wenn es auf einem Produktionsserver bereitgestellt wird. Nach der Optimierung der Serverumgebung, z. B. der Datenbank und des Webservers, sollten Sie die [Bereitstellungswerkzeug für statische Ansichtsdateien](../cli/static-view-file-deployment.md) , um statische Ansichtsdateien in die `pub/static` Verzeichnis.

Dies verbessert die Leistung, indem alle erforderlichen statischen Dateien bei der Bereitstellung bereitgestellt werden, anstatt Commerce zu zwingen, statische Dateien während der Laufzeit dynamisch zu lokalisieren und zu kopieren (materialisieren).

Im Produktionsmodus:

- Statische Ansichtsdateien werden nicht materialisiert und URLs für sie werden spontan zusammengestellt. Statische Ansichtsdateien werden über die [cache](https://glossary.magento.com/cache) nur.
- Fehler werden im Dateisystem protokolliert und dem Benutzer nie angezeigt.
- Sie können Cache-Typen aktivieren und deaktivieren _only_ mithilfe der [Befehlszeile](../cli/manage-cache.md#config-cli-subcommands-cache-en).
- You _cannot_ Aktivieren oder deaktivieren Sie Cache-Typen mit dem Admin.

## Wartungsmodus

Führen Sie die Commerce-Anwendung im Wartungsmodus aus, um Ihre Site offline zu schalten, während Sie Wartungs-, Upgrade- oder Konfigurationsaufgaben ausführen. Im Wartungsmodus leitet die Site Besucher zu einem Standard- `Service Temporarily Unavailable` Seite.

Sie können eine [benutzerspezifische Wartungsseite](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html), aktivieren und deaktivieren Sie den Wartungsmodus manuell und konfigurieren Sie den Wartungsmodus, damit Besucher von autorisierten IP-Adressen den Speicher normal anzeigen können. Siehe [Aktivieren und Deaktivieren des Wartungsmodus](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

Wenn Sie Commerce in der Cloud-Infrastruktur verwenden, wird die Commerce-Anwendung während der Bereitstellungsphase im Wartungsmodus ausgeführt. Nach erfolgreichem Abschluss der Bereitstellung kehrt die Commerce-Anwendung im Produktionsmodus zur Ausführung zurück. Siehe [Bereitstellungshinweise](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) im _Commerce Cloud-Handbuch_.
