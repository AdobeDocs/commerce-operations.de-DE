---
title: 'ACSD-54007: Undefinierter Array-Schlüssel _scope-Fehler beim Importieren von Kundendaten'
description: Wenden Sie den Patch ACSD-54007 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Importieren von Kundendaten ein Fehler mit nicht definiertem Array-Schlüssel _scope angezeigt wird.
feature: Data Import/Export
role: Admin, Developer
exl-id: df0fc9f4-1d42-47bc-b161-d2f109996684
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-54007: Undefinierter Array-Schlüssel _scope-Fehler beim Importieren von Kundendaten

Der Patch ACSD-54007 behebt das Problem, dass beim Import von Kundendaten ein Fehler vom Typ *Nicht definierter Array-Schlüssel _scope* auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-54007. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Importieren von Kundendaten wird der Fehler *Undefinierter Array-Schlüssel _scope* angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**, setzen Sie **[!UICONTROL Entity Type]** auf **[!UICONTROL Stock Sources]** und importieren Sie die CSV-Quelldatei (die Quellcode, SKU, Menge und Status enthält).
1. Wählen Sie Kunden und Adressen (einzelne Datei) aus und versuchen Sie, die CSV-Datei zu importieren, die die Adressdetails des Kunden enthält.

<u>Erwartete Ergebnisse</u>:

Du bekommst keine Fehler.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler: *Warnung: Undefinierter Array-Schlüssel &quot;_scope&quot;in /var/www/html/vendor/magento/module-customer-import-export/Model/ResourceModel/Import/CustomerComposite/Data.php in Zeile 84*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
