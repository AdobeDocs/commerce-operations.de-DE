---
title: 'MDVA-39181: Verwandte Produktregeln zeigen Produkte aus Kategorien an, die in der Regel nicht definiert sind'
description: Der Patch MDVA-39181 behebt das Problem, dass verwandte Produktregeln Produkte aus einer Kategorie zeigen, die in der Regel nicht definiert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-39181. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Categories, Products
role: Admin
exl-id: 98f65b7d-2cb3-49ff-95ef-c23a922e49f2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-39181: Verwandte Produktregeln zeigen Produkte aus Kategorien an, die in der Regel nicht definiert sind

Der Patch MDVA-39181 behebt das Problem, dass verwandte Produktregeln Produkte aus einer Kategorie zeigen, die in der Regel nicht definiert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-39181. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Zugehörige Produktregeln zeigen Produkte aus Kategorien an, die nicht in der Regel definiert sind.

<u>Voraussetzungen</u>:

Beispieldaten installieren.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Attributmarke und fügen Sie sie dem **Tops-Attributsatz** hinzu.
1. Wählen Sie **Josie**, **Augusta** und **Ingrid** Jackets aus, die der Marke Kitty von **Women** > **Tops** > **Jackets-Kategorie** hinzugefügt werden sollen.
1. Wählen Sie die Jacken **Beaumont**, **Hyperion** und **Kenobi** aus, um sie der Marke Kitty von **Men** > **Tops** > **Jacket category** hinzuzufügen.
1. Erstellen Sie ein verwandtes Produkt mit:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Produkte, die übereinstimmen:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Anzuzeigende Produkte:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Öffnen Sie SKU WJ04 vom Frontend und prüfen Sie die entsprechenden Produkte.
1. Aktualisieren Sie die Kategorie-ID von **Frauen** > **Tops** > **Jackets** , falls sie sich von dieser unterscheidet.

<u>Erwartete Ergebnisse</u>:

In verwandten Produkten werden nur Produkte derselben Marke und derselben untergeordneten Kategorie angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Zugehörige Produkte werden von derselben Marke, aber von einer zufälligen übergeordneten Kategorie angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
