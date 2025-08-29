---
title: 'ACSD-66302: Artikel auf der Wunschliste, die nach Store-ID statt nach Website gefiltert wurden'
description: Wenden Sie den Patch ACSD-66302 an, um das Adobe Commerce-Problem zu beheben, bei dem Wunschlistenelemente nach Store-ID anstelle von Website- [!DNL GraphQL]  gefiltert werden.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7f9a13a9a8cc666c8aa9d964da8aaff01913d35f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---


# ACSD-66302: Artikel auf der Wunschliste, die nach Store-ID statt nach Website gefiltert wurden

Der Patch ACSD-66302 behebt das Problem, dass Wunschlistenelemente in [!DNL GraphQL]-Anfragen nach Store-ID statt nach Website gefiltert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-66302. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wunschlistenelemente werden fälschlicherweise nach Store-ID statt nach Website gefiltert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie eine zusätzliche Storeview.
1. Gehen Sie in Admin zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]** und setzen Sie **[!UICONTROL Enable Multiple Wish Lists]** auf `Yes`.
1. Gehen Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]** und setzen Sie **[!UICONTROL Add Store Code to Urls]** auf `Yes`.
1. Kundenkonto erstellen.
1. Verwenden Sie eine [!DNL GraphQL] Anfrage, um das Authentifizierungs-Token des Kunden abzurufen.
1. Melden Sie sich als Kunde an.
1. Wählen Sie die **[!UICONTROL Default Store View]** aus und fügen Sie das Produkt zur Wunschliste hinzu.
1. Store-Ansicht zu &quot;*&quot;*.
1. Bestätigen Sie, dass das Produkt weiterhin auf der Wunschliste angezeigt wird (korrektes Verhalten).
1. Führen Sie die folgende [!DNL GraphQL] aus:

```
{
  customer {
    wishlists {
      id
      name
      items_count
      items_v2 {
        items {
          id
          product {
            uid
            name
            sku
          }
        }
      }
    }
  }
}
```

1. Führen Sie die Abfrage im Standardspeicher durch. Das Produkt wird erwartungsgemäß angezeigt.
1. Führen Sie dieselbe Abfrage im Testspeicher aus. Das Produkt wird nicht angezeigt.

<u>Erwartete Ergebnisse</u>:

Das Produkt sollte über [!DNL GraphQL] Abfragen in allen Store-Ansichten innerhalb derselben Website sichtbar sein.

<u>Tatsächliche Ergebnisse</u>:

Produkt verschwindet von der Wunschliste, wenn die Store-Ansichten gewechselt werden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
