---
title: 'ACSD-53824: Bereitstellung schlägt beim Setup-Upgrade fehl'
description: Wenden Sie den ACSD-53824-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Bereitstellung beim Setup-Upgrade fehlschlägt
feature: Attributes, Upgrade
role: Admin, Developer
exl-id: 9038190b-5779-47b5-b4fb-ccd0a769dc61
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%
---
# ACSD-53824: Bereitstellung schlägt beim Setup-Upgrade fehl

Mit dem Patch ACSD-53824 wird das Problem behoben, dass die Bereitstellung beim Setup-Upgrade fehlschlägt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.38 installiert ist. Die Patch-ID ist ACSD-53824. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - P2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bereitstellung schlägt beim Setup-Upgrade fehl.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie die Infrastruktur mit **[!DNL MariaDB]** auf dem Galera-Cluster.
1. Stellen Sie die `wsrep_max_ws_size` auf *2 GB* ein.
1. Neue Adobe Commerce-Instanz installieren
1. Spannvorrichtungen aus Profil mittlerer Leistung erzeugen:
   `php bin/magento setup:performance:generate-fixtures -s setup/performance-toolkit/profiles/ee/medium.xml`
1. Generieren Sie mehr als **12000** Attribute mit Mehrfachauswahl.
1. Verwenden Sie dann den `Run setup: Upgrade`.

<u>Erwartete Ergebnisse</u>:

Die `setup:upgrade` wird fehlerfrei abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Die `setup:upgrade` schlägt mit [!DNL MySQL] Fehlern fehl:

`Allowed memory size of 6442450944 bytes exhausted in ../module-catalog/Setup/Patch/Data/UpdateMultiselectAttributesBackendTypes.php`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
