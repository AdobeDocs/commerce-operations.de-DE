---
title: 'ACSD-63406: Abgelaufene persistente Anführungszeichen werden nicht gelöscht, wenn der Cron-Auftrag persistent_clear_expired ausgeführt wird'
description: Wenden Sie den Patch ACSD-63406 an, um das Adobe Commerce-Problem zu beheben, bei dem die abgelaufenen persistenten Anführungszeichen nicht von einem Cron-Auftrag gelöscht werden, wenn der Cron-Auftrag „persistent_clear_expired“ ausgeführt wird.
feature: Quotes, Shopping Cart
role: Admin, Developer
exl-id: 795d1ddf-0d5b-406c-870b-36cb92cf07fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-63406: Abgelaufene persistente Anführungszeichen werden bei Ausführung `persistent_clear_expired` Cron-Auftrags nicht gelöscht

Der Patch ACSD-63406 behebt das Problem, dass die abgelaufenen persistenten Anführungszeichen von keinem Cron-Auftrag gelöscht werden, wenn der `persistent_clear_expired` Cron-Auftrag ausgeführt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 installiert ist. Die Patch-ID ist ACSD-63406. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Abgelaufene persistente Anführungszeichen werden von keinem Cron-Auftrag gelöscht, wenn der `persistent_clear_expired` Cron-Auftrag ausgeführt wird.

<u>Schritte zur Reproduktion</u>:

1. Kategorie und Produkt erstellen.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**.
   1. Setzen Sie alle Optionen auf *Ja*.
   1. Setzen Sie **[!UICONTROL Persistence Lifetime (seconds)]** auf *60*.
1. Kundenkonto in der Storefront erstellen und sich anmelden.
1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Melden Sie sich ab, warten Sie 60 Sekunden und melden Sie sich erneut an.

<u>Erwartete Ergebnisse</u>:

Der `persistent_clear_expired` Cron-Auftrag sollte persistente Anführungszeichen löschen, die auf den Einstellungen für die Persistenzlebensdauer in der Konfiguration basieren.

<u>Tatsächliche Ergebnisse</u>:

Der `is_persistent` für das Kundenangebot verbleibt *1* in der Angebotstabelle.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
