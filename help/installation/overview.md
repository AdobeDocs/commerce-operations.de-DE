---
title: Übersicht über die lokale Installation
description: Erfahren Sie mehr über den lokalen Installationsprozess für Adobe Commerce. Erfahren Sie mehr über Server-Anforderungen, Einrichtungsschritte und Best Practices für die Bereitstellung.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# Übersicht über die lokale Installation

Diese Seite bietet einen Überblick über die Installation von Adobe Commerce in Ihrer eigenen Infrastruktur. Der Installationsprozess umfasst das Einrichten Ihrer Serverumgebung, das Abrufen der erforderlichen Software und Anmeldeinformationen und das Ausführen des Installationsbefehls.

Die lokale Adobe Commerce-Software kann in etwa 30 bis 60 Minuten installiert werden. Die Zeit, die zum Einrichten der Server-Umgebung vor der Installation benötigt wird, hängt jedoch von Ihren Erfahrungen und den von Ihnen ausgewählten Technologien ab.

>[!TIP]
>
>Sie sollten über technisches Zwischenwissen und Serverzugriff verfügen, um erfolgreich fortzufahren.

Die Installation erstellt einen voll funktionsfähigen Adobe Commerce-Store mit einer [Storefront für Kunden](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) und einem [Admin-Panel](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin). Sie müssen Ihre Datenbank-Anmeldeinformationen, Domain-Informationen und Authentifizierungsschlüssel parat haben, bevor Sie den Prozess beginnen.

## Händlerpflichten

Mit Adobe Commerce On-Premise können Sie Ihre eigene Infrastruktur hosten und verwalten, einschließlich Server, Hosting-Umgebungen und Systemwartung. Adobe bietet spezielle Unterstützung für das zentrale Commerce-Programm, einschließlich:

- Zugriff auf Produktaktualisierungen und Fehlerbehebungen
- Sicherheits-Patches zur Behebung von Sicherheitslücken
- Umfassende Dokumentation, die Sie bei der Verwaltung und Optimierung Ihrer selbst gehosteten Lösung unterstützt

Sie haben die volle Kontrolle über Ihre Umgebung, was eine bessere Anpassung und Flexibilität ermöglicht, aber Sie sind dafür verantwortlich, die Leistung, Sicherheit und Skalierbarkeit der Infrastruktur sicherzustellen. Sie sind beispielsweise für Folgendes verantwortlich:

- Design, Implementierung, Konfiguration, Wartung, Fehlerbehebung und Leistungstests für alle Adobe Commerce On-Premise-Systeme.
   - Server, Betriebssystem, Datenbanken, [!DNL PHP], Suche, Caching, vollständiger Seiten-Cache und Content Delivery Network. Häufige Themen können (aber nicht beschränkt auf) [!DNL Nginx/Apache], [!DNL PHP], [!DNL MySQL/MariaDB], [!DNL Redis], [!DNL Elasticsearch/OpenSearch], [!DNL RabbitMQ], [!DNL Varnish], [!DNL DNS], [!DNL SSL/TLS certificates] und alle verwendeten [!DNL CDN] sein.
- Kapazitätsplanung, automatische Skalierung, Clustering, Backups, Disaster Recovery
- Alle Produkt- und Kundendaten, Design, Konfiguration und Einrichtung, Anwendungs- und Datenbankpflege, Code-Bereitstellung, Versionsaktualisierungen und Patch-Anwendungen
- Überwachung und Benachrichtigung per APM/Protokollierung/Benachrichtigung (z. B. [!DNL New Relic], [!DNL Datadog], [!DNL ELK])
- Sicherheits-Patching für Betriebssystem, [!DNL PHP], Datenbank, Middleware-Härtung und Updates

## Workflow

Die folgende Abbildung zeigt die wichtigsten Schritte bei der Installation von Adobe Commerce für On-Premise-Umgebungen:

![Funktionsweise der Installation](../assets/installation/on-premises-install.drawio.svg)

### Einrichten der Serverumgebung

Installieren und konfigurieren Sie PHP, Webserver, Datenbank und Suchmaschine gemäß den [Voraussetzungen](prerequisites/overview.md).

### Authentifizierungsschlüssel abrufen

Generieren Sie neue [Authentifizierungsschlüssel](prerequisites/authentication-keys.md) (oder kopieren Sie bestehende Schlüssel) aus Commerce Marketplace, um auf Adobe Commerce Composer-Pakete zuzugreifen.

### Abrufen der Adobe Commerce-Software

Laden Sie mithilfe von [Composer](prerequisites/commerce.md) (empfohlen) herunter oder klonen Sie es von GitHub für Entwicklungsbeiträge.

Wenn Sie einen Beitrag zur Magento Open Source-Codebasis leisten oder das Programm anpassen möchten, [ Sie das GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)Repository (klonen). Diese Methode erfordert Vertrautheit mit GitHub und Composer.

### Installieren des Programms

Führen Sie den Installationsbefehl mit Ihrer spezifischen Konfiguration aus. Vollständige Beispiele finden Sie [ &quot;](composer.md)&quot;.

>[!NOTE]
>
>Wenn die Schritte fehlschlagen, weil die erforderliche Software nicht ordnungsgemäß eingerichtet ist, überprüfen Sie die [Voraussetzungen](prerequisites/overview.md).

### Überprüfen der Installation

[Testen](next-steps/verify.md) Sie Ihre Storefront und Ihr Admin-Panel, um sicherzustellen, dass alles ordnungsgemäß funktioniert.

## Häufige Installationsprobleme

- **Berechtigungsfehler**: Stellen Sie sicher, dass das Dateisystem über die erforderlichen Eigentümer- und Zugriffsrechte verfügt
- **Datenbankverbindungsfehler**: Überprüfen der Datenbankanmeldeinformationen und der Netzwerkverbindung
- **Fehler bei Authentifizierungsschlüsseln**: Überprüfen Sie, ob Ihre Commerce Marketplace-Schlüssel gültig und aktiv sind
- **Speicherbeschränkungen**: Sicherstellen einer ausreichenden PHP-Speicherzuweisung (mindestens 2 GB empfohlen)
