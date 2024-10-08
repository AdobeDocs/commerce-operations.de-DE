---
title: "MDVA-42584: Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert"
description: Der Patch MDVA-42584 behebt das Problem, dass der Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert wird, wenn sein einfaches Produkt aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42584. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-42584: Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert

Der Patch MDVA-42584 behebt das Problem, dass der Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert wird, wenn sein einfaches Produkt aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42584. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Lagerstatus des konfigurierbaren Produkts im Backend wird nicht automatisch aktualisiert, wenn sein einfaches Produkt über API oder Import auf **Auf Lager** gesetzt ist.

<u>Voraussetzungen</u>:

MSI installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt, **InvCheck001**, mit zwei Optionen: **InvCheck001-M** und **InvCheck001-L**.
1. Beide einfachen Produkte sollten eine Menge aufweisen und **Auf Lager** sein, sodass das konfigurierbare Produkt auch im Backend **Auf Lager** ist.
1. Aktualisieren Sie jetzt beide einfachen Produkte und legen Sie &quot;Menge&quot;auf &quot;**0**&quot;und &quot;Lagerstatus&quot;auf &quot;**Nicht auf Lager**&quot;fest.
1. Aktualisieren Sie das konfigurierbare Produkt und überprüfen Sie, ob der Lagerstatus auf **Nicht auf Lager** aktualisiert wurde.
1. Verwenden Sie den folgenden API-Endpunkt und setzen Sie das einfache Produkt **InvCheck01-M** auf **Auf Lager** mit Menge > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Gehen Sie zum Backend und überprüfen Sie die Menge und den Lagerstatus des einfachen Produkts **InvCheck001-M**. Sie wird auf **Auf Lager** aktualisiert.
1. Aktualisieren Sie das konfigurierbare Produkt und überprüfen Sie den Lagerstatus.

<u>Erwartete Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts **InvCheck001** im Backend wird automatisch auf **In Stock** aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts ist immer noch **nicht auf Lager**.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
