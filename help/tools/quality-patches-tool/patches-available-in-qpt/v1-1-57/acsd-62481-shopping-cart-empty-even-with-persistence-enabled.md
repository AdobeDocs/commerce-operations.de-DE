---
title: 'ACSD-62481: Der Warenkorb bleibt auch bei aktiviertem [!UICONTROL Persistence] leer'
description: Wenden Sie den Patch ACSD-62481 an, um das Adobe Commerce-Problem zu beheben, bei dem die Warenkorbfunktion bei Verwendung des Anmelde-Popup während des Auscheckens fehlschlägt.
feature: Shopping Cart, Checkout
role: Admin, Developer
exl-id: 79fb3161-f56e-45f3-9933-cf95703f1554
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-62481: Der Warenkorb bleibt auch bei aktiviertem *[!UICONTROL Persistence]* leer

Mit dem Patch ACSD-62481 wird das Problem behoben, dass die Funktion „Warenkorb beibehalten“ bei Verwendung des Anmelde-Popups während des Auscheckens fehlschlägt, da das Kontrollkästchen &quot;*[!UICONTROL Remember Me]*&quot; fehlt und Produkte nach dem Abmelden aus dem Warenkorb verschwinden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62481. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Funktion für persistente Warenkörbe schlägt fehl, wenn das Anmelde-Popup während des Auscheckens verwendet wird, da das Kontrollkästchen *[!UICONTROL Remember Me]* fehlt. Dies führt dazu, dass Produkte nach dem Abmelden aus dem Warenkorb verschwinden.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie im Admin-Bereich das Gastkonto und die Einstellungen für den persistenten Warenkorb wie folgt:

   * Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** und setzen Sie *[!UICONTROL Allow Guest Checkout]* auf *Nein*.

      * Klicken Sie auf **[!UICONTROL Save Config]**.

   * Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]** und setzen Sie *[!UICONTROL Enable Persistence]* auf *Ja*.
   * Belassen Sie alle anderen Einstellungen als Standard, ändern Sie *[!UICONTROL Clear Persistence on Sign Out]* jedoch in *Nein*.

      * Klicken Sie auf **[!UICONTROL Save Config]**.

1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]** , um ein einfaches Produkt zum Katalog hinzuzufügen.

   * Füllen Sie die erforderlichen Mindestdetails aus und stellen Sie sicher, dass sie auf Lager sind.

1. Erstellen Sie im Frontend ein Kundenkonto mit dem Hauptformular `(../customer/account/create/)` und melden Sie sich ab.
1. Fügen Sie das Produkt als Gast zum Warenkorb hinzu.
1. Öffnen Sie den Mini-Warenkorb mit dem Symbol oben rechts und klicken Sie dann auf **[!UICONTROL View and Edit Cart]**.
1. Zur Kasse gehen.
1. Melden Sie sich über das eingeblendete Popup-Dialogfeld beim neuen Kundenkonto an und melden Sie sich ab.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb enthält die Produkte des zuvor angemeldeten Benutzers.

<u>Tatsächliche Ergebnisse</u>:

* Der Warenkorb ist leer.
* Das Popup-Anmeldedialogfeld zeigt die *[!UICONTROL Remember Me]* nicht an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: Upgrades und Patches > Anwenden von Patches im Handbuch zu Commerce in Cloud-Infrastruktur .

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
