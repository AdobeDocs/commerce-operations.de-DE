---
title: 'ACSD-66952: Der Cache wird bei jedem PLP- oder Warenkorbbesuch gelöscht, wenn eine Zielregel festgelegt ist'
description: Wenden Sie den ACSD-66952 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem der Cache bei jedem PLP- oder Warenkorbbesuch gelöscht wurde, was zu einem unnötigen Leistungsaufwand führte, wenn eine Zielregel festgelegt wurde.
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
source-git-commit: 1aec8de86696ffc9ecb13100e6ffa1f912b281fb
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# ACSD-66952: Der Cache wird bei jedem PLP- oder Warenkorbbesuch gelöscht, wenn eine Zielregel festgelegt ist

Der Patch ACSD-66952 behebt das Problem, dass der Cache bei jedem PLP- oder Warenkorbbesuch gelöscht wird, was zu einem Leistungsaufwand führt, wenn eine Zielregel festgelegt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-66952. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Problem, bei dem der Cache bei jedem PLP- oder Warenkorbbesuch gelöscht wird, was zu Leistungsaufwand führt, wenn eine Zielregel festgelegt wird.

<u>Schritte zur Reproduktion</u>:

1. Generieren Sie einen kleinen Beispieldatensatz.
1. Erstellen Sie Zielregelwerte wie folgt:
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *Verwandte Produkte*
      * **[!UICONTROL Status]** = *aktiv*
      * **[!UICONTROL Apply to]** = *Verwandte Produkte*
   1. **[!UICONTROL Products to Match]**
      * Belassen Sie den Standardwert.
   1. **[!UICONTROL Products to Display]**
      * Wenn **ALLE** dieser Bedingungen &quot;*&quot;*, **[!UICONTROL Product Category]** = *Konstanter Wert 111111*
1. Überwachung der Protokolle auf Anfragen zur Cache-Invalidierung starten
1. Besuchen Sie die Produktseite.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und navigieren Sie zur Seite „Warenkorb“.

<u>Erwartete Ergebnisse</u>:

Die Anwendung sollte den Cache beim Durchsuchen der Site nicht ungültig machen.

<u>Tatsächliche Ergebnisse</u>:

Cache-Tags werden ungültig gemacht.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch
