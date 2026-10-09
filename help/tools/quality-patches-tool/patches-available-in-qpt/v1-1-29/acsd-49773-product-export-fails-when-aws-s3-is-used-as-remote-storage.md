---
title: 'ACSD-49773: Der Produktexport schlägt fehl, wenn AWS S3 als Remote-Speicher verwendet wird'
description: Wenden Sie den Patch ACSD-49773 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktexport fehlschlägt, wenn AWS S3 als Remote-Speicher verwendet wird.
feature: Data Import/Export, Iaas, Products, Storage
role: Admin
exl-id: 82f1299f-52b6-4f87-b01c-072d1661c022
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
subfeature_v2:
  - id: df5e974b-6742-4873-a687-a6bedaafdaa2
    internal-label: IaaS
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%
---
# ACSD-49773: Der Produktexport schlägt fehl, wenn AWS S3 als Remote-Speicher verwendet wird

Mit dem Patch ACSD-49773 wird das Problem behoben, dass der Produktexport fehlschlägt, wenn AWS S3 als Remote-Speicher verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49773. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Produktexport schlägt fehl, wenn AWS S3 als Remote-Speicher verwendet wird.

<u>Schritte zur Reproduktion</u>:

1. Installieren eines großen Datenprofils.
1. Erstellen Sie ein AWS-Konto und konfigurieren Sie einen S3-Bucket und einen IAM-Benutzer.
1. Aktualisieren Sie `app/etc/env.php` mit den Konfigurationen.
1. `bin/magento setup:upgrade` ausführen.
1. Wechseln Sie zum Backend und führen Sie einen vollständigen Produktexport durch.
1. Überwachen Sie den Status der Warteschlangenmeldung aus der `[queue_message_status]`.
1. Überprüfen Sie die Systemprotokolle.

<u>Erwartete Ergebnisse</u>:

Der Produktexport wird fehlerfrei abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

In den Systemprotokollen wird ein Fehler protokolliert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
