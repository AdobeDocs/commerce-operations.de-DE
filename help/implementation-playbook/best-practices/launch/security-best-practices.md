---
title: Sichern der Commerce-Site und -Infrastruktur
description: Erhalten Sie die Sicherheit, indem Sie Best Practices für die Sicherheit beim Einrichten, Konfigurieren und Aktualisieren von Adobe Commerce-Installationen implementieren.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '2004'
ht-degree: 0%

---

# Sichern der Commerce-Site und -Infrastruktur

Die Einrichtung und Pflege einer sicheren Umgebung für Adobe Commerce-Projekte, die in der Cloud-Infrastruktur bereitgestellt werden, ist eine Verantwortung, die von Adobe Commerce-Kunden, Lösungspartnern und Adobe gemeinsam getragen wird. In diesem Handbuch werden Best Practices für die Kundenseite der Gleichung vorgestellt.

Obwohl Sie nicht alle Sicherheitsrisiken beseitigen können, wird durch die Anwendung dieser Best Practices die Sicherheit von Commerce-Installationen beeinträchtigt. Eine sichere Site und Infrastruktur machen eine weniger attraktive Zielgruppe für böswillige Angriffe aus, gewährleisten die Sicherheit der Lösung und der sensiblen Informationen der Kunden und tragen dazu bei, sicherheitsrelevante Vorfälle zu minimieren, die Site-Störungen und kostspielige Untersuchungen verursachen können.

>[!NOTE]
>
>Informationen zu den Rollen und Verantwortlichkeiten für die Sicherung und Wartung von Adobe Commerce-Projekten in Cloud-Infrastrukturen finden Sie im [Handbuch zur gemeinsamen Verantwortung](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) im Adobe Trust Center.

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Prioritäten

Adobe betrachtet die folgenden Empfehlungen als für alle Kunden von höchster Priorität. Implementieren Sie diese wichtigen Best Practices für die Sicherheit in alle Commerce-Implementierungen:

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Zwei-Faktor-Authentifizierung für Ihren Administrator und alle SSH-Verbindungen aktivieren**

- [Sicherheit für Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html)

- [Sichere SSH-Verbindungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html) (Cloud-Infrastruktur)

Wenn die MFA für ein Projekt aktiviert ist, müssen alle Adobe Commerce-Konten in Cloud-Infrastrukturkonten mit SSH-Zugriff einem Authentifizierungs-Workflow folgen. Für diesen Workflow ist entweder ein zweifaktorieller Authentifizierungscode (2FA) oder ein API-Token und SSH-Zertifikat erforderlich, um auf die Umgebung zugreifen zu können.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Sichern des Administrators**

- [Nicht standardmäßige Admin-URL konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) anstatt die Standardeinstellung zu verwenden `admin` oder einen gemeinsamen Begriff wie `backend`. Diese Konfiguration reduziert die Exposition gegenüber Skripten, die versuchen, einen nicht autorisierten Zugriff auf Ihre Site zu erhalten.

- [Erweiterte Sicherheitseinstellungen konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html)- Fügen Sie URLs einen geheimen Schlüssel hinzu, erfordern Sie, dass bei Passwörtern die Groß-/Kleinschreibung beachtet wird, und beschränken Sie die Sitzungslänge des Administrators, das Passwortzeitintervall und die Anzahl der zulässigen Anmeldeversuche, bevor Sie ein Admin-Benutzerkonto sperren. Um die Sicherheit zu erhöhen, konfigurieren Sie die Dauer der Inaktivität der Tastatur, bevor die aktuelle Sitzung abläuft, und verlangen, dass beim Benutzernamen und Kennwort die Groß- und Kleinschreibung beachtet wird.

- [ReCAPTCHA aktivieren](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html) , um den Administrator vor automatisierten Brute-Force-Angriffen zu schützen.

- Beachten Sie beim Zuweisen das Prinzip der geringsten Berechtigung [Administratorberechtigungen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html) Rollen und Rollen für Admin-Benutzerkonten.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Aktualisierung auf die neueste Version von Adobe Commerce**

Halten Sie den Code aktualisiert von [Aktualisieren Ihres Commerce-Projekts auf die neueste Version](#upgrade-to-the-latest-release) von Adobe Commerce, Commerce Services und Erweiterungen, einschließlich Sicherheits-Patches, Hotfixes und anderen Patches, die von Adobe bereitgestellt werden.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Sichere vertrauliche Konfigurationswerte**

Verwendung [Konfigurationsverwaltung](../../../configuration/cli/set-configuration-values.md) , um kritische Konfigurationswerte zu sperren.

Die `lock config` und `lock env` CLI-Befehle konfigurieren Umgebungsvariablen, um zu verhindern, dass sie vom Administrator aktualisiert werden. Der Befehl schreibt den Wert in die `<Commerce base dir>/app/etc/env.php` -Datei. (Informationen zu Commerce zu Cloud-Infrastrukturprojekten finden Sie unter [Speicherkonfigurationsverwaltung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html#sensitive-data).

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Ausführen von Sicherheitsscans**

Verwenden Sie die [Commerce Security Scan-Dienst](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) um alle Adobe Commerce-Sites auf bekannte Sicherheitsrisiken und Malware zu überwachen und sich für Patch-Updates und Sicherheitsbenachrichtigungen anzumelden.

## Sicherstellen von Erweiterungen und benutzerdefiniertem Code

Wenn Sie Adobe Commerce erweitern, indem Sie Erweiterungen von Drittanbietern aus dem Adobe Commerce Marketplace hinzufügen oder benutzerdefinierten Code hinzufügen, stellen Sie die Sicherheit dieser Anpassungen sicher, indem Sie die folgenden Best Practices anwenden:

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Wählen Sie einen Partner oder einen Lösungs-Integrator (SI), der sich gut mit Sicherheit auskennt.**—Sichere Integrationen und sichere Bereitstellung von benutzerdefiniertem Code durch Auswahl von Organisationen, die sichere Entwicklungspraktiken anwenden und über eine solide Übersicht über die Vermeidung und Behebung von Sicherheitsproblemen verfügen.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Verwenden sicherer Erweiterungen**—Identifizieren Sie die geeignetsten und sichersten Erweiterungen für Commerce-Implementierungen, indem Sie sich mit Ihrem Lösungsintegrator oder -entwickler in Verbindung setzen und folgende Schritte ausführen [Best Practices für Adobe-Erweiterungen](../planning/extensions.md).

- Nur Quellerweiterungen vom Adobe Commerce Marketplace oder über den Lösungsintegrator. Wenn die Erweiterung über einen Integrator abgerufen wird, stellen Sie sicher, dass das Eigentum an der Erweiterungslizenz übertragbar ist, falls sich der Integrator ändert.

- Reduzierung der Risikoexposition durch Begrenzung der Anzahl von Erweiterungen und Anbietern.

- Überprüfen Sie nach Möglichkeit den Erweiterungscode auf Sicherheitsaspekte, bevor Sie mit der Commerce-Anwendung integrieren.

- Stellen Sie sicher, dass die Entwickler von PHP-Erweiterungen die Adobe Commerce-Entwicklungsrichtlinien, -Prozesse und -Best Practices für die Sicherheit befolgen. Insbesondere müssen Entwickler die Verwendung von PHP-Funktionen vermeiden, die zur Ausführung von Remote-Code oder zu schwacher Kryptographie führen können. Siehe [Sicherheit](https://developer.adobe.com/commerce/php/best-practices/security/) im *Handbuch mit Best Practices für Entwickler von Erweiterungen*.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Audit-Code**—Überprüfen Sie Ihren Server und das Quellcode-Repository auf Entwicklungsübrige. Stellen Sie sicher, dass es keine zugänglichen Protokolldateien, öffentlich sichtbaren Git-Verzeichnisse, Tunnel zum Ausführen von SQL-Anweisungen, Datenbank-Dumps, PHP-Info-Dateien oder anderen nicht geschützten Dateien gibt, die nicht erforderlich sind und bei einem Angriff verwendet werden könnten.

## Aktualisierung auf die neueste Version

Adobe veröffentlicht laufend aktualisierte Lösungskomponenten, um die Sicherheit zu verbessern und Kunden besser vor möglichen Kompromissen zu schützen. Die Aktualisierung auf die neueste Version der Adobe Commerce-Anwendung, installierte Dienste und Erweiterungen und die Anwendung aktueller Patches sind die erste und beste Verteidigungslinie gegen Sicherheitsbedrohungen.

Commerce veröffentlicht in der Regel vierteljährlich Sicherheitsupdates, behält sich jedoch das Recht vor, Hotfixes für größere Sicherheitsbedrohungen zu veröffentlichen, die auf Prioritäts- und anderen Faktoren basieren.

In den folgenden Ressourcen finden Sie Informationen zu verfügbaren Adobe Commerce-Versionen, Versionszyklen sowie zum Upgrade- und Patch-Prozess:

- [Veröffentlichte Versionen](../../../release/versions.md)
- [Produktverfügbarkeit](../../../release/product-availability.md) (Adobe Commerce-Dienste und von Adobe erstellte Erweiterungen)
- [Adobe Commerce-Lebenszyklusrichtlinie](../../../release/lifecycle-policy.md)
- [Aktualisierungshandbuch](../../../upgrade/overview.md)
- [Anwenden von Patches](../../../upgrade/patches/overview.md)

>[!TIP]
>
>Abrufen der neuesten Sicherheitsinformationen und Abmildern von bekannten Sicherheitsproblemen durch Abonnieren von [Adobe Security Notification Service](https://www.adobe.com/subscription/adbeSecurityNotifications.html).

## Entwicklung eines Notfallwiederherstellungsplans

Wenn Ihr Commerce-Standort gefährdet ist, können Sie durch die Entwicklung und Implementierung eines umfassenden Notfallwiederherstellungsplans Schäden vermeiden und den normalen Geschäftsbetrieb schnell wiederherstellen.

Wenn ein Kunde aufgrund einer Katastrophe die Wiederherstellung einer Commerce-Instanz benötigt, kann Adobe dem Kunden Sicherungsdateien bereitstellen. Der Kunde und gegebenenfalls der Lösungsintegrator können die Wiederherstellung durchführen.

Im Rahmen eines Notfallwiederherstellungsplans empfiehlt Adobe dringend, dass die Kunden [Exportieren der Adobe Commerce-Anwendungskonfiguration](../../../configuration/cli/export-configuration.md) , um die Umverteilung zu erleichtern, wenn dies für die Kontinuität des Geschäftsbetriebs erforderlich ist. Der Hauptgrund für den Export der Konfiguration in das Dateisystem besteht darin, dass die Systemkonfiguration Vorrang vor der Datenbankkonfiguration hat. In einem schreibgeschützten Dateisystem muss die Anwendung neu bereitgestellt werden, um sensible Konfigurationseinstellungen zu ändern und so eine zusätzliche Schutzschicht zu bieten.

### Zusätzliche Informationen

**Adobe Commerce wird in der Cloud-Infrastruktur bereitgestellt**

- [Sicherung und Wiederherstellung nach Katastrophen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)

- [Speicherkonfigurationsverwaltung für Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)

**Adobe Commerce vor Ort eingesetzt**

- [Ideen zur Notfallwiederherstellung](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [Sicherung und Wiederherstellung](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [Konfigurationseinstellungen exportieren](../../../configuration/cli/export-configuration.md)

   - [Konfigurationseinstellungen importieren](../../../configuration/cli/import-configuration.md)

   - [Backup und Rollback des Dateisystems, der Medien und der Datenbank](../../../installation/tutorials/backup.md)

## Sichere Website und Infrastruktur verwalten

In diesem Abschnitt werden Best Practices für die Wartung der Site- und Infrastruktursicherheit einer Adobe Commerce-Installation zusammengefasst. Viele dieser Best Practices konzentrieren sich auf den allgemeinen Schutz der Computerinfrastruktur, sodass einige Empfehlungen bereits umgesetzt werden.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Nicht autorisierten Zugriff sperren**—Arbeiten Sie mit Ihrem Hosting-Partner zusammen, um einen VPN-Tunnel einzurichten, um den nicht autorisierten Zugriff auf die Commerce-Site und Kundendaten zu blockieren. Richten Sie einen SSH-Tunnel ein, um den nicht autorisierten Zugriff auf die Commerce-Anwendung zu blockieren.

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Webanwendungs-Firewall verwenden**—Analysieren Sie den Traffic und entdecken Sie verdächtige Muster, z. B. Kreditkarteninformationen, die mithilfe einer Web Application Firewall an eine unbekannte IP-Adresse gesendet werden.

Adobe Commerce-Installationen, die in der Cloud-Infrastruktur bereitgestellt werden, können integrierte WAF-Dienste verwenden, die mit dem [Integration von Fastly Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Erweiterte Kennwortsicherheitseinstellungen konfigurieren**—Richten Sie sichere Passwörter ein und ändern Sie sie mindestens alle 90 Tage, wie vom PCI Data Security Standard in Abschnitt 8.2.4 empfohlen. Siehe [Sicherheitseinstellungen für Administratoren konfigurieren](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html).

![Checkliste](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **HTTPS verwenden**—Wenn die Commerce-Site neu implementiert ist, starten Sie die gesamte Site mit HTTPS. Google verwendet nicht nur HTTPS als Ranking-Faktor, viele Benutzer erwägen auch nicht den Kauf über eine Site, es sei denn, diese ist mit HTTPS gesichert.

## Protect gegen Malware

Malware-Angriffe, die auf E-Commerce-Sites abzielen, sind allzu häufig, und Bedrohungsakteure entwickeln ständig neue Wege, Kreditkarten und personenbezogene Daten aus Transaktionen zu sammeln.

Adobe hat jedoch festgestellt, dass die meisten Website-Kompromisse nicht auf einen innovativen Hacker zurückzuführen sind. Stattdessen nutzen Bedrohungsakteure oft vorhandene, ungepatchte Verwundbarkeiten, schlechte Passwörter und schwache Eigentums- und Berechtigungseinstellungen im Dateisystem aus.

Bei den am häufigsten aufgetretenen Angriffen wird bösartiger Code in die absolute Kopf- oder Fußzeile eines Kundenspeichers eingefügt. Dort erfasst der Code Formulardaten, die ein Kunde in das Storefront eingibt, einschließlich Anmeldeinformationen des Kunden und Formulardaten zum Checkout. Anschließend werden diese Daten zu böswilligen Zwecken an einen anderen Ort und nicht an das Commerce-Backend gesendet. Außerdem kann Malware den Admin bei der Ausführung von Code, der das ursprüngliche Zahlungsformular ersetzt, durch ein gefälschtes Formular beeinträchtigen, das alle vom Zahlungsdienstleister festgelegten Schutzmaßnahmen außer Kraft setzt.

Client-seitige Kreditkarten-Skimmers sind eine Art Malware, die Code in Commerce-Website-Inhalte einbettet, die im Browser eines Benutzers ausgeführt werden können, wie in der folgenden Abbildung dargestellt.

![Datenfluss für Malware-Angriffe auf E-Commerce-Sites](../../../assets/playbooks/malware-data-flow.svg)

Wenn bestimmte Aktionen ausgeführt werden, z. B. ein Benutzer, der ein Formular sendet oder einen Feldwert ändert, serialisiert der Skimmer die Daten und sendet sie an Endpunkte von Drittanbietern. Diese Endpunkte sind normalerweise andere kompromittierte Websites, die als Weiterleitung dienen, um die Daten an ihr endgültiges Ziel zu senden.


>[!TIP]
>
>Wenn eine Commerce-Site von einem Malware-Angriff betroffen ist, befolgen Sie die Adobe Commerce-Best Practices für [Reaktion auf einen Sicherheitsvorfall](../maintenance/respond-to-security-incident.md).

### Die häufigsten Angriffe kennen

Nachstehend finden Sie eine Liste häufiger Angriffe, für die Adobe empfiehlt, dass alle Commerce-Kunden sich bewusst sind und Maßnahmen zum Schutz vor Folgendem treffen:

- **Site-Depression**—Ein Angreifer beschädigt eine Website, indem er das Erscheinungsbild der Website ändert oder eigene Nachrichten hinzufügt. Obwohl der Zugriff auf die Website und die Benutzerkonten kompromittiert wurde, bleiben die Zahlungsinformationen häufig sicher.

- **Botschaften**- Der Commerce-Server des Kunden wird Teil eines Bots, der Spam-E-Mails sendet. Auch wenn Benutzerdaten in der Regel nicht kompromittiert sind, kann der Domänenname des Kunden durch Spam-Filter auf die Blockierungsliste gesetzt werden, was die Bereitstellung von E-Mails aus der Domain verhindert. Alternativ dazu kann die Site des Kunden Teil eines Bootnetzes werden, das einen verteilten Denial-of-Service (DDoS)-Angriff auf eine/mehrere andere Site/s verursacht. Das Botnetz blockiert möglicherweise den eingehenden IP-Traffic zum Commerce-Server, was verhindert, dass Kunden einkaufen können.

- **Direkte Serverangriffe**—Die Daten sind kompromittiert, Backdoors und Malware werden installiert und der Betrieb der Website ist betroffen. Zahlungsinformationen, die nicht auf dem Server gespeichert sind, sind durch diese Angriffe weniger wahrscheinlich gefährdet.

- **Stille Kartenerfassung**—Bei diesem katastrophalen Angriff installieren Eindringlinge versteckte Malware oder Kartenerfassungssoftware, oder, schlimmer noch, ändern Sie den Checkout-Prozess, um Kreditkartendaten zu sammeln. Anschließend werden die Daten an eine andere Site zum Verkauf im Dark Web gesendet. Solche Angriffe können über einen längeren Zeitraum unbemerkt bleiben und zu erheblichen Beeinträchtigungen der Kundenkonten und Finanzinformationen führen.

- **Stilles Keylogging**—Der Bedrohungsakteur installiert den Schlüsselprotokollierungscode auf dem Kundenserver, um Administratoranmeldeinformationen zu erfassen, damit er sich anmelden und andere Angriffe starten kann, ohne erkannt zu werden.

### Protect gegen Passwortverschlüsselungsangriffe

Brute Force Password Guessing-Angriffe können zu nicht autorisiertem Administratorzugriff führen. Protect Sie Ihre Site vor diesen Angriffen, indem Sie die folgenden Best Practices befolgen:

- Identifizieren und schützen Sie alle Stellen, an denen von außerhalb auf die Commerce-Installation zugegriffen werden kann.

  Sie können den Zugriff auf den Administrator sichern, der im Allgemeinen den höchsten Schutz erfordert, indem Sie Adobe befolgen [vorrangige Empfehlungen](#priority-recommendations) beim Konfigurieren Ihres Commerce-Projekts.

- Steuern Sie den Zugriff auf die Commerce-Site, indem Sie eine Zugriffssteuerungsliste einrichten, die nur den Zugriff auf Benutzer ermöglicht, die von einer bestimmten IP-Adresse oder einem bestimmten Netzwerk stammen.

  Sie können eine Fastly Edge ACL mit einem benutzerdefinierten VCL-Codefragment verwenden, um eingehende Anforderungen zu filtern und den Zugriff nach IP-Adresse zuzulassen. Siehe [Benutzerdefinierte VCL für das Zulassen von Anforderungen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).


  >[!TIP]
  >
  >Wenn Sie Remote-Mitarbeiter beschäftigen, stellen Sie sicher, dass die IP-Adressen von Remote-Mitarbeitern in der Adressliste mit Zugriffsberechtigung auf die Commerce-Site enthalten sind.

### Verhindern von Clickjacking-Exploits

Adobe schützt Ihren Speicher vor Clickjacking-Angriffen durch Bereitstellung der `X-Frame-Options` HTTP-Anfrage-Header, den Sie in Anfragen an Ihre Storefront einbeziehen können. Siehe [Verhindern von Clickjacking-Exploits](../../../configuration/security/xframe-options.md) im *Adobe Commerce-Konfigurationshandbuch*.
