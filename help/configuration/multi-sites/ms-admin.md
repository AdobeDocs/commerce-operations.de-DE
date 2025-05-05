---
title: Einrichten mehrerer Websites, Stores und Store-Ansichten in der Admin Console
description: Konfigurieren Sie zusätzliche Websites, Stores und Store-Ansichten in Commerce Admin.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---

# Einrichten mehrerer Ansichten in der Admin Console

Für diese Aufgabe müssen Sie für jeden Store eine Stammkategorie (und ggf. zusätzliche Kategorien) erstellen. Die in diesem Thema erörterten Aufgaben bieten eine Möglichkeit, mehrere Stores einzurichten. Weitere Informationen finden Sie in den folgenden Ressourcen im Commerce-Benutzerhandbuch:

- [Kategorien](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/categories/categories)
- [Hinzufügen von Websites](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [URLs speichern](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/site-store/store-urls)
- [Inhalt](https://experienceleague.adobe.com/de/docs/commerce-admin/content-design/content-menu)

>[!INFO]
>
>Nur zum Beispiel verwenden wir eine französische Website mit Website-Code `french` in diesem Thema. Schritt-für-Schritt-Tutorials finden Sie unter [Tutorial: Einrichten mehrerer Websites mit Apache](ms-apache.md) und [Tutorial: Einrichten mehrerer Websites mit Nginx](ms-nginx.md)

## Schritt 1: Erstellen von Stammkategorien

Das Erstellen einer Stammkategorie ist optional, aber wir zeigen in diesem Tutorial, wie Sie dies tun können, falls Sie möchten, dass jede Website eine eindeutige Stammkategorie hat. Sie können bei Bedarf zusätzliche Kategorien erstellen.

Erstellen einer Stammkategorie:

1. Melden Sie sich bei Admin als Benutzer an, der zum Erstellen von Kategorien berechtigt ist.
1. Klicken Sie **Katalog** > **Kategorien**.
1. Klicken Sie **Stammkategorie hinzufügen**.
1. Geben Sie **Feld „Kategoriename** einen eindeutigen Namen ein, um diese Kategorie zu identifizieren.
1. Stellen Sie sicher, dass Kategorie aktivieren auf **Ja** eingestellt ist.

   Weitere Informationen zu den anderen Optionen auf dieser Seite finden Sie unter [Stammkategorien](https://experienceleague.adobe.com/de/docs/commerce-admin/catalog/categories/category-root).

   Die folgende Abbildung zeigt ein Beispiel.

   ![Erstellen und Aktivieren einer Stammkategorie](../../assets/configuration/add-root-category.png)

1. Klicken Sie **Speichern**.
1. Wiederholen Sie diese Aufgaben so oft wie nötig, um Stammkategorien für Ihre Stores zu erstellen.

## Schritt 2: Erstellen von Websites

So erstellen Sie eine Website:

1. Melden Sie sich bei Admin als Benutzer an, der zum Erstellen von Websites, Stores und Store-Ansichten berechtigt ist.
1. Klicken Sie auf **Stores** > **Einstellungen** > **Alle Stores**.
1. Klicken Sie auf der _Stores_-Seite auf **Website erstellen**.

   - **Name** - Geben Sie einen Namen ein, um die Website zu identifizieren.
   - **Code** - Geben Sie einen eindeutigen Code ein. Wenn Sie beispielsweise über einen französischen Store verfügen, können Sie `french` eingeben
   - **Sortierreihenfolge** - Geben Sie eine optionale numerische Sortierreihenfolge ein.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Website hinzufügen](../../assets/configuration/multi-site-website.png)

1. Klicken Sie **Website speichern**.
1. Wiederholen Sie diese Aufgaben so oft wie nötig, um Ihre Websites zu erstellen.

## Schritt 3: Erstellen Sie Stores

So erstellen Sie einen Store:

1. Klicken Sie im Bedienfeld _Admin_ auf **Stores** > **Settings** > **All Stores**.
1. Klicken Sie auf der _Stores_-Seite auf **Store erstellen**.

   - **Website** - Klicken Sie auf den Namen der Website, mit der dieser Store verknüpft werden soll.
   - **Name** - Geben Sie einen Namen ein, um den Store zu identifizieren.
   - **Code** - Geben Sie einen eindeutigen Code ein, um den Store zu identifizieren.
   - **Stammkategorie** - Klicken Sie auf den Namen der Stammkategorie für diesen Store.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Einen Store hinzufügen](../../assets/configuration/multi-site-store.png)

1. Klicken Sie **Speichern**.
1. Wiederholen Sie diese Aufgaben so oft wie nötig, um Ihre Stores zu erstellen.

## Schritt 4: Store-Ansichten erstellen

So erstellen Sie eine Store-Ansicht:

1. Klicken Sie im Bedienfeld _Admin_ auf **Stores** > **Settings** > **All Stores**.
1. Klicken Sie auf der Seite „Stores **auf „Store-Ansicht**.

   - **Store** - Klicken Sie auf den Namen des Stores, mit dem Sie diese Store-Ansicht verknüpfen möchten.
   - **Name** - Geben Sie einen Namen ein, um diese Store-Ansicht zu identifizieren.
   - **Code** - Geben Sie einen eindeutigen Namen ein, um diese Store-Ansicht zu identifizieren.
   - **status** - Wählen Sie **Aktiviert** aus.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Einen Store hinzufügen](../../assets/configuration/multi-site-storeview.png)

1. Klicken Sie **Store-Ansicht speichern**.
1. Wiederholen Sie diese Aufgaben so oft wie nötig, um Ihre Store-Ansichten zu erstellen.

## Schritt 5: Ändern der Website-Basis-URL

Um mit einer eindeutigen URL wie `http://french.magento.mg` auf eine Website zuzugreifen, müssen Sie die Basis-URL für jede Site in der Admin-Liste ändern.

So ändern Sie die Website-Basis-URL:

1. Klicken Sie im Bedienfeld _Admin_ auf **Stores** > **Settings** > **Configuration** > **General** > **Web**.
1. Klicken Sie in der **Store-**&quot; oben auf der Seite auf den Namen einer Ihrer Websites, wie in der folgenden Abbildung dargestellt.

   ![Bereich auswählen](../../assets/configuration/multi-site-scope.png)

1. Erweitern Sie im rechten Bereich **Basis-URLs**.
1. Deaktivieren Sie _Abschnitt_ Basis-URLs **die Option „Systemwert**.
1. Geben Sie die `http://french.magento.mg`-URL in die Felder **Basis-**) und **Basis-Link-**) ein.

1. Wiederholen Sie den vorherigen Schritt im Abschnitt _Basis-URLs (sicher_.

   >[!INFO]
   >
   >Wenn Sie eine Basis-URL für die Bereitstellung von Adobe Commerce in der Cloud-Infrastruktur einrichten, müssen Sie den ersten Punkt durch drei Bindestriche ersetzen. Wenn Ihre Basis-URL beispielsweise `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` ist, geben Sie `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` ein. Wenn Sie eine Basis-URL für lokale Tests einrichten, verwenden Sie einen Punkt.

1. Klicken Sie **Konfiguration speichern**.

1. Wiederholen Sie diese Aufgaben für andere Websites.

## Schritt 6: Hinzufügen des Store-Codes zur Basis-URL

Commerce bietet Ihnen die Möglichkeit, den Store-Code zur Site-Basis-URL hinzuzufügen, was die Einrichtung mehrerer Stores vereinfacht. Mit dieser Option müssen Sie keine Ordner im Commerce-Dateisystem erstellen, um `index.php` und `.htaccess` zu speichern.

Dadurch wird verhindert, dass `index.php` und `.htaccess` bei zukünftigen Upgrades nicht mehr mit der Commerce-Code-Basis synchronisiert werden.

Siehe [Commerce-Benutzerhandbuch](https://experienceleague.adobe.com/de/docs/commerce-admin/stores-sales/site-store/store-urls).

So fügen Sie den Store-Code zur Basis-URL hinzu:

1. Klicken Sie im Bedienfeld _Admin_ auf **Stores** > **Settings** > **Configuration** > **General** > **Web**.
1. Klicken Sie in der **Store** Ansicht“ oben auf der Seite auf **Standardkonfiguration** wie in der folgenden Abbildung dargestellt.

   ![Wählen Sie den Standardkonfigurationsbereich aus](../../assets/configuration/multi-site-default.png)

1. Erweitern Sie im rechten Bereich **URL-Optionen**.
1. Deaktivieren Sie das **Systemwert verwenden** neben _Store-Code zu URLs hinzufügen_.
1. Klicken Sie in der _Store-Code zu URLs hinzufügen_ auf **Ja**.

   ![Fügen Sie den Store-Code zur Store-Basis-URL hinzu](../../assets/configuration/multi-site-add-store-url.png)

1. Klicken Sie **Konfiguration speichern**.
1. Leeren Sie den Cache, wenn Sie dazu aufgefordert werden. (**System** > **Cache-**).

## Schritt 7: Ändern der Standard-URL für die Store-Ansicht

Sie müssen diesen letzten Schritt ausführen, da Sie den Zugriff auf den Administrator verlieren. Ihr Zugriff wird nach dem Einrichten virtueller Hosts wie in den Webserver-spezifischen Themen beschrieben zurückgegeben.

So ändern Sie die Standard-URL der Store-Ansicht:

1. Klicken Sie im Bedienfeld _Admin_ auf **Stores** > **Settings** > **Configuration** > **General** > **Web**.

1. Klicken Sie in der _Store-_&quot; oben auf der Seite auf **Standardkonfiguration**.

   ![Wählen Sie den Standardkonfigurationsbereich aus](../../assets/configuration/multi-site-default.png)

1. Erweitern Sie im rechten Bereich **Basis-URLs**.
1. Deaktivieren Sie _Abschnitt_ Basis-URLs **die Option „Systemwert**.
1. Geben Sie die `http://magento.mg`-URL in die Felder **Basis-**) und **Basis-Link-**) ein.

1. Wiederholen Sie den vorherigen Schritt im Abschnitt **Basis-URLs (sicher**.

   >[!INFO]
   >
   >Wenn Sie eine Basis-URL für Adobe Commerce in der Cloud-Infrastruktur einrichten, müssen Sie den ersten Punkt durch drei Bindestriche ersetzen. Wenn Ihre Basis-URL beispielsweise `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` ist, geben Sie `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` ein.

1. Klicken Sie **Konfiguration speichern**.

>[!INFO]
>
>Der Code der Website-, Store- und Store-Ansicht kann nur Buchstaben (a-z oder A-Z), Zahlen (0-9) und Unterstriche (_) enthalten. Außerdem muss das erste Zeichen ein Buchstabe sein. Wenn Groß- oder Kleinschreibung verwendet wird, wird die Groß-/Kleinschreibung bei der Übereinstimmung intern nicht beachtet, um das Überschreiben von Konfigurationseinstellungen durch Umgebungsvariablen zu ermöglichen. Siehe [Verwenden von Umgebungsvariablen zum Überschreiben der Konfigurationseinstellungen](../reference/override-config-settings.md#environment-variables).