---
title: "ACSD-42807: Benutzerdefiniertes Währungszeichen nicht auf Storefront angezeigt"
description: Der Patch ACSD-42807 behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-42807. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
feature: Storefront
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-42807: Benutzerdefiniertes Währungszeichen wird nicht auf der Storefront angezeigt

Der Patch ACSD-42807 behebt das Problem, dass das benutzerdefinierte Währungszeichen nicht auf der Storefront angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-42807. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das benutzerdefinierte Währungszeichen wird nicht auf der Storefront angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Store** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **Währungseinstellungen** und wählen Sie eine beliebige benutzerdefinierte Währung aus. Beispiel: **Mexikanischer Peso**.
1. Wechseln Sie zu **Store** > **Einstellungen** > **Konfigurationen** > **Allgemein** > **Gebietsschemaoptionen** und wählen Sie **Spanisch (Mexiko)** aus.
1. Wechseln Sie zu **Store** > **Währungssymbole** und konfigurieren Sie das Währungssymbol in **MX$**.
1. Überprüfen Sie das Währungssymbol auf der Vorderseite.

<u>Erwartete Ergebnisse</u>:

Das Standardwährungssymbol lautet &quot;MX$&quot;, wobei die Währung auf &quot;Mexikanischer Peso&quot;und das Gebietsschema auf &quot;Spanisch (Mexiko)&quot;eingestellt ist.

<u>Tatsächliche Ergebnisse</u>:

Das Standardwährungssymbol zeigt &quot;$&quot;.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
