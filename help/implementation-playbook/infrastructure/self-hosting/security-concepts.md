---
title: Sicherheitskonzepte für Adobe Commerce, die selbst gehostet werden
description: Erfahren Sie mehr über das selbstständige Hosting von Sicherheitsideen und -konzepten sowie Best Practices, die Sie berücksichtigen sollten. Erfahren Sie mehr über Konzepte wie schreibgeschützte Dateisysteme, Malware-Scannen und viele andere Themen, die beim Hosten von Adobe Commerce berücksichtigt werden können.
landing-page-description: Erfahren Sie mehr über Sicherheitskonzepte und -aspekte, die Sie beim Hosten von Adobe Commerce selbst beachten sollten.
short-description: Erfahren Sie Strategien und Sicherheitskonzepte für das Hosting von Adobe Commerce selbst.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 0d5c2d3ae44008142797c7ac91530a9df98ae004
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---


# Sicherheitskonzepte

Sicherheit sollte stets ein starkes Augenmerk auf alles im Zusammenhang mit einem E-Commerce-Projekt sein. Ohne eine starke Sicherheitslage ist die Fläche, die angegriffen werden kann, exponentiell größer. Die präsentierten Konzepte und Ideen bieten Methoden, die nachweislich die üblicherweise ausgenutzten häufigen Schwachstellen reduzieren.

Die folgenden Konzepte sind in keiner bestimmten Reihenfolge aufgeführt. Sie sollen einige zu berücksichtigende Ideen und Konzepte liefern. Viele sind kostenlos oder erfordern nur eine minimale Einrichtung und Konfiguration und nachfolgende Überwachung. Forschen Sie diese Themen außerhalb dieses Tutorials an, um sicherzustellen, dass Sie ein tiefes Verständnis der hier vorgestellten Konzepte haben.

## Schreibgeschütztes Dateisystem

Das reine Dateisystemkonzept wurde von [Adobe Commerce in Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. Dadurch wird ein wichtiger Bereich, der von einem schlechten Schauspieler genutzt wird, vollständig entfernt. Viele Exploits haben davon profitiert, eine Datei zu ändern, die sich voraussichtlich in der Commerce-Anwendung befindet, um die Erkennung zu vermeiden. Anstatt eine zu erstellen, ändert der fehlerhafte Akteur den Inhalt einer vorhandenen Datei, um eine unerwartete Aktion auszuführen. Durch das schreibgeschützte Dateisystem wird dieser Angriffsvektor erheblich reduziert.

## Verwenden von zwei Faktor-Authentifizierungs- und Passwort-Managern

Geben Sie nie Kennwörter frei. Jeder Admin-Benutzer sollte über sein eigenes Konto mit einer korrekten ACL verfügen. Stellen Sie sicher, dass die Identifizierung von zwei Faktoren nie deaktiviert oder entfernt wird. Wenn Sie Admin-Zugriff auf einen Drittanbieter gewähren, stellen Sie sicher, dass das Kennwort von einem Kennwortmanager generiert und nie wiederverwendet wird.

## Malware-Scans

Malware-Scans werden normalerweise von einem Hosting-Provider gefunden, der versucht, sich auf Adobe Commerce zu spezialisieren. Diese Bibliothek bekannter Malware und Exploits ist eine immer größer werdende Liste, da neue Bedrohungen entdeckt, getestet und diagnostiziert werden. Informieren Sie sich, ob der Hosting-Anbieter über einen solchen Dienst verfügt und ob diese automatisch oder nur auf Anfrage ausgeführt werden können. Es gibt auch Dienste, die Sie abonnieren können, die ihre eigene Bibliothek bekannter Exploits verwenden können, um Ihre Commerce-Anwendung ständig auf Exploits zu überprüfen. Einige davon sind nur extern, einige können der Infrastruktur hinzugefügt werden, um eine interne Tiefensuche aller Ordner, Dateien und sogar der Datenbank zu ermöglichen. Es gibt einige Anbieter mit langjähriger Erfahrung in diesem Bereich, von Sansec.io über Sucuri und natürlich MageReport. Einige sind kostenlos, andere mit entsprechenden Kosten. Wenn Sie wissen, dass dies verfügbar ist und sich mit Ihrem Adobe Commerce-Architekten und DevOps-Team gründlich unterhalten, finden Sie die richtige Lösung.

## Site-weites Analyse-Tool für Commerce

Die [Site-weites Analyse-Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} ist ein proaktives Self-Service-Tool und zentrales Repository mit detaillierten Systemeinblicken und Empfehlungen, um die Sicherheit und Bedienbarkeit Ihrer Adobe Commerce-Installation sicherzustellen. Es bietet rund um die Uhr eine Leistungsüberwachung, Berichte und Beratung in Echtzeit, um potenzielle Probleme zu identifizieren und bessere Sichtbarkeit in Bezug auf Gesundheit, Sicherheit und Anwendungskonfigurationen der Website zu erreichen. Dies trägt zur Verkürzung der Auflösungszeit und zur Verbesserung der Site-Stabilität und -Leistung bei.

## Aktivieren und Überprüfen der Einstellungen für die Admin-Aktionsprotokollierung

Diese finden Sie nach der Anmeldung beim Adobe Commerce-Administrator und Navigieren zu Stores > Konfiguration > Erweitert > Admin > Admin-Aktionsprotokollierung . Dies bietet eine Liste der Ereignisse, die überwacht und aufgezeichnet werden. Es ist nützlich bei der forensischen Analyse auf einer ausgebeuteten Site, wenn der Verdacht besteht, dass sie Zugang zum Commerce-Administrator erhalten. Diese Protokollierung und dieser Bericht können hilfreich sein, um zu sehen, welche Ereignisse der schlechte Schauspieler durchgeführt hat. Wenn die Protokollierung von Admin-Aktionen deaktiviert ist, ist dies ein Hinweis darauf, dass sie von einer Person für die Abdeckung deaktiviert wurde. Entfernen Sie die Protokollierung bei der Ausführung bestimmter Aktionen.

## Baseline-Server für SSH-Zugriff

Dies ist schwieriger zu erklären, dass die meisten Themen im Tutorial zu Sicherheitskonzepten . Die Grundidee dafür ist es, einen Server bereitzustellen, der als Mittler für SSH-Zugriff fungiert. Auf diese Weise lassen Ihre Produktionsserver keine externen SSH-Verbindungen zu. Sie können diesen Bastion-Server erstellen und eine lokale IP-Maske verwenden, um sicherzustellen, dass nur bestimmte Server SSH in sie aufnehmen dürfen.

## Überprüfen von ACL-Rollen und -Berechtigungen

Jedem Admin-Benutzer von Adobe Commerce wird eine ACL-Rolle zugewiesen. Diese Rolle sollte erstellt werden, um nur die Funktion bereitzustellen, die den Auftrag ausführen muss. Die ACL-Rollen sollten häufig bewertet werden, um sicherzustellen, dass sie nicht mehr Autorität als nötig bieten. Erstellen Sie bei Bedarf viele ACL-Rollen mit Verantwortlichkeiten. Wird einem Dritten Zugriff aus irgendeinem Grund gewährt, sollten diese so bald wie möglich deaktiviert werden. Fragen Sie sie, wie lange sie unbedingt Zugriff benötigen, und legen Sie ein automatisches Ablaufdatum fest, wenn sie einen Administrator-Benutzer erstellen.

## Admin-Benutzer und SSH-Benutzerzugriff häufig überprüfen

Um unerwünschte oder nicht autorisierte Admin-Benutzererstellungen zu erkennen, sollte die Liste der Admin-Benutzer häufig geprüft werden. Eine gute Faustregel besteht darin, jeden Monat zu überprüfen, wer über SSH und Administratorzugriff auf die Adobe Commerce-Anwendung verfügt. Wenn neue Benutzer erkannt werden, deaktivieren Sie ihr Konto und befolgen Sie die Unternehmensrichtlinien und -verfahren für einen solchen Vorfall. Es ist einfacher, den Zugriff eines Benutzers wieder zu aktivieren, als sich von einer Exploit wiederherzustellen.

## Datenbankbereinigung

Schränken Sie den Zugriff auf Produktionsdaten ein. Diese benannten Teamkollegen sollten die Möglichkeit haben, Produktionsdatenbanken abzurufen und sie von echten Daten zu bereinigen. Wenn das Entfernen der Daten eine Option ist, schneiden Sie die entsprechenden Tabellen wie Bestellungen, Anführungszeichen und Kunden ab. Manchmal möchten Sie jedoch den vollständigen Datensatz, aber die Werte können anonymisiert werden. Dies trifft normalerweise in einer Staging-Umgebung zu. Dies ist auch vor Upgrades nützlich. Indem Sie das tatsächliche Datenvolumen, aber anonymisiert haben, stellen Sie sicher, dass Sie die Zeit testen und validieren, um eine Bereitstellung für die Aktualisierung ordnungsgemäß auszuführen. Wenn Sie über einen begrenzten Datensatz verfügen, können Sie den Aktualisierungsprozess und die zeitliche Verteilung unterschätzen.

Beispiel für eine Zufälligkeit für Kundeninformationen Hier ist ein Beispiel für das Ändern der E-Mail-Adresse eines Kunden mit einer zufälligen Zeichenfolge und allen Vor- und Nachnamen-Feldern in einigen Standardtabellen, in denen Adobe Commerce Daten speichert. **Denken Sie daran, alle Tabellen auf vertrauliche Daten zu überprüfen. Diese Liste enthält nicht alle Tabellen, in denen Kundendaten gespeichert werden können.**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++Sie können auch Tabellen abschneiden, anstatt zu versuchen, sie zu anonymisieren

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++Informationen vollständig Beispiel Hier ist ein Beispiel für das Entfernen aller Bestellungen, Anführungszeichen, Kreditkarten und mehr vor dem Start oder für eine niedrigere Entwicklungsumgebung

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## Umgebungsvariablen verwenden

[!BADGE Nur Adobe Commerce in Cloud]{type=Informative}

Die Verwendung von Umgebungsvariablen hilft Ihnen dabei, bestimmte Werte festzulegen, die für jede Umgebung geändert werden können und sollten. Sie können beispielsweise für jede Umgebung eine andere Admin-URL verwenden. Wenn Sie diesen Wert als Umgebungsvariable festlegen, können Sie dies konfigurieren und bei Bedarf auch schnell über die Cloud-Benutzeroberfläche auf diesen Wert verweisen.

Weitere Informationen zu diesem Thema finden Sie in Experience League [Commerce in Cloud-Infrastruktur-Umgebungsvariablen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## Scanwerkzeuge für Software-Sicherheitsrisiken

Die CI/CD-Pipeline kann ein leistungsstarkes Tool sein und dazu beitragen, einige Aufgaben zu automatisieren. Insbesondere die Möglichkeit für einen Entwickler, Code zu übertragen, der ausnutzbar sein kann, ist immer eine reale Möglichkeit. Peer-Code-Rezensionen fangen solche Artikel normalerweise, aber weil es ein menschliches Element ist, treten Fehler auf. Die automatisierte Codescan reduziert die Möglichkeit unerwarteter Sicherheitslücken in einer neu eingeführten Funktion. Diese Tools können sogar eingesetzt werden, um das Zusammenführen von Code in die Live-Codebasis zu verhindern. Es gibt viele Möglichkeiten und Werkzeuge, um automatisierte Code-Sicherheits- und Qualitätsscans zu bieten. Es kann robuste benutzerdefinierte Tools geben, die jedoch ständig aktualisiert und angepasst werden müssen. Eine Alternative besteht darin, proaktiv aktualisierte Tools wie synk.io und den Code-Inspektor von Amazon anzuwenden.

## Web Application Firewall

Eine Webanwendungs-Firewall oder eine WAF, wie häufig verwendet wird, wenn Sie mit DevOps oder einem Hosting-Anbieter sprechen.

Web Application Firewalls (WAFs) verhindern, dass böswilliger Traffic auf Websites und in Netzwerken zugreift, indem der Traffic nach einer Reihe von Sicherheitsregeln gefiltert wird. Der Traffic, der von Triggern auf Regeln angewendet wird, wird blockiert, bevor er Ihre Sites oder Ihr Netzwerk beschädigen kann.

Adobe Commerces Cloud WAF bietet eine WAF-Richtlinie mit einem Regelsatz, der Ihre Adobe Commerce-Webanwendungen vor einer Vielzahl von Angriffen schützt. Wenn Sie eine Self-Hosting-Option wählen, sind Sie dafür verantwortlich, eine WAF zu finden und die Regeln zu konfigurieren. Einige Hosting-Provider und WAF-Provider verfügen über einen generischen Regelsatz, der einen guten Start darstellt. Sie erwarten jedoch einige Arbeit, damit die Dinge für Ihr Projekt funktionieren.

Die WAF untersucht den Web- und Admin-Traffic, um verdächtige Aktivitäten zu identifizieren. Sie wertet den GET- und den POST-Traffic (HTTP-API-Aufrufe) aus und wendet den Regelsatz an, um zu bestimmen, welcher Traffic blockiert werden soll. Die WAF kann eine Vielzahl von Angriffen verhindern, darunter SQL-Injection-Angriffe, Cross-Site-Scripting-Angriffe, Angriffe durch Datenexfiltration und HTTP-Protokollverletzungen.

Als Cloud-basierter Service benötigt die WAF keine Hardware oder Software, um zu installieren oder zu warten. Fastly, ein bestehender Technologiepartner, bietet die Software und das Know-how. Ihre hochperformante, immer aktive WAF-Datei befindet sich in jedem Cache-Knoten des globalen Bereitstellungsnetzwerks von Fastly.

Weitere Informationen zu den von Fastly bereitgestellten WAF-Dateien in Adobe Commerce on Cloud finden Sie im [Häufig gestellte Fragen zur Adobe Commerce-Wissensdatenbank](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
