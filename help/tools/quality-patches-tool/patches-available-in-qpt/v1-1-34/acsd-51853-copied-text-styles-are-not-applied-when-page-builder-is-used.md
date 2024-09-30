---
title: "ACSD-51853: Kopierte Textstile werden nicht mit dem Seitenaufbau angewendet."
description: Wenden Sie den Patch ACSD-51853 an, um das Adobe Commerce-Problem zu beheben, bei dem die kopierten Textstile nicht angewendet werden, wenn der Seiten-Builder verwendet wird.
feature: Page Builder
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-51853: Kopierte Textstile werden nicht mit dem Seitenaufbau angewendet

Der Patch ACSD-51853 behebt das Problem, dass die kopierten Textstile nicht angewendet werden, wenn der Seiten-Builder verwendet wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.34 installiert ist. Die Patch-ID ist ACSD-51853. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kopierte Textstile werden nicht angewendet, wenn der Seitenaufbau verwendet wird

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin an.
1. Navigieren Sie zu > **content** > **pages** > **Öffnen Sie eine beliebige Seite** > **Mit Seitenaufbau bearbeiten**.
1. Ziehen Sie Zeilen und *Text* aus **[!UICONTROL Elements]**.
1. Kopieren Sie **angereicherter Inhalt**, fügen Sie diesen Text in ein **[!UICONTROL Page Builder]** ein.

<u>Erwartete Ergebnisse</u>

Der kopierte Text wird mit allen Stilen eingefügt.

<u>Tatsächliche Ergebnisse</u>

Der kopierte Text wird als Klartext eingefügt und alle Stile gehen verloren.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
