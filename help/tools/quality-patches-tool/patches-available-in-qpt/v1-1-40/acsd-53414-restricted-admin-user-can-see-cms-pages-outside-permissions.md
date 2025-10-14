---
title: 'ACSD-53414: Administratoren mit eingeschränkter Zugriffsberechtigung können CMS-Seiten außerhalb ihres Zugriffsbereichs anzeigen'
description: Wenden Sie den Patch „ACSD-53414“ an, um das Adobe Commerce-Problem zu beheben, bei dem ein Benutzer mit eingeschränktem Administratorzugriff CMS-Seiten außerhalb seines Berechtigungsbereichs sehen kann.
feature: CMS
role: Admin, Developer
exl-id: 86658336-679b-4fe0-9d26-56064ff0c604
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-53414: Administratoren mit eingeschränkter Zugriffsberechtigung können CMS-Seiten außerhalb ihres Zugriffsbereichs anzeigen

Mit dem Patch „ACSD-53414“ wird das Problem behoben, dass ein Admin-Benutzer mit eingeschränkten Rechten CMS-Seiten außerhalb seines Berechtigungsbereichs sehen kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-53414. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Administratoren mit eingeschränkten Rechten können CMS-Seiten über ihren Berechtigungsbereich hinaus anzeigen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Website („sub_website„), einen Store („sub_store„) und einen Store („storeview„).
1. Erstellen Sie eine Rolle „sub_expert“, die den Umfang von sub_website und sub_store zulässt. Nur die folgenden Berechtigungen zuweisen: [!UICONTROL Dashboard] und [!UICONTROL Pages].
1. Erstellen Sie einen neuen Admin-Benutzer und weisen Sie ihn der Rolle sub_expert zu.
1. Weisen Sie die folgenden CSM-Seiten zu „sub_storeview“ und „Standard-storeview“ zu.

   * [!UICONTROL 404 Not Found] > Untergeordnete Storeview
   * [!UICONTROL 503 Service Unavailable] > Standardmäßige Storeview

1. Melden Sie sich bei Admin mit dem in Schritt 3 erstellten Admin-Benutzer an.
1. Überprüfen Sie das CMS-Seitenraster.

<u>Erwartete Ergebnisse</u>:

*[!UICONTROL 503 Service Unavailable]* Seite ist für den Web-Administrator bzw. die Web-Administratorin nicht sichtbar.

<u>Tatsächliche Ergebnisse</u>:

*[!UICONTROL 503 Service Unavailable]* ist für den Web-Administrator sichtbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
