---
title: "ACSD-52657: Minicart wird im zweiten Speicher, der Subdomain verwendet, nicht aktualisiert."
description: Wenden Sie den Patch ACSD-52657 an, um das Adobe Commerce-Problem zu beheben, bei dem der Minicart beim zweiten Store, der eine Subdomain verwendet, nicht aktualisiert wird.
feature: Shopping Cart
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-52657: Minicart wird beim zweiten Store, der die Subdomain verwendet, nicht aktualisiert

Der Patch ACSD-52657 behebt das Problem, bei dem der Minicart im zweiten Speicher, der eine Subdomain verwendet, nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-52657. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Minicart wird im sekundären Speicher, der eine Subdomain verwendet, nicht aktualisiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen zweiten Store und konfigurieren Sie eine Subdomain für die Basis-URL.
1. Aktualisieren Sie die Cookie-Domäne auf die allgemeine Domäne.
1. Fügen Sie im Hauptspeicher ein Produkt zum Warenkorb hinzu.
1. Aktualisieren Sie den zweiten Storebericht und navigieren Sie dann zur Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb und der Minicart werden in der Subdomain aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Minicart wird nicht aktualisiert, wenn der sekundäre Store aktualisiert wird, aber die Warenkorbseite zeigt das hinzugefügte Produkt an und Sie können in dieser Sitzung eine Bestellung aufgeben (`PHPSESSID` -Cookie wird freigegeben).

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
