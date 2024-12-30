---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---
# Sichere Webserver-Kommunikation

In diesem Abschnitt wird ein Beispiel für die Sicherung der Kommunikation zwischen dem Webserver und der Suchmaschine (Elasticsearch oder OpenSearch) mithilfe einer Kombination aus TLS-Verschlüsselung (Transport Layer Security) und [HTTP-Standardauthentifizierung](https://datatracker.ietf.org/doc/html/rfc2617) erläutert. Sie können optional auch andere Authentifizierungstypen konfigurieren. Wir stellen Verweise für diese Informationen bereit.

(Ein älterer Begriff, Secure Sockets Layer (SSL), wird häufig synonym mit TLS verwendet. In diesem Thema wird auf *TLS* verwiesen.

>[!WARNING]
>
>Sofern nicht anders angegeben, müssen alle Befehle in diesem Thema als Benutzer mit `root` Berechtigungen eingegeben werden.

## Recommendations

Wir empfehlen Folgendes:

* Ihr Webserver verwendet TLS.

  TLS sprengt den Rahmen dieses Themas. Wir empfehlen jedoch dringend, in der Produktion ein echtes Zertifikat und kein selbstsigniertes Zertifikat zu verwenden.

* Ihre Suchmaschine wird auf demselben Host wie ein Webserver ausgeführt. Das Ausführen der Suchmaschine und des Webservers auf verschiedenen Hosts würde den Rahmen dieses Themas sprengen.

  Der Vorteil, dass Suchmaschinen und Webserver auf denselben Host gesetzt werden, besteht darin, dass das Abfangen verschlüsselter Kommunikation unmöglich wird. Der Suchmaschinen-Webserver muss nicht mit dem Adobe Commerce-Webserver identisch sein. Beispielsweise kann Adobe Commerce Apache ausführen und Elasticsearch/OpenSearch kann nginx ausführen.

  Wenn die Suchmaschine im öffentlichen Web verfügbar gemacht wird, sollten Sie die Authentifizierung konfigurieren. Wenn Ihre Suchmaschineninstanz in Ihrem Netzwerk geschützt ist, ist dies möglicherweise nicht erforderlich. Arbeiten Sie mit Ihrem Hosting-Anbieter zusammen, um zu bestimmen, welche Sicherheitsmaßnahmen Sie zum Schutz Ihrer Instanz implementieren sollten.

## Weitere Informationen zu TLS

Siehe eine der folgenden Ressourcen:

* Apache

   * [Anleitung zur starken Verschlüsselung in Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [So erstellen Sie ein SSL-Zertifikat auf Apache für Ubuntu 14.04 (DigitalOcean-Tutorial)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Einrichten eines mit SSL gesicherten Webservers mit CentOS (CentOS Wiki)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL-Beendigung](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [So erstellen Sie ein SSL-Zertifikat auf Nginx für Ubuntu 14.04 (DigitalOcean-Tutorial)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL-Zertifikatinstallation (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
