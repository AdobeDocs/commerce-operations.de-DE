---
title: 'ACSD-51892: Leistungsproblem, bei dem Konfigurationsdateien mehrmals geladen werden'
description: Wenden Sie den ACSD-51892-Patch an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem Konfigurationsdateien während der Bereitstellung mehrmals geladen werden.
feature: Observability
role: Admin
exl-id: ef3d3b85-b6a0-4037-95c0-e84125fa9088
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51892: Leistungsproblem, bei dem Konfigurationsdateien mehrmals geladen werden

Mit dem Patch ACSD-51892 wird das Leistungsproblem behoben, das durch das Laden der `app/etc/env.php`- und `app/etc/config.php`-Dateien jedes Mal auftritt, wenn auf Bereitstellungskonfigurationswerte in einer einzigen Anfrage zugegriffen wird. Das übermäßige Lesen von Dateien belastet das System, was zu einer Verschlechterung der Gesamtleistung führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51892. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6-p2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es gibt ein Leistungsproblem, bei dem die Konfigurationsdateien mehrmals geladen werden.

<u>Schritte zur Reproduktion</u>:

1. Führen Sie eine Bereitstellung oder ein Upgrade auf Adobe Commerce 2.4.6 oder höher durch.
1. Überprüfen Sie die Dateisystemprotokolle auf den Zugriff auf `app/etc/env.php`- und `app/etc/config.php`-Dateien, während die Bereitstellung ausgeführt wird.

<u>Erwartete Ergebnisse</u>:

Die Bereitstellung ist innerhalb des regulären Zeitraums erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

* Die Server haben Schwierigkeiten, auf die von Ihnen eingegebenen Befehle zu reagieren. Dies führt zu *Fehler 503 Zeitüberschreitung beim ersten Byte* beim Zugriff auf die Website.
* Es gibt mehrere Einträge in den Protokolldateien mit Zugriff auf `app/etc/env.php`- und `app/etc/config.php`.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
