---
title: 'MDVA-40601: Es können keine Daten zu einer Kategorie abgerufen werden, die durch eine geplante Aktualisierung über GraphQL geändert wurde.'
description: Der MDVA-40601 Adobe Commerce-Qualitäts-Patch behebt das Problem, dass Benutzer einen Fehler erhalten, wenn sie Informationen über Kategorien erhalten, die durch geplante Aktualisierungen über GraphQL geändert wurden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-40601. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Categories, GraphQL
role: Admin
exl-id: c50e9f77-66eb-4c4c-b0b5-b77db84a4a0b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40601: Es können keine Daten zu einer Kategorie abgerufen werden, die durch eine geplante Aktualisierung über GraphQL geändert wurde.

Der MDVA-40601 Adobe Commerce-Qualitäts-Patch behebt das Problem, dass Benutzer einen Fehler erhalten, wenn sie Informationen über Kategorien erhalten, die durch geplante Aktualisierungen über GraphQL geändert wurden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-40601. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 und 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer erhalten eine Fehlermeldung, wenn sie versuchen, Informationen über Kategorien abzurufen, die durch geplante Aktualisierungen über GraphQL geändert wurden.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie eine Kategoriestruktur mit einer Unterkategorie wie unten gezeigt ein:

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category
   </code>
   </pre>

1. Führen Sie die GraphQL-Abfrage mit der Kennung &quot;Beliebige Kategorie&quot;49 aus.

   <pre>
    <code class="language-graphql">
    query {
     category(id: 49) {
      name
      children {
        name
       }
     }
   }
   </code>
   </pre>

   Ergebnis:

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "category": {
          "name": "Some category",
          "children": [
            {
              "name": "Some child category"
            }
          ]
        }
      }
    }
    </code>
    </pre>

1. Erstellen Sie ein Planupdate für &quot;Some Category&quot;mit einem anderen Kategorienamen.
1. Warten Sie, bis die Aktualisierung des Zeitplans aktiviert wurde.
1. Führen Sie dieselbe Abfrage wie oben beschrieben aus.

<u>Erwartete Ergebnisse</u>:

Sie erhalten dasselbe Ergebnis, jedoch mit dem aktualisierten Kategorienamen.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler:

<pre>
<code class="language-graphql">
{
  "errors": [
    {
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "category"
      ]
    }
  ],
  "data": {
    "category": null
  }
}
</code>
</pre>

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) verfügbare Patches.
