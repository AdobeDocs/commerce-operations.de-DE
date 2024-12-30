---
title: 'MDVA-43718: Beim Zugriff auf den freigegebenen Katalog wird der Fehler „Verbraucher hat keine Zugriffsberechtigung auf Ressourcen“ angezeigt'
description: Der Patch MDVA-43718 löst das Problem, dass der Fehler *Verbraucher nicht berechtigt ist, auf %resources zuzugreifen.* Wird beim Zugriff auf einen freigegebenen Katalog über eine benutzerdefinierte Integration angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-43718. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Catalog Management
role: Admin
exl-id: 2ced2177-aeff-4c36-8d34-6028539b66bd
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-43718: Beim Zugriff auf den freigegebenen Katalog wird der Fehler „Verbraucher hat keine Zugriffsberechtigung auf Ressourcen“ angezeigt

Der MDVA-43718 Patch löst das Problem, dass der Fehler *Privatkund ist nicht berechtigt, auf %resources zuzugreifen.* wird beim Zugriff auf einen freigegebenen Katalog über eine benutzerdefinierte Integration angezeigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-43718. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Zugriff auf einen freigegebenen Katalog über eine benutzerdefinierte Integration wird der folgende Fehler angezeigt: *Der Benutzer ist nicht berechtigt, auf %resources zuzugreifen*.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Integration über Admin > **System** > **Integration** > **Integration hinzufügen**.
1. Fügen Sie Zugriff auf die folgenden Ressourcen hinzu und aktivieren Sie die Integration:

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog::manage
   * Magento_CATALOG::catalog

1. Verwenden des Integrationszugriffs: `rest/default/V1/sharedCatalog/1`

<u>Erwartete Ergebnisse</u>:

Details zum freigegebenen Katalog werden zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird zurückgegeben:

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
