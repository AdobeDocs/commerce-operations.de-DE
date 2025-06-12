---
title: 'ACSD-52657: Minicart wird bei der zweiten Storeview, die die Subdomain verwendet, nicht aktualisiert'
description: Wenden Sie den Patch ACSD-52657 an, um das Adobe Commerce-Problem zu beheben, bei dem das Minicart bei der zweiten Storeview, die eine Subdomain verwendet, nicht aktualisiert wird.
feature: Shopping Cart
role: Admin, Developer
exl-id: feec9dde-5532-481b-9410-7f6be9df4be7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52657: Minicart wird bei der zweiten Storeview, die die Subdomain verwendet, nicht aktualisiert

Mit dem Patch „ACSD-52657“ wird das Problem behoben, dass das Minicart bei der zweiten Storeview, die eine Subdomain verwendet, nicht aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-52657. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Minicart wird im sekundären Store-Review, der eine Subdomain verwendet, nicht aktualisiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zweite Storeview und konfigurieren Sie eine Subdomain für die Basis-URL.
1. Aktualisieren Sie die Cookie-Domain, sodass sie die gemeinsame Domain hat.
1. Fügen Sie im Hauptspeicher ein Produkt zum Warenkorb hinzu.
1. Aktualisieren Sie die zweite Storeview und gehen Sie dann zur Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb und der Minicart werden in der Subdomain aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Minicart wird nicht aktualisiert, wenn der sekundäre Store aktualisiert wird, aber die Warenkorbseite zeigt das hinzugefügte Produkt an, und Sie können eine Bestellung in dieser Sitzung aufgeben (`PHPSESSID` Cookie wird freigegeben).

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
