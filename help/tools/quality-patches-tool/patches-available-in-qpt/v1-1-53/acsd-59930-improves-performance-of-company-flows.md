---
title: 'ACSD-59930: Verbessert die Leistung der Unternehmensflüsse'
description: Wenden Sie den Patch ACSD-59930 an, um das Adobe Commerce-Problem zu beheben, bei dem im Admin-Bedienfeld ein *Zeitüberschreitungsfehler* angezeigt wird, wenn ein Unternehmen mit einem Administrator erstellt, gespeichert oder gelöscht wird, das *1000+* Adressen im Adressbuch hat.
feature: Customers, B2B
role: Admin, Developer
exl-id: eaa6c78d-13e3-439d-90f7-70c1c96c3197
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930: Verbessert die Leistung der Unternehmensflüsse

Mit dem Patch ACSD-59930 *wird das Problem behoben, dass im Admin* Bedienfeld der Fehler „Zeitüberschreitung“ angezeigt wird, wenn ein Unternehmen mit einem Administrator erstellt, gespeichert oder gelöscht wird, dessen Adressbuch *1000+* Adressen enthält. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53 installiert ist. Die Patch-ID ist ACSD-59930. Dieses Problem wird voraussichtlich in Adobe Commerce B2B-1.5.0 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Verbessert die Leistung der Flüsse zum Erstellen, Speichern und Löschen des Unternehmens.

<u>Voraussetzungen:</u>:

Installieren und Aktivieren von Adobe Commerce B2B-Modulen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Kunden mit *1000+* Adressen im *[!UICONTROL Address Book]*.
1. Erstellen Sie eine Firma und verwenden Sie den oben genannten Kunden als Administrator.
1. Rette die Firma.

<u>Erwartete Ergebnisse</u>:

Das Unternehmen wurde erfolgreich erstellt, ohne dass Zeitüberschreitungsfehler angezeigt wurden.

<u>Tatsächliche Ergebnisse</u>:

Ein Zeitüberschreitungsfehler wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
