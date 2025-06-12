---
title: 'ACSD-48204: Die Katalogpreisregel, die auf dem Attribut *Ja/Nein* erstellt wurde, berücksichtigt den ausgewählten Umfang nicht.'
description: Wenden Sie den Patch ACSD-48204 an, um das Adobe Commerce-Problem zu beheben, bei dem die auf dem Attribut „Ja/Nein“ erstellte Katalogpreisregel den ausgewählten Bereich nicht berücksichtigt.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-48204: Katalogpreisregel, die auf dem Attribut *Ja/Nein* erstellt wurde, berücksichtigt den ausgewählten Umfang nicht.

Der Patch ACSD-48204 behebt das Problem, dass die auf der Grundlage des Attributs *Ja/Nein* erstellte Katalogpreisregel den ausgewählten Umfang nicht berücksichtigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-48204. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Katalogpreisregel, die auf dem Attribut *Ja/Nein* erstellt wurde, berücksichtigt den ausgewählten Umfang nicht.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Websites (Standard und W2).
1. Erstellen Sie ein Produktattribut vom Typ *Ja/Nein*.
   * [!UICONTROL Default value] = [!UICONTROL No] festlegen
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Erstellen Sie ein konfigurierbares Produkt basierend auf einem beliebigen Attribut mit zwei Varianten (V1 und V2).
   * Fügen Sie das Attribut *Ja/Nein* zum konfigurierbaren Variantenattribut hinzu
   * Legen Sie für eine der Varianten (V1) den Wert auf der nicht standardmäßigen Website (W2) auf *[!UICONTROL Yes]* fest
1. Erstellen Sie eine Katalogregel:
   * Auf beide Websites angewendet
   * Bedingung: *Ja/Nein* Attributwert ist *[!UICONTROL Yes]*
   * Rabatt = 50 %
1. Öffnen Sie das konfigurierbare Produkt auf der nicht standardmäßigen -Website (W2).
1. Überprüfen Sie, ob auf die Variante V1 der Rabatt von 50 % angewendet wurde.
1. Öffnen Sie die V1-Variante in der Adobe Commerce Admin.
   * Zur Standard-Website wechseln
   * Keine Änderungen vornehmen und das Produkt speichern
1. Aktualisieren Sie die konfigurierbare Seite mit der Produkt-Storefront.

<u>Erwartete Ergebnisse</u>:

Für die Variante V1 gilt weiterhin der Rabatt von 50 %, da keine Änderungen vorgenommen wurden.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt verschwindet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
