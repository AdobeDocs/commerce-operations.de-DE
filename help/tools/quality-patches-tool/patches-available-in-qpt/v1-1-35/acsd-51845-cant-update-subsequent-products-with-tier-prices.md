---
title: 'ACSD-51845: Nachfolgende Produkte können nicht mit Stufenpreisen und verschiedenen Attributsätzen per asynchroner Massenaktualisierung aktualisiert werden [!DNL API]'
description: Wenden Sie den ACSD-51845-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Sie nachfolgende Produkte nicht über asynchrone Massenvorgänge mit Stufenpreisen und verschiedenen Attributsätzen aktualisieren  [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: 83d97946-83da-4c1b-8f2a-21a64ee84e93
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51845: Nachfolgende Produkte können nicht mit Stufenpreisen und verschiedenen Attributsätzen über asynchrone [!DNL API] aktualisiert werden

Mit dem Patch ACSD-51845 wird das Problem behoben, dass nachfolgende Produkte nicht über asynchrone [!DNL REST API] mit Stufenpreisen und verschiedenen Attributsätzen aktualisiert werden können. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51845. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Aktualisierung schlägt für nachfolgende Produkte mit Stufenpreisen und verschiedenen Attributsätzen über asynchrone [!DNL REST API] fehl.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie [!DNL RabbitMQ].
1. Erstellen Sie zwei Attributsätze.
1. Erstellen Sie zwei **Einfache Produkte** und weisen Sie jedes Produkt einem anderen Attributsatz zu.
1. Fügen Sie **jedes Produkt einen** Kundengruppenpreis“ hinzu.
1. Aktualisieren Sie beide Produkte in derselben [!DNL API].
1. Stellen Sie sicher, dass der `bin/magento queue:consumers:start async.operations.all`-Befehl ausgeführt wird.
1. Überprüfen Sie den Status der [!DNL API].

<u>Erwartete Ergebnisse</u>:

Die Ausführung des Services war erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

Das System gibt die Fehlermeldung zurück: *Das Produkt konnte nicht gespeichert werden. Bitte erneut versuchen.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
