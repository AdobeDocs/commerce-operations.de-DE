---
title: 'ACSD-62979: Eine falsche Store-ID in der GraphQL-Kopfzeile verursacht einen schwerwiegenden Speicherfehler'
description: Wenden Sie den Patch ACSD-62979 an, um das Adobe Commerce-Problem zu beheben, bei dem die Verwendung der falschen Store-ID in der GraphQL-Kopfzeile einen schwerwiegenden Speicherfehler verursacht
feature: GraphQL
role: Admin, Developer
exl-id: 832baae1-34b4-4ca8-bfa9-221aa60da67e
source-git-commit: 187a0056971e6bec324b5cc9d374375bbfb84dd8
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-62979: Eine falsche Store-ID in der GraphQL-Kopfzeile verursacht einen schwerwiegenden Speicherfehler

Der Patch ACSD-62979 behebt das Problem, dass die Verwendung der falschen Store-ID in der GraphQL-Kopfzeile einen schwerwiegenden Speicherfehler verursacht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-62979. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6, 2.4.6-p7, 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es wurde ein Problem behoben, bei dem die Verwendung der falschen Store-ID in der GraphQL-Kopfzeile einen schwerwiegenden Speicherfehler verursachte.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**). **[!UICONTROL Add Store Code to Urls]** aktivieren.
1. Führen Sie unter GraphQL eine Abfrage mit dem falschen Wert für die Store-Kopfzeile aus.

```graphql
{
  categoryList(filters: { ids: { eq: "2" } }) {
    uid
    level
    name
    url_path
    image
    children {
      uid
      level
      name
      url_path
      image
      children {
        uid
        level
        name
        url_path
        image
        children {
          uid
          level
          name
          url_path
          image
        }
      }
    }
  }
}
```

<u>Erwartete Ergebnisse</u>:

Fehlermeldung: „Der angeforderte Store wurde nicht gefunden. Überprüfen Sie den Store und versuchen Sie es erneut.“

<u>Tatsächliche Ergebnisse</u>:

Schwerwiegender Fehler wie:

```Allowed memory size of 792723456 bytes exhausted```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
