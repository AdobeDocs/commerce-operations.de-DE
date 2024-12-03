---
title: 'ACSD-55031: Fehler "Typ "gemischt"kann nicht null sein"bei der Kompilierung'
description: Wenden Sie den Patch ACSD-55031 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler *Typ "gemischt"während der Kompilierung nach der Installation einer benutzerdefinierten Erweiterung nicht null sein kann*.
feature: Extensions
role: Admin, Developer
exl-id: 770d35aa-7ce2-4517-b393-b7c623c9f779
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# ACSD-55031: `Type "mixed" cannot be nullable`-Fehler während der Kompilierung

Der Patch ACSD-55031 behebt das Problem, bei dem der `Type "mixed" cannot be nullable`-Fehler während der Kompilierung nach der Installation einer benutzerdefinierten Erweiterung auftrat. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-55031. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der `Type "mixed" cannot be nullable`-Fehler tritt während der Kompilierung auf.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie eine benutzerdefinierte Erweiterung.
1. Führen Sie den Befehl `bin/magento setup:di:compile` aus.

<u>Erwartete Ergebnisse</u>:

Während der Kompilierung treten keine Fehler auf.

<u>Tatsächliche Ergebnisse</u>:

Die Datei `var/log/system.log` enthält den Fehler:

```
report.ERROR: Type "mixed" cannot be nullable
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
