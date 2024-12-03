---
title: 'MDVA-27239: Querverkaufsprodukte werden nicht angezeigt'
description: Der Patch MDVA-27239 behebt das Problem, dass Crosssell-Produkte nicht angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.
feature: Products
role: Admin
exl-id: ab8fe64d-adbe-4756-be43-1a35ba6b4123
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-27239: Querverkaufsprodukte werden nicht angezeigt

Der Patch MDVA-27239 behebt das Problem, dass Crosssell-Produkte nicht angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4, 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Cross-Sell-Produkte werden nicht im Querverkaufsblock auf der Warenkorbseite angezeigt.

<u>Voraussetzungen</u>:

1. Deaktivieren Sie das Magento_TargetRule-Modul oder entfernen Sie es aus dem Layout-Block Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Produkt erstellen 1.
1. Erstellen Sie ein Planupdate für Produkt 1, sodass die neu erstellten Produkte eine andere Zeile_ID als entity_id aufweisen.
1. Erstellen Sie Produkt 2, Produkt 3 und Produkt 4.
1. Legen Sie Produkt 3 als Crosssell für Produkt 4 fest.
1. Legen Sie Produkt 4 als Crosssell für Produkt 2 fest.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie Produkt 4 und Produkt 2 zum Warenkorb hinzu.
1. Überprüfen Sie die Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Produkt 3 wird in Querverkaufsblöcken angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der Querverkaufsblock ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
