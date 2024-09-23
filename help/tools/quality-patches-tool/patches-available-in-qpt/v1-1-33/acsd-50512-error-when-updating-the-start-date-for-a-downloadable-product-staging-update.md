---
title: "ACSD-50512: Fehler beim Aktualisieren des Startdatums für ein herunterladbares Produkt-Staging-Update"
description: Wenden Sie den Patch ACSD-51892 an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem der Fehler *Der herunterladbare Link ist nicht mit dem Produkt verknüpft ist. Überprüfen Sie den Link und versuchen Sie es erneut*, tritt auf, wenn das Startdatum für ein herunterladbares Produkt-Staging-Update aktualisiert wird.
feature: Products, Staging
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-50512: Fehler beim Aktualisieren des Startdatums für herunterladbare Produkt-Staging-Update

Der Patch ACSD-50512 behebt das Problem, dass der Fehler *Der herunterladbare Link nicht mit dem Produkt in Verbindung steht. Überprüfen Sie den Link und versuchen Sie es erneut*, tritt beim Aktualisieren des Startdatums für ein herunterladbares Produkt-Staging-Update auf. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51502. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Fehler *Der herunterladbare Link steht nicht im Zusammenhang mit dem Produkt. Überprüfen Sie den Link und versuchen Sie es erneut*, tritt beim Aktualisieren des Startdatums für ein herunterladbares Produkt-Staging-Update auf.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein herunterladbares Produkt mit *herunterladbaren Links* und *Beispiellinks*.
1. Erstellen Sie eine geplante Aktualisierung für dasselbe Produkt und speichern Sie das Produkt.
1. Bearbeiten Sie die vorkonfigurierte geplante Aktualisierung (ab Schritt 2) und ändern Sie das Startdatum.
1. Speichern Sie die geplante Aktualisierung.

<u>Erwartete Ergebnisse</u>:

Die Änderungen an der geplanten Aktualisierung werden erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den Fehler: *Der herunterladbare Link ist nicht mit dem Produkt verbunden. Überprüfen Sie den Link und versuchen Sie es erneut*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
