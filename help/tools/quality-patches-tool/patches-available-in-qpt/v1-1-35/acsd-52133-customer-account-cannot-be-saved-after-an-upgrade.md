---
title: 'ACSD-52133: Kundenkonto kann nach einem Upgrade nicht gespeichert werden'
description: Wenden Sie den Patch ACSD-52133 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann.
feature: Customers, Upgrade
role: Admin
exl-id: 4a0e6ed8-3e35-40ce-bb49-8ccfcde437a0
source-git-commit: 82667023bbaa9d725eb52dacb8bd47042bdfe028
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-52133: Kundenkonto kann nach einem Upgrade nicht gespeichert werden

>[!NOTE]
>
>Dieser Patch wird aufgrund eines Konflikts mit dem Sicherheits-Patch nicht mehr unterstützt ([-08](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08).

Mit dem Patch ACSD-52133 wird das Problem behoben, dass ein Kundenkonto nach einem Upgrade nicht gespeichert werden kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52133. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Kundenkonto kann nach einem Upgrade nicht gespeichert werden.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce Version 2.4.4.
1. Erstellen Sie einen Kunden.
1. Aktualisieren Sie Adobe Commerce auf 2.4.6 von der früheren Version 2.4.4, in der bereits ein Kunde erstellt wurde.
1. Legen Sie den Verschlüsselungsschlüssel in `env.php` wie folgt fest:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Legen Sie die folgenden Werte für jeden Kunden unter der `customer_entity` in die Datenbank fest:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bearbeiten Sie den Kunden, für den die oben genannten Werte aktualisiert wurden.
1. Klicken Sie auf **[!UICONTROL Save Customer]** oder **[!UICONTROL Save and Continue Edit]**

<u>Erwartete Ergebnisse</u>:

Der Kunde wurde erfolgreich und fehlerfrei gespeichert.

<u>Tatsächliche Ergebnisse</u>:

* Der Kundendatensatz wird nicht gespeichert.
* Der Administrator sieht die folgende Fehlermeldung: *Beim Speichern des Kunden ist ein Fehler aufgetreten.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
