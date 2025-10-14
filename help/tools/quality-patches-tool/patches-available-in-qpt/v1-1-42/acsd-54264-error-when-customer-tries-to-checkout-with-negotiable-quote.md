---
title: 'ACSD-54264: Fehler, wenn der Kunde versucht, mit einem verhandelbaren Angebot auszuchecken'
description: Wenden Sie den Patch „ACSD-54264“ an, um das Adobe Commerce-Problem zu beheben, bei dem die Fehlermeldung „Das angeforderte Attribut kann nicht aktualisiert werden. Die Zeile „ID:store_id“ wird angezeigt, wenn ein Kunde versucht, mit einem verhandelbaren Angebot aus einer anderen Store-Ansicht auszuchecken.
feature: B2B, Checkout
role: Admin, Developer
exl-id: b1696228-b2ed-44eb-9e75-bf25ccf2f1cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-54264: Fehler erscheint, wenn der Kunde versucht, mit verhandelbarem Angebot auszuchecken

Der Patch „ACSD-54264“ behebt das Problem, dass eine Fehlermeldung *Sie können das angeforderte Attribut nicht aktualisieren. Zeilenkennung: store_id* wird angezeigt, wenn ein Kunde versucht, mit einem verhandelbaren Angebot aus einer anderen Store-Ansicht auszuchecken. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-54264. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine Fehlermeldung *Sie können das angeforderte Attribut nicht aktualisieren. Zeilenkennung: store_id* wird angezeigt, wenn ein Kunde versucht, mit einem verhandelbaren Angebot aus einer anderen Store-Ansicht auszuchecken.

<u>Voraussetzungen</u>:

Adobe Commerce B2B-Module sind installiert und aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Store-Ansicht für die Standard-Website.
1. Aktivieren Sie die *[!UICONTROL B2B Quote]* in der Konfiguration.
1. Melden Sie sich als Firmenkunde in einer der Store-Ansichten an.
1. Fügen Sie dem *[!UICONTROL Shopping Cart]* ein Produkt hinzu.
1. Reichen Sie das Angebot zur Überprüfung ein.
1. Wenn Sie ein Administrator sind, gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** und senden Sie das genehmigte Angebot.
1. Ändern Sie als Firmenkunde die Shop-Ansicht in eine andere Shop-Ansicht.
1. Versuchen Sie, auszuchecken.

<u>Erwartete Ergebnisse</u>:

Der Kunde gibt eine Bestellung mit diesem Angebot auf.

<u>Tatsächliche Ergebnisse</u>:

* Der Fehler tritt beim Speichern der Versandinformationen auf:

  `You cannot update the request attribute. Row ID: store_id =#`

* Der folgende Fehler wird protokolliert:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
