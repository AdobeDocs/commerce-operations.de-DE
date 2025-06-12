---
title: 'ACSD-51230: Geschenkkartenkonto wird gelöscht'
description: Wenden Sie den Patch ACSD-51230 an, um das Adobe Commerce-Problem zu beheben, bei dem das Geschenkkartenkonto gelöscht wird, wenn die teilweise Rückerstattung eines einfachen Produkts aus einer Bestellung verarbeitet wird.
feature: Customer Service, Gift, Marketing Tools
role: Admin
exl-id: a4aed574-3908-42e0-ac32-911f61b44995
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-51230: Geschenkkartenkonto wird gelöscht

Der Patch ACSD-51230 behebt das Problem, dass das Geschenkkartenkonto gelöscht wird, wenn die teilweise Rückerstattung eines einfachen Produkts aus einer Bestellung verarbeitet wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51230. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Geschenkgutscheinkonto wird gelöscht, wenn die teilweise Rückerstattung eines einfachen Produkts aus einer Bestellung verarbeitet wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Bestellung mit einer *Geschenkkarte* und einem *einfachen Produkt* (z. B. *hinzufügen: SKU: GI000XX000XXX PC046CP042076, SKU:*) - (alle Zahlungs- und Versandmethoden funktionieren).
1. Rechnung der Bestellung.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Für die Geschenkkarte wird ein Konto erstellt.
1. Wechseln Sie jetzt zu **[!UICONTROL Order]** und erstellen Sie eine **[!UICONTROL Credit Memo]**.
1. Ändern Sie die Menge für die *Geschenkkarte* auf 0 und aktualisieren Sie sie. Dies führt zu einer teilweisen Rückerstattung für das *einfache Produkt*.
1. Klicken Sie auf **[!UICONTROL Refund]**.
1. Aktualisieren Sie nun die **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Das neu erstellte Konto wird gelöscht.

<u>Erwartete Ergebnisse</u>

Das Geschenkkartenkonto kann verwendet werden, da die Rückerstattung für die Geschenkkarte nicht erstellt wurde.

<u>Tatsächliche Ergebnisse</u>

Das Geschenkkartenkonto wird gelöscht und die Geschenkkarte wird nicht zurückerstattet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
