---
title: 'MDVA-39195: "Zum Warenkorb hinzufügen"ist auf Kategorieseite inaktiv'
description: Der Patch MDVA-39195 behebt das Problem, dass die Schaltfläche "Zum Warenkorb hinzufügen"auf der Kategorieseite inaktiv ist, wenn die Umleitung zum Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39195. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: Categories, Orders, Shopping Cart
role: Admin
exl-id: 2c391f54-3b9e-4e72-944b-b003e4ade9b9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-39195: &quot;Zum Warenkorb hinzufügen&quot;ist auf Kategorieseite inaktiv

Der Patch MDVA-39195 behebt das Problem, dass die Schaltfläche **Zum Warenkorb hinzufügen** auf der Kategorieseite inaktiv ist, wenn die Umleitung zum Warenkorb aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39195. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Schaltfläche **Zum Warenkorb hinzufügen** ist auf der Kategorieseite inaktiv, wenn die Umleitung zum Warenkorb aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > Einstellungen > **Konfiguration** > **Verkauf** > **Checkout**.
1. Erweitern Sie den Abschnitt **Warenkorb** .
1. Setzen Sie die **nach dem Hinzufügen einer Produktumleitung zum Warenkorb** auf &quot;Ja&quot;.
1. Besuchen Sie die Seite Kategorie .

<u>Erwartete Ergebnisse</u>:

**Zum Warenkorb hinzufügen** ist auf der Kategorieseite aktiv.

<u>Tatsächliche Ergebnisse</u>:

Die Schaltfläche **Zum Warenkorb hinzufügen** ist auf der Kategorieseite inaktiv.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
