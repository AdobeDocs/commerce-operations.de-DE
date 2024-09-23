---
title: "MDVA-38827: Kunden erhalten einen Auftragsversandfehler per E-Mail."
description: "Der Patch MDVA-38827 behebt das Problem, dass Kunden eine E-Mail zum Bestellversand mit der folgenden Fehlermeldung erhalten: *Es tut uns leid, dass bei der Generierung dieses Inhalts ein Fehler aufgetreten ist*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38827. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll."
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827: Kunden erhalten per E-Mail einen Auftragsversandfehler

Der Patch MDVA-38827 behebt das Problem, bei dem Kunden eine E-Mail zum Bestellversand mit der folgenden Fehlermeldung erhalten: *Es tut uns leid, es ist ein Fehler beim Generieren dieses Inhalts aufgetreten*. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-38827. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce auf Cloud-Infrastruktur 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn die Option Kunden per E-Mail benachrichtigen für den Versand ausgewählt ist, erhalten Kunden eine E-Mail mit der folgenden Fehlermeldung: *Es tut uns leid, es ist ein Fehler beim Generieren dieses Inhalts aufgetreten*.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Marketing** > **Kommunikation** > **E-Mail-Vorlagen** und wählen Sie **Neue Vorlage hinzufügen** aus.
   * Wählen Sie **Magento Sales** > **New Shipping**.
   * Klicken Sie auf **Vorlage laden**.
   * Fügen Sie einen Vorlagennamen hinzu (z. B. die Kernversandvorlage) und klicken Sie auf **Speichern**.
1. Wechseln Sie zu **Store** > Einstellungen > **Konfiguration** > **Verkauf** > **E-Mail-Vertrieb**:
   * Aktivieren Sie **Versandkommentare**.
   * Wählen Sie unter &quot;E-Mail-Vorlage für Versandkommentar&quot;und &quot;E-Mail-Vorlage für Versandkommentar&quot;die Option **Kernversandvorlage** (siehe Schritt 1 &quot;Vorlagennamen hinzufügen&quot;).
1. Bestellung aufgeben. Gehen Sie zum Admin-Bedienfeld > **Verkauf** > **Bestellung**, klicken Sie auf **Ansicht** und senden Sie dann die Bestellung.
1. Der Bestellstatus ändert sich von &quot;Ausstehend&quot;zu &quot;Verarbeitung&quot;.
1. Klicken Sie im linken Seitenleistenmenü auf **Sendungen** und dann auf **Ansicht** , um die Reihenfolge anzuzeigen.
1. Fügen Sie einen Kommentar im Text **Kommentar** unter **Versandverlauf** hinzu und aktivieren Sie das Kontrollkästchen **Kunden per E-Mail benachrichtigen** .
1. Klicken Sie auf **Kommentar senden**.

<u>Erwartete Ergebnisse</u>:

Es wird eine Verkaufs-E-Mail mit Versandkommentaren erzeugt.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird in der E-Mail empfangen: *Es tut uns leid, dass bei der Erstellung dieses Inhalts ein Fehler aufgetreten ist.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
