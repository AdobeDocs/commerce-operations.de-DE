---
title: 'ACSD-61366: Der Befehl „bin/magento setup:static-content:deploy —jobs 4“ schlägt mit einem Fehler bei mehreren Vorgängen fehl'
description: Wenden Sie den Patch ACSD-61366 an, um das Adobe Commerce-Problem zu beheben, bei dem der Befehl „bin/magento setup:static-content:deploy —jobs 4“ auf mehrere Auftragsfehler mit dem Fehler *Port muss innerhalb des Host-Parameters konfiguriert werden* stößt, obwohl der Port für die DB-Verbindung angegeben wurde.
feature: SCD
role: Admin, Developer
exl-id: d71a4833-a236-429b-a4e5-7d7d51c2caeb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366: Beim `bin/magento setup:static-content:deploy --jobs 4`-Befehl treten mehrere Auftragsfehler mit einem Fehler auf

Der Patch ACSD-61366 behebt das Problem, dass der `bin/magento setup:static-content:deploy --jobs 4`-Befehl mehrere Auftragsfehler aufweist, wobei der Fehler *Port muss innerhalb des Host-Parameters konfiguriert werden* obwohl der Port für die DB-Verbindung angegeben wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-61366. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der `bin/magento setup:static-content:deploy --jobs 4`-Befehl tritt bei mehreren Auftragsfehlern mit dem Fehler *Port muss im Host-Parameter konfiguriert werden* auf, obwohl der Port für die DB-Verbindung angegeben wurde.

<u>Schritte zur Reproduktion</u>:

1. Geben Sie in `app/etc/env.php` einen Port in der Datenbankverbindung an.
1. `bin/magento setup:static-content:deploy --jobs 4` ausführen.

<u>Erwartete Ergebnisse</u>:

Die Bereitstellung statischer Inhalte wird erfolgreich abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Der Befehl schlägt fehl mit dem Fehler *Port muss innerhalb des Host-Parameters konfiguriert werden*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
