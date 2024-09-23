---
title: "ACSD-52736: [!UICONTROL Cart Price Rule] funktioniert nicht wie erwartet."
description: Wenden Sie den Patch ACSD-52736 an, um das Adobe Commerce-Problem zu beheben, bei dem ein [!UICONTROL Cart Price Rule] , der die Anforderungen an die konfigurierbare Produktmenge enthält, nicht erwartungsgemäß funktioniert.
feature: Shopping Cart, Products
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] funktioniert nicht erwartungsgemäß

Der Patch ACSD-52736 behebt das Problem, dass ein [!UICONTROL Cart Price Rule], der die Anforderungen für konfigurierbare Produktmengen enthält, nicht erwartungsgemäß funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.36 installiert ist. Die Patch-ID ist ACSD-52736. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein [!UICONTROL Cart Price Rule] -Wert, der die Anforderungen für eine konfigurierbare Produktmenge enthält, funktioniert nicht erwartungsgemäß.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Warenkorbregel:
   * [!UICONTROL Apply] = Prozentsatz des Produktpreisrabatts
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Wenden Sie die Regel nur auf die Artikel des Warenkorbs an, die den folgenden Bedingungen entsprechen: Die Menge im Warenkorb ist 1.
2. Fügen Sie dem Warenkorb ein Produkt mit [!UICONTROL Qty] = 2 hinzu.
3. Überprüfen Sie die Warenkorbpreise.

<u>Erwartete Ergebnisse</u>:

Die Regel wird nicht angewendet, da die Menge der Produkte im Warenkorb *2* beträgt.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt wird angewendet.

<u> Zusätzliche Schritte, die nach der Patch-Installation erforderlich sind</u>:

Nach Anwendung des Patches müssen die Bedingungen der Warenkorbregel mit dem Attribut *Menge* entfernt und erneut hinzugefügt werden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
