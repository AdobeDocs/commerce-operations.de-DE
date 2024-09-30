---
title: "ACSD-47107: Katalogpreisregel wird auf benutzerdefinierte Optionen angewendet"
description: Wenden Sie den Patch ACSD-47107 an, um das Adobe Commerce-Problem zu beheben, bei dem die Katalogpreisregel auf benutzerdefinierte Optionen angewendet wird.
feature: Catalog Management, Orders, Price Rules
role: Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-47107: Katalogpreisregel wird auf benutzerdefinierte Optionen angewendet

Der Patch ACSD-47107 behebt das Problem, dass die Katalogpreisregel auf benutzerdefinierte Optionen angewendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47107. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Katalogpreisregel wird auf benutzerdefinierte Optionen angewendet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Katalogpreisregel.
1. Setzen Sie sie auf *Anwenden als Prozentsatz des ursprünglichen Preises* und fügen Sie einen 10-%-Rabatt hinzu.
1. Wählen Sie ein beliebiges Produkt aus.
1. Erstellen Sie einige benutzerdefinierte Optionen.
1. Überprüfen Sie den Preis auf der Vorderseite.

<u>Erwartete Ergebnisse</u>:

Die Katalogpreisregel wird nicht auf benutzerdefinierte Optionen angewendet, sondern nur auf den ursprünglichen Preis des Produkts.

<u>Tatsächliche Ergebnisse</u>:

Die Katalogpreisregel wird auf benutzerdefinierte Optionen angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
