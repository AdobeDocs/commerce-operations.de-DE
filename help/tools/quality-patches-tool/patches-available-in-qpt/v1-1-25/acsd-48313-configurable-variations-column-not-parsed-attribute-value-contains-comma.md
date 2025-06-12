---
title: 'ACSD-48313: [!UICONTROL configurable_variations] Spalte wird nicht geparst, wenn der Attributwert ein Komma enthält'
description: Wenden Sie den Patch ACSD-48313 an, um das Adobe Commerce-Problem zu beheben, bei dem die [!UICONTROL configurable_variations] nicht geparst wird, wenn der Attributwert ein Komma enthält.
feature: Attributes, Configuration
role: Admin
exl-id: 1ce0c8dc-0d03-4ebd-b02a-08090b244190
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-48313: **[!UICONTROL configurable_variations]** Spalte wird nicht geparst, wenn der Attributwert ein Komma enthält

Der Patch ACSD-48313 löst das Problem, dass **[!UICONTROL configurable_variations]** Spalte nicht geparst wird, wenn der Attributwert ein Komma enthält. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48313. Die Version, in der dieses Problem behoben wird, ist noch nicht verfügbar.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nach dem Export von konfigurierbaren Produkten kann die resultierende Datei aufgrund eines Formatierungsproblems mit dem Attribut **[!UICONTROL configurable_variations]** nicht erneut importiert werden. Dies geschieht, wenn Attributoptionen vorhanden sind, die ein Komma enthalten.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und erstellen Sie ein neues Attribut _Größe_:
1. Katalogeingabetyp für Store-Inhaber: **[!UICONTROL Dropdown]**.
1. Erstellen Sie Optionen mit einem Komma, z. B.:
   * 10,2 cm
   * 15,5 cm
1. **[!UICONTROL Advanced Attribute Properties]** - Umfang: _Global_.
1. Erstellen Sie ein neues konfigurierbares Produkt mit der Funktion Konfigurationen erstellen .
1. Wählen Sie das obige Attribut _Größe_ und die beiden Optionen aus, die das Komma enthalten.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** und erstellen Sie einen neuen Produktexport (führen Sie den cron-Trigger aus, um die CSV-Dateigenerierung zu starten).
1. Wechseln Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** und versuchen Sie, dieselbe oben erstellte CSV-Datei erneut zu importieren.

<u>Erwartete Ergebnisse</u>:

Der Benutzer sollte in der Lage sein, die Datei zu importieren.

<u>Tatsächliche Ergebnisse</u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
