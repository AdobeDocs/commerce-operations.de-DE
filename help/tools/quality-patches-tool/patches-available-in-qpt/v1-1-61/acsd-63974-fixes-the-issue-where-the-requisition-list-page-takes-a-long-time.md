---
title: 'ACSD-63974: Behebt langsame [!UICONTROL Requisition List] mit Paginierung'
description: Wenden Sie den Patch ACSD-63974 an, um das Problem zu beheben, dass das Laden der [!UICONTROL Requisition List]-Seite viel Zeit in Anspruch nimmt, wenn zu viele Elemente vorhanden sind.
feature: B2B
role: Admin, Developer
source-git-commit: e5f8112b870e3550b4f3a9113be48428a54d454a
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# ACSD-63974: Behebt langsame [!UICONTROL Requisition List] mit Paginierung

Mit dem Patch ACSD-63974 wird das Problem behoben, dass das Laden der **[!UICONTROL Requisition List]**-Seite viel Zeit in Anspruch nimmt, wenn zu viele Elemente vorhanden sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 installiert ist. Die Patch-ID ist ACSD-63974. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Laden der Seite **[!UICONTROL Requisition List]** dauert lange, wenn viele Elemente vorhanden sind (2000+). Dies liegt daran, dass keine Paginierung erfolgt, sodass alle Elemente gleichzeitig geladen werden.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**.
1. Setzen Sie **[!UICONTROL Enable Requisition List]** auf *Ja*.
1. Generieren Sie über 2.000 Produkte, indem Sie `simple_products` Knoten in `setup/performance-toolkit/profiles/ce/small.xml` bearbeiten.
1. Führen Sie den Befehl aus:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Erstellen Sie einen Kunden und melden Sie sich an.
1. Fügen Sie alle Produkte zum **[!UICONTROL Requisition List]** hinzu.
1. Zeigen Sie die **[!UICONTROL Requisition List]** in der Storefront an.


<u>Erwartete Ergebnisse</u>:

Die Seite sollte innerhalb einer angemessenen Zeit geladen werden.


<u>Tatsächliche Ergebnisse</u>:

Die Ladezeit der Seite steigt mit der Anzahl der Elemente, da alle Elemente gleichzeitig geladen werden, da keine Paginierung erfolgt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: Upgrades und Patches > Anwenden von Patches im Handbuch zu Commerce in Cloud-Infrastruktur .

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
