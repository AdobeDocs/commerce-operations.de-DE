---
title: 'ACSD-51884: Pfad des Produktbild-Caches beim Größenänderungsbefehl falsch'
description: Wenden Sie den Patch ACSD-51884 an, um das Adobe Commerce-Problem zu beheben, bei dem der Cache-Pfad für das Produktbild nach dem Ausführen des Befehls zum Ändern der Größe falsch wird.
feature: Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-51884: Cache-Pfad des Produktbilds beim Größenbefehl falsch

Der Patch ACSD-51884 behebt das Problem, bei dem ein interner Fehler auftritt, bei dem der Cache-Pfad des Produktbilds nach der Ausführung des Befehls zur Größenanpassung falsch wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-51884. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Cache-Pfad des Produktbilds wird beim Befehl zum Ändern der Größe falsch angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website/einen neuen Store/eine neue Storeinstanz.
1. Erstellen Sie ein Produkt, weisen Sie es beiden Websites zu und laden Sie das Produktbild hoch.
1. Erstellen Sie ein neues Design (siehe angehängte Adobe.zip).
1. Ändern Sie in `app/design/Adobe/theme/etc/view.xml`:

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

nach

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Wenden Sie das Design auf den zuvor erstellten Store an.
1. Überprüfen Sie die Produktseite auf der zweiten Website. Das Produktbild wird korrekt angezeigt.
1. Leeren-Cache verwenden:
   `bin/magento cache:flush`
1. Überprüfen Sie die Produktseite auf der zweiten Website.

<u>Erwartete Ergebnisse</u>:

Das Produktbild wird korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produktbild ist nicht vorhanden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
