---
title: 'ACSD-51892: Leistungsproblem, bei dem Konfigurationsdateien mehrmals geladen werden'
description: Wenden Sie den Patch ACSD-51892 an, um das Adobe Commerce-Leistungsproblem zu beheben, bei dem Konfigurationsdateien während der Bereitstellung mehrmals geladen werden.
feature: Observability
role: Admin
exl-id: ef3d3b85-b6a0-4037-95c0-e84125fa9088
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51892: Leistungsproblem, bei dem Konfigurationsdateien mehrmals geladen werden

Der Patch ACSD-51892 behebt das Leistungsproblem, das sich aus dem Laden der `app/etc/env.php` - und `app/etc/config.php` -Dateien bei jedem Zugriff auf die Konfigurationswerte der Bereitstellung in einer einzelnen Anfrage ergibt. Das übermäßige Lesen von Dateien belastet das System, was zu einer Verschlechterung der Gesamtleistung führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51892. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6-p2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es gibt ein Leistungsproblem, bei dem die Konfigurationsdateien mehrmals geladen werden.

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie die Bereitstellung oder Aktualisierung auf Adobe Commerce 2.4.6 oder höher durch.
1. Prüfen Sie die Dateisystemprotokolle auf den Zugriff auf `app/etc/env.php` - und `app/etc/config.php` -Dateien während der Bereitstellung.

<u>Erwartete Ergebnisse</u>:

Die Implementierung ist innerhalb des regulären Zeitrahmens erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

* Die Server haben Schwierigkeiten, auf alle von Ihnen eingegebenen Befehle zu reagieren. Dies führt zu *Fehler 503 des ersten Byte-Timeouts* beim Zugriff auf die Website.
* Es gibt mehrere Einträge in Protokolldateien mit Zugriff auf `app/etc/env.php` - und `app/etc/config.php` -Dateien.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
