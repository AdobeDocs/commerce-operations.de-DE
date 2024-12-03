---
title: 'ACSD-59930: Verbessert die Leistung der Flüsse des Unternehmens'
description: Wenden Sie den Patch ACSD-59930 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Erstellen, Speichern oder Löschen eines Unternehmens mit einem Administrator, der über * 1000+* Adressen im Adressbuch verfügt, im Admin-Bedienfeld ein *Timeout*-Fehler angezeigt wird.
feature: Customers, B2B
role: Admin, Developer
exl-id: eaa6c78d-13e3-439d-90f7-70c1c96c3197
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930: Verbessert die Leistung der Flüsse des Unternehmens

Der Patch ACSD-59930 behebt das Problem, dass beim Erstellen, Speichern oder Löschen eines Unternehmens mit einem Administrator, der über *1000+* -Adressen im Adressbuch verfügt, im Admin-Bedienfeld ein Fehler vom Typ *Timeout* angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53 installiert ist. Die Patch-ID ist ACSD-59930. Bitte beachten Sie, dass dieses Problem in Adobe Commerce B2B-1.5.0 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Verbessert die Leistung der Erstellungs-, Speichern- und Löschvorgänge des Unternehmens.

<u>Voraussetzungen:</u>:

Installieren und aktivieren Sie die Adobe Commerce B2B-Module.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Kunden mit den Adressen *1000+* im Ordner *[!UICONTROL Address Book]*.
1. Erstellen Sie ein Unternehmen und verwenden Sie den obigen Kunden als Administrator.
1. Speichern Sie das Unternehmen.

<u>Erwartete Ergebnisse</u>:

Das Unternehmen wurde erfolgreich erstellt, ohne dass Timeout-Fehler angezeigt wurden.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein Timeout-Fehler angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
