---
title: Mehrere Websites oder Stores
description: Erfahren Sie, wie Sie mehrere Websites starten oder Store-Ansichten mit verschiedenen Optionen, Domains und Inhalten implementieren können.
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Mehrere Websites oder Stores

Eine einzige Instanz der Adobe Commerce-Software ermöglicht es Ihnen, mehrere Websites zu starten oder Ansichten zu speichern, die unterschiedliche Attribute und Inhalte verwenden, z. B.:

- Standardsprachen
- Domain-Namen
- Kategorien
- PRODUCT
- Währungen

Diese flexible Lösung ermöglicht es einer Commerce-Codebasis und einem Administrator, verschiedene Stores zu verwalten und anzuzeigen. Sie konfigurieren die Websites, Stores und Store-Ansichten im Admin-Bereich. Verwenden Sie bestimmte Variablen in virtuellen Hosts, um die Commerce-Anwendung mithilfe dieser Websites oder Store-Ansichten zu starten.

Eine typische Verwendung besteht darin, Stores mit verschiedenen Optionen in verschiedenen Domains einzurichten. Beispielsweise könnten Sie einen Satz von Kategorien und Produkten in einer Domain und einen anderen Satz von Kategorien und Produkten in einer separaten Domain in einer anderen Sprache haben.

Sie konfigurieren die Websites, Stores und Store-Ansichten in Commerce Admin. Verwenden Sie die Variablen `MAGE_RUN_TYPE` und `MAGE_RUN_CODE` in virtuellen Hosts, um die Commerce-Anwendung mithilfe dieser Websites oder Store-Ansichten zu starten.

Betrachten Sie die folgenden Begriffe:

- **Website** - ist der Container der obersten Ebene für Sites, Versandmethoden, Zahlungsmethoden und mehr. Um vollständig separate Websites zu erstellen, die keinen Warenkorb, keine Versandmethoden oder andere freigeben, müssen Sie separate Websites erstellen.

  Website-Kundenkonten können von mehreren Websites innerhalb einer Commerce-Instanz gemeinsam genutzt werden. Eine Website enthält mindestens einen Store. Katalogpreise sollten auf der Ebene der Website verwaltet werden.

- **Store** - ist in einer Website enthalten. Umgekehrt enthält ein Store mindestens eine *Store-Ansicht*.

  Mehrere Stores können Warenkorb, Benutzersitzungen, Zahlungs-Gateways und mehr teilen, aber sie haben separate Katalogstrukturen und Katalogpreise.

  Katalogmenge (Inventar) kann nicht auf Store-Ebene verwaltet werden. Inventar wird nur auf Website- oder globaler Ebene verwaltet.

  Shop-Ansichten ändern die Darstellung von Seiten und werden normalerweise verwendet, um einen Shop mit unterschiedlichen Layouts oder Sprachen anzuzeigen. Sie können verschiedene Währungen pro Shop-Ansicht verwalten.

  Jede Website und jede Shop-Ansicht muss über eine eindeutige Kennung verfügen. Diese Kennung ist erforderlich, um die Variablen `MAGE_RUN_TYPE` und `MAGE_RUN_CODE` wie folgt zu verwenden:

- `MAGE_RUN_TYPE` kann entweder `store` oder `website` sein

   - Verwenden Sie `website` , um eine Website in Ihre Storefront zu laden.
   - Verwenden Sie `store`, um eine beliebige Store-Ansicht in Ihre Storefront zu laden.

- `MAGE_RUN_CODE` ist der eindeutige Website- oder Store-Ansichts-Code, der `MAGE_RUN_TYPE` entspricht

Im Folgenden finden Sie eine Zusammenfassung der Aufgaben, die Sie ausführen müssen:

1. [Einrichten von Websites, Stores und Store-Ansichten in Admin.](ms-admin.md)
1. Erstellen Sie einen virtuellen Host, um viele Websites zu laden, oder einen virtuellen Host pro Commerce-Website oder Store-Ansicht, um spezifische Anweisungen für jeden Store zuzulassen.
1. Übergeben Sie die Werte von `MAGE_RUN_TYPE` und `MAGE_RUN_CODE` an den Webserver.
