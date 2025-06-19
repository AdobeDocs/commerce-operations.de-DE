---
title: 'ACSD-46815: Bereitstellung statischer Inhalte schlägt mit einer kompakten Strategie fehl'
description: Wenden Sie den Patch ACSD-46815 an, um das Adobe Commerce-Problem zu beheben, bei dem die Bereitstellung statischer Inhalte bei einer kompakten Strategie fehlschlägt.
feature: Deploy, Page Content, SCD
role: Admin
exl-id: 66941a83-daf8-4bb2-a575-b615e1c5dc7c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-46815: Bereitstellung statischer Inhalte schlägt bei Verwendung einer kompakten Strategie fehl

Mit dem Patch ACSD-46815 wird das Problem behoben, dass die Bereitstellung statischer Inhalte fehlschlägt, wenn die Komprimierungsstrategie verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46815. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bereitstellung statischer Inhalte schlägt bei der Bereitstellung mit einer kompakten Strategie fehl.

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie den statischen Inhalt mit einer kompakten Strategie bereit, indem Sie den folgenden Befehl ausführen:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Erwartete Ergebnisse</u>:

Die Bereitstellung statischer Inhalte wird fehlerfrei abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Die Bereitstellung statischer Inhalte schlägt mit einer kompakten Strategie fehl. Während der Bereitstellung tritt der folgende Fehler auf: *Der Inhalt aus &quot;/app/pub/static/adminhtml/Magento/base/default/&quot;.Die Datei /node_modules/@spectrum-css/vars/dist/spectrum-global.css kann nicht gelesen werden.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) in unserer Entwicklerdokumentation.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
