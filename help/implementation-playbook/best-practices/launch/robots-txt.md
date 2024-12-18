---
title: Best Practices für die Konfiguration von Web-Crawlern
description: Erfahren Sie, wie Sie mithilfe der Dateien „robots.txt“ und „sitemap.xml“ Anweisungen zu Ihrer Adobe Commerce-Site an Web-Crawler übergeben.
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Best Practices für die Konfiguration von Web-Crawlern

Dieser Artikel enthält Best Practices für die Verwendung von `robots.txt`- und `sitemap.xml` in Adobe Commerce, einschließlich Konfiguration und Sicherheit. Diese Dateien weisen Web-Crawler (normalerweise Suchmaschinenroboter) an, Seiten auf einer Website zu durchsuchen. Die Konfiguration dieser Dateien kann die Leistung der Site und die Suchmaschinenoptimierung verbessern.

>[!NOTE]
>
>Diese Best Practices gelten nur für Projekte, die die native Adobe Commerce-Storefront verwenden. Sie gelten nicht für Adobe Commerce-Projekte, die andere Storefront-Lösungen verwenden (z. B. Adobe Experience Manager, Headless).

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Adobe Commerce auf Cloud-Infrastruktur

Ein standardmäßiges Adobe Commerce-Projekt enthält eine Hierarchie mit einer einzelnen Website-, Store- und Store-Ansicht. Für komplexere Implementierungen können Sie zusätzliche Websites, Stores und Store-Ansichten für eine Storefront mit _Sites_.

### Storefronts mit einer Site

Befolgen Sie diese Best Practices beim Konfigurieren der `robots.txt`- und `sitemap.xml` für Storefronts mit einer Website:

- Stellen Sie sicher, dass Ihr Projekt [`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) Version 2002.0.12 oder höher verwendet.
- Verwenden Sie das Admin-Programm, um der `robots.txt` Inhalte hinzuzufügen.

  >[!TIP]
  >
  >Zeigen Sie die automatisch generierte `robots.txt` für Ihren Store unter `<domain.your.project>/robots.txt` an.

- Verwenden Sie das Admin-Programm, um eine `sitemap.xml`-Datei zu generieren.

  >[!IMPORTANT]
  >
  >Aufgrund des schreibgeschützten Dateisystems in Adobe Commerce in Cloud-Infrastrukturprojekten müssen Sie den `pub/media` angeben, bevor Sie die Datei generieren.

- Verwenden Sie ein benutzerdefiniertes Fastly-VCL-Snippet für beide Dateien, um vom Stammverzeichnis Ihrer Site zum `pub/media/`-Speicherort umzuleiten:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Testen Sie die Umleitung, indem Sie die Dateien in einem Webbrowser anzeigen. Zum Beispiel `<domain.your.project>/robots.txt` und `<domain.your.project>/sitemap.xml`. Stellen Sie sicher, dass Sie den Stammpfad verwenden, für den Sie die Umleitung konfiguriert haben, und nicht einen anderen Pfad.

>[!INFO]
>
>Siehe [Hinzufügen von Sitemaps und Suchmaschinenrobotern](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) für detaillierte Anweisungen.


### Storefronts mit mehreren Sites

Mit einer einzigen Implementierung von Adobe Commerce in der Cloud-Infrastruktur können Sie mehrere Stores einrichten und ausführen. Siehe [Einrichten mehrerer Websites oder Stores](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites).

Die gleichen Best Practices für die Konfiguration der `robots.txt`- und `sitemap.xml`-Dateien für [Storefronts mit einer Site](#single-site-storefronts) gelten für Storefronts mit mehreren Sites, mit zwei wichtigen Unterschieden:

- Stellen Sie sicher, dass die `robots.txt`- und `sitemap.xml`-Dateinamen die Namen der entsprechenden Sites enthalten. Beispiel:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Verwenden Sie ein leicht geändertes benutzerdefiniertes Fastly-VCL-Fragment, um für beide Dateien in Ihren Sites vom Stammverzeichnis Ihrer Sites zum `pub/media`-Speicherort umzuleiten:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce On-Premises

Verwenden Sie das Admin-Programm, um die `robots.txt`- und `sitemap.xml`-Dateien zu konfigurieren, damit Bots keine unnötigen Inhalte scannen und indizieren (siehe [Suchmaschinenroboter](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Bei lokalen Bereitstellungen hängt der Speicherort der Dateien von der Installation von Adobe Commerce ab. Schreiben Sie die Dateien in `/path/to/commerce/pub/media/` oder `/path/to/commerce/media`, je nachdem, was für Ihre Installation geeignet ist.

## Sicherheit

Geben Sie den Administratorpfad nicht in Ihrer `robots.txt` an. Das Offenlegen des Administratorpfads ist eine Schwachstelle für Website-Hacking und möglichen Datenverlust. Entfernen Sie den Administratorpfad aus der `robots.txt`.

Schritte zum Bearbeiten der `robots.txt` und Entfernen aller Einträge im Administratorpfad finden Sie unter [Marketing-Benutzerhandbuch > SEO und Suche > Suchmaschinenroboter](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Wenn Sie Hilfe benötigen, [ Sie ein Adobe Commerce-Support-Ticket ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Weitere Informationen

- [Grundlegendes zu Websites, Stores und Store-Ansichten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Hinzufügen von Websites](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Verwenden Sie Fastly, um bösartigen Traffic für Ihre Adobe Commerce-Sites zu blockieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt gibt einen 404-Fehler in Adobe Commerce auf Cloud Infrastructure 2.3.x aus](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
