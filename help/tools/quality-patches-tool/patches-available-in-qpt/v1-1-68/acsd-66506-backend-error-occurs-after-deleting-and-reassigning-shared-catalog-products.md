---
title: 'ACSD-66506: Backend-Fehler tritt nach dem Löschen und Neuzuweisen von Shared Catalog-Produkten auf'
description: Wenden Sie den Patch ACSD-66506 an, um das Adobe Commerce-Problem zu beheben, bei dem das Backend den Fehler ausgibt * Das angeforderte Produkt existiert nicht. Überprüfen Sie das Produkt und versuchen Sie es erneut*, nachdem Sie zuvor zugewiesene Produkte gelöscht und einem freigegebenen Katalog neue zugewiesen haben.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: db08c58b-7e14-4bd8-af85-8f63aba9051b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '446'
ht-degree: 0%
---
# ACSD-66506: Backend-Fehler tritt nach dem Löschen und Neuzuweisen von Shared Catalog-Produkten auf

Der Patch ACSD-66506 behebt das Problem, dass das Backend den Fehler *Das angeforderte Produkt existiert nicht. Überprüfen Sie das Produkt und versuchen Sie es erneut* nachdem Sie zuvor zugewiesene Produkte gelöscht und einem freigegebenen Katalog neue zugewiesen haben. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66506. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nach dem Löschen zuvor zugewiesener Produkte und dem Zuweisen neuer Produkte zu einem **[!UICONTROL Shared Catalog]** gibt das Backend den folgenden Fehler zurück: *Das angeforderte Produkt ist nicht vorhanden. Überprüfen Sie das Produkt und versuchen Sie es erneut*

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einige Produkte mit dem Leistungs-Toolkit: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. Gehen Sie zu **[!UICONTROL [!DNL B2B] Features]** Konfiguration und legen Sie **[!UICONTROL Enable Company]** und **[!UICONTROL Enable Shared Catalog]** auf `Yes` fest.
1. Erstellen Sie einen neuen freigegebenen Katalog.
1. Weisen Sie alle generierten Produkte dem neu erstellten freigegebenen Katalog zu.
1. Verwenden Sie **[!UICONTROL Product Import]** , um ein Produkt zu löschen, das dem freigegebenen Katalog zugewiesen wurde.
   1. Exportieren Sie ein Produkt gefiltert nach SKU.
   1. Wählen Sie **[!UICONTROL Import Behavior: Delete]** aus und importieren Sie dann dieselbe Datei.
1. Öffnen Sie die **[!UICONTROL Shared Catalog]** und konfigurieren Sie Preise und Struktur.
   1. Wählen Sie **[!UICONTROL Set Pricing and Structure]** aus.
   1. Klicken Sie auf **[!UICONTROL Next]** und dann auf **[!UICONTROL Generate Catalog]**.
   1. Klicken Sie auf **[!UICONTROL Save]**.

<u>Erwartete Ergebnisse</u>:

Es tritt kein Fehler auf und Produkte verbleiben im freigegebenen Katalog, auch wenn ein Fehler auftritt.

<u>Tatsächliche Ergebnisse</u>:

Ein Fehler tritt auf: *Das angeforderte Produkt ist nicht vorhanden. Überprüfen Sie das Produkt und versuchen Sie es*, und alle Produkte werden aus dem freigegebenen Katalog entfernt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
