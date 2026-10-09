---
title: 'MDVA-41236: Für das Produkt können keine neuen geplanten Updates erstellt oder vorhandene bearbeitet werden'
description: Der Patch MDVA-41236 behebt das Problem, dass Benutzende keine neuen geplanten Updates für das Produkt erstellen oder bearbeiten können, wenn das „Enddatum“ zuvor entfernt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41236. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Products, Staging
role: Admin
exl-id: 82192778-4f25-40a0-882e-d52d32c433c2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%
---
# MDVA-41236: Für das Produkt können keine neuen geplanten Updates erstellt oder vorhandene bearbeitet werden

Der Patch MDVA-41236 behebt das Problem, dass Benutzende keine neuen geplanten Updates für das Produkt erstellen oder bearbeiten können, wenn das „Enddatum“ zuvor entfernt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41236. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende können keine neuen Zeitpläne erstellen oder vorhandene für Produkte bearbeiten, wenn das „Enddatum“ zuvor entfernt wurde.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt mit dem Status *deaktivieren*.
1. Fügen Sie ein geplantes Update hinzu, um dieses Produkt zu aktivieren.
   * Fügen Sie zukünftige Start- und Enddaten hinzu.
1. Bearbeiten Sie das geplante Update, indem Sie das **Enddatum“**.
1. Bearbeiten Sie den Zeitplan erneut und versuchen Sie, ein **Enddatum“**. Ein Fehler tritt auf.
1. Aktualisieren Sie die Seite und navigieren Sie erneut zu **Geplantes Update bearbeiten**.
1. Klicken Sie auf **Aus Update entfernen** > **Update löschen**.
1. Jetzt sollte das geplante Update nicht mehr oben auf der Seite zur Produktbearbeitung angezeigt werden.
1. Versuchen Sie, ein neues geplantes Update zu erstellen, das sich mit der vorherigen Dauer überschneidet.

<u>Erwartete Ergebnisse</u>:

* In Schritt 4 ist kein Fehler aufgetreten. Der Administrator kann die geplante Aktualisierung ohne Fehler aktualisieren, da der Zeitplan noch nicht aktiv ist.
* Der Administrator bzw. die Administratorin kann die vorherige Aktualisierung löschen und eine neue erstellen.

<u>Tatsächliche Ergebnisse</u>:

Benutzende erhalten die folgende Fehlermeldung:

*Fehler: Zukünftige Aktualisierung ist in diesem Zeitraum bereits vorhanden. Einen anderen Bereich festlegen und erneut versuchen.*


## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
