---
title: Installation überprüfen
description: Führen Sie diese Schritte aus, um sicherzustellen, dass Ihre lokale Installation von Adobe Commerce oder Magento Open Source erfolgreich war.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Installation überprüfen

Navigieren Sie zu [storefront](https://glossary.magento.com/storefront) in einem Webbrowser. Wenn beispielsweise Ihre Installationsbasis [URL](https://glossary.magento.com/url) is `http://www.example.com`, geben Sie ihn in die Adresse oder Adressleiste Ihres Browsers ein.

Die folgende Abbildung zeigt eine Beispiel-Storefront-Seite. Wenn es wie folgt angezeigt wird, war Ihre Installation ein Erfolg!

![Storefront mit dem Luma-Design](../../assets/installation/install-success_store-luma.png)

## Überprüfen der Storefront (keine Beispieldaten)

Navigieren Sie in einem Webbrowser zur Storefront. Wenn Ihre Basis-URL der Installation beispielsweise `http://www.example.com`, geben Sie ihn in die Adresse oder Adressleiste Ihres Browsers ein.

Die folgende Abbildung zeigt eine Beispiel-Storefront-Seite. Wenn es wie folgt angezeigt wird, war Ihre Installation ein Erfolg!

![Storefront, die eine erfolgreiche Installation überprüft](../../assets/installation/install-success_store.png)

Wenn die Seite eine `404 (Not Found)` Fehler oder zeigt keine Stile an, siehe [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360032994352).

## Überprüfen des Administrators

Navigieren Sie zu [Admin](https://glossary.magento.com/magento-admin) in einem Webbrowser. Wenn Ihre Basis-URL der Installation beispielsweise `http://www.example.com`und der Admin-URI lautet `admin_au1nT`, eingeben `http://www.example.com/admin_au1nT` in der Adresse oder Standortleiste Ihres Browsers.

(Die [Admin](https://glossary.magento.com/admin) Der URI wird durch den Wert der `backend-frontname` Installationsparameter.)

Melden Sie sich bei entsprechender Aufforderung als Administrator an.

Die folgende Abbildung zeigt eine Beispiel-Admin-Seite. Wenn es wie folgt angezeigt wird, war Ihre Installation ein Erfolg!

![Administrator, der eine erfolgreiche Installation überprüft](../../assets/installation/install_success_admin.png)

Wenn die Seite keine Stile anzeigt, lesen Sie [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360032994352).

Wenn Sie einen 404 (Not Found)-Fehler ähnlich dem folgenden erhalten, lesen Sie [PHP-Versionsfehler oder 404 beim Zugriff auf Adobe Commerce im Browser](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
