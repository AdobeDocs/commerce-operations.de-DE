---
title: '''ACSD-48857: Änderungen können nach der Bearbeitung mit [!DNL Page Builder] nicht gespeichert werden'
description: Wenden Sie den Patch ACSD-48857 an, um das Adobe Commerce-Problem zu beheben, bei dem der Benutzer nach der Bearbeitung mit [!DNL Page Builder] keine Änderungen speichern kann.
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857: Änderungen können nach der Bearbeitung mit [!DNL Page Builder] nicht gespeichert werden

Der Patch ACSD-48857 behebt das Problem, dass der Benutzer nach der Bearbeitung mit [!DNL Page Builder] keine Änderungen speichern kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID lautet ACSD-48857. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer kann Änderungen nach der Bearbeitung mit [!DNL Page Builder] nicht speichern.

<u>Zu reproduzierende Schritte</u>

1. Melden Sie sich bei der Admin-Website an.
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** , um eine leere CMS-Seite zu erstellen.
1. Führen Sie dieses SQL-Skript aus, um den folgenden **[!UICONTROL Content]** -Feldwert festzulegen:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Kehren Sie in Admin zu **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** zurück.
1. Bearbeiten Sie Ihre Seite.
1. Navigieren Sie zur Registerkarte **[!UICONTROL Content]** .
1. Klicken Sie auf **[!UICONTROL Save]**.

<u>Erwartete Ergebnisse</u>

Die Bereinigung von HTML-Inhalten ist implementiert. Dadurch werden vom Texteditor erstellte HTML-Attribute für [!DNL Page Builder] entfernt.

<u>Tatsächliche Ergebnisse</u>

Die Seite bleibt nicht gespeichert und die Ladefunktion dreht sich weiter. In der Konsole wird der folgende Fehler erzeugt:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
