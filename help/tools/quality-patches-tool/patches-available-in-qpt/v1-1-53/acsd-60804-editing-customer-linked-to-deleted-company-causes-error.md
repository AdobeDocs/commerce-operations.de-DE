---
title: 'ACSD-60804: Die Bearbeitung eines mit einer gelöschten Firma verknüpften Kunden führt zu einem Fehler'
description: Wenden Sie den Patch ACSD-60804 an, um das Adobe Commerce-Problem zu beheben, bei dem das Bearbeiten eines Kunden, der mit einer gelöschten Firma verknüpft ist, einen Fehler verursacht *Aufruf einer Nutzerfunktion getSuperUserId() auf null*.
feature: Companies, Customers, B2B
role: Admin, Developer
exl-id: 09241160-f5ed-41f8-8bb6-2bb8ed5cccd5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '375'
ht-degree: 0%
---
# ACSD-60804: Die Bearbeitung eines mit einer gelöschten Firma verknüpften Kunden führt zu einem Fehler

Der Patch ACSD-60804 behebt das Problem, dass das Bearbeiten eines Kunden, der mit einer gelöschten Firma verknüpft ist, einen Fehler verursacht *Aufruf einer Memberfunktion getSuperUserId() auf null*. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 installiert ist. Die Patch-ID ist ACSD-60804. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Bearbeiten eines Kunden, der mit einer gelöschten Firma verknüpft ist, verursacht einen Fehler *Aufruf einer Memberfunktion getSuperUserId() auf null*.

<u>Voraussetzungen:</u>:

Installieren und Aktivieren von Adobe Commerce B2B-Modulen.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**.
1. Melden Sie sich bei `mysql` für die -Instanz an.
1. Löschen Sie die Firma, bei der `entity_id` = *1*.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bearbeiten Sie den Kunden, der beim Erstellen des Unternehmens automatisch erstellt wurde.

<u>Erwartete Ergebnisse</u>:

Der Kunde wird bearbeitet, ohne dass ein Ausnahmefehler ausgelöst wird.

<u>Tatsächliche Ergebnisse</u>:

Ein Fehler tritt auf: *Aufruf einer Memberfunktion getSuperUserId() auf null* wenn dem Kunden keine Firma zugeordnet ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
