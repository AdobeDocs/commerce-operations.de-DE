---
title: Installation überprüfen
description: Führen Sie diese Schritte aus, um sicherzustellen, dass Ihre lokale Adobe Commerce-Installation erfolgreich war.
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Installation überprüfen

Navigieren Sie in einem Webbrowser zur Storefront. Wenn die Basis-URL Ihrer Installation beispielsweise &quot;`http://www.example.com`&quot; ist, geben Sie sie in die Adresse oder Adressleiste Ihres Browsers ein.

Die folgende Abbildung zeigt eine Beispiel-Storefront-Seite. Wenn es wie folgt angezeigt wird, war Ihre Installation ein Erfolg!

![Storefront mit dem Luma-Design](../../assets/installation/install-success_store-luma.png)

## Überprüfen der Storefront (keine Beispieldaten)

Navigieren Sie in einem Webbrowser zur Storefront. Wenn die Basis-URL Ihrer Installation beispielsweise &quot;`http://www.example.com`&quot; ist, geben Sie sie in die Adresse oder Adressleiste Ihres Browsers ein.

Die folgende Abbildung zeigt eine Beispiel-Storefront-Seite. Wenn es wie folgt angezeigt wird, war Ihre Installation ein Erfolg!

![Storefront, die eine erfolgreiche Installation überprüft](../../assets/installation/install-success_store.png)

Wenn auf der Seite ein `404 (Not Found)` -Fehler angezeigt wird oder keine Stile angezeigt werden, finden Sie weitere Informationen unter [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360032994352).

## Überprüfen des Administrators

Navigieren Sie in einem Webbrowser zum Administrator . Wenn die Basis-URL Ihrer Installation beispielsweise &quot;`http://www.example.com`&quot; lautet und der Admin-URI &quot;`admin_au1nT`&quot;, geben Sie &quot;`http://www.example.com/admin_au1nT`&quot;in die Adresse oder Standortleiste Ihres Browsers ein.

(Der Administrator-URI wird durch den Wert des Installationsparameters `backend-frontname` angegeben.)

Melden Sie sich bei entsprechender Aufforderung als Administrator an.

Die folgende Abbildung zeigt eine Beispiel-Admin-Seite. Wenn es wie folgt angezeigt wird, war Ihre Installation ein Erfolg!

![Admin, der eine erfolgreiche Installation überprüft](../../assets/installation/install_success_admin.png)

Wenn auf der Seite keine Stile angezeigt werden, finden Sie weitere Informationen unter [Fehlerbehebung](https://support.magento.com/hc/en-us/articles/360032994352).

Wenn Sie einen 404-Fehler (Nicht gefunden) erhalten, der dem folgenden ähnelt, finden Sie weitere Informationen unter [PHP-Versionsfehler oder 404 beim Zugriff auf Adobe Commerce im Browser](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
