---
title: 'ACSD-51102: Katalogregel wird auf eine große Anzahl von Produkten angewendet, die nicht korrekt indiziert sind'
description: Wenden Sie den ACSD-51102-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, nicht korrekt indiziert wird, wenn die Regel durch ein geplantes Update aktiviert wird.
feature: Catalog Management, Products
role: Admin
exl-id: 35a8078d-667b-4101-8562-ece052b44c9c
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# ACSD-51102: Katalogregel wird auf eine große Anzahl von Produkten angewendet, die nicht korrekt indiziert sind

Mit dem Patch ACSD-51102 wird das Problem behoben, dass eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, nicht korrekt indiziert wird, wenn die Regel durch eine geplante Aktualisierung aktiviert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51102. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, wird nicht korrekt indiziert, wenn die Regel durch eine geplante Aktualisierung aktiviert wird.

Voraussetzungen:

* Cron-Auftrag wird jede Minute eingerichtet und ausgeführt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen großen Katalog mit Tausenden von Produkten, um die Laufzeit der *Katalogregel)-* von mehr als 120 Sekunden zu erreichen, wenn Katalogregeln aktiviert sind.
2. Erstellen Sie zwei Katalogregeln mit dem Status *Aktiv*, der auf *Nein* gesetzt ist.  Beispiel: *Test 1* und *Test 2*. Jede Regel sollte sich auf alle Produkte im Katalog auswirken und dazu führen, dass der Indexer länger als 120 Sekunden ausgeführt wird.
3. Stellen Sie sicher, dass der Status des Indexers &quot;*&quot;*.
4. Erstellen Sie geplante Aktualisierungen, um diese beiden Regeln zu aktivieren. *Test 2* Der Zeitplan sollte kurz nach dem *Test 1* beginnen. Beispielsweise mit einem Unterschied von 1 Minute.
5. Überprüfen Sie die Produktpreise auf der Storefront.

<u>Erwartete Ergebnisse</u>

Es werden Rabatte von beiden Regeln angewendet.

<u>Tatsächliche Ergebnisse</u>

Es wird nur der erste Regelrabatt angewendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>) im [!DNL Quality Patches Tool].
