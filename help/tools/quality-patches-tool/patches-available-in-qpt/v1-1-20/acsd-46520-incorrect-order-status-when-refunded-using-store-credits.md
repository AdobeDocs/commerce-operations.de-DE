---
title: 'ACSD-46520: Falscher Bestellstatus bei Rückerstattung über Ladenguthaben'
description: Dieser Artikel bietet eine Lösung für das Problem, dass Benutzende einen falschen Bestellstatus erhalten, wenn sie mithilfe von Store-Guthaben zurückerstattet werden.
feature: Orders, Returns
role: Admin
exl-id: 67740003-a71e-41bf-afda-ca3e32290115
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-46520: Falscher Bestellstatus bei Rückerstattung über Ladenguthaben

Mit dem Patch ACSD-46520 wird das Problem gelöst, dass Benutzende einen falschen Bestellstatus erhalten, wenn sie über Ladenguthaben zurückerstattet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46520. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 und 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende erhalten bei der Rückerstattung über Ladenguthaben einen falschen Bestellstatus.

<u>Schritte zur Reproduktion</u>:

1. Kundenkonto in der Storefront erstellen und sich anmelden.
1. Weisen Sie dem Kunden vom Administrator Gutschriften aus dem Store zu. Die Ladenguthaben sollten die gesamte Bestellung abdecken.
1. Bestellen Sie mit den Gutschriften aus dem Geschäft.
1. Rechnung der Bestellung.
1. Erstellen Sie eine Gutschrift, um den gesamten Bestellbetrag zurückzuerstatten.
Aktivieren Sie das Kontrollkästchen **[!UICONTROL Refund to store credit]** .
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Bestellstatus lautet *Geschlossen*.

<u>Tatsächliche Ergebnisse</u>:

Der Bestellstatus ist *Abgeschlossen* was nicht der richtige Status ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder [!DNL Magento Open Source] On-Premise: [Quality Patches Tools > Usage](/help/tools/quality-patches-tool/usage.md) im Handbuch Quality Patches Tool.
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
