---
title: 'ACSD-54472: Kunden einer abgelehnten Firma können sich weiterhin authentifizieren'
description: Wenden Sie den ACSD-54472 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem sich die Kunden eines abgelehnten Unternehmens weiterhin authentifizieren können und Kunden eines blockierten und abgelehnten Unternehmens weiterhin Bestellungen aufgeben können.
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472: Kunden einer abgelehnten Firma können sich weiterhin authentifizieren

Mit dem Patch ACSD-54472 wird das Problem behoben, dass sich die Kunden eines abgelehnten Unternehmens weiterhin authentifizieren können und Kunden eines blockierten und abgelehnten Unternehmens weiterhin Bestellungen aufgeben können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54472. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Kunden eines abgelehnten Unternehmens können sich weiterhin authentifizieren, und Kunden eines blockierten und abgelehnten Unternehmens können weiterhin Bestellungen aufgeben.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Firma.
1. Fügen Sie Produkte über [!DNL GraphQL] zum Warenkorb hinzu.
1. Ändern Sie den Unternehmensstatus in *Blockiert*.
1. Senden Sie eine [!DNL GraphQL] Anfrage, um die Bestellung aufzugeben und ein verhandelbares Angebot zu erstellen.
1. Ändern Sie den Unternehmensstatus in *Abgelehnt*.
1. Senden Sie eine [!DNL GraphQL], um das Benutzerautorisierungs-Token des Unternehmens abzurufen.
1. Kundenstatus auf &quot;*&quot;*.
1. Senden Sie eine [!DNL GraphQL], um das Benutzerautorisierungs-Token des Unternehmens abzurufen.

<u>Erwartete Ergebnisse</u>:

* Bestellung und verhandelbares Angebot werden nicht vom Benutzer der Firma *Blocked* platziert.
* Autorisierungs-Token wird für den Benutzer des Unternehmens *Abgelehnt* nicht abgerufen.
* Autorisierungs-Token wurde für den Kunden *Inaktiv* nicht abgerufen.

<u>Tatsächliche Ergebnisse</u>:

* Bestellung und verhandelbares Angebot werden vom Benutzer des *Blocked* Unternehmens platziert.
* Autorisierungs-Token wird für den Benutzer des Unternehmens *Abgelehnt* abgerufen.
* Autorisierungs-Token wird für den Kunden *inaktiv* abgerufen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
