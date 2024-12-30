---
title: 'ACSD-62475: Behebt Probleme beim Zusammenführen von Geschenkkarten im Warenkorb'
description: Wenden Sie den Patch ACSD-62475 an, um das Adobe Commerce-Problem zu beheben, bei dem Geschenkkartenprodukte mit unterschiedlichen Details fälschlicherweise zu einem einzigen Zeileneintrag im Warenkorb zusammengeführt werden.
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: fc97c3c0-dc1b-4546-aad0-ef3b4b6a3415
source-git-commit: 6803cf2bf27e99300f682308517011b73127fd94
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475: Behebt Probleme beim Zusammenführen von Geschenkkarten im Warenkorb

Mit dem Patch ACSD-62475 wird das Problem behoben, dass Geschenkkartenprodukte mit unterschiedlichen Details fälschlicherweise zu einem einzigen Zeileneintrag im Warenkorb zusammengeführt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-62475. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Geschenkkartenprodukte, die zum Warenkorb mit eindeutigen Absender- oder Empfängerdetails hinzugefügt werden, werden fälschlicherweise zu einem einzigen Zeileneintrag zusammengeführt, was zu Dateninkonsistenzen führt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein [!UICONTROL Gift Card] Produkt mit den folgenden Einstellungen:
   * **[!UICONTROL Card Type]**: [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**: 10

1. Erstellen Sie in der Storefront einen neuen Benutzer und melden Sie sich an.

1. Fügen Sie das Geschenkkartenprodukt mit den folgenden Details zum Warenkorb hinzu:
   * **[!UICONTROL Sender Name]**: Absender 1
   * **[!UICONTROL Sender Email**]: sender1@test.com
   * **[!UICONTROL Recipient Name**]: Empfänger 1
   * **[!UICONTROL Recipient Email**]: recipient1@test.com


1. Abmelden

1. Fügen Sie dasselbe Geschenkkartenprodukt mit den folgenden Details zum Warenkorb hinzu:
   * **[!UICONTROL Sender Name]**: Sender 2
   * **[!UICONTROL Sender Email**]: sender2@test.com
   * **[!UICONTROL Recipient Name**]: Empfänger 2
   * **[!UICONTROL Recipient Email**]: recipient2@test.com

1. Melden Sie sich wieder an und überprüfen Sie den Warenkorb.

<u>Erwartete Ergebnisse</u>:

Beide Geschenkgutscheine sollten als zwei separate Zeileneinträge mit den jeweiligen Details angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die Geschenkgutscheine werden zu einem einzigen Zeileneintrag mit einer Menge von 2 zusammengeführt, wobei die Details der ersten Geschenkgutscheine beibehalten werden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
