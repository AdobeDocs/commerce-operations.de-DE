---
title: 'ACSD-64137: Die Suche nach Abholorten per Postleitzahl funktioniert bei der niederländischen Lokalisierung nicht richtig'
description: Wenden Sie den Patch ACSD-64137 an, um das Problem zu beheben, dass die Suche nach Abholorten per Postleitzahl für die niederländische Lokalisierung nicht richtig funktioniert.
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 4947133daaffb919aeba986c8a6b88ecb2e1b943
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# ACSD-64137: Die Suche nach Abholorten per Postleitzahl funktioniert bei der niederländischen Lokalisierung nicht richtig

Der Patch ACSD-64137 behebt das Problem, dass die Suche nach Abholorten per Postleitzahl bei der niederländischen Lokalisierung nicht richtig funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 installiert ist. Die Patch-ID ist ACSD-64137. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Postleitzahlsuche für die Niederlande zeigt keine Ergebnisse auf der Frontend-Checkout-Seite an. Es funktioniert jedoch nach Stadt und zeigt die entsprechende Adresse ohne Suche an.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine neue Instanz mit Inventarmodulen.
1. Erstellen eines benutzerdefinierten Lagers.
1. Erstellen Sie zwei Quellen mit niederländischen Adressen und weisen Sie sie dem Lager zu (Postleitzahlen 7311ER und 7311AE).
1. Erstellen Sie ein einfaches Produkt und fügen Sie Inventar hinzu.
1. Aktivieren Sie **[!UICONTROL In-Store Delivery]**, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** navigieren.
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**. **[!UICONTROL Provider]** auf *Offline-Berechnung* gesetzt.
1. Führen Sie den folgenden Befehl aus, um Geo-Namen für NL zu importieren.

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. Fügen Sie das Produkt zum Warenkorb hinzu und gehen Sie zum Versandschritt.
1. Wählen Sie **[!UICONTROL Pick In Store]** aus. Klicken Sie dann auf **[!UICONTROL Select Other]** , um andere Stores auszuwählen.
1. Geben Sie *7311* oder *7311AE* in das **[!UICONTROL Select Store]** Suchformular ein.


**Erwartete Ergebnisse**:

* Übereinstimmende Stores sollten befüllt werden.

**Tatsächliche Ergebnisse**:

* Keine Ergebnisse gefunden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
