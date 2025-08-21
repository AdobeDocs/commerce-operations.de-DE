---
title: 'ACP2E-3731: Produktexporte mit [!UICONTROL Catalog, Search] Sichtbarkeit schließen Datensätze aus anderen Store-Ansichten ein'
description: Wenden Sie den ACP2E-3731-Patch an, um das Adobe Commerce zu beheben, bei dem Produktexporte mit dem Sichtbarkeitsfilter , der auf gesetzt ist, [!UICONTROL Catalog, Search] falsche Zeilen in Multi-Store-Setups aufgrund von Attributvariationen im Speicherbereich enthalten.
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731: Produktexporte mit [!UICONTROL Catalog, Search] Sichtbarkeit schließen Datensätze aus anderen Store-Ansichten ein

Mit dem Patch ACP2E-3731 wird das Problem behoben, dass Produktexporte mit *[!UICONTROL Catalog, Search]* Sichtbarkeit fälschlicherweise Datensätze aus anderen Store-Ansichten in Multi-Store-Umgebungen enthalten. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID lautet ACP2E-3731. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p9

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produktexporte enthalten falsche Zeilen, wenn der Sichtbarkeitsfilter in Setups mit mehreren Stores aufgrund von Variationen bei Attributen im Store auf *[!UICONTROL Catalog, Search]* gesetzt ist.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie im Admin-Bedienfeld zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** , um eine zusätzliche Website-, Store- und Store-Ansicht zu erstellen.
1. Navigieren Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**. Klicken Sie auf **[!UICONTROL Add Attribute Set]** , um ein Attribut zu erstellen. Setzen Sie **[!UICONTROL Based On]** auf *Standard*.
1. Erstellen Sie ein Produkt und weisen Sie es sowohl der Haupt- als auch der sekundären Website zu.
1. Legen Sie einen Textwert für das neu erstellte Attribut fest, wobei **[!UICONTROL Scope]** auf &quot;*Alle Store-Ansichten“*.
1. Ändern Sie den Bereich in die Ansicht des sekundären Speichers und aktualisieren Sie das Attribut mit einem anderen Wert.
1. Ändern Sie den Bereich in die standardmäßige Store-Ansicht und die sekundäre Store-Ansicht und legen Sie dann die Sichtbarkeit des Produkts auf &quot;*einzeln sichtbar“*.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Export]** und wählen Sie *Produkte* aus dem Dropdown-Menü aus.
1. Legen Sie einen Filter mit **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]* fest und klicken Sie auf **[!UICONTROL Continue]**.
1. Führen Sie den folgenden Befehl aus, um den Export zu verarbeiten:

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. Überprüfen Sie die exportierte Datei.

<u>Erwartete Ergebnisse</u>:

Nur die gefilterten Datensätze werden exportiert.

<u>Tatsächliche Ergebnisse</u>:

Die exportierte Datei enthält eine Zeile für die sekundäre Speicheransicht, die nicht den beim Export festgelegten Filterkriterien entspricht.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
