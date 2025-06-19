---
title: 'MDVA-44703: Die Bestellsummen im Bericht „Bestellungen“ sind falsch berechnet'
description: Der Patch MDVA-44703 behebt das Problem, dass die Bestellsummen im Bericht Bestellungen für den Benutzer mit eingeschränkten Administratorrechten falsch berechnet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44703. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
feature: Orders
role: Admin
exl-id: bdd38ba6-f282-4026-8f65-b76543859123
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44703: Die Bestellsummen im Bericht „Bestellungen“ sind falsch berechnet

Der Patch MDVA-44703 behebt das Problem, dass die Bestellsummen im Bericht Bestellungen für den Benutzer mit eingeschränkten Administratorrechten falsch berechnet werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44703. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bestellsummen im Bericht „Bestellungen“ sind für den eingeschränkten Admin-Benutzer falsch berechnet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Website mit zwei Stores.
1. Erstellen Sie einen Benutzer mit eingeschränktem Administratorzugriff, der nur auf die neue Website zugreifen darf.
1. Melden Sie sich als eingeschränkter Admin-Benutzer an.
1. Erstellen Sie zwei Bestellungen mit unterschiedlichen Gesamtwerten, eine für jeden neuen Store.
1. Rechnungen für die Bestellungen erstellen.
1. Navigieren Sie zu **Berichte** > **Vertrieb** und öffnen Sie **Bestellungsbericht**.
1. Statistiken aktualisieren.
1. Siehe den Bericht für jeden Shop.

<u>Erwartete Ergebnisse</u>:

Die Verkaufssummen entsprechen dem Bestellbetrag jedes Geschäfts.

<u>Tatsächliche Ergebnisse</u>:

Die aggregierte Verkaufssumme für die gesamte Website wird für jeden Shop angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
