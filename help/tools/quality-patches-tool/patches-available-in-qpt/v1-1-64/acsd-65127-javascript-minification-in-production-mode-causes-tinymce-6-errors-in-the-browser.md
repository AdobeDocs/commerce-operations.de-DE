---
title: 'ACSD-65127: Die JavaScript-Minimierung im Produktionsmodus verursacht  [!DNL TinyMCE] -6-Fehler im Browser'
description: Wenden Sie den Patch ACSD-65127 an, um das Adobe Commerce-Problem zu beheben, bei dem die Aktivierung der JavaScript-Minimierung im Produktionsmodus dazu führte [!DNL TinyMCE] 6 Fehler in der Browser-Konsole zu generieren, die die Funktionalität und das Benutzererlebnis beeinträchtigten.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-65127: Die JavaScript-Minimierung im Produktionsmodus verursacht [!DNL TinyMCE] 6 Fehler im Browser

Der Patch ACSD-65127 behebt das Problem, dass durch die Aktivierung der JavaScript-Minimierung im Produktionsmodus [!DNL TinyMCE] 6 Fehler in der Browser-Konsole generiert, die die Funktionalität und das Benutzererlebnis beeinträchtigen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 installiert ist. Die Patch-ID ist ACSD-65127. Beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Aktivierung der JavaScript-Minimierung im Produktionsmodus führte dazu, dass [!DNL TinyMCE] 6 Fehler in der Browser-Konsole generierte, was sich auf die Funktionalität und das Benutzererlebnis auswirkte.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie die Konfiguration fest, indem Sie die folgenden Befehle ausführen:

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. Produktionsmodus aktivieren.

```
bin/magento deploy:mode:set production
```

1. Navigieren Sie in der Admin -Seitenleiste zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Klicken Sie auf **[!UICONTROL Edit]** eines der aufgelisteten Produkte, blättern Sie nach unten zu **[!UICONTROL Content]** und wählen Sie **[!UICONTROL Show Editor]** aus.

<u>Erwartete Ergebnisse</u>:

Keine JS-Fehler in der Browser-Konsole.

<u>Tatsächliche Ergebnisse</u>:

*404*-Fehler in der Browser-Konsole für die JS-`tiny_mce_6/plugins/help/js/i18n/keynav/en.js`.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
