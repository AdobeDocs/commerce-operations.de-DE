---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---
# Sichere Webserverkommunikation

In diesem Thema wird ein Beispiel für die Sicherung der Kommunikation zwischen Ihrem Webserver und der Suchmaschine (Elasticsearch oder OpenSearch) mithilfe einer Kombination aus Transport Layer Security (TLS)-Verschlüsselung und [Grundlegende HTTP-Authentifizierung](https://datatracker.ietf.org/doc/html/rfc2617). Sie können optional auch andere Authentifizierungstypen konfigurieren. Für diese Informationen werden Verweise bereitgestellt.

(Ein älterer Begriff, Secure Sockets Layer (SSL), wird häufig synonym mit TLS verwendet. In diesem Thema beziehen wir uns auf *TLS*.

>[!WARNING]
>
>Sofern nicht anders angegeben, müssen alle Befehle in diesem Thema als Benutzer mit `root` -Berechtigungen.

## Recommendations

Wir empfehlen Folgendes:

* Ihr Webserver verwendet TLS.

  TLS überschreitet den Rahmen dieses Themas. Wir empfehlen jedoch dringend, ein echtes Zertifikat in der Produktion und kein selbstsigniertes Zertifikat zu verwenden.

* Ihre Suchmaschine läuft auf demselben Host wie ein Webserver. Das Ausführen der Suchmaschine und des Webservers auf verschiedenen Hosts ist über den Rahmen dieses Themas hinaus möglich.

  Der Vorteil, dass Suchmaschinen und Webserver auf denselben Host gesetzt werden, besteht darin, dass das Abfangen verschlüsselter Kommunikation unmöglich wird. Der Webserver der Suchmaschine muss nicht mit dem Adobe Commerce-Webserver übereinstimmen. Adobe Commerce kann beispielsweise Apache ausführen und Elasticsearch/OpenSearch kann nginx ausführen.

  Wenn die Suchmaschine für das öffentliche Web verfügbar gemacht wird, sollten Sie die Authentifizierung konfigurieren. Wenn Ihre Suchmaschineninstanz in Ihrem Netzwerk geschützt ist, ist dies möglicherweise nicht erforderlich. Arbeiten Sie mit Ihrem Hosting-Provider zusammen, um zu ermitteln, welche Sicherheitsmaßnahmen Sie implementieren sollten, um Ihre Instanz zu schützen.

## Weitere Informationen zu TLS

Sehen Sie sich eine der folgenden Ressourcen an:

* Apache

   * [Anleitung zur Verschlüsselung mit Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Erstellen eines SSL-Zertifikats auf Apache für Ubuntu 14.04 (DigitalOcean-Tutorial)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Einrichten eines SSL-gesicherten Webservers mit CentOS (CentOS-Wiki)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx SSL-Beendigung](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Erstellen eines SSL-Zertifikats unter Nginx für Ubuntu 14.04 (DigitalOcean-Tutorial)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL-Zertifikatinstallation (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
