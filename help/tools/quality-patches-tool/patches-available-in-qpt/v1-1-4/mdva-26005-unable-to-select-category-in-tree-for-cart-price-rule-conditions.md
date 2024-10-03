---
title: "MDVA-26005: Die Kategorie im Baum kann nicht für die Regelbedingungen für den Warenkorbpreis ausgewählt werden."
description: Der Patch MDVA-26005 behebt das Problem, dass Benutzer keine Kategorie in der Kategoriestruktur für die Regelbedingungen des Warenkorbs auswählen können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-26005. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.
feature: Categories, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-26005: Kategorie im Baum kann nicht für Regelbedingungen zum Warenkorbpreis ausgewählt werden

Der Patch MDVA-26005 behebt das Problem, dass Benutzer keine Kategorie in der Kategoriestruktur für die Regelbedingungen des Warenkorbs auswählen können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-26005. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es kann keine Kategorie in der Kategoriestruktur für die Regelbedingungen für den Warenkorbpreis ausgewählt werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue oder bearbeiten Sie eine vorhandene Regel zum Warenkorbpreis.
1. Wählen Sie im Abschnitt Aktion die Kategorie unter Bedingung aus.
1. Rendern Sie den Kategoriebaum und versuchen Sie, eine Kategorie auszuwählen.

<u>Erwartete Ergebnisse</u>:

Sie können eine Kategorie auswählen.

<u>Tatsächliche Ergebnisse</u>:

Sie können aufgrund eines JS-Fehlers keine Kategorie auswählen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.