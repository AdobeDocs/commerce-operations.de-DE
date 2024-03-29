---
title: Einrichten mehrerer Websites, Stores und Speichern von Ansichten im Admin
description: Konfigurieren Sie zusätzliche Websites, Stores und Store-Ansichten im Commerce Admin.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: f7c82844fd6d006e4ebbcf56f6e10338f67d0bdd
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---

# Mehrere Ansichten in der Admin-Konsole einrichten

Für diese Aufgabe müssen Sie für jeden Store eine Stammkategorie (und ggf. zusätzliche Kategorien) erstellen. Die in diesem Thema behandelten Aufgaben bieten eine Möglichkeit, mehrere Stores einzurichten. Weitere Informationen finden Sie in den folgenden Ressourcen im Commerce-Benutzerhandbuch:

- [Kategorien](https://docs.magento.com/user-guide/catalog/categories.html)
- [Hinzufügen von Websites](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Store-URLs](https://docs.magento.com/user-guide/stores/store-urls.html)
- [Inhalt](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>Nur zu Beispielzwecken verwenden wir eine französische Website mit Website-Code `french` in diesem Thema. Schrittweise Tutorials finden Sie unter [Tutorial: Einrichten mehrerer Websites mit Apache](ms-apache.md) und [Tutorial: Einrichten mehrerer Websites mit nginx](ms-nginx.md)

## Schritt 1: Stammkategorien erstellen

Das Erstellen einer Stammkategorie ist optional. Wir zeigen jedoch in diesem Tutorial, wie Sie dies durchführen können, falls Sie möchten, dass jede Website über eine eindeutige Stammkategorie verfügt. Sie können bei Bedarf weitere Kategorien erstellen.

So erstellen Sie eine Stammkategorie:

1. Melden Sie sich bei Admin als Benutzer an, der zur Erstellung von Kategorien berechtigt ist.
1. Klicks **Katalog** > **Kategorien**.
1. Klicks **Stammkategorie hinzufügen**.
1. Im **Kategoriename** eingeben, geben Sie einen eindeutigen Namen ein, um diese Kategorie zu identifizieren.
1. Stellen Sie sicher, dass Kategorie aktivieren auf **Ja**.

   Weitere Informationen zu den anderen Optionen auf dieser Seite finden Sie unter [Stammkategorien](https://docs.magento.com/user-guide/catalog/category-root.html).

   Die folgende Abbildung zeigt ein Beispiel.

   ![Erstellen und Aktivieren einer Stammkategorie](../../assets/configuration/add-root-category.png)

1. Klicks **Speichern**.
1. Wiederholen Sie diese Schritte so oft wie nötig, um Stammkategorien für Ihre Geschäfte zu erstellen.

## Schritt 2: Erstellen von Websites

So erstellen Sie eine Website:

1. Melden Sie sich bei Admin als Benutzer an, der zum Erstellen von Websites, Geschäften und Store-Ansichten berechtigt ist.
1. Klicks **Stores** > **Einstellungen** > **Alle Stores**.
1. Im _Stores_ Seite, klicken **Website erstellen**.

   - **Name**- Geben Sie einen Namen ein, um die Website zu identifizieren.
   - **Code**—Geben Sie einen eindeutigen Code ein. Wenn Sie beispielsweise einen französischen Store haben, können Sie `french`
   - **Sortierfolge**—Geben Sie eine optionale numerische Sortierreihenfolge ein.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Website hinzufügen](../../assets/configuration/multi-site-website.png)

1. Klicks **Website-Speicherung**.
1. Wiederholen Sie diese Schritte so oft wie nötig, um Ihre Websites zu erstellen.

## Schritt 3: Stores erstellen

So erstellen Sie einen Store:

1. Im _Admin_ Bereich, klicken Sie **Stores** > **Einstellungen** > **Alle Stores**.
1. Im _Stores_ Seite, klicken **Store erstellen**.

   - **Internetseite**—Klicken Sie auf den Namen der Website, mit der dieser Store verbunden werden soll.
   - **Name**—Geben Sie einen Namen ein, um den Store zu identifizieren.
   - **Code**- Geben Sie einen eindeutigen Code ein, um den Store zu identifizieren.
   - **Stammkategorie**—Klicken Sie auf den Namen der Stammkategorie für diesen Store.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Store hinzufügen](../../assets/configuration/multi-site-store.png)

1. Klicks **Store speichern**.
1. Wiederholen Sie diese Schritte so oft wie nötig, um Ihre Stores zu erstellen.

## Schritt 4: Erstellen von Store-Ansichten

So erstellen Sie eine Store-Ansicht:

1. Im _Admin_ Bereich, klicken Sie **Stores** > **Einstellungen** > **Alle Stores**.
1. Klicken Sie auf der Seite Stores auf **Store-Ansicht erstellen**.

   - **Store**—Klicken Sie auf den Namen des Stores, mit dem diese Store-Ansicht verknüpft werden soll.
   - **Name**—Geben Sie einen Namen ein, um diese Store-Ansicht zu identifizieren.
   - **Code**—Geben Sie einen eindeutigen Namen ein, um diese Store-Ansicht zu identifizieren.
   - **Status**—select **Aktiviert**.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Store hinzufügen](../../assets/configuration/multi-site-storeview.png)

1. Klicks **Speicheransicht**.
1. Wiederholen Sie diese Aufgaben so oft wie nötig, um Ihre Store-Ansichten zu erstellen.

## Schritt 5: Ändern der URL der Website-Basis

Für den Zugriff auf eine Website mithilfe einer eindeutigen URL wie `http://french.magento.mg`müssen Sie die Basis-URL für jede Website im Admin ändern.

So ändern Sie die URL der Website-Basis:

1. Im _Admin_ Bereich, klicken Sie **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Web**.
1. Aus dem **Store-Ansicht** Klicken Sie oben auf der Seite auf den Namen einer Ihrer Websites, wie in der folgenden Abbildung dargestellt.

   ![Perimeter auswählen](../../assets/configuration/multi-site-scope.png)

1. Erweitern Sie im rechten Bereich **Basis-URLs**.
1. Im _Basis-URLs_ Abschnitt löschen **Systemwert verwenden**.
1. Geben Sie die `http://french.magento.mg` URL in der **Basis-URL** und **Base Link URL** -Felder.

1. Wiederholen Sie den vorherigen Schritt im _Basis-URLs (sicher)_ Abschnitt.

   >[!INFO]
   >
   >Wenn Sie eine Basis-URL für die Bereitstellung von Adobe Commerce in der Cloud-Infrastruktur einrichten, müssen Sie den ersten Punkt durch drei Bindestriche ersetzen. Wenn Ihre Basis-URL beispielsweise `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, eingeben `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Wenn Sie eine Basis-URL für lokale Tests einrichten, verwenden Sie einen Punkt.

1. Klicks **Konfiguration speichern**.

1. Wiederholen Sie diese Schritte für andere Websites.

## Schritt 6: Hinzufügen des Store-Codes zur Basis-URL

Commerce bietet Ihnen die Möglichkeit, den Store-Code zur Site-Basis-URL hinzuzufügen, was die Einrichtung mehrerer Stores vereinfacht. Mit dieser Option müssen Sie keine Ordner im Commerce-Dateisystem erstellen, um sie zu speichern `index.php` und `.htaccess`.

Dies verhindert `index.php` und `.htaccess` bei zukünftigen Upgrades nicht mehr mit der Commerce-Codebase synchronisiert werden.

Siehe [Benutzerhandbuch für Commerce](https://docs.magento.com/user-guide/stores/store-urls.html).

So fügen Sie den Store-Code zur Basis-URL hinzu:

1. Im _Admin_ Bereich, klicken Sie **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Web**.
1. Aus dem **Store-Ansicht** Liste oben auf der Seite klicken Sie auf **Standardkonfiguration** wie in der folgenden Abbildung dargestellt.

   ![Standardkonfigurationsperimeter auswählen](../../assets/configuration/multi-site-default.png)

1. Erweitern Sie im rechten Bereich **URL-Optionen**.
1. Löschen Sie die **Systemwert verwenden** Kontrollkästchen neben _Hinzufügen von Store-Code zu URLs_.
1. Aus dem _Hinzufügen von Store-Code zu URLs_ Liste, klicken Sie **Ja**.

   ![Fügen Sie den Store-Code zur Store-Basis-URL hinzu.](../../assets/configuration/multi-site-add-store-url.png)

1. Klicks **Konfiguration speichern**.
1. Wenn Sie dazu aufgefordert werden, leeren Sie den Cache. (**System** > **Cacheverwaltung**).

## Schritt 7: Ändern der Standard-URL für die Store-Ansichtsbasis

Sie müssen diesen Schritt zuletzt ausführen, da Sie den Zugriff auf den Administrator verlieren. Ihr Zugriff wird zurückgegeben, nachdem Sie virtuelle Hosts eingerichtet haben, wie in den Web-Server-spezifischen Themen beschrieben.

So ändern Sie die Standard-URL der Store-Ansichtsbasis:

1. Im _Admin_ Bereich, klicken Sie **Stores** > **Einstellungen** > **Konfiguration** > **Allgemein** > **Web**.

1. Aus dem _Store-Ansicht_ Liste oben auf der Seite klicken Sie auf **Standardkonfiguration**.

   ![Standardkonfigurationsperimeter auswählen](../../assets/configuration/multi-site-default.png)

1. Erweitern Sie im rechten Bereich **Basis-URLs**.
1. Im _Basis-URLs_ Abschnitt löschen **Systemwert verwenden**.
1. Geben Sie die `http://magento.mg` URL in der **Basis-URL** und **Base Link URL** -Felder.

1. Wiederholen Sie den vorherigen Schritt im **Basis-URLs (sicher)** Abschnitt.

   >[!INFO]
   >
   >Wenn Sie eine Basis-URL für Adobe Commerce in der Cloud-Infrastruktur einrichten, müssen Sie den ersten Punkt durch drei Bindestriche ersetzen. Wenn Ihre Basis-URL beispielsweise `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, eingeben `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Klicks **Konfiguration speichern**.

>[!INFO]
>
>Der Code für die Website-, Store- und Store-Ansicht kann nur Buchstaben (a-z oder A-Z), Zahlen (0-9) und Unterstriche (_) enthalten. Außerdem muss das erste Zeichen ein Brief sein. Wenn Groß- oder Kleinschreibung verwendet wird, wird bei der Übereinstimmung intern nicht zwischen Groß- und Kleinschreibung unterschieden, damit Konfigurationseinstellungen über Umgebungsvariablen außer Kraft gesetzt werden können. Siehe [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](../reference/override-config-settings.md#environment-variables).