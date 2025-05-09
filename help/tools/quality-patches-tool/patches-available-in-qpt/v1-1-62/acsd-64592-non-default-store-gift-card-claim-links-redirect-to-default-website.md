---
title: 'ACSD-64592: Nicht standardmäßige Links für Geschenkgutscheine werden zur Standard-Website weitergeleitet'
description: Wenden Sie den Patch ACSD-64592 an, um das Problem zu beheben, dass bei einer Einrichtung mit mehreren Websites beim Kauf einer virtuellen Geschenkkarte von der sekundären (nicht standardmäßigen) Website der Link für den Geschenkkartencode in der E-Mail die standardmäßige Website-URL enthält.
feature: Gift, Products
role: Admin, Developer
source-git-commit: 39866e1cf8f2afd892c9e151259a446d0277d58f
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# ACSD-64592: Nicht standardmäßige Links für Geschenkgutscheine werden zur Standard-Website weitergeleitet

Mit dem Patch ACSD-64592 wird ein Problem behoben, bei dem in einer Umgebung mit mehreren Websites beim Kauf einer virtuellen Geschenkkarte von einer sekundären (nicht primären) Website die E-Mail mit dem Link für den Geschenkkartencode Benutzer zur URL der Standardwebsite weiterleitet. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.9 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der Einrichtung mehrerer Websites leitet beim Kauf einer virtuellen Geschenkkarte von einer sekundären (nicht standardmäßigen) Website die E-Mail mit dem Link für den Geschenkkartencode die Benutzer zur URL der Standardwebsite weiter.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine sekundäre Website-, Store- und Store-Ansicht.
1. Konfigurieren Sie verschiedene Basis-URLs für die Basis- und die sekundäre Website.
1. Erstellen Sie eine virtuelle Geschenkkarte mit einigen Betragsoptionen.
1. Generieren Sie einen neuen Code-Pool unter **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**.
1. Bestellen Sie auf der sekundären Website mit dem Geschenkgutscheinprodukt.
1. Die Bestellung im Commerce Admin fakturieren.
1. Überprüfen Sie die URL im Link für den Geschenkkartencode der E *Mail „Sie haben ein Geschenk von Zwei erhalten*.

<u>Erwartete Ergebnisse</u>:

Der Link für den Geschenkgutschein-Code sollte den Link zur zweiten Website enthalten.

<u>Tatsächliche Ergebnisse</u>:

Der Link für den Geschenkgutschein-Code enthält die standardmäßige Website-URL, auch wenn die Bestellung auf der zweiten Website aufgegeben wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:
* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
