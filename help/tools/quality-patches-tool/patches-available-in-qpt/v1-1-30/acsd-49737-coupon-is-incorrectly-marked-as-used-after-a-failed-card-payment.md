---
title: 'ACSD-49737: Gutschein wird fälschlicherweise als nach einer fehlgeschlagenen Kartenzahlung verwendet gekennzeichnet'
description: Wenden Sie den Patch ACSD-49737 an, um das Adobe Commerce-Problem zu beheben, bei dem der Gutschein fälschlicherweise als nach einer fehlgeschlagenen Kartenzahlung als verwendet markiert wurde.
feature: Orders, Payments
role: Admin
exl-id: 09060026-8d64-49f6-a85a-3230a52030fb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49737: Der Coupon wird fälschlicherweise als *verwendet* nach einer fehlgeschlagenen Kartenzahlung markiert

Der Patch ACSD-49737 behebt das Problem, dass der Gutschein nach einer fehlgeschlagenen Kartenzahlung fälschlicherweise als *used* markiert wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-49737. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Gutschein wird nach einer fehlgeschlagenen Kartenzahlung fälschlicherweise als *verwendet* markiert.

<u>Voraussetzungen</u>:

1. Konfigurieren Sie die **[!UICONTROL Braintree sandbox payment]** -Methode.
1. Stellen Sie sicher, dass der Benutzer [*sales.rule.update.coupon.usage*](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/message-queues/consumers.html?lang=en) eingerichtet ist und ausgeführt wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **[!UICONTROL Cart Price Rule]** mit automatisch generierten Couponcodes.
1. Melden Sie sich als Kunde an.
1. Fügen Sie Produkte zum Warenkorb hinzu.
1. Wenden Sie einen automatisch generierten Gutscheincode an.
1. Versuchen Sie, eine Bestellung mit einer fehlgeschlagenen Zahlung zu tätigen.
1. Überprüfen Sie die Nutzung des Gutscheins im Tab **[!UICONTROL Manage Coupon Codes]** unter **[!UICONTROL Cart Price Rule]**.

<u>Erwartete Ergebnisse</u>:

Der Gutschein sollte nicht als *Verwendet* gekennzeichnet werden, wenn die Zahlung fehlgeschlagen ist.

<u>Tatsächliche Ergebnisse</u>:

* Couponcode lautet: - Verwendet: *Ja*, Verwendete Zeiten: *1*
* Der Couponcode ist nur für eine einmalige Verwendung gültig.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Zusätzliche Schritte, die nach der Patch-Installation erforderlich sind

(Dieser Abschnitt ist optional. Möglicherweise sind nach dem Anwenden des Patches einige Schritte erforderlich, um das Problem zu beheben.) 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
