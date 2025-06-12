---
title: 'ACSD-50512: Fehler beim Aktualisieren des Startdatums für ein herunterladbares Produkt-Staging-Update'
description: Wenden Sie den ACSD-51892-Patch an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem der Fehler *Der herunterladbare Link bezieht sich nicht auf das Produkt.Überprüfen Sie den Link und versuchen Sie es erneut*, tritt beim Aktualisieren des Startdatums für ein herunterladbares Produkt-Staging-Update auf.
feature: Products, Staging
role: Admin
exl-id: 9c3b4d45-c500-46a7-8679-a8aa9e0a66d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-50512: Fehler beim Aktualisieren des Startdatums für das herunterladbare Produkt-Staging-Update

Mit dem Patch ACSD-50512 wird das Problem behoben, bei dem der Fehler *Der herunterladbare Link bezieht sich nicht auf das Produkt. Überprüfen Sie den Link und versuchen Sie es erneut* dies tritt auf, wenn Sie das Startdatum für ein herunterladbares Produkt-Staging-Update aktualisieren. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51502. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Fehler *Der herunterladbare Link ist nicht mit dem Produkt verknüpft. Überprüfen Sie den Link und versuchen Sie es erneut* dies tritt auf, wenn Sie das Startdatum für ein herunterladbares Produkt-Staging-Update aktualisieren.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein herunterladbares Produkt mit *herunterladbaren Links* und *Beispiel-Links*.
1. Erstellen Sie eine geplante Aktualisierung für dasselbe Produkt und speichern Sie das Produkt.
1. Bearbeiten Sie das vorkonfigurierte geplante Update (ab Schritt 2) und ändern Sie das Startdatum.
1. Speichern Sie die geplante Aktualisierung.

<u>Erwartete Ergebnisse</u>:

Die Änderungen am geplanten Update wurden erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *Der herunterladbare Link ist nicht mit dem Produkt verknüpft. Link überprüfen und erneut*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
