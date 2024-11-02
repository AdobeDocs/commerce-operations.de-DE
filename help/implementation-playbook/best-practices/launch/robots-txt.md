---
title: Best Practices für die Konfiguration von Webcrawlern
description: Erfahren Sie, wie Sie mithilfe von "robots.txt"- und "sitemap.xml"-Dateien Anweisungen über Ihre Adobe Commerce-Website an Webcrawler weitergeben.
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Best Practices für die Konfiguration von Webcrawlern

Dieser Artikel enthält Best Practices für die Verwendung von `robots.txt` - und `sitemap.xml` -Dateien in Adobe Commerce, einschließlich Konfiguration und Sicherheit. Diese Dateien weisen Webcrawler (typischerweise Suchmaschinen-Roboter) an, wie Seiten auf einer Website durchsucht werden. Die Konfiguration dieser Dateien kann die Site-Leistung und Suchmaschinenoptimierung verbessern.

>[!NOTE]
>
>Diese Best Practices gelten nur für Projekte, die die native Adobe Commerce-Storefront verwenden. Sie gelten nicht für Adobe Commerce-Projekte, die andere Storefront-Lösungen verwenden (z. B. Adobe Experience Manager, Headless).

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Adobe Commerce auf Cloud-Infrastruktur

Ein standardmäßiges Adobe Commerce-Projekt enthält eine Hierarchie mit einer Website-, Store- und Store-Ansicht. Bei komplexeren Implementierungen können Sie zusätzliche Websites, Stores und Ansichten für eine Storefront mit _mehreren Sites_ erstellen.

### Storefronts mit nur einer Site

Befolgen Sie diese Best Practices bei der Konfiguration der `robots.txt` - und `sitemap.xml` -Dateien für Einzelsite-Storefronts:

- Stellen Sie sicher, dass Ihr Projekt die [`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package)-Version 2002.0.12 oder höher verwendet.
- Verwenden Sie die Admin-Anwendung, um der Datei `robots.txt` Inhalte hinzuzufügen.

  >[!TIP]
  >
  >Zeigen Sie die automatisch generierte `robots.txt` -Datei für Ihren Store unter `<domain.your.project>/robots.txt` an.

- Verwenden Sie die Admin-Anwendung, um eine `sitemap.xml` -Datei zu generieren.

  >[!IMPORTANT]
  >
  >Aufgrund des schreibgeschützten Dateisystems in Adobe Commerce bei Cloud-Infrastrukturprojekten müssen Sie den Pfad &quot;`pub/media`&quot;angeben, bevor Sie die Datei generieren.

- Verwenden Sie ein benutzerdefiniertes Fastly VCL-Snippet, um für beide Dateien vom Stamm Ihrer Site zum Speicherort `pub/media/` umzuleiten:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Testen Sie die Umleitung, indem Sie die Dateien in einem Webbrowser anzeigen. Beispiel: `<domain.your.project>/robots.txt` und `<domain.your.project>/sitemap.xml`. Vergewissern Sie sich, dass Sie den Stammpfad verwenden, für den Sie die Umleitung konfiguriert haben, und nicht einen anderen Pfad.

>[!INFO]
>
>Detaillierte Anweisungen finden Sie unter [Hinzufügen von Sitemap- und Suchmaschinen-Robotern](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) .


### Storefronts mit mehreren Sites

Sie können mehrere Stores mit einer einzigen Implementierung von Adobe Commerce in der Cloud-Infrastruktur einrichten und ausführen. Siehe [Einrichten mehrerer Websites oder Stores](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites).

Die gleichen Best Practices für die Konfiguration der `robots.txt` - und `sitemap.xml` -Dateien für die [Storefronts mit einer einzelnen Site](#single-site-storefronts) gelten für Storefronts mit mehreren Sites mit zwei wichtigen Unterschieden:

- Stellen Sie sicher, dass die Dateinamen `robots.txt` und `sitemap.xml` die Namen der entsprechenden Sites enthalten. Beispiel:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Verwenden Sie ein leicht modifiziertes benutzerdefiniertes Fastly VCL-Snippet, um vom Stamm Ihrer Sites zum Speicherort `pub/media` für beide Dateien auf allen Ihren Sites umzuleiten:

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

Verwenden Sie die Admin-Anwendung, um die Dateien `robots.txt` und `sitemap.xml` zu konfigurieren, um zu verhindern, dass Bots unnötigen Inhalt scannen und indizieren (siehe [Suchmaschinen-Roboter](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Bei lokalen Bereitstellungen hängt das Schreiben der Dateien von der Installation von Adobe Commerce ab. Schreiben Sie die Dateien in `/path/to/commerce/pub/media/` oder `/path/to/commerce/media`, je nachdem, welcher Wert für Ihre Installation geeignet ist.

## Sicherheit

Stellen Sie Ihren Admin-Pfad nicht in Ihrer `robots.txt` -Datei bereit. Der Admin-Pfad offen zu legen ist eine Schwachstelle für das Site-Hacking und einen möglichen Datenverlust. Entfernen Sie den Administratorpfad aus der Datei &quot;`robots.txt`&quot;.

Anweisungen zum Bearbeiten der Datei `robots.txt` und zum Entfernen aller Einträge des Admin-Pfads finden Sie unter [Marketing-Benutzerhandbuch > SEO und Suche > Suchmaschinen-Roboter](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Wenn Sie Hilfe benötigen, senden Sie [ein Adobe Commerce Support-Ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Weitere Informationen

- [Websites, Stores und Ansichten verstehen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Websites hinzufügen](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Verwenden Sie Sofort, um böswilligen Traffic für Ihre Adobe Commerce-Sites zu blockieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt gibt in Adobe Commerce einen 404-Fehler in der Cloud-Infrastruktur 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html) aus
