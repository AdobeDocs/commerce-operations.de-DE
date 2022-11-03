---
title: Best Practices zum Konfigurieren von Dateien "robots.txt"und "sitemap.xml"
description: Erfahren Sie, wie Sie Anweisungen über Ihre Adobe Commerce-Website an Webcrawler weitergeben.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# Best Practices für die Konfiguration `robots.txt` und `sitemap.xml` files

Dieser Artikel enthält Best Practices für die Verwendung von `robots.txt` und `sitemap.xml` -Dateien in Adobe Commerce, einschließlich Konfiguration und Sicherheit. Diese Dateien weisen Webroboter (typischerweise Suchmaschinen-Roboter) an, wie Seiten auf einer Website durchsucht werden. Die Konfiguration dieser Dateien kann die Site-Leistung und Suchmaschinenoptimierung verbessern.

>[!NOTE]
>
>Diese Best Practices gelten nur für Projekte, die die native Adobe Commerce-Storefront verwenden. Sie gelten nicht für Adobe Commerce-Projekte, die andere Storefront-Lösungen verwenden (z. B. Adobe Experience Manager, Headless).

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Adobe Commerce auf Cloud-Infrastruktur

Ein standardmäßiges Adobe Commerce-Projekt enthält eine Hierarchie mit einer Website-, Store- und Store-Ansicht. Für komplexere Implementierungen können Sie zusätzliche Websites, Stores und Ansichten für eine _Multi-Site_ Storefront.

### Storefronts mit nur einer Site

Befolgen Sie diese Best Practices bei der Konfiguration der `robots.txt` und `sitemap.xml` -Dateien für Einzelsite-Storefronts:

- Vergewissern Sie sich, dass Ihr Projekt [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) Version 2002.0.12 oder höher.
- Verwenden Sie die Admin-Anwendung, um Inhalte zur `robots.txt` -Datei.

   >[!TIP]
   >
   >Automatisch generierte anzeigen `robots.txt` -Datei für Ihren Store unter `<domain.your.project>/robots.txt`.

- Verwenden Sie die Admin-Anwendung, um eine `sitemap.xml` -Datei.

   >[!IMPORTANT]
   >
   >Aufgrund des schreibgeschützten Dateisystems in Adobe Commerce für Cloud-Infrastrukturprojekte müssen Sie die `pub/media` Pfad vor dem Generieren der Datei.

- Verwenden Sie ein benutzerdefiniertes Fastly VCL-Snippet, um vom Stamm Ihrer Site zur `pub/media/` Speicherort für beide Dateien:

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- Testen Sie die Umleitung, indem Sie die Dateien in einem Webbrowser anzeigen. Beispiel: `<domain.your.project>/robots.txt` und `<domain.your.project>/sitemap.xml`. Stellen Sie sicher, dass Sie den Stammpfad verwenden, für den Sie die Umleitung konfiguriert haben, und keinen anderen Pfad.

>[!INFO]
>
>Siehe [Sitemap- und Suchmaschinenroboter hinzufügen](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) für detaillierte Anweisungen.


### Storefronts mit mehreren Sites

Sie können mehrere Stores mit einer einzigen Implementierung von Adobe Commerce in der Cloud-Infrastruktur einrichten und ausführen. Siehe [Einrichten mehrerer Websites oder Stores](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Die gleichen Best Practices für die Konfiguration der `robots.txt` und `sitemap.xml` Dateien für [Storefronts mit nur einer Site](#single-site-storefronts) gilt für Storefronts mit mehreren Sites mit zwei wichtigen Unterschieden:

- Stellen Sie sicher, dass die Variable `robots.txt` und `sitemap.xml` Dateinamen enthalten die Namen der entsprechenden Sites. Beispiel:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Verwenden Sie ein geringfügig modifiziertes benutzerdefiniertes Fastly VCL-Snippet, um vom Stamm Ihrer Sites zum `pub/media` Speicherort für beide Dateien Ihrer Sites:

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
   }
   ```

## Adobe Commerce vor Ort

Verwenden Sie die Admin-Anwendung, um die `robots.txt` und `sitemap.xml` Dateien, um zu verhindern, dass Bots unnötige Inhalte scannen und indizieren (siehe [Suchmaschinen-Roboter](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Bei lokalen Bereitstellungen hängt das Schreiben der Dateien von der Installation von Adobe Commerce ab. Schreiben Sie die Dateien in `/path/to/commerce/pub/media/` oder `/path/to/commerce/media`, je nachdem, welcher Zeitpunkt für Ihre Installation geeignet ist.

## Sicherheit

Geben Sie Ihren Admin-Pfad nicht in Ihrer `robots.txt` -Datei. Der Admin-Pfad offen zu legen ist eine Schwachstelle für das Site-Hacking und einen möglichen Datenverlust. Entfernen Sie den Administratorpfad aus dem `robots.txt` -Datei.

Schritte zum Bearbeiten der `robots.txt` und alle Einträge des Admin-Pfads entfernen, siehe [Marketing-Benutzerhandbuch > SEO und Suche > Suchmaschinen-Roboter](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Wenn Sie Hilfe benötigen, [Senden eines Adobe Commerce Support-Tickets](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.md#submit-ticket).

## Zusätzliche Informationen

- [Grundlegendes zu Websites, Geschäften und Store-Ansichten](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Websites hinzufügen](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Verwenden Sie Fast, um böswilligen Traffic für Ihre Adobe Commerce-Sites zu blockieren.](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt gibt in Adobe Commerce in der Cloud-Infrastruktur 2.3.x einen 404-Fehler aus](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.md)
