---
title: Invisible [!DNL reCAPTCHA] schlägt beim Checkout fehl und verhindert die Auftragserteilung
description: Wenden Sie den Patch ACSD-54656 an, um das Adobe Commerce-Problem zu beheben, bei  [!DNL reCAPTCHA]  das unsichtbare Element beim Checkout nicht ordnungsgemäß funktioniert, was die Platzierung einer Bestellung verhindert.
feature: Checkout, Gift
role: Admin, Developer
exl-id: 08850189-2e1b-4132-8d63-ce447b1f1211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-54656: Invisible [!DNL reCAPTCHA] funktioniert beim Checkout nicht richtig, was die Platzierung einer Bestellung verhindert.

Mit dem Patch ACSD-54656 wird das Problem behoben, dass das unsichtbare [!DNL reCAPTCHA] beim Checkout nicht ordnungsgemäß funktioniert, was die Platzierung einer Bestellung verhindert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46 installiert ist. Die Patch-ID ist ACSD-54656. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Unsichtbare [!DNL reCAPTCHA] funktionieren beim Checkout nicht richtig, was die Platzierung einer Bestellung verhindert.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie auf der [!UICONTROL Checkout]-Seite jede Art von [!DNL reCAPTCHA] für Geschenkkarten.
1. Fügen Sie das Produkt zum Warenkorb hinzu und gehen Sie zur Seite **[!UICONTROL Checkout]** .
1. Erweitern Sie das Geschenkgutscheinformular und füllen Sie einen gültigen Geschenkgutschein aus.
1. Klicken Sie auf **[!UICONTROL See balance and apply]** Schaltfläche.

<u>Erwartete Ergebnisse</u>:

Geschenkkarte wurde erfolgreich angewendet.

<u>Tatsächliche Ergebnisse</u>:

Es wird eine Fehlermeldung angezeigt: *[!DNL reCAPTCHA]Validierung fehlgeschlagen. Bitte erneut versuchen*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
