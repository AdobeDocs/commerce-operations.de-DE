---
title: 'ACSD-52277: Admin-Benutzer wurde bei der Auswahl der Shop-Ansicht beim Erstellen einer neuen Bestellung falsch umgeleitet'
description: Wenden Sie den ACSD-52277 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem ein Administrator-Benutzer nicht ordnungsgemäß umgeleitet wird, nachdem Sie beim Erstellen einer neuen Bestellung in Admin Store View ausgewählt haben.
exl-id: 61ef59a9-7a31-441f-a763-2d8016498fa7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52277: Admin-Benutzer wurde bei der Auswahl der Shop-Ansicht beim Erstellen einer neuen Bestellung falsch umgeleitet

Der Patch ACSD-52277 behebt das Problem, dass ein Admin-Benutzer nicht ordnungsgemäß umgeleitet wird, nachdem er Store View ausgewählt hat, wenn er eine neue Bestellung in Admin erstellt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 installiert ist. Die Patch-ID ist ACSD-52277. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Administrator bzw. eine Administratorin wird nicht ordnungsgemäß umgeleitet, nachdem er bzw. sie beim Erstellen einer neuen Bestellung die Option „Store-Ansicht“ ausgewählt hat.

<u>Schritte zur Reproduktion</u>

1. Installieren Sie eine neue Instanz.
1. Erstellen Sie ein Produkt.
1. Erstellen Sie eine zusätzliche Website, einen Store und zwei Store-Ansichten.
1. Erstellen Sie eine Bestellung bei Admin durch Auswahl von *Store-Ansicht 1*.

<u>Erwartete Ergebnisse</u>:

Der/die Benutzende wird zur Bestellseite weitergeleitet.

<u>Tatsächliche Ergebnisse</u>:

Der/die Benutzende wird nach Auswahl der Store-Ansicht nicht zur Bestellseite weitergeleitet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
