---
title: 'ACSD-67039: Kundendatensätze wurden aufgrund der Überprüfung des Systemattributs „rp_token“ nicht gespeichert'
description: Wenden Sie den Patch ACSD-67039 an, um das Adobe Commerce-Problem zu beheben, bei dem die Kodierung von diakritischen Zeichen zu Validierungsunterbrechungen bei rp_token führt.
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: e5995e28-b6b5-4955-a52a-895842c6b6e8
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 1%
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
*`rp_token_created_at` =* 2021-04-29 20:06:14*
1. Navigieren Sie im Admin-Bedienfeld zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Bearbeiten Sie den Kunden, für den Sie die oben genannten Werte aktualisiert haben.
1. Klicken Sie auf **[!UICONTROL Save Customer]** oder **[!UICONTROL Save and Continue Edit]**.

<u>Erwartete Ergebnisse</u>:

Die Kundenwerte wurden erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der Kundendatensatz wird nicht gespeichert und der Administrator sieht die Fehlermeldung „Beim Speichern des Kunden ist *Fehler aufgetreten.*
Die `system.log` enthält den folgenden Fehler:

```text
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > &#x200B;](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch
