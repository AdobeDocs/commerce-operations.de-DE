---
title: "ACSD-52133: Kundenkonto kann nach einem Upgrade nicht gespeichert werden"
description: Wenden Sie den Patch ACSD-52133 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann.
feature: Customers, Upgrade
role: Admin
source-git-commit: 809defe75d7b218d8085f85ff815472a531040cf
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-52133: Kundenkonto kann nach einem Upgrade nicht gespeichert werden

Der Patch ACSD-52133 behebt das Problem, dass ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52133. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kundenkonto kann nach einem Upgrade nicht gespeichert werden.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce-Version 2.4.4.
1. Erstellen Sie einen Kunden.
1. Aktualisieren Sie Adobe Commerce von der früheren Version 2.4.4 auf 2.4.6, wo bereits ein Kunde erstellt wurde.
1. Legen Sie den Verschlüsselungsschlüssel wie unten in `env.php` fest:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Legen Sie die folgenden Werte für jeden Kunden unter der Tabelle `customer_entity` in der Datenbank fest:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bearbeiten Sie den Kunden, für den die obigen Werte aktualisiert wurden.
1. Klicken Sie auf **[!UICONTROL Save Customer]** oder **[!UICONTROL Save and Continue Edit]**

<u>Erwartete Ergebnisse</u>:

Der Kunde wird erfolgreich ohne Fehler gespeichert.

<u>Tatsächliche Ergebnisse</u>:

* Der Kundendatensatz wird nicht gespeichert.
* Dem Administrator wird die folgende Fehlermeldung angezeigt: *Beim Speichern des Kunden ist etwas schief gelaufen.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] veröffentlicht: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool]-Handbuch, ob der Patch für Ihr Adobe Commerce-Problem verfügbar ist.
* [Best Practices für die Änderung von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Playbook für die Commerce-Implementierung

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
