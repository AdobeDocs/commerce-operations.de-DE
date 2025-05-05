---
title: 'ACSD-63793: Importprozesse interagieren auf verschiedenen Browser-Registerkarten miteinander'
description: Wenden Sie den Patch ACSD-63793 an, um das Adobe Commerce-Problem zu beheben, bei dem sich Importprozesse auf verschiedenen Browser-Registerkarten gegenseitig beeinflussen.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 60ad8dff5a3f26d0eab536d8824cb6579cb88a5a
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-63793: Importprozesse interagieren auf verschiedenen Browser-Registerkarten miteinander

Mit dem Patch ACSD-63793 wird das Problem behoben, dass sich Importprozesse auf verschiedenen Browser-Registerkarten gegenseitig beeinflussen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 installiert ist. Die Patch-ID ist ACSD-63793. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Import von Daten über die Admin-Benutzeroberfläche beeinträchtigt einen anderen Import, sodass Daten von einem Import in einem anderen verarbeitet werden.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.
1. Legen Sie **[!UICONTROL Entity Type]** auf *[!UICONTROL Customers and Addresses]fest (einzelne Datei)*.
1. Legen Sie **[!UICONTROL Import Behavior]** auf *[!UICONTROL Add/Update]* fest.
1. Gültige Datei zum Importieren auswählen.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Check Data]** .
1. Lassen Sie diese Registerkarte geöffnet.
1. Öffnen Sie eine neue Registerkarte und wiederholen Sie die Schritte mit einer Datei, die ungültige Daten enthält (z. B. zwei identische E-Mails für verschiedene Kunden).
1. Wechseln Sie zurück zur ersten Registerkarte.
1. Klicken Sie unten auf die Schaltfläche **[!UICONTROL Import]** .

<u>Erwartete Ergebnisse</u>:

Der Importvorgang sollte sich gegenseitig nicht stören.

<u>Tatsächliche Ergebnisse</u>:

Der Importvorgang wird abgeschlossen und die Berichtsdatei kann heruntergeladen werden. Dies zeigt einen Fehler in der zweiten Zeile an. Daten von einem anderen Import werden verarbeitet, auch wenn die anfängliche Validierung fehlerfrei durchgeführt wurde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
