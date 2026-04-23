---
title: 'ACSD-64111: Behebt den Fehler *InvalidArgumentException: Class does not exist* beim Festlegen verschachtelter Bedingungen für eine Produktkomponente in [!DNL Page Builder]'
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-64111: Behebt den Fehler *InvalidArgumentException: Class does not exist* beim Festlegen verschachtelter Bedingungen für eine Produktkomponente in [!DNL Page Builder]

Der Patch ACSD-64111 behebt das Problem, dass *InvalidArgumentException: Class nicht vorhanden* Fehler in `vendor/magento/module-rule/Model/ConditionFactory.php:50` auftritt, wenn verschachtelte Bedingungen für eine Produktkomponente in [!DNL Page Builder] festgelegt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 installiert ist. Die Patch-ID ist ACSD-64111. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden)  2.4.6-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Hinzufügen eines *[!UICONTROL Conditions Combination]* in der Widget-Bedingung &lt;*id=&#39;166&#39;/> für Produkte wird der Fehler „InvalidArgumentException: Class does not exist in /app/&lt;project id\>/vendor/magento/module-rule/Model/ConditionFactory.php*&quot; ausgegeben.[!DNL Page Builder]

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Adobe Commerce-Administrator an.
1. Navigieren Sie zu **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Fügen Sie eine neue Seite hinzu (oder bearbeiten Sie eine vorhandene Seite).
1. Erweitern Sie den Abschnitt **[!UICONTROL Content]** und klicken Sie auf **[!UICONTROL Edit with Page Builder]**.
1. Fügen Sie eine neue Zeile und dann das **[!UICONTROL Products]** Widget hinzu.
1. Konfigurieren Sie das **[!UICONTROL Products]**-Widget.
1. Wählen Sie die **[!UICONTROL Condition]** unter **[!UICONTROL Select Products By]** aus.
1. Fügen Sie eine neue Bedingung hinzu und wählen Sie **[!UICONTROL Conditions Combination]** aus der Dropdown-Liste aus.

<u>Erwartete Ergebnisse</u>:

Keine Fehler in den Protokollen.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Ausnahme wird in den Protokollen aufgezeichnet:

*report.CRITICAL: InvalidArgumentException: Klasse ist in vendor/magento/module-rule/Model/ConditionFactory.php nicht vorhanden:50*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
