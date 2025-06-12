---
title: 'ACSD-50336: E-Mails zu Produktwarnungen werden nicht gesendet'
description: Wenden Sie den Patch ACSD-50336 an, um das Adobe Commerce-Problem zu beheben, bei dem die Benachrichtigungs-E-Mails für das Produkt nicht gesendet werden, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wird.
feature: Communications, Personalization, Products
role: Admin
exl-id: 45dd12af-a3b2-4cfa-be90-af1c7b5f74b3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-50336: E-Mails zu Produktwarnungen werden nicht gesendet

Mit dem Patch ACSD-50336 wird das Problem behoben, dass keine E-Mails zu Warnungen gesendet werden, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-50336. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

E-Mails zu Produktwarnungen werden nicht gesendet, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wird.

<u>Voraussetzungen</u>:

Richten Sie Produktwarnhinweise ein, wenn ein Produkt wieder zum Lager hinzugefügt wird.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Kunde in der Storefront an.
1. Öffnen Sie ein nicht vorrätiges Produkt.
1. Abonnieren Sie eine Benachrichtigung, wenn das Produkt *wieder auf Lager* ist.
1. Aktualisieren Sie das Produkt von [!UICONTROL Admin] auf &quot;_auf Lager_.

<u>Erwartete Ergebnisse</u>:

Eine E-Mail-Benachrichtigung über das Produkt *das wieder auf Lager ist* wird an den Kunden gesendet.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält keine E-Mail-Benachrichtigung über das Produkt *wieder auf Lager*. Im Protokoll wird der folgende Fehler angezeigt:

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
