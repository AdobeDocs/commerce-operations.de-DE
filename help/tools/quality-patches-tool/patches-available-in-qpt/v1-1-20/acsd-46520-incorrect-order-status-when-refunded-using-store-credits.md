---
title: 'ACSD-46520: Unrichtiger Bestellstatus bei Rückerstattung mittels Gutschriften für Geschäfte'
description: Dieser Artikel bietet eine Lösung für das Problem, dass Benutzer einen falschen Bestellstatus erhalten, wenn sie mit Store-Gutschriften zurückerstattet werden.
feature: Orders, Returns
role: Admin
exl-id: 67740003-a71e-41bf-afda-ca3e32290115
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-46520: Unrichtiger Bestellstatus bei Rückerstattung mittels Gutschriften für Geschäfte

Der Patch ACSD-46520 löst das Problem, dass Benutzer einen falschen Bestellstatus erhalten, wenn sie mit Store-Gutschriften zurückerstattet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46520. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 und 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer erhalten einen falschen Bestellstatus, wenn sie mit Gutschriften zurückerstattet werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Kundenkonto in der Storefront und melden Sie sich an.
1. Weisen Sie dem Kunden vom Administrator Store-Gutschriften zu. Die Gutschriften aus dem Geschäft sollten die gesamte Bestellung abdecken.
1. Bestellung unter Verwendung der Gutscheine.
1. Rechnungsstellung.
1. Erstellen Sie ein Kreditmemo, um den vollen Betrag der Bestellung zurückzuerstatten.
Aktivieren Sie das Kontrollkästchen **[!UICONTROL Refund to store credit]** .
1. Überprüfen Sie den Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Der Bestellstatus lautet *Geschlossen*.

<u>Tatsächliche Ergebnisse</u>:

Der Bestellstatus lautet *Abgeschlossen*, was nicht dem korrekten Status entspricht.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder [!DNL Magento Open Source] vor Ort: [Tools für Qualitätsmuster > Nutzung](/help/tools/quality-patches-tool/usage.md) im Handbuch zum Werkzeug für Qualitätsmuster.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie anhand von  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch zum Werkzeug für Qualitätsmuster.
