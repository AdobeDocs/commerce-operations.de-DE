---
title: '"ACSD-61366: Der Befehl "bin/magento setup:static-content:deploy —jobs 4"tritt auf mehrere Auftragsfehler mit einem Fehler."'
description: Wenden Sie den Patch ACSD-61366 an, um das Adobe Commerce-Problem zu beheben, bei dem der Befehl "bin/magento setup:static-content:deploy —jobs 4"mehrere Auftragsfehler mit dem Fehler "Port muss innerhalb des Host-Parameters* konfiguriert werden"feststellt, obwohl der Port für die DB-Verbindung angegeben wurde.
feature: SCD
role: Admin, Developer
source-git-commit: b671dc30cd511d63dbbbaa6edd47ee36c1351620
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366: Der Befehl &quot;`bin/magento setup:static-content:deploy --jobs 4`&quot;tritt bei mehreren Auftragsfehlern mit einem Fehler auf

Der Patch ACSD-61366 behebt das Problem, bei dem der Befehl `bin/magento setup:static-content:deploy --jobs 4` mehrere Auftragsfehler feststellt, wobei der *Port innerhalb des Host-Parameters* -Fehlers konfiguriert werden muss, obwohl der Port für die DB-Verbindung angegeben wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-61366. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Befehl `bin/magento setup:static-content:deploy --jobs 4` treten mehrere Auftragsfehler mit dem Fehler *Port muss innerhalb des Host-Parameters* konfiguriert werden, obwohl der Port für die DB-Verbindung angegeben wurde.

<u>Zu reproduzierende Schritte</u>:

1. Geben Sie einen Anschluss in der Datenbankverbindung in `app/etc/env.php` an.
1. Führen Sie den Befehl `bin/magento setup:static-content:deploy --jobs 4` aus.

<u>Erwartete Ergebnisse</u>:

Die Bereitstellung statischer Inhalte wurde erfolgreich abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Der Befehl schlägt mit dem Fehler *Port muss innerhalb des Host-Parameters* konfiguriert werden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.