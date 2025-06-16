---
title: 'ACSD-66093: In den Feldern für den Gast-Kundennamen ist eine E-Mail-Eingabe zulässig, die zu ungültigen Bestell-E-Mails führt'
description: Wenden Sie den Patch ACSD-66093 an, um das Adobe Commerce-Problem zu beheben, bei dem es möglich ist, E-Mail-Adressen in die Felder Gastkunde **[!UICONTROL First Name]** und **[!UICONTROL Last Name]** einzugeben und ungültige E-Mails zur Bestellbestätigung zu senden.
feature: Checkout
role: Admin, Developer
source-git-commit: 6ee2f99b53424071fda4cba9396aa039621135fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---


# ACSD-66093: In den Feldern für den Gast-Kundennamen ist eine E-Mail-Eingabe zulässig, die zu ungültigen Bestell-E-Mails führt

Mit dem Patch ACSD-66093 wird das Problem behoben, dass E-Mail-Adressen in die Felder **[!UICONTROL First Name]** und **[!UICONTROL Last Name]** des Gastkunden eingegeben werden konnten, was zu ungültigen E-Mails zur Bestellbestätigung führte. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 installiert ist. Die Patch-ID ist ACSD-66093. Beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p11

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

E-Mail-Adressen konnten in die Felder **[!UICONTROL First Name]** und **[!UICONTROL Last Name]** des Gastkunden eingegeben werden, was zu ungültigen E-Mails zur Bestellbestätigung führte.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie Produkte als Gastkunde zum Warenkorb hinzu.
2. Zur Kasse gehen.
3. Füllen Sie die E-Mail-Adresse mit &quot;test1@gmail.co&quot; aus.
4. **[!UICONTROL First Name]** mit &quot;<test2@gmail.co>&quot; ausfüllen.
5. **[!UICONTROL Last Name]** mit &quot;<test3@gmail.co>&quot; ausfüllen.
6. Füllen Sie andere erforderliche Felder aus.
7. Bestellung aufgeben.

<u>Erwartete Ergebnisse</u>:

Validierungsmeldungen sollten angezeigt werden, die darauf hinweisen, dass die **[!UICONTROL First Name]**- und **[!UICONTROL Last Name]**-Felder ungültig sind, z *B. „Vorname ist ungültig! und Nachname ist ungültig!* und die Bestellung sollte nicht aufgegeben werden.

<u>Tatsächliche Ergebnisse</u>:

Bestellung wird aufgegeben.
**[!UICONTROL First Name]** und **[!UICONTROL Last Name]** Felder werden wie eingegeben gespeichert.
Die E-Mail zur Bestellbestätigung wird an alle drei E-Mails gesendet: test1@gmail.co, test2@gmail.co und test3@gmail.co.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
