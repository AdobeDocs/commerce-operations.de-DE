---
title: 'ACSD-67039: Kundendatensätze wurden aufgrund der Überprüfung des Systemattributs „rp_token“ nicht gespeichert'
description: Wenden Sie den Patch ACSD-67039 an, um das Adobe Commerce-Problem zu beheben, bei dem die Kodierung von diakritischen Zeichen zu Validierungsunterbrechungen bei rp_token führt.
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 231555e071ebc5edb36182f6b8d4f60acee4f61e
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039: Kundendatensätze wurden aufgrund der Validierung `rp_token` Systemattributs nicht gespeichert

Mit dem Patch ACSD-67039 wird das Problem behoben, dass aufgrund der Validierung des `rp_token` Systemattributs keine Kundendatensätze gespeichert wurden und die Diakritik-Validierung nur auf die resultierende Kunden-E-Mail angewendet wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-67039. Beachten Sie, dass dieses Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p9

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Kodierung diakritischer Zeichen führt bei `rp_token` zu Validierungsfehlern, die von der Validierung ausgeschlossen sind. Diakritische Zeichen sind nur für E-Mail-Adressen zulässig, wie vorgesehen.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce Version 2.4.4.
1. Erstellen Sie einen Kunden.
1. Aktualisieren Sie Adobe Commerce auf Version 2.4.6 der früheren Version 2.4.4, in der der Kunde bereits erstellt wurde.
1. Setzen Sie den Verschlüsselungsschlüssel auf `env.php` =
   *D337B914E91FF703B1E94BA4156AADF0*
1. Legen Sie die folgenden Werte für jeden Kunden unter der `customer_entity`-Tabelle in der Datenbank fest:
*`rp_token` = *INCR4869*
*`rp_token_created_at` = *2021-04-29 20:06:14*
1. Navigieren Sie im Admin-Bedienfeld zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bearbeiten Sie den Kunden, für den Sie die oben genannten Werte aktualisiert haben.
1. Klicken Sie auf **[!UICONTROL Save Customer]** oder **[!UICONTROL Save and Continue Edit]**.

<u>Erwartete Ergebnisse</u>:

Die Kundenwerte wurden erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der Kundendatensatz wird nicht gespeichert und der Administrator sieht die Fehlermeldung „Beim Speichern des Kunden ist *Fehler aufgetreten.*
Die `system.log` enthält den folgenden Fehler:

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch
