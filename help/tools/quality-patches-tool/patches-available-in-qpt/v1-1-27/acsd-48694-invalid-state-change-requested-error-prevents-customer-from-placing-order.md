---
title: 'ACSD-48694: Fehler wegen ungültiger Statusänderung angefordert verhindert, dass der Kunde eine Bestellung aufgibt'
description: Wenden Sie den Patch ACSD-48694 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler „Ungültige Statusänderung angefordert“ einen Kunden daran hindert, eine Bestellung aufzugeben.
feature: Admin Workspace, Orders
role: Admin
exl-id: 6b9fa474-1d9d-411d-bbca-ce7463cfeb0d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-48694: *Ungültige Statusänderung angefordert* Fehler verhindert, dass der Kunde eine Bestellung aufgibt

Der Patch ACSD-48694 behebt das Problem, dass der Fehler *Ungültige Statusänderung angefordert* einen Kunden daran hindert, eine Bestellung aufzugeben. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 installiert ist. Die Patch-ID ist ACSD-48694. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Fehler *Ungültige Statusänderung angefordert* verhindert, dass ein Kunde eine Bestellung aufgibt.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie eine leichte Verzögerung während der `/estimate-shipping-methods` hinzu, indem Sie eine `sleep()` bei `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` Funktion einbeziehen, sodass die `/estimate-shipping-methods` Anfrage nach der `/shipping-information` abgeschlossen wird, wenn Sie während des Checkouts vom Versandschritt zum Zahlungsschritt wechseln.
1. Konfigurieren Sie die Sitzung so, dass [!DNL Redis] mit der Einstellung *disable_locking: 1* verwendet wird.
1. Öffnen Sie **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** und aktivieren Sie *[!UICONTROL Persistent Shopping Cart]*.
1. Melden Sie sich als Kunde an und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Lassen Sie die Kundensitzung ablaufen. Das persistente Cookie und der Warenkorb bleiben bestehen.
1. Gehen Sie nun zur Kasse, fügen Sie die Lieferadresse hinzu und navigieren Sie zum Abschnitt Zahlung .
1. Gehen Sie zurück zur Startseite oder zu einer anderen Seite und melden Sie sich mit dem Kundenkonto an.
1. Die Sitzung soll erneut ablaufen.
1. Gehen Sie nun direkt zur Kasse und navigieren Sie zum Schritt Zahlung .
1. Versuchen Sie, die Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

* Es liegt kein Fehler vor.
* Die Bestellung wurde erfolgreich aufgegeben und *Seite „Vielen*&quot; wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der Fehler *Ungültige Statusänderung angefordert* wird angezeigt, aber die Bestellung wird aufgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
