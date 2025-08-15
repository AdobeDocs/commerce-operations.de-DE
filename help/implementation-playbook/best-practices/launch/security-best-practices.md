---
title: Sichern der Commerce-Site und -Infrastruktur
description: Aufrechterhaltung der Sicherheit durch Implementierung von Best Practices für die Sicherheit beim Einrichten, Konfigurieren und Aktualisieren von Adobe Commerce-Installationen.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# Sichern der Commerce-Site und -Infrastruktur

Das Einrichten und Verwalten einer sicheren Umgebung für Adobe Commerce-Projekte, die in der Cloud-Infrastruktur bereitgestellt werden, ist eine gemeinsame Aufgabe von Adobe Commerce-Kunden, Lösungspartnern und Adobe. Ziel dieses Handbuchs ist es, Best Practices für die Kundenseite der Gleichung bereitzustellen.

Obwohl Sie nicht alle Sicherheitsrisiken ausschließen können, wird durch die Anwendung dieser Best Practices der Sicherheitszustand von Commerce-Installationen beeinträchtigt. Eine sichere Website und Infrastruktur macht das Ziel für bösartige Angriffe weniger attraktiv, gewährleistet die Sicherheit der Lösung und der vertraulichen Informationen der Kunden und trägt dazu bei, sicherheitsbezogene Vorfälle zu minimieren, die zu Site-Unterbrechungen und kostspieligen Ermittlungen führen können.

>[!NOTE]
>
>Informationen zu den Rollen und Zuständigkeiten für die Sicherung und Wartung von Adobe Commerce-Projekten in Cloud[Infrastrukturen finden Sie unter „Modell der gemeinsamen ](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart)&quot; im _Handbuch für Adobe Commerce-Sicherheit und -Compliance_.

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Vorrangige Empfehlungen

Adobe betrachtet die folgenden Empfehlungen für alle Kunden als besonders wichtig. Implementieren Sie diese wichtigen Best Practices für die Sicherheit in allen Commerce-Bereitstellungen:

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Aktivieren Sie die Zwei-Faktor-Authentifizierung für Ihren Administrator und alle SSH-Verbindungen**

- [Sicherheit für Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html)

- [Sichere SSH-Verbindungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html) (Cloud-Infrastruktur)

Wenn MFA für ein Projekt aktiviert ist, müssen alle Adobe Commerce in Cloud-Infrastrukturkonten mit SSH-Zugriff einem Authentifizierungs-Workflow folgen. Dieser Workflow erfordert für den Zugriff auf die Umgebung entweder einen Zwei-Faktor-Authentifizierungs-Code (2FA) oder ein API-Token und ein SSH-Zertifikat.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Sichern Sie den Administrator**

- [Konfigurieren Sie eine nicht standardmäßige Admin](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url)URL, anstatt den `admin` oder einen allgemeinen Begriff wie `backend` zu verwenden. Diese Konfiguration reduziert das Risiko von Skripten, die versuchen, nicht autorisierten Zugriff auf Ihre Site zu erhalten.

- [Erweiterte Sicherheitseinstellungen konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html) - Fügen Sie URLs einen geheimen Schlüssel hinzu, verlangen Sie, dass bei Kennwörtern die Groß-/Kleinschreibung beachtet wird, und beschränken Sie die Länge der Admin-Sitzung, das Kennwortlebensdauerintervall und die Anzahl der zulässigen Anmeldeversuche, bevor Sie ein Admin-Benutzerkonto sperren. Um die Sicherheit zu erhöhen, konfigurieren Sie die Dauer der Tastaturinaktivität, bevor die aktuelle Sitzung abläuft, und verlangen Sie, dass bei Benutzername und Kennwort die Groß-/Kleinschreibung beachtet wird.

- [Aktivieren Sie ReCAPTCHA](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html), um den Administrator vor automatischen Brute-Force-Angriffen zu schützen.

- Befolgen Sie das Prinzip der geringsten Berechtigung bei der Zuweisung [Administratorberechtigungen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html) zu Rollen und Rollen zu Admin-Benutzerkonten.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Upgrade auf die neueste Version von Adobe Commerce**

Halten Sie Ihren Code auf dem neuesten Stand[ indem Sie Ihr Commerce-Projekt auf die neueste Version ](#upgrade-to-the-latest-release) Adobe Commerce, Commerce Services und Erweiterungen aktualisieren, einschließlich Sicherheits-Patches, Hotfixes und anderer von Adobe bereitgestellter Patches.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Sicherheitsrelevante Konfigurationswerte**

Verwenden Sie [Konfigurationsverwaltung](../../../configuration/cli/set-configuration-values.md), um kritische Konfigurationswerte zu sperren.

Die `lock config`- und `lock env` CLI-Befehle konfigurieren Umgebungsvariablen, um zu verhindern, dass diese vom Administrator aktualisiert werden. Der Befehl schreibt den Wert in die `<Commerce base dir>/app/etc/env.php`. (Informationen zu Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Store-Konfigurationsverwaltung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html#sensitive-data).)

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Sicherheitsüberprüfungen durchführen**

Verwenden Sie den [Commerce Security Scan Service](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), um alle Adobe Commerce-Websites auf bekannte Sicherheitsrisiken und Malware zu überwachen und sich für den Erhalt von Patch-Updates und Sicherheitsbenachrichtigungen anzumelden.

## Gewährleistung der Sicherheit von Erweiterungen und benutzerdefiniertem Code

Wenn Sie Adobe Commerce erweitern, indem Sie Erweiterungen von Drittanbietern aus dem Adobe Commerce Marketplace hinzufügen, oder benutzerdefinierten Code hinzufügen, stellen Sie die Sicherheit dieser Anpassungen sicher, indem Sie die folgenden Best Practices anwenden:

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Wählen Sie einen Partner oder Lösungsintegrator (SI) aus, der sich gut mit Sicherheit auskennt** - Stellen Sie sichere Integrationen und die sichere Bereitstellung von benutzerdefiniertem Code sicher, indem Sie Organisationen auswählen, die sichere Entwicklungspraktiken befolgen und nachweislich Sicherheitsprobleme verhindern und beheben.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Sichere Erweiterungen verwenden** - Ermitteln Sie die am besten geeigneten und sichersten Erweiterungen für Commerce-Bereitstellungen, indem Sie sich mit Ihrem Lösungsintegrator oder -entwickler in Verbindung setzen und die Best Practices für [Adobe Extensions befolgen](../planning/extensions.md).

- Nur Quellerweiterungen vom Adobe Commerce Marketplace oder über den Lösungsintegrator. Wenn die Erweiterung von einem Integrator bezogen wird, stellen Sie sicher, dass das Eigentum an der Erweiterungslizenz übertragbar ist, falls der Integrator wechselt.

- Verringerung des Risikos durch Begrenzung der Anzahl von Erweiterungen und Anbietern.

- Überprüfen Sie nach Möglichkeit den Erweiterungs-Code auf Sicherheit, bevor Sie ihn mit dem Commerce-Programm integrieren.

- Stellen Sie sicher, dass die Entwickler von PHP-Erweiterungen die Entwicklungsrichtlinien, Prozesse und Best Practices für die Sicherheit von Adobe Commerce befolgen. Insbesondere müssen Entwickler die Verwendung von PHP-Funktionen vermeiden, die zu entfernter Code-Ausführung oder schwacher Kryptografie führen können. Siehe [Sicherheit](https://developer.adobe.com/commerce/php/best-practices/security/) im *Best Practices für die Entwicklung von Erweiterungen*.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Prüfcode** - Überprüfen Sie Ihr Server- und Quell-Code-Repository auf Entwicklungsreste. Stellen Sie sicher, dass es keine zugänglichen Protokolldateien, öffentlich sichtbaren Git-Verzeichnisse, Tunnel zum Ausführen von SQL-Anweisungen, Datenbank-Dumps, PHP-Info-Dateien oder andere ungeschützte Dateien gibt, die nicht erforderlich sind und bei einem Angriff verwendet werden könnten.

## Aktualisieren auf die neueste Version

Adobe veröffentlicht kontinuierlich aktualisierte Lösungskomponenten, um die Sicherheit zu verbessern und Kunden besser vor möglichen Gefahren zu schützen. Die Aktualisierung auf die neueste Version der Adobe Commerce-Anwendung, installierte Services und Erweiterungen und die Anwendung aktueller Patches ist die erste und beste Verteidigungslinie gegen Sicherheitsbedrohungen.

Commerce veröffentlicht in der Regel vierteljährlich Sicherheits-Updates, behält sich jedoch das Recht vor, Hotfixes für wichtige Sicherheitsbedrohungen basierend auf Prioritätsfaktoren und anderen Faktoren zu veröffentlichen.

In den folgenden Ressourcen finden Sie Informationen zu verfügbaren Adobe Commerce-Versionen, Versionszyklen sowie zum Upgrade- und Patch-Prozess:

- [Veröffentlichte Versionen](../../../release/versions.md)
- [Produktverfügbarkeit](../../../release/product-availability.md) (Adobe Commerce-Services und von Adobe erstellte Erweiterungen)
- [Adobe Commerce-Lebenszyklusrichtlinie](../../../release/lifecycle-policy.md)
- [Aktualisierungshandbuch](../../../upgrade/overview.md)
- [Anwenden von Patches](../../../upgrade/patches/overview.md)

>[!TIP]
>
>Abonnieren Sie den [Adobe Security Notification Service](https://www.adobe.com/subscription/adbeSecurityNotifications.html), um die neuesten Sicherheitsinformationen zu erhalten und bekannte Sicherheitsprobleme zu beheben.

## Entwickeln eines Plans für die Notfallwiederherstellung

Wenn Ihr Commerce-Standort gefährdet ist, können Sie Schäden kontrollieren und den normalen Geschäftsbetrieb schnell wiederherstellen, indem Sie einen umfassenden Disaster Recovery-Plan entwickeln und implementieren.

Wenn ein Kunde aufgrund eines Systemausfalls die Wiederherstellung einer Commerce-Instanz benötigt, kann Adobe dem Kunden Sicherungsdateien bereitstellen. Der Kunde und ggf. der Lösungsintegrator können die Wiederherstellung durchführen.

Als Teil eines Disaster Recovery-Plans empfiehlt Adobe Kunden dringend, [ihre Adobe Commerce-Anwendungskonfiguration zu exportieren](../../../configuration/cli/export-configuration.md) um die erneute Bereitstellung zu erleichtern, wenn sie für Business Continuity-Zwecke erforderlich ist. Der Hauptgrund für den Export der Konfiguration in das Dateisystem besteht darin, dass die Systemkonfiguration Vorrang vor der Datenbankkonfiguration hat. In einem schreibgeschützten Dateisystem muss die Anwendung erneut bereitgestellt werden, um vertrauliche Konfigurationseinstellungen zu ändern und so eine zusätzliche Schutzschicht zu bieten.

### Weitere Informationen

**In der Cloud-Infrastruktur bereitgestellte Adobe Commerce**

- [Sicherung und Notfallwiederherstellung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)

- [Store-Konfigurationsverwaltung für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)

**Adobe Commerce lokal bereitgestellt**

- [Konfigurationseinstellungen exportieren](../../../configuration/cli/export-configuration.md)

   - [Konfigurationseinstellungen importieren](../../../configuration/cli/import-configuration.md)

   - [Sichern und Rollback von Dateisystem, Medien und Datenbank](../../../installation/tutorials/backup.md)

## Pflege einer sicheren Website und Infrastruktur

In diesem Abschnitt werden Best Practices für die Gewährleistung der Site- und Infrastruktursicherheit für eine Adobe Commerce-Installation zusammengefasst. Viele dieser Best Practices konzentrieren sich auf die Sicherung der Computerinfrastruktur im Allgemeinen, sodass einige der Empfehlungen möglicherweise bereits implementiert sind.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Blockieren des nicht autorisierten Zugriffs** - Richten Sie gemeinsam mit Ihrem Hosting-Partner einen VPN-Tunnel ein, um den nicht autorisierten Zugriff auf die Commerce-Site und die Kundendaten zu blockieren. Richten Sie einen SSH-Tunnel ein, um nicht autorisierten Zugriff auf die Commerce-Anwendung zu blockieren.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Web Application Firewall verwenden** - Analysieren Sie den Traffic und entdecken Sie verdächtige Muster, z. B. Kreditkarteninformationen, die mithilfe einer Web Application Firewall an eine unbekannte IP-Adresse gesendet werden.

Adobe Commerce-Installationen, die auf der Cloud-Infrastruktur bereitgestellt werden, können integrierte WAF-Services nutzen, die mit der [Fastly Services-Integration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Erweiterte Kennwortsicherheitseinstellungen konfigurieren** - Richten Sie sichere Kennwörter ein und ändern Sie diese mindestens alle 90 Tage, wie vom PCI-Datensicherheitsstandard in Abschnitt 8.2.4 empfohlen. Siehe [Konfigurieren von Admin-Sicherheitseinstellungen](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html).

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **HTTPS verwenden** - Wenn die Commerce-Site neu implementiert ist, starten Sie die gesamte Site mit HTTPS. Google verwendet nicht nur HTTPS als Ranking-Faktor, sondern viele Benutzende erwägen sogar, von einer Site zu kaufen, es sei denn, sie ist mit HTTPS gesichert.

## Schutz vor Malware

Malware-Angriffe auf E-Commerce-Websites sind nur allzu verbreitet, und Bedrohungsakteure entwickeln ständig neue Möglichkeiten, Kreditkarten- und personenbezogene Daten aus Transaktionen zu sammeln.

Adobe hat jedoch festgestellt, dass die meisten Site-Kompromisse nicht auf einen innovativen Hacker zurückzuführen sind. Stattdessen nutzen Bedrohungsakteure häufig bestehende, ungepatchte Sicherheitslücken, fehlerhafte Passwörter sowie schwache Eigentums- und Berechtigungseinstellungen im Dateisystem.

Bei den häufigsten Angriffen wird bösartiger Code in die absolute Kopf- oder Fußzeile eines Kundengeschäfts eingefügt. Dort erfasst der Code Formulardaten, die ein Kunde in die Storefront eingibt, einschließlich Kunden-Anmeldedaten und Checkout-Formulardaten. Diese Daten werden dann zu böswilligen Zwecken an einen anderen Speicherort und nicht an das Commerce-Backend gesendet. Außerdem kann Malware den Admin dazu bringen, Code auszuführen, der das ursprüngliche Zahlungsformular durch ein gefälschtes Formular ersetzt, das alle vom Zahlungsanbieter festgelegten Schutzmechanismen überschreibt.

Client-seitige Kreditkartenabtaster sind eine Art von Malware, die Code in Inhalte von Händlerwebseiten einbettet, die im Browser eines Benutzers ausgeführt werden können, wie in der folgenden Abbildung dargestellt.

![Datenfluss für Malware-Angriffe auf E-Commerce-Sites](../../../assets/playbooks/malware-data-flow.svg)

Nach dem Eintreten bestimmter Aktionen, z. B. wenn ein Benutzer ein Formular sendet oder einen Feldwert ändert, serialisiert der Skimmer die Daten und sendet sie an Drittanbieter-Endpunkte. Bei diesen Endpunkten handelt es sich normalerweise um andere kompromittierte Websites, die als Relais dienen, um die Daten an das endgültige Ziel zu senden.


>[!TIP]
>
>Wenn eine Commerce-Site von einem Malware-Angriff betroffen ist, befolgen Sie die Best Practices von Adobe Commerce für [Reaktion auf einen Sicherheitsvorfall](../maintenance/respond-to-security-incident.md).

### Die häufigsten Angriffe kennen

Nachfolgend finden Sie eine Liste mit häufigen Angriffskategorien, die Adobe allen Commerce-Kunden empfiehlt, sich bewusst zu sein und Maßnahmen zum Schutz vor folgenden Angriffen zu ergreifen:

- **Site-**: Ein Angreifer beschädigt eine Website, indem er das visuelle Erscheinungsbild der Website ändert oder eigene Nachrichten hinzufügt. Obwohl der Zugriff auf die Website und Benutzerkonten gefährdet wurde, bleiben Zahlungsinformationen oft sicher.

- **BotNet**: Der Commerce-Server des Kunden wird Teil eines Bot-Netzwerks, das Spam-E-Mails sendet. Obwohl die Benutzerdaten in der Regel nicht kompromittiert sind, kann der Domain-Name des Kunden durch Spam-Filter auf die Blockierungsliste gesetzt werden, wodurch der Versand von E-Mails aus der Domain verhindert wird. Alternativ wird die Website des Kunden Teil eines Bot-Netzes, was einen Distributed Denial of Service (DDoS)-Angriff auf eine andere(n) Website(s) verursacht. Das Bot-Netz blockiert möglicherweise den eingehenden IP-Traffic an den Commerce-Server und verhindert so, dass Kunden einkaufen können.

- **Direkte Serverangriffe** - Daten sind gefährdet, Backdoors und Malware werden installiert und der Standortbetrieb wird beeinträchtigt. Zahlungsinformationen, die nicht auf dem Server gespeichert sind, werden durch diese Angriffe mit geringerer Wahrscheinlichkeit gefährdet.

- **Stille Kartenerfassung** - Bei diesem verheerendsten Angriff installieren Eindringlinge versteckte Malware oder Kartenerfassungssoftware oder, schlimmer noch, ändern den Checkout-Prozess, um Kreditkartendaten zu erfassen. Anschließend werden die Daten an eine andere Website gesendet, die über das Dark Web zum Verkauf angeboten wird. Solche Angriffe bleiben über einen längeren Zeitraum unbemerkt und können zu erheblichen Beeinträchtigungen von Kundenkonten und Finanzinformationen führen.

- **Stille Schlüsselerfassung**: Der Bedrohungsakteur installiert Schlüsselerfassungscode auf dem Kundenserver, um Administratorberechtigungen zu erfassen, damit er sich anmelden und andere Angriffe ausführen kann, ohne entdeckt zu werden.

### Schützen vor Angriffen durch das Erraten von Passwörtern

Das Erraten von Brute-Force-Passwörtern kann zu unbefugtem Administratorzugriff führen. Schützen Sie Ihre Site vor diesen Angriffen, indem Sie die folgenden Best Practices befolgen:

- Identifizieren und schützen Sie alle Stellen, an denen die Commerce-Installation von außen zugänglich ist.

  Sie können den Zugriff auf den Administrator, der im Allgemeinen den höchsten Schutz benötigt, sicherstellen, indem Sie bei der Konfiguration Ihres Commerce[Projekts die Prioritätsempfehlungen](#priority-recommendations) von Adobe befolgen.

- Steuern Sie den Zugriff auf die Commerce-Site, indem Sie eine Zugriffssteuerungsliste einrichten, die nur den Zugriff für Benutzer von einer bestimmten IP-Adresse oder einem bestimmten Netzwerk ermöglicht.

  Sie können eine Fastly Edge ACL mit einem benutzerdefinierten VCL-Code-Fragment verwenden, um eingehende Anfragen zu filtern und den Zugriff nach IP-Adresse zuzulassen. Siehe [Benutzerdefinierte VCL zum Zulassen von Anfragen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).


  >[!TIP]
  >
  >Wenn Sie Remote-Mitarbeiter beschäftigen, stellen Sie sicher, dass die IP-Adressen der Remote-Mitarbeiter in der Liste der Adressen mit Zugriffsberechtigung auf die Commerce-Site enthalten sind.

### Verhindern von Clickjacking-Angriffen

Adobe schützt Ihren Store vor Clickjacking-Angriffen, indem es die `X-Frame-Options` HTTP-Anfrage-Kopfzeile bereitstellt, die Sie in Anfragen an Ihre Storefront einbeziehen können. Siehe [Verhindern von Clickjacking](../../../configuration/security/xframe-options.md) im *Adobe Commerce-Konfigurationshandbuch*.
