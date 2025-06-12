---
title: 'ACSD-52831: Bei aktiviertem  [!DNL Google reCAPTCHA v3 Invisible]  können keine verhandelbaren Angebotsaufträge platziert werden'
description: Wenden Sie den ACSD-52831 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Sie keine verhandelbaren Angebotsbestellungen aufgeben können, wenn  [!DNL Google reCAPTCHA v3 Invisible]  aktiviert ist.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: fa09e41f-f6c3-4cc7-a814-0e1ac5e9ea2e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-52831: Bei aktivierter [!DNL Google reCAPTCHA v3 Invisible] können keine verhandelbaren Angebotsaufträge platziert werden

Mit dem Patch ACSD-52831 wird das Problem behoben, dass bei aktiviertem [!DNL Google reCAPTCHA v3 Invisible] keine verhandelbaren Angebotsaufträge erteilt werden können. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52831. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei aktiviertem [!DNL Google reCAPTCHA v3 Invisible] können keine verhandelbaren Angebotsaufträge platziert werden.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die B2B-Angebotsfunktion.
1. Aktivieren Sie [!DNL Google reCAPTCHA v3 Invisible] in der Storefront, um Checkout/Bestellung aufgeben zu können.
1. Erstellen Sie ein Angebot und fahren Sie mit diesem Angebot zur Kasse.
1. Aufgrund des CAPTCHA-Fehlers ist es nicht möglich, eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

Das Angebot geht zur Kasse.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die Fehlermeldung *reCAPTCHA-Validierung fehlgeschlagen, versuchen Sie es erneut*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
