---
title: 'MDVA-43859: Fehler „Keine solche Entität mit customerId =" protokolliert, wenn sich ein gelöschter Kunde anmeldet'
description: Mit dem Patch MDVA-43859 wird das Problem behoben, dass der Fehler *Keine solche Entität mit customerId =* protokolliert wird, wenn ein gelöschter Kunde versucht, sich anzumelden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43859. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Variables
role: Admin
exl-id: b8451b08-978a-44a2-8664-4369e832423b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-43859: Fehler „Keine solche Entität mit customerId =&quot; protokolliert, wenn sich ein gelöschter Kunde anmeldet

Der Patch MDVA-43859 behebt das Problem, dass der Fehler *Keine solche Entität mit customerId =* protokolliert wird, wenn ein gelöschter Kunde versucht, sich anzumelden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43859. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Fehler *Keine solche Entität mit customerId =* wird protokolliert, wenn ein gelöschter Kunde versucht, sich anzumelden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Kundenkonto aus dem Frontend.
1. Melden Sie sich ab und melden Sie sich bei dem in Schritt 1 erstellten Kundenkonto an.
1. Laden Sie das Backend in einem anderen Browser und wechseln Sie zum Kundenraster.
1. Löschen Sie den in Schritt 1 erstellten Kunden.
1. Wechseln Sie zurück zum ersten Browser und versuchen Sie, sich abzumelden.

<u>Erwartete Ergebnisse</u>:

Der Kunde wird ohne Fehler zur Anmeldeseite weitergeleitet.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde erhält den folgenden Fehler: *Keine solche Entität mit customerId =*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
