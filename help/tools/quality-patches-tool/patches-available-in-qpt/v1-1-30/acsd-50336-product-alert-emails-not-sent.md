---
title: "ACSD-50336: E-Mails mit Produktwarnungen werden nicht gesendet"
description: Wenden Sie den Patch ACSD-50336 an, um das Adobe Commerce-Problem zu beheben, bei dem E-Mails zur Produktwarnung nicht gesendet werden, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wird.
feature: Communications, Personalization, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-50336: E-Mails mit Produktwarnung werden nicht gesendet

Der Patch ACSD-50336 behebt das Problem, dass E-Mails mit Produktwarnungen nicht gesendet werden, wenn ein Produkt wieder auf Lager ist oder der Preis geändert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-50336. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Warnungen-E-Mails werden nicht gesendet, wenn ein Produkt wieder vorrätig ist oder der Preis geändert wird.

<u>Voraussetzungen</u>:

Richten Sie Produktwarnungen ein für den Fall, dass ein Produkt wieder vorrätig hinzugefügt wird.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich als Kunde an der Storefront an.
1. Öffnen Sie ein Produkt, das nicht auf Lager ist.
1. Abonnieren Sie , um eine Benachrichtigung zu erhalten, wenn das Produkt *wieder auf Lager ist*.
1. Aktualisieren Sie das Produkt von [!UICONTROL Admin] auf _zurück auf Lager_.

<u>Erwartete Ergebnisse</u>:

Eine E-Mail-Benachrichtigung, dass das Produkt *wieder auf Lager* ist, wird an den Kunden gesendet.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält keine E-Mail-Benachrichtigung, dass das Produkt *wieder auf Lager* ist. Der folgende Fehler wird im Protokoll angezeigt:

```
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] [] 
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
