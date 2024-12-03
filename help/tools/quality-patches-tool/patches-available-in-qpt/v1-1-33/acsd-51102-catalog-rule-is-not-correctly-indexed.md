---
title: 'ACSD-51102: Katalogregel angewendet auf eine große Anzahl von Produkten nicht korrekt indiziert'
description: Wenden Sie den Patch ACSD-51102 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, nicht richtig indiziert wird, wenn die Regel durch eine geplante Aktualisierung aktiviert wird.
feature: Catalog Management, Products
role: Admin
exl-id: 35a8078d-667b-4101-8562-ece052b44c9c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# ACSD-51102: Katalogregel angewendet auf eine große Anzahl von Produkten nicht korrekt indiziert

Der Patch ACSD-51102 behebt das Problem, dass eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, nicht richtig indiziert wird, wenn die Regel durch eine geplante Aktualisierung aktiviert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51102. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Katalogregel, die auf eine große Anzahl von Produkten angewendet wird, wird nicht korrekt indiziert, wenn die Regel durch eine geplante Aktualisierung aktiviert wird.

Voraussetzungen:

* Cron-Auftrag wird eingerichtet und jede Minute ausgeführt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen großen Katalog mit Tausenden von Produkten, um die Laufzeit für die *Katalogregel*-Indexer von mehr als 120 Sekunden zu erreichen, wenn Katalogregeln aktiviert werden.
2. Erstellen Sie zwei Katalogregeln mit dem Status *Aktiv* , der auf *Nein* festgelegt ist.  Beispiel: *Test 1* und *Test 2*. Jede Regel sollte sich auf alle Produkte im Katalog auswirken und dazu führen, dass der Indexer länger als 120 Sekunden ausgeführt wird.
3. Stellen Sie sicher, dass der Status des Indexers *Bereit* ist.
4. Erstellen Sie geplante Aktualisierungen, um diese beiden Regeln zu aktivieren. *Test 2* sollte kurz nach *Test 1* beginnen. Beispiel: mit einer 1-minütigen Differenz.
5. Überprüfen Sie die Produktpreise an der Storefront.

<u>Erwartete Ergebnisse</u>

Es werden Rabatte von beiden Regeln angewendet.

<u>Tatsächliche Ergebnisse</u>

Es wird nur der Rabatt der ersten Regel angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](</help/tools/quality-patches-tool/usage.md>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
