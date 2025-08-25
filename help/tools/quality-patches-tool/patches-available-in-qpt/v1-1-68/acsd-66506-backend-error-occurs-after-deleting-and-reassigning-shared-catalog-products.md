---
title: 'ACSD-66506: Backend-Fehler tritt nach dem Löschen und Neuzuweisen von Shared Catalog-Produkten auf'
description: Wenden Sie den Patch ACSD-66506 an, um das Adobe Commerce-Problem zu beheben, bei dem das Backend den Fehler ausgibt * Das angeforderte Produkt existiert nicht. Überprüfen Sie das Produkt und versuchen Sie es erneut*, nachdem Sie zuvor zugewiesene Produkte gelöscht und einem freigegebenen Katalog neue zugewiesen haben.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506: Backend-Fehler tritt nach dem Löschen und Neuzuweisen von Shared Catalog-Produkten auf

Der Patch ACSD-66506 behebt das Problem, dass das Backend den Fehler *Das angeforderte Produkt existiert nicht. Überprüfen Sie das Produkt und versuchen Sie es erneut* nachdem Sie zuvor zugewiesene Produkte gelöscht und einem freigegebenen Katalog neue zugewiesen haben. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66506. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nach dem Löschen zuvor zugewiesener Produkte und dem Zuweisen neuer Produkte zu einem **[!UICONTROL Shared Catalog]** gibt das Backend den folgenden Fehler zurück: *Das angeforderte Produkt ist nicht vorhanden. Überprüfen Sie das Produkt und versuchen Sie es erneut*

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einige Produkte mit dem Leistungs-Toolkit: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. Gehen Sie zu **[!UICONTROL [!DNL B2B] Features]** Konfiguration und legen Sie **[!UICONTROL Enable Company]** und **[!UICONTROL Enable Shared Catalog]** auf `Yes` fest.
1. Erstellen Sie einen neuen freigegebenen Katalog.
1. Weisen Sie alle generierten Produkte dem neu erstellten freigegebenen Katalog zu.
1. Verwenden Sie **[!UICONTROL Product Import]** , um ein Produkt zu löschen, das dem freigegebenen Katalog zugewiesen wurde.
   1. Exportieren Sie ein Produkt gefiltert nach SKU.
   1. Wählen Sie **[!UICONTROL Import Behavior: Delete]** aus und importieren Sie dann dieselbe Datei.
1. Öffnen Sie die **[!UICONTROL Shared Catalog]** und konfigurieren Sie Preise und Struktur.
   1. Wählen Sie **[!UICONTROL Set Pricing and Structure]** aus.
   1. Klicken Sie auf **[!UICONTROL Next]** und dann auf **[!UICONTROL Generate Catalog]**.
   1. Klicken Sie auf **[!UICONTROL Save]**.

<u>Erwartete Ergebnisse</u>:

Es tritt kein Fehler auf und Produkte verbleiben im freigegebenen Katalog, auch wenn ein Fehler auftritt.

<u>Tatsächliche Ergebnisse</u>:

Ein Fehler tritt auf: *Das angeforderte Produkt ist nicht vorhanden. Überprüfen Sie das Produkt und versuchen Sie es*, und alle Produkte werden aus dem freigegebenen Katalog entfernt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
