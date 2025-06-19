---
title: 'ACSD-55339: Problem beim Zuschneiden von SKUs in verhandelbaren Anführungszeichen für Adobe Commerce beheben'
description: Wenden Sie den Patch ACSD-55339 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkt-SKUs mit führenden Nullen gekürzt werden, was zu Verhandlungsfehlern führt.
feature: B2B, Quotes
role: Admin, Developer
exl-id: 7a9f92df-fb3e-4723-b731-155c6c4fc431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339: Problem beim Zuschneiden von SKUs in verhandelbaren Anführungszeichen für Adobe Commerce beheben

Mit dem Patch ACSD-55339 wird das Problem behoben, dass Produkt-SKUs mit führenden Nullen gekürzt werden, was zu Fehlern während des Verhandlungsprozesses führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.56 installiert ist. Die Patch-ID ist ACSD-55339. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce B2B 1.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Numerische Produkt-SKUs mit führenden Nullen werden bei Verwendung in verhandelbaren Anführungszeichen abgeschnitten, was zu Fehlern führt, die eine Aktualisierung der Mengen oder die Festlegung von Preisen verhindern.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zum Abschnitt „Produkterstellung“ im Admin-Bedienfeld.
1. Legen Sie die [!UICONTROL SKU] für das Produkt als 01910 fest.
1. Melden Sie sich bei der Storefront an und führen Sie die folgenden Schritte aus:
   1. Fügen Sie das Produkt zum Warenkorb hinzu.
   1. Warenkorb anzeigen und bearbeiten.
   1. Angebot anfordern.
1. Navigieren Sie zu [!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View] und [!UICONTROL Add Products by SKU] - 01910.

**Hinweis:** Die SKU wird als *1910* anstelle von *01910* angezeigt. Diese Diskrepanz verhindert, dass der Benutzer die Menge aktualisiert oder Preise festlegt, da im Katalog kein Produkt mit der SKU 1910 vorhanden ist.

<u>Erwartete Ergebnisse</u>:

Das verhandelbare Angebot sollte erfolgreich und fehlerfrei aktualisiert werden.

<u>Tatsächliche Ergebnisse</u>:

Es wird eine Warnmeldung angezeigt, die darauf hinweist, dass das Produkt nicht existiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
