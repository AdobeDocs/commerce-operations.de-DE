---
title: 'ACSD-59366: Teams mit deaktivierten Benutzern löschen, die nicht in der Team-Liste sichtbar sind'
description: Wenden Sie den Patch ACSD-59366 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Fehler auftritt, wenn Sie versuchen, ein Team zu löschen, das deaktivierte Benutzende enthält, die nicht in der Teamliste sichtbar sind.
feature: GraphQL, Companies
role: Admin, Developer
exl-id: 406d2242-38f9-4852-b311-0ee57c4a7c26
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '395'
ht-degree: 0%
---
# ACSD-59366: Teams mit deaktivierten Benutzern löschen, die nicht in der Team-Liste sichtbar sind

Der Patch ACSD-59366 behebt das Problem, dass ein Fehler auftritt, wenn Sie versuchen, ein Team zu löschen, das deaktivierte Benutzende enthält, die nicht in der Team-Liste sichtbar sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 installiert ist. Die Patch-ID ist ACSD-59366. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Fehler tritt auf, wenn Sie ein Team löschen, das deaktivierte Benutzende enthält, die nicht in der Team-Liste sichtbar sind.

<u>Voraussetzungen</u>:

Adobe Commerce B2B-Module werden installiert und Unternehmen werden aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie und melden Sie sich als Unternehmensbenutzer an.
1. Erstellen Sie unter „Unternehmensstruktur“ ein neues Team.
1. Erstellen Sie unter dem neuen Team einen neuen Benutzer.
1. Bearbeiten Sie den neuen Benutzer und deaktivieren Sie ihn.
1. Wählen Sie das Team aus und löschen Sie.

<u>Erwartete Ergebnisse</u>:

Das Team hat einen oder mehrere inaktive Benutzer. Durch das Löschen des Teams wird die Zuweisung dieser Benutzer aufgehoben. Inaktive Benutzer finden Sie im Abschnitt [!UICONTROL Company Users] .

<u>Tatsächliche Ergebnisse</u>:

Beim Versuch, ein Team mit einem deaktivierten Benutzer zu löschen, tritt ein Fehler auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
