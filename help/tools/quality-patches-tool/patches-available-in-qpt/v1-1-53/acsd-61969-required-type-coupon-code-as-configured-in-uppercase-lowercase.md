---
title: 'ACSD-61969: Erforderlich, um Couponcode wie in Großbuchstaben oder Kleinbuchstaben konfiguriert einzugeben'
description: Wenden Sie den Patch ACSD-61969 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Benutzer den Couponcode genau so eingeben muss, wie er in Großbuchstaben oder Kleinbuchstaben konfiguriert ist.
feature: Price Rules
role: Admin, Developer
source-git-commit: b2660e3ca0dedbe4c9d8fa441f2e49b2e096474b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969: Erforderlich, um Couponcode wie in Großbuchstaben oder Kleinbuchstaben konfiguriert einzugeben

Der Patch ACSD-61969 behebt das Problem, dass ein Benutzer den Couponcode genau so eingeben muss, wie er in Großbuchstaben oder Kleinbuchstaben konfiguriert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-61969. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Sie müssen den Couponcode genau so eingeben, wie in Großbuchstaben oder Kleinbuchstaben konfiguriert, wenn Sie ihn vom Backend aus anwenden. Bei der Erstellung der Admin-Reihenfolge wird zwischen Groß- und Kleinschreibung unterschieden, bei der Storefront wird jedoch nicht zwischen Groß- und Kleinschreibung unterschieden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine *[!UICONTROL Cart Price Rule]* mit einem bestimmten Coupon *TEST*. Stellen Sie sicher, dass der Couponcode in Großbuchstaben geschrieben ist.
1. Erstellen Sie eine Bestellung in der Admin-Konsole.
1. Fügen Sie *test* zum Feld *[!UICONTROL Apply Coupon Code]* hinzu und klicken Sie auf den Pfeil neben dem Feld, um den Gutschein anzuwenden.
1. Beobachten Sie das Ergebnis.

<u>Erwartete Ergebnisse</u>:

Der Gutschein wurde erfolgreich angewendet. Beim Feld Coupon wird nicht zwischen Groß- und Kleinschreibung unterschieden.

<u>Tatsächliche Ergebnisse</u>:

Der Gutschein wird nicht angewendet. Der folgende Fehler wird angezeigt:

*Der Couponcode &quot;test&quot;ist ungültig. Überprüfen Sie den Code und versuchen Sie es erneut.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
