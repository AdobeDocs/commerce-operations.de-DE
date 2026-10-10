---
title: 'MDVA-38827: Kunden erhalten Bestellversandfehler per E-Mail'
description: 'Mit dem Patch MDVA-38827 wird das Problem behoben, dass Kunden eine E-Mail mit einer Bestellsendung erhalten, die die folgende Fehlermeldung enthält: *Es tut uns leid, bei der Erstellung dieses Inhalts ist ein Fehler aufgetreten*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38827. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.'
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%
---
# MDVA-38827: Kunden erhalten Bestellversandfehler per E-Mail

Der Patch MDVA-38827 behebt das Problem, dass Kunden eine E-Mail mit einer Bestellsendung erhalten, die die folgende Fehlermeldung enthält: *Es tut uns leid, bei der Erstellung dieses Inhalts ist ein Fehler aufgetreten*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38827. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn die Option Kunden per E-Mail benachrichtigen für den Versand ausgewählt ist, erhalten Kunden eine E-Mail mit der folgenden Fehlermeldung: *Beim Generieren dieses Inhalts ist ein Fehler aufgetreten*.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **Marketing** > **Kommunikation** > **E-Mail-** und wählen Sie **Neue Vorlage hinzufügen**.
   * Wählen Sie **Magento Sales** > **Neue Lieferung**.
   * Klicken Sie auf **Vorlage**.
   * Fügen Sie einen Vorlagennamen hinzu (z. B. „Core-Versandvorlage„) und klicken Sie auf **Speichern**.
1. Wechseln Sie zu **Store** > Einstellungen > **Konfiguration** > **Verkauf** > **Verkaufs-E-Mail**:
   * Aktivieren Sie **Versandkommentare**.
   * Wählen Sie **Core-Versandvorlage** (siehe den Teil „Vorlagennamen hinzufügen“ in Schritt 1) unter E-Mail-Vorlage für Versandkommentare und E-Mail-Vorlage für Versandkommentare für Gäste aus.
1. Bestellung aufgeben. Gehen Sie zum Admin-Bedienfeld > **Verkauf** > **Bestellung**, klicken Sie auf **Anzeigen** und versenden Sie dann die Bestellung.
1. Der Bestellstatus ändert sich von „Ausstehend“ in „Verarbeitung läuft“.
1. Klicken Sie **linken Seitenleiste auf** Sendungen“ und dann auf **Anzeigen**, um die Bestellung anzuzeigen.
1. Fügen Sie in **Kommentartext** unter **Versandverlauf** einen Kommentar ein und aktivieren Sie das Kontrollkästchen **Kunden per E-Mail benachrichtigen**.
1. Klicken Sie **Kommentar übermitteln**.

<u>Erwartete Ergebnisse</u>:

Verkaufs-E-Mail mit Versandkommentaren wird generiert.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird in der E-Mail empfangen: *Beim Generieren dieses Inhalts ist ein Fehler aufgetreten.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
