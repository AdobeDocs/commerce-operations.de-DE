---
title: 'ACSD-51636: Der Unternehmensadministrator bzw. die Unternehmensadministratorin kann keine neuen Benutzenden aus dem Kundenkontoabschnitt hinzufügen'
description: Wenden Sie den Patch ACSD-51636 an, um das Adobe Commerce-Problem zu beheben, bei dem der Unternehmensadministrator keine neuen Benutzer aus dem Abschnitt Kundenkonto hinzufügen kann, obwohl er über alle erforderlichen Rollen und Berechtigungen verfügt.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 46e79ae3-ea24-4cb2-b06e-e82cec33b16c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%
---
# ACSD-51636: Der Unternehmensadministrator bzw. die Unternehmensadministratorin kann keine neuen Benutzenden aus dem Kundenkontoabschnitt hinzufügen

Mit dem Patch ACSD-51636 wird das Problem behoben, dass der Unternehmensadministrator keine neuen Benutzer aus dem Abschnitt Kundenkonto hinzufügen kann, obwohl er über alle erforderlichen Rollen und Berechtigungen verfügt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.34 installiert ist. Die Patch-ID ist ACSD-51636. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Unternehmensadministrator bzw. die Unternehmensadministratorin kann keine neuen Benutzenden aus dem Abschnitt Kundenkonto hinzufügen, obwohl er bzw. sie über alle erforderlichen Rollen und Berechtigungen verfügt.

Voraussetzungen:

* B2B-Modul ist installiert.
* Die Unternehmensfunktion ist aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Firma.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bearbeiten Sie **[!UICONTROL Company Admin]** Typ in *Kunde*.
1. Melden Sie sich als Kunde an.
1. Gehen Sie zu **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** und fügen Sie Details für den Benutzer hinzu und aktivieren Sie ihn.
1. Speichern Sie den neuen Benutzer.

<u>Erwartete Ergebnisse</u>

Der Administrator bzw. die Administratorin kann einen neuen Benutzer hinzufügen.

<u>Tatsächliche Ergebnisse</u>

* Der Administrator erhält eine Fehlermeldung: *Etwas ist schiefgelaufen*.
* Der Administrator kann keinen neuen Kunden erstellen.
* Das Protokoll enthält den folgenden Fehler:

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
