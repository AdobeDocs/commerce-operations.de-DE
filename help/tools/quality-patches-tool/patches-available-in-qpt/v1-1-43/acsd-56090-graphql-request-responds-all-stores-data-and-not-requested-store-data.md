---
title: "ACSD-56090: GraphQL-Antwort ist nicht speicherspezifisch"
description: Wenden Sie den Patch ACSD-56090 an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Antwort alle Speicherdaten anstelle der Store-spezifischen Daten enthält.
feature: GraphQL
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-56090: GraphQL-Antwort ist nicht speicherspezifisch

Der Patch ACSD-56090 behebt das Problem, dass die GraphQL-Antwort alle Speicherdaten anstelle der Store-spezifischen Daten enthält. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-56090. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Antwort enthält alle Speicherdaten anstelle der Store-spezifischen Daten.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** an und erstellen Sie zwei Stammkategorien.
1. Jede Stammkategorie sollte eine Unterkategorie aufweisen.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL All stores]** > Zwei Stores existieren mit unterschiedlichen Stammkategorien für jeden von ihnen. (Jeder Speicher sollte mindestens eine Store-Ansicht haben.)
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Erstellen eines Produkts mit

* Alle zugewiesenen Stamm- und Unterkategorien
* Alle zugewiesenen Websites.

1. Führen Sie die GraphqQL-Abfrage aus (add header — store = &#39;storename ):

```
   query {
     products(filter: { url_key: { eq: "abc" } }) {
       items {
         categories {
           name
           id
           url_path
           breadcrumbs {
             category_id
             category_name
             category_level
           }
         }
       }
     }
   }
```

1. Überprüfen Sie die Antwort nach der Ausführung der GraphqQL-Abfrage.

<u>Erwartete Ergebnisse</u>:

Die Store-spezifischen Daten werden zurückgegeben

<u>Tatsächliche Ergebnisse</u>:

Die zurückgegebenen Daten sind nicht speicherspezifisch.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
