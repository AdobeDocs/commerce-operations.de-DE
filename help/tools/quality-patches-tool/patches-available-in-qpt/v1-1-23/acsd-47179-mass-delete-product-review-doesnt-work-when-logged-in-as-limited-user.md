---
title: 'ACSD-47179: Das massenhafte Löschen von Produktbewertungen funktioniert nicht, wenn Sie als eingeschränkte Benutzerrolle angemeldet sind'
description: Wenden Sie den Patch ACSD-47179 an, um das Adobe Commerce-Problem zu beheben, bei dem die Massenlöschung von Produktüberprüfungen nicht funktioniert, wenn Sie als eingeschränkte Benutzerrolle angemeldet sind.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
exl-id: 7131ee47-fadc-4e93-b8b2-5b2e0521ad97
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179: Das massenhafte Löschen von Produktbewertungen funktioniert nicht, wenn Sie als eingeschränkte Benutzerrolle angemeldet sind

Mit dem Patch ACSD-47179 wird das Problem behoben, dass das massenhafte Löschen von Produktüberprüfungen nicht funktioniert, wenn Sie als eingeschränkte Benutzerrolle angemeldet sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47179. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das massive Löschen von Produktüberprüfungen funktioniert nicht, wenn Sie als eingeschränkte Benutzerrolle angemeldet sind.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine sekundäre Website.
1. Erstellen Sie eine Benutzerrolle, die auf die sekundäre Website mit voller Berechtigung für die folgenden Abschnitte beschränkt ist:
   * Katalog
   * KUNDE
   * Marketing
1. Erstellen Sie ein Produkt und weisen Sie es der sekundären Website zu.
1. Fügen Sie dem Produkt zwei Bewertungen aus dem Frontend hinzu.
1. Melden Sie sich beim [!DNL Commerce] Admin mit dem soeben erstellten eingeschränkten Admin-Benutzer an.
1. Versuchen, ausstehende Überprüfungen massenweise zu löschen.

<u>Erwartete Ergebnisse</u>:

Ein Administrator mit ausreichenden Berechtigungen kann ausstehende Überprüfungen massenweise löschen.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: _Etwas ist schiefgelaufen. In support_report.log generierte Ausnahme_

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
