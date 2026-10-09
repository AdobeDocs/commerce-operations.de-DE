---
title: 'ACSD-56515: Admin mit Berechtigungen auf Website-Ebene kann [!UICONTROL Dynamic Block] nicht bearbeiten'
description: Wenden Sie den ACSD-56515-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Admins mit Berechtigungen auf Website-Ebene die [!UICONTROL Dynamic Block] nicht hinzufügen oder bearbeiten können.
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: dd3e61a4-aba4-4f86-b4fe-88ca4276ace5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '384'
ht-degree: 0%
---
# ACSD-56515: Admin mit Berechtigungen auf Website-Ebene kann [!UICONTROL Dynamic Block] nicht bearbeiten

Mit dem Patch „ACSD-56515“ wird das Problem behoben, dass Admins mit Berechtigungen auf Website-Ebene die [!UICONTROL Dynamic Block] nicht hinzufügen oder bearbeiten können. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56515. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator bzw. die Administratorin mit Berechtigungen auf Website-Ebene kann die [!UICONTROL Dynamic Block] nicht hinzufügen oder bearbeiten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine sekundäre Website mit Store und StoreReview.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]** und erstellen Sie eine Benutzerrolle, die auf den sekundären Website-Umfang mit allen verfügbaren Ressourcen beschränkt ist.
1. Erstellen Sie einen Admin-Benutzer mit der oben erstellten Rolle.
1. Melden Sie sich mit dem eingeschränkten Admin-Benutzer an und erstellen Sie ein [!UICONTROL Dynamic Block].

<u>Erwartete Ergebnisse</u>:

Der Administrator bzw. die Administratorin mit Einschränkungen für die Website kann eine [!UICONTROL Dynamic Block] erstellen.

<u>Tatsächliche Ergebnisse</u>:

Es wird folgender Fehler angezeigt: *Weitere Berechtigungen sind erforderlich, um dieses Element anzuzeigen*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
