---
title: Verhindern und Reagieren auf einen Sicherheitsvorfall
description: Erfahren Sie mehr über Best Practices zur Vermeidung und Reaktion auf Sicherheitsvorfälle in Ihrer Adobe Commerce im Rahmen eines Cloud-Infrastrukturprojekts.
role: Admin, Developer, Leader, User
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Best Practices zur Verhinderung und Reaktion auf einen Sicherheitsvorfall

Die Adobe Commerce-Sicherheit funktioniert unter einer [Freigegebene Verantwortung](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) -Modell. Es ist wichtig zu verstehen, für welche Adobe und welche technischen Teams verantwortlich sind. Unten finden Sie eine Zusammenfassung [Best Practices für die Sicherheit](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) , um sicherzustellen, dass Ihr Projekt über die besten Sicherheitskontrollen verfügt und wie Sie am besten auf einen Sicherheitsvorfall reagieren können.

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur

## Reaktion auf einen Vorfall

Bei der Reaktion auf einen Sicherheitsvorfall gibt es viele Aspekte. Wenn Sie vermuten, dass Sie in letzter Zeit einen Sicherheitsvorfall für Ihr Adobe Commerce-Projekt in der Cloud-Infrastruktur aufgetreten sind, müssen Sie alle Zugriffsrechte für das Administratorkonto prüfen, erweiterte MFA-Steuerelemente (Multi-Factor Authentication) aktivieren, wichtige Protokolle beibehalten und Sicherheitsaktualisierungen für Ihre Adobe Commerce-Version überprüfen.

Weitere Empfehlungen finden Sie unten. Sie können dazu beitragen, nicht autorisierten Zugriff zu verhindern und den Prozess für die weitere Analyse von Vorfällen zu starten.

## Vorbeugen von Sicherheitsvorfällen

Befolgen Sie diese Best Practices für die Sicherheit, um proaktiv Sicherheitsvorfälle zu verhindern, die sich auf Ihre Adobe Commerce-Sites und -Storefronts auswirken:

- [2FA für Administratorzugriff aktivieren](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
Die Authentifizierung mit zwei Faktoren wird häufig verwendet und es kommt häufig vor, Zugriffscodes für verschiedene Websites in derselben App zu generieren. Dadurch wird sichergestellt, dass nur Sie sich bei Ihrem Benutzerkonto anmelden können. Wenn Sie Ihr Passwort verlieren oder ein Bot versucht es zu erraten, fügt die Zwei-Faktor-Authentifizierung eine Schutzschicht hinzu.
- [MFA für SSH-Zugriff aktivieren](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
Wenn die MFA für ein Projekt aktiviert ist, müssen alle Adobe Commerce-Konten in Cloud-Infrastrukturkonten mit SSH-Zugriff einem Authentifizierungs-Workflow folgen, der entweder einen zweifakultativen Authentifizierungscode (2FA) oder ein API-Token und ein SSH-Zertifikat erfordert, um auf die Umgebung zugreifen zu können.
- Aktualisieren Sie auf die neueste Version von Adobe Commerce.
Adobe veröffentlicht Sicherheits- und Funktions-Patches für jede unterstützte Version von Adobe Commerce.
- Einrichtung und Verwendung eines [Nicht standardmäßige Admin-URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe empfiehlt die Verwendung einer eindeutigen, benutzerdefinierten Admin-URL anstelle der standardmäßigen `admin` oder einen gemeinsamen Begriff wie *Backend*. Obwohl diese Konfigurationsänderung Ihre Site nicht direkt vor einem bestimmten fehlerhaften Schauspieler schützt, kann sie die Exposition gegenüber Skripten reduzieren, die versuchen, unberechtigten Zugriff zu erhalten.
- Verhindern Sie die Bearbeitung oder Aktualisierung von Konfigurationswerten im Admin mithilfe der  [`bin/magento config:set` CLI-Befehl mit dem `lock env` Konfigurationsoption](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Diese Option sperrt entweder den Konfigurationswert so, dass er nicht im Admin bearbeitet werden kann, oder verhindert Änderungen an einer bereits gesperrten Einstellung. Wenn Sie diese Option verwenden, werden Konfigurationsänderungen in die `<Commerce base dir>/app/etc/env.php` -Datei.
- Einrichten und Ausführen der [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html).
Mit dem erweiterten Sicherheitsscan können Sie jede Ihrer Adobe Commerce-Sites, einschließlich PWA, auf bekannte Sicherheitsrisiken und Malware überwachen und Patchaktualisierungen und Sicherheitsbenachrichtigungen erhalten.
- [Überprüfen und aktualisieren Sie den Admin-Benutzerzugriff](https://docs.magento.com/user-guide/system/permissions-users-all.html) und [Sicherheitseinstellungen](https://docs.magento.com/user-guide/stores/security-admin.html).
   - Es wird empfohlen, alte, nicht verwendete oder verdächtige Konten zu entfernen und Kennwörter für alle Admin-Benutzer zu drehen.
   - Überprüfen und aktualisieren Sie die erweiterten Sicherheitseinstellungen&lt; für Ihr Projekt. Die Konfiguration der Admin-Sicherheit bietet Ihnen die Möglichkeit, URLs einen geheimen Schlüssel hinzuzufügen, die Groß-/Kleinschreibung von Kennwörtern zu verlangen und die Dauer von Admin-Sitzungen, einschließlich der Lebensdauer von Kennwörtern, sowie die Anzahl der Anmeldeversuche zu begrenzen, die unternommen werden können, bevor das Admin-Benutzerkonto gesperrt wird. Um die Sicherheit zu erhöhen, können Sie die Dauer der Inaktivität der Tastatur konfigurieren, bevor die aktuelle Sitzung abläuft, und verlangen, dass beim Benutzernamen und Kennwort die Groß- und Kleinschreibung beachtet wird.
- Adobe Commerce in prüfen [Cloud-Projektbenutzer](https://devdocs.magento.com/cloud/project/user-admin.html).
Es wird empfohlen, alte, nicht verwendete oder verdächtige Konten zu entfernen und Benutzer aufzufordern, ihre Passwörter zu ändern.
- Prüfung [SSH-Schlüssel](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) für Adobe Commerce in der Cloud-Infrastruktur.
Es wird empfohlen, SSH-Schlüssel zu überprüfen, zu löschen und zu drehen.
- Implementieren Sie ACL (Access Control List) für Admin.
Sie können eine ACL-Liste für schnelle Edge in Kombination mit einer benutzerdefinierten [VCL-Codeausschnitt](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) um eingehende Anfragen zu filtern und den Zugriff nach IP-Adresse dem Administrator zu ermöglichen.

## Ereignis analysieren

Der erste Schritt der Incident-Analyse besteht darin, so viele Fakten wie möglich zu sammeln, so schnell es geht. Die Erfassung von Informationen über den Vorfall kann Ihnen dabei helfen, die potenzielle Ursache des Vorfalls zu ermitteln. Adobe Commerce bietet die folgenden Tools, die Sie bei der Analyse von Vorfällen unterstützen.

- [Admin-Aktionsprotokolle überprüfen](https://docs.magento.com/user-guide/system/action-log-report.html).
Der Bericht &quot;Aktionsprotokolle&quot;zeigt einen detaillierten Datensatz aller Admin-Aktionen an, die für die Protokollierung aktiviert sind. Jeder Datensatz ist mit einem Zeitstempel versehen und registriert die IP-Adresse und den Namen des Benutzers. Die Protokolldetails enthalten Admin-Benutzerdaten und zugehörige Änderungen, die während der Aktion vorgenommen wurden.
- Analysieren Sie Ereignisse mit der [Beobachtung des Adobe Commerce-Tools](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Mit dem Tool &quot;Beobachtung für Adobe Commerce&quot;können Sie komplexe Probleme analysieren, um Ursachen zu identifizieren. Anstatt unterschiedliche Daten zu verfolgen, können Sie Ihre Zeit damit verbringen, Ereignisse und Fehler zu korrelieren, um tiefere Einblicke in die Ursachen von Leistungsengpässen zu erhalten.
Das Tool soll einen klaren Überblick über einige potenzielle Site-Probleme geben, damit Sie die Ursache identifizieren und die Site optimal funktionieren. Klicken Sie auf den Link zur Dokumentation zum Tool &quot;Beobachtung für Adobe Commerce&quot;, um auf die Dokumentation zu diesem Tool zuzugreifen. In der Dokumentation finden Sie einen Abschnitt mit allen Informationen, die Sie auf der **Sicherheit** Registerkarte.
- Analysieren von Protokollen mit [New Relic-Protokolle](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Adobe Commerce on Cloud Infrastructure Pro-Projekte umfassen [New Relic-Protokolle](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) Dienst. Der Dienst ist so vorkonfiguriert, dass alle Protokolldaten aus Ihren Staging- und Produktionsumgebungen aggregiert werden, um sie in einem zentralen Protokollverwaltungs-Dashboard anzuzeigen.
Sie können den New Relic Logs-Dienst verwenden, um die folgenden Aufgaben auszuführen:
   - Verwendung [New Relic-Abfragen](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) , um aggregierte Protokolldaten zu durchsuchen.
   - Visualisieren Sie Protokolldaten über die New Relic Logs-Anwendung.

## Zusätzliche Informationen

- [Root Ursache Analysis Framework](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
