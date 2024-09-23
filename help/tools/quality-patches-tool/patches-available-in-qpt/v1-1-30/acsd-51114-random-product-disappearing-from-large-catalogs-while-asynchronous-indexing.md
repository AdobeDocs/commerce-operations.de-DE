---
title: "ACSD-51114: Zufällige Produkte wurden aus großen Katalogen ausgeblendet, wenn die asynchrone Indizierung aktiviert ist."
description: Wenden Sie den Patch ACSD-51114 an, um das Adobe Commerce-Problem zu beheben. Wenn die asynchrone Indizierung aktiviert ist, verschwanden Random-Produkte aus großen Katalogen.
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114: Zufällige Produkte verschwanden aus großen Katalogen, wenn die asynchrone Indizierung aktiviert ist

>[!NOTE]
>
>Dieser Patch ist veraltet.

Der Patch ACSD-51114 behebt das Problem Random-Produkte verschwanden aus großen Katalogen, wenn die asynchrone Indizierung aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-51114. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der [[!DNL Quality Patches Tool]:Suchen Sie auf der Seite nach Patches]. Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Zufällige Produkte verschwanden aus großen Katalogen, wenn die asynchrone Indizierung aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Satz von 10 Produkten.
1. Setzen Sie alle Indexer auf den Modus **[!UICONTROL Update on Save]** .
1. Erstellen Sie eine Kategorie und weisen Sie ihr alle Produkte zu.
1. Deaktivieren Sie alle Produkte.
1. Öffnen Sie die Kategorie und vergewissern Sie sich, dass dort keine Produkte vorhanden sind.
1. Setzen Sie alle Indexer auf den Modus **[!UICONTROL Update on Schedule]** .
1. Setzen Sie die `DEFAULT_BATCH_SIZE` in `lib/internal/Magento/Framework/Mview/View.php#L31` auf 2.
1. Aktivieren Sie Produkte in der folgenden Reihenfolge: 1., 9., 2., 5., 10., 3.
1. Führen Sie den Cron-Befehl aus.
1. Öffnen Sie die Kategorie erneut.

<u>Erwartete Ergebnisse</u>:

Alle aktivierten Produkte werden angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Alle aktivierten Produkte werden nicht angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
