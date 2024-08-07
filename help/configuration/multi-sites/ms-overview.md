---
title: Mehrere Websites oder Stores
description: Erfahren Sie, wie Sie mehrere Websites starten oder Store-Ansichten mit verschiedenen Optionen, Domänen und Inhalten implementieren können.
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Mehrere Websites oder Stores

Mit einer einzelnen Instanz der Adobe Commerce-Software können Sie mehrere Websites starten oder Ansichten speichern, die unterschiedliche Attribute und Inhalte verwenden, z. B.:

- Standardsprachen
- Domänennamen
- Kategorien
- Produkte
- Währungen

Diese flexible Lösung ermöglicht es einer Commerce-Codebasis und einem Administrator, verschiedene Stores zu verwalten und anzuzeigen. Sie konfigurieren die Websites, Stores und speichern Ansichten in der Admin-Konsole. Verwenden Sie bestimmte Variablen in virtuellen Hosts, um die Commerce-Anwendung mit diesen Websites zu starten oder Ansichten zu speichern.

Eine typische Verwendung besteht darin, Stores mit verschiedenen Optionen in verschiedenen Domänen einzurichten. Sie könnten beispielsweise eine Gruppe von Kategorien und Produkten auf einer Domäne und eine andere Gruppe von Kategorien und Produkten auf einer separaten Domäne in einer anderen Sprache haben.

Sie konfigurieren die Websites, Stores und speichern Ansichten im Commerce Admin. Verwenden Sie die Variablen `MAGE_RUN_TYPE` und `MAGE_RUN_CODE` in virtuellen Hosts, um die Commerce-Anwendung mit diesen Websites oder Store-Ansichten zu starten.

Beachten Sie die folgenden Begriffe:

- **Website** - ist der Container auf oberster Ebene für Sites, Bereitstellungsmethoden, Zahlungsmethoden und mehr. Um vollständig separate Sites zu erstellen, die keinen Warenkorb, keine Versandmethoden oder andere verwenden, müssen Sie separate Websites erstellen.

  Website-Kundenkonten können auf mehreren Websites innerhalb einer einzelnen Commerce-Instanz freigegeben werden. Eine Website enthält mindestens einen Store. Die Katalogpreise sollten auf Website-Ebene verwaltet werden.

- **Store**: ist auf einer Website enthalten. Ein Store wiederum enthält mindestens eine *Store-Ansicht*.

  Mehrere Stores können Warenkorb, Benutzersitzungen, Zahlungskanäle und mehr gemeinsam nutzen, sie verfügen jedoch über separate Katalogstrukturen und einen separaten Katalogpreis.

  Katalogmenge (Inventar) kann nicht auf der Store-Ebene verwaltet werden. Das Inventar wird nur auf Website- oder globaler Ebene verwaltet.

  Store-Ansichten ändern die Darstellung von Seiten und werden normalerweise verwendet, um einen Store mit verschiedenen Layouts oder Sprachen anzuzeigen. Sie können verschiedene Währungen pro Store-Ansicht verwalten.

  Jede Website und jede Store-Ansicht muss über eine eindeutige Kennung verfügen. Diese Kennung ist erforderlich, um die Variablen `MAGE_RUN_TYPE` und `MAGE_RUN_CODE` wie folgt zu verwenden:

- `MAGE_RUN_TYPE` kann entweder `store` oder `website` sein

   - Verwenden Sie `website` , um eine Website in Ihre Storefront zu laden.
   - Verwenden Sie `store` , um eine beliebige Store-Ansicht in Ihre Storefront zu laden.

- `MAGE_RUN_CODE` ist der eindeutige Website- oder Store-Ansichtscode, der `MAGE_RUN_TYPE` entspricht.

Im Folgenden finden Sie eine Zusammenfassung der Aufgaben, die Sie ausführen müssen:

1. [Richten Sie Websites, Stores und Ansichten in der Admin-Konsole ein.](ms-admin.md)
1. Erstellen Sie einen virtuellen Host, um viele Websites oder einen virtuellen Host pro Commerce-Website oder Store-Ansicht zu laden, um bestimmte Anweisungen für jeden Store zuzulassen.
1. Übergeben Sie die Werte `MAGE_RUN_TYPE` und `MAGE_RUN_CODE` an den Webserver.
