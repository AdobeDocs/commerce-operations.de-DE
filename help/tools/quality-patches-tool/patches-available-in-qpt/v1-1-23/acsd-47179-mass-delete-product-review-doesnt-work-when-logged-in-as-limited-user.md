---
title: 'ACSD-47179: Massenlöschung von Produktüberprüfungen funktioniert nicht, wenn als eingeschränkte Benutzerrolle angemeldet.'
description: Wenden Sie den Patch ACSD-47179 an, um das Adobe Commerce-Problem zu beheben, bei dem das Massenlöschen von Produktüberprüfungen nicht funktioniert, wenn Sie als eingeschränkte Benutzerrolle angemeldet sind.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
exl-id: 7131ee47-fadc-4e93-b8b2-5b2e0521ad97
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179: Massenlöschung von Produktüberprüfungen funktioniert nicht, wenn als eingeschränkte Benutzerrolle angemeldet.

Der Patch ACSD-47179 behebt das Problem, dass das Massenlöschen von Produktüberprüfungen nicht funktioniert, wenn sie als eingeschränkte Benutzerrolle angemeldet sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 installiert ist. Die Patch-ID ist ACSD-47179. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das gebündelte Löschen von Produktüberprüfungen funktioniert nicht, wenn Sie als eingeschränkte Benutzerrolle angemeldet sind.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine sekundäre Website.
1. Erstellen Sie eine Benutzerrolle, die auf die sekundäre Website beschränkt ist und über die vollständige Berechtigung für die folgenden Abschnitte verfügt:
   * Katalog
   * Kunde
   * Marketing
1. Erstellen Sie ein Produkt und weisen Sie es der sekundären Website zu.
1. Fügen Sie dem Produkt zwei Bewertungen vom Frontend hinzu.
1. Melden Sie sich mit dem soeben erstellten eingeschränkten Administratorbenutzer bei [!DNL Commerce] Admin an.
1. Versuchen Sie, ausstehende Überprüfungen gebündelt zu löschen.

<u>Erwartete Ergebnisse</u>:

Ein Administrator mit ausreichenden Berechtigungen kann ausstehende Prüfungen in großem Umfang löschen.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler: _Irgendetwas ist schiefgelaufen. Ausnahme, die in support_report.log_ generiert wurde

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
