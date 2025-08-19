---
title: 'ACSD-66149: IPN-Handler gibt *500* für nicht unterstützte Typen zurück'
description: Wenden Sie den Patch ACSD-66149 an, um das Adobe Commerce-Problem zu beheben, bei dem der IPN-Handler nicht unterstützte oder unbekannte IPN-Typen ignoriert, wodurch das Problem nicht protokolliert wird, der Prozess unterbrochen wird und außerdem ein 500-Fehler zurückgegeben wird.
feature: Payments
role: Admin, Developer
source-git-commit: 81e8bf62c026023f71d52c219357bd7911275f69
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# ACSD-66149: IPN-Handler gibt *500* für nicht unterstützte Typen zurück

Der Patch ACSD-66149 behebt das Problem, dass der IPN-Handler (Instant Payment Notification) bei nicht unterstützten oder unbekannten IPN-Typen einen *500*-Fehler zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID ist ACSD-66149. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Problem besteht darin, dass der IPN-Handler bei nicht unterstützten oder unbekannten IPN-Typen einen *500*-Fehler zurückgibt. Es tritt auf, wenn PayPal IPN sendet, wobei einige Felder fehlen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein benutzerdefiniertes Modul, das alle Arten unbekannter IPN-Typen von PayPal emuliert.
1. Erstellen Sie mindestens ein Produkt.
1. Konfigurieren Sie PayPal Express mit Ihren eigenen Anmeldedaten.
1. Bestellen Sie bei PayPal Express.
1. Führen Sie den PayPal-Emulator aus.

<u>Erwartete Ergebnisse</u>:

Der Anwendungs-IPN-Handler ignoriert falsche IPN-Typen und erzeugt keine *500* Fehler:

```Order 000000001: Status processing — HTTP 500```

<u>Tatsächliche Ergebnisse</u>:

Die Anwendung erzeugt viele *500* Fehler bei der Verarbeitung falscher IPNs und verarbeitet sporadisch einige Bestellungen nicht, wenn die erwarteten Felder fehlen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch
