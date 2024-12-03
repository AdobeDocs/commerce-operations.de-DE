---
title: 'MDVA-43167: Massenaktion des Administrationsnetzwerks gilt nicht für mehrseitige Seiten'
description: Der Patch MDVA-43167 behebt das Problem, dass die Massenaktion des Administrationsnetzwerks nicht für mehrere Seiten gilt, wenn der Admin-Benutzer alle Bestellungen auswählt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-43167. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
feature: Admin Workspace, Orders
role: Admin
exl-id: 992f8a90-300e-41aa-b03d-b8a647dddd51
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-43167: Massenaktion des Administrationsnetzwerks gilt nicht für mehrseitige Seiten

Der Patch MDVA-43167 behebt das Problem, dass die Massenaktion des Administrationsnetzwerks nicht für mehrere Seiten gilt, wenn der Admin-Benutzer alle Bestellungen auswählt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-43167. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Massenaktion der Administrationsreihenfolge gilt nicht für mehrere Seiten, wenn der Admin-Benutzer alle Bestellungen auswählt.

<u>Zu reproduzierende Schritte</u>:

1. Kaufen Sie jedes Produkt dreimal, um drei Bestellungen zu erstellen.
1. Navigieren Sie zu **Raster für Verkaufsaufträge**.
1. Ändern Sie die Paginierung in den benutzerdefinierten Wert 2.
1. Wählen Sie alle aus.
1. Wählen Sie **Massenaktion halten** aus.

<u>Erwartete Ergebnisse</u>:

Alle drei Bestellungen werden ausgesetzt.

<u>Tatsächliche Ergebnisse</u>:

Nur die beiden sichtbaren Bestellungen werden ausgesetzt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
