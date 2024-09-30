---
title: "ACSD-48058: Neuindizierung des Produktpreises funktioniert nicht, wenn einem gebündelten Produkt keine Website zugewiesen wurde"
description: Wenden Sie den Patch ACSD-48058 an, um das Adobe Commerce-Problem zu beheben, bei dem die Neuindizierung des Produktpreises nicht funktioniert, wenn das gebündelte Produkt keiner Website zugewiesen ist.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48058: Neuindizierung des Produktpreises funktioniert nicht, wenn einem gebündelten Produkt keine Website zugewiesen wurde

Der Patch ACSD-48058 behebt das Problem, dass die Neuindizierung des Produktpreises nicht funktioniert, wenn das gebündelte Produkt keiner Website zugewiesen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID lautet ACSD-48058. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Neuindizierung des Produktpreises funktioniert nicht, wenn das gebündelte Produkt keiner Website zugewiesen ist.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie ein neues gebündeltes Produkt oder bearbeiten Sie ein vorhandenes gebündeltes Produkt.
   * Klicken Sie auf die Registerkarte **[!UICONTROL Product in Websites]** und deaktivieren Sie alle Kontrollkästchen (Websites).
   * Produkt speichern
1. Führen Sie eine Neuindizierung durch.

<u>Erwartete Ergebnisse</u>:

Die Neuindizierung wurde erfolgreich durchgeführt.

<u>Tatsächliche Ergebnisse</u>:

Beim Ausführen des Produktpreisindex wird der folgende Fehler ausgegeben:

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
