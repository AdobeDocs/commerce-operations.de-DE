---
title: 'ACSD-64684: Validierungsfehler beim Speichern einer Geschenkkarte mit einem Wert über 999 aufgrund des Kommas in Tausend (1.000)'
description: Wenden Sie den Patch ACSD-64684 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Speichern einer Geschenkkarte mit einem Wert über 999 aufgrund des Kommas in „Tausend“ (1.000) ein Validierungsfehler auftritt.
feature: Catalog Management
role: Admin, Developer
source-git-commit: 58d385c0e3479f5f9d826dc6e892c8ec2ebfdbb5
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-64684: Validierungsfehler beim Speichern einer Geschenkkarte mit einem Wert über 999 aufgrund des Kommas in Tausend (1.000)

Mit dem Patch ACSD-64684 wird das Problem behoben, dass beim Speichern einer Geschenkkarte mit einem Wert über 999 aufgrund des Kommas in „Tausend“ (1.000) ein Validierungsfehler auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 installiert ist. Die Patch-ID ist ACSD-64684. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Bearbeiten und Speichern einer Geschenkkarte mit einem Wert größer als 999 tritt aufgrund eines Kommas (Tausendertrennzeichen) in der Zahl ein Validierungsfehler auf, z. B. „Tausender“ (1.000).

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Geschenkkartenprodukt.
   1. Geben Sie 1.000 als [!UICONTROL Amount] ein.
   1. Klicken Sie auf **[!UICONTROL Save]**.

<u>Erwartete Ergebnisse</u>:

* Die neue Geschenkkarte mit einem Betrag von 1.000 wird eingespart.

<u>Tatsächliche Ergebnisse</u>:

* Ein Validierungsfehler tritt auf, wenn der Betrag der Geschenkkarte größer als 999 ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
