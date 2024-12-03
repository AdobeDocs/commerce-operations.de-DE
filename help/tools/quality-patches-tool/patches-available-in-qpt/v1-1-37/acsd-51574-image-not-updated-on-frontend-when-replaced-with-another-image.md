---
title: 'ACSD-51574: Bild wird nicht auf der Vorderseite aktualisiert, wenn es durch ein anderes Bild ersetzt wird'
description: Wenden Sie den Patch ACSD-51574 an, um das Adobe Commerce-Problem zu beheben, bei dem das Bild nicht auf der Vorderseite aktualisiert wird, nachdem es durch ein anderes Bild ersetzt wurde.
feature: Configuration
role: Admin
exl-id: 199674fc-c3b3-4fee-9061-f0546833c1cd
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-51574: Bild wird nicht auf der Vorderseite aktualisiert, wenn es durch ein anderes Bild ersetzt wird

Der Patch ACSD-51574 behebt das Problem, dass das Bild nicht auf der Vorderseite aktualisiert wird, nachdem es durch ein anderes Bild ersetzt wurde. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-51574. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Bild wird nicht auf der Vorderseite aktualisiert, nachdem es durch ein anderes Bild ersetzt wurde.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt mit einigen Bildern.
1. Bearbeiten Sie das Produkt und laden Sie ein Bild mit einem bekannten Namen hoch (Beispiel: *image.jpg*).
1. Speichern Sie das Produkt.
1. Bearbeiten Sie das Produkt erneut, löschen Sie die alte Version des Bildes und laden Sie die neue Version des Bildes mit demselben Namen hoch. **Stellen Sie sicher, dass sich die neue Version deutlich von dem Problem unterscheidet.**
1. Speichern Sie das Produkt. Sowohl Admin als auch Frontend zeigen die Bilder an.
1. Bearbeiten Sie das Produkt erneut und laden Sie dasselbe neue Bild erneut hoch (unter demselben Namen).
1. Speichern Sie das Produkt und überprüfen Sie die Produktseite auf der Vorderseite.

<u>Erwartete Ergebnisse</u>:

Das beim zweiten Mal hochgeladene Bild sollte das neue Bild zusammen mit dem umbenannten Bildnamen sein.

<u>Tatsächliche Ergebnisse</u>:

Das beim zweiten Mal hochgeladene Bild ist die zuvor gelöschte ältere Version des Bildes anstelle des gleichen neuen Bildes.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
