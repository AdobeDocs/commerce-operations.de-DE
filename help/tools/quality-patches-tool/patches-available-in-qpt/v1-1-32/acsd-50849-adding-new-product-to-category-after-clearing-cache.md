---
title: "ACSD-50849: Das Hinzufügen eines neuen Produkts nach dem Löschen des Cache führt zu Inkongruenzen"
description: Wenden Sie den Patch ACSD-50849 an, um das Adobe Commerce-Problem zu beheben, bei dem das Hinzufügen eines neuen Produkts zur Kategorie nach dem Löschen des Caches zu einer Inkongruenz zwischen Positionen und Auswahl der vorhandenen Produkte führt.
feature: Cache, Categories, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-50849: Das Hinzufügen eines neuen Produkts nach dem Löschen des Cache führt zu inkonformen Ergebnissen

Der Patch ACSD-50849 behebt das Problem, dass das Hinzufügen eines neuen Produkts zur Kategorie nach dem Löschen des Caches zu einer Inkongruenz zwischen Positionen und Auswahl der vorhandenen Produkte führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) QPT 1.1.32 installiert ist. Die Patch-ID ist ACSD-50849. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn Sie ein neues Produkt zur Kategorie hinzufügen, nachdem Sie den Cache geleert haben, stimmen die Positionen und Auswahlen der vorhandenen Produkte nicht überein.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Produkte.
1. Weisen Sie einer Kategorie ein Produkt zu.
1. Öffnen Sie die Kategorie über den Administrator.
1. Löschen Sie den Cache-Wert `bin/magento cache:flush`.
1. Fügen Sie der Kategorie das zweite Produkt hinzu.

<u>Erwartete Ergebnisse</u>:

Die in der Kategorie zugewiesenen vorhandenen Produkte werden nicht automatisch entfernt.

<u>Tatsächliche Ergebnisse</u>:

Das erste (vorhandene) Produkt wird automatisch entfernt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
