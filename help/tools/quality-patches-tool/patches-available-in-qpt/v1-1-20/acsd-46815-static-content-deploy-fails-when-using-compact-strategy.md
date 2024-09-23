---
title: "ACSD-46815: Bereitstellung statischer Inhalte schlägt bei kompakter Strategie fehl."
description: Wenden Sie den Patch ACSD-46815 an, um das Adobe Commerce-Problem zu beheben, bei dem die Bereitstellung statischer Inhalte bei Verwendung einer kompakten Strategie fehlschlägt.
feature: Deploy, Page Content, SCD
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-46815: Bereitstellung statischer Inhalte schlägt bei Verwendung einer kompakten Strategie fehl

Der Patch ACSD-46815 behebt das Problem, bei dem die Bereitstellung statischer Inhalte fehlschlägt, wenn die kompakte Strategie verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20 installiert ist. Die Patch-ID lautet ACSD-46815. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Bereitstellung statischer Inhalte schlägt bei der Bereitstellung mit einer kompakten Strategie fehl.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie den statischen Inhalt mit einer kompakten Strategie bereit, indem Sie den folgenden Befehl ausführen:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Erwartete Ergebnisse</u>:

Die Bereitstellung statischer Inhalte wird ohne Fehler abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Die Bereitstellung statischer Inhalte schlägt mit einer kompakten Strategie fehl. Der folgende Fehler tritt während des Bereitstellungsprozesses auf: *Der Inhalt von /app/pub/static/adminhtml/Magento/base/default/./node_modules/@spectrum-css/vars/dist/spectrum-global.css Datei kann nicht gelesen werden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce für die Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
