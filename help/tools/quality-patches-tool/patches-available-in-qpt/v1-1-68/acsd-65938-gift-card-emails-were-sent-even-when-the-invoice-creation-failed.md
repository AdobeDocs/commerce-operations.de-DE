---
title: 'ACSD-65938: E-Mails zu Geschenkkarten werden auch dann gesendet, wenn die Rechnungserstellung fehlgeschlagen ist'
description: Wenden Sie den Patch ACSD-65938 an, um das Problem zu beheben, dass E-Mails mit Geschenkgutscheinen gesendet wurden, bevor die Rechnung erfolgreich gespeichert und übergeben wurde, und um sicherzustellen, dass E-Mails nach dem ordnungsgemäßen Speichern der Rechnung ausgelöst werden.
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: a6e85c9a-cbf6-4b4a-927b-43ec2ce827fc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%
---
# ACSD-65938: E-Mails zu Geschenkkarten werden auch dann gesendet, wenn die Rechnungserstellung fehlgeschlagen ist

Der Patch des ACSD-65938 behebt ein Problem, bei dem E-Mails mit Geschenkkarten gesendet wurden, bevor die Rechnung erfolgreich gespeichert und übergeben wurde. Mit dieser Fehlerbehebung werden E-Mails jetzt erst ausgelöst, nachdem die Rechnung erfolgreich gespeichert wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-65938. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Geschenkkarten-E-Mails wurden gesendet, bevor bestätigt wurde, dass die Rechnung erfolgreich erstellt und gespeichert wurde, was dazu führte, dass E-Mails gesendet wurden, auch wenn die Erstellung der Rechnung fehlgeschlagen war.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim **[!UICONTROL Admin]** Panel an.
2. Navigieren Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]** und legen Sie **[!UICONTROL Generate Gift Card Account when Order Item is]** auf *Fakturiert* fest.
3. Erstellen Sie ein neues Geschenkkartenprodukt.
4. Fügen Sie das Geschenkprodukt zum Warenkorb hinzu und fahren Sie mit der **[!UICONTROL checkout]** fort. Sie können **[!UICONTROL Check/Money Order]** als Zahlungsmethode verwenden.
5. Bestellung aufgeben.
6. Ändern Sie die `OrderRepository`, um eine Ausnahme während der Auftragserteilung zu simulieren.
7. Senden Sie eine POST-Anfrage an `rest/default/V1/order/<ORDER_ID>/invoice` mit der folgenden Payload:

   ```json
   {
     "capture": true,
     "notify": true
   }
   ```


<u>Erwartete Ergebnisse</u>:

Wenn die Erstellung der Rechnung fehlschlägt, sollte keine E-Mail mit der Geschenkkarte gesendet werden.

<u>Tatsächliche Ergebnisse</u>:

Die E-Mail mit der Geschenkkarte wird gesendet, obwohl die Erstellung der Rechnung fehlgeschlagen ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
