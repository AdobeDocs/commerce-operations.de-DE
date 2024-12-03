---
title: 'ACSD-48204: Auf dem Attribut *Ja/Nein* erstellte Katalogpreisregel berücksichtigt den ausgewählten Umfang nicht'
description: Wenden Sie den Patch ACSD-48204 an, um das Adobe Commerce-Problem zu beheben, bei dem die auf dem Attribut *Ja/Nein* erstellte Katalogpreisregel den ausgewählten Umfang nicht berücksichtigt.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-48204: Katalogpreisregel, die basierend auf dem Attribut *Ja/Nein* erstellt wurde, berücksichtigt den ausgewählten Umfang nicht

Der Patch ACSD-48204 behebt das Problem, dass die auf dem Attribut *Ja/Nein* basierende Katalogpreisregel den ausgewählten Umfang nicht berücksichtigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID lautet ACSD-48204. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Katalogpreisregel, die basierend auf dem Attribut *Ja/Nein* erstellt wurde, berücksichtigt den ausgewählten Umfang nicht.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Websites (Standard und W2).
1. Erstellen Sie ein Produktattribut vom Typ *Ja/Nein* .
   * Setzen Sie [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Erstellen Sie ein konfigurierbares Produkt basierend auf einem beliebigen Attribut mit zwei Varianten (V1 und V2).
   * Fügen Sie dem Attributsatz mit den konfigurierbaren Varianten das Attribut *Ja/Nein* hinzu.
   * Setzen Sie für eine der Varianten (V1) den Wert auf *[!UICONTROL Yes]* auf der nicht standardmäßigen Website (W2).
1. Erstellen Sie eine Katalogregel:
   * Auf beide Websites angewendet
   * Bedingung: *Ja/Nein* Attributwert ist *[!UICONTROL Yes]*
   * Rabatt = 50 %
1. Öffnen Sie das konfigurierbare Produkt auf der nicht standardmäßigen Website (W2).
1. Vergewissern Sie sich, dass auf die V1-Variante der 50 %-Rabatt angewendet wird.
1. Öffnen Sie die V1-Variante im Adobe Commerce Admin.
   * Zur Standardwebsite wechseln
   * Nehmen Sie keine Änderungen vor und speichern Sie das Produkt
1. Aktualisieren Sie die konfigurierbare Produkt-Storefront-Seite.

<u>Erwartete Ergebnisse</u>:

Für die V1-Variante wird weiterhin der 50-%-Rabatt angewendet, da keine Änderungen vorgenommen wurden.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt verschwindet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
