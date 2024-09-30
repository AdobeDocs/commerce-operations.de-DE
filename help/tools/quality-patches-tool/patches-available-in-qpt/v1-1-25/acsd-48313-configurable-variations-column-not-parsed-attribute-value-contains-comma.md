---
title: 'ACSD-48313: [!UICONTROL configurable_variations] Spalte nicht geparst, wenn Attributwert Komma enthält.'
description: Wenden Sie den Patch ACSD-48313 an, um das Adobe Commerce-Problem zu beheben, bei dem die Spalte [!UICONTROL configurable_variations] nicht analysiert wird, wenn der Attributwert ein Komma enthält.
feature: Attributes, Configuration
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-48313: **[!UICONTROL configurable_variations]** Spalte wird nicht geparst, wenn der Attributwert Komma enthält

Der Patch ACSD-48313 behebt das Problem, dass die Spalte **[!UICONTROL configurable_variations]** nicht analysiert wird, wenn der Attributwert ein Komma enthält. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID lautet ACSD-48313. Die Version, in der dieses Problem behoben wird, ist noch nicht verfügbar.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach dem Export konfigurierbarer Produkte kann die resultierende Datei aufgrund eines Formatierungsproblems mit dem Attribut **[!UICONTROL configurable_variations]** nicht erneut importiert werden. Dies geschieht, wenn Attributoptionen vorhanden sind, die ein Komma enthalten.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und erstellen Sie ein neues Attribut _Größe_:
1. Katalogeingabetyp für Store Owner: **[!UICONTROL Dropdown]**
1. Erstellen Sie Optionen mit einem Komma, z. B.:
   * 10,2 cm
   * 15,5 cm
1. **[!UICONTROL Advanced Attribute Properties]** - Umfang: _Global_.
1. Erstellen Sie ein neues konfigurierbares Produkt mithilfe der Funktion Konfigurationen erstellen .
1. Wählen Sie das obige Attribut _Größe_ und die beiden Optionen, die das Komma enthalten.
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** und erstellen Sie einen neuen Produktexport (führen Sie den Cron aus, um die Erstellung der CSV-Datei Trigger).
1. Gehen Sie zu **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** und versuchen Sie, dieselbe CSV-Datei erneut zu importieren, die oben erstellt wurde.

<u>Erwartete Ergebnisse</u>:

Benutzer sollten die Datei importieren können.

<u>Tatsächliche Ergebnisse</u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
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
