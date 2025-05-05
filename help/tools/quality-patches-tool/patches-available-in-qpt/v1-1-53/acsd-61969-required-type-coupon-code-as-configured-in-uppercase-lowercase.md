---
title: 'ACSD-61969: Gutscheincode muss in Groß- oder Kleinbuchstaben eingegeben werden'
description: Wenden Sie den Patch ACSD-61969 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Benutzer den Gutscheincode genau so eingeben muss, wie er in Groß- oder Kleinschreibung konfiguriert ist.
feature: Price Rules
role: Admin, Developer
exl-id: 4bdf797b-2570-49f8-8e03-952b49ed1d18
source-git-commit: 5e12738f3ff6960f31cc34d74667c6902c9d4f8d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969: Gutscheincode muss in Groß- oder Kleinbuchstaben eingegeben werden

Mit dem Patch ACSD-61969 wird das Problem behoben, dass ein Benutzer den Gutscheincode genau so eingeben muss, wie er in Groß- oder Kleinschreibung konfiguriert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-61969. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Sie müssen den Gutscheincode bei der Anwendung über das Backend genauso in Groß- oder Kleinbuchstaben eingeben, wie er konfiguriert wurde. Bei der Erstellung von Admin-Aufträgen wird zwischen Groß- und Kleinschreibung unterschieden, bei der Storefront wird jedoch nicht zwischen Groß- und Kleinschreibung unterschieden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine *[!UICONTROL Cart Price Rule]* mit einem bestimmten Coupon *TEST*. Achten Sie darauf, dass der Gutscheincode großgeschrieben ist.
1. Erstellen Sie eine Bestellung in der Admin Console.
1. Fügen Sie *Feld *[!UICONTROL Apply Coupon Code]*&#x200B;den* „Test“ hinzu und klicken Sie auf den Pfeil neben dem Feld, um den Coupon anzuwenden.
1. Beobachten Sie das Ergebnis.

<u>Erwartete Ergebnisse</u>:

Der Coupon wurde erfolgreich angewendet. Beim Couponfeld wird nicht zwischen Groß- und Kleinschreibung unterschieden.

<u>Tatsächliche Ergebnisse</u>:

Der Coupon wird nicht angewendet. Der folgende Fehler wird angezeigt:

*Der Gutscheincode „Test“ ist ungültig. Überprüfen Sie den Code und versuchen Sie es erneut.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
