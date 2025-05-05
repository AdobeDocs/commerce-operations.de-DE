---
title: 'ACSD-63870: Kunde hat sich während der Änderung des Unternehmensstatus nicht ordnungsgemäß abgemeldet'
description: Wenden Sie den Patch ACSD-63870 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Firmenkunde nicht ordnungsgemäß abgemeldet wird, wenn sich der Unternehmensstatus während einer aktiven Kundensitzung ändert.
feature: Customers, B2B, Companies
role: Admin, Developer
source-git-commit: 3544eaef7812524a098e851ac8a2c140f33f7668
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# ACSD-63870: Kunde hat sich während der Änderung des Unternehmensstatus nicht ordnungsgemäß abgemeldet

Mit dem Patch ACSD-63870 wird das Problem behoben, dass ein Firmenkunde nicht ordnungsgemäß abgemeldet wird, wenn sich der Unternehmensstatus während einer aktiven Kundensitzung ändert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 installiert ist. Die Patch-ID ist ACSD-63870. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Fehler bei der Kundenabmeldung, wenn der Unternehmensstatus während einer aktiven Kundensitzung geändert wird.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren der B2B-Funktionalität.
1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie eine neue Firma und markieren Sie sie als *Aktiv*.
1. Melden Sie sich als Unternehmensbenutzer an und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Gehen Sie bis zum [!UICONTROL Shipping Address] Schritt zur Kasse. Geben Sie die Adresse nicht ein.
1. Wechseln Sie zu „Admin“ und ändern Sie den Unternehmensstatus in *Ausstehende Genehmigung*.
1. Gehen Sie zurück zum Frontend und füllen Sie die Lieferadresse aus.

<u>Erwartete Ergebnisse</u>:

Kunde wurde abgemeldet.

<u>Tatsächliche Ergebnisse</u>:

* Benutzende erhalten den Fehler *Irgendetwas ist schiefgelaufen*.
* `var/log/exception.log` enthält:

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Zusätzliche Schritte nach der Patch-Installation erforderlich

(Dieser Abschnitt ist optional. Nach der Anwendung des Patches sind möglicherweise einige Schritte erforderlich, um das Problem zu beheben.) 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.

