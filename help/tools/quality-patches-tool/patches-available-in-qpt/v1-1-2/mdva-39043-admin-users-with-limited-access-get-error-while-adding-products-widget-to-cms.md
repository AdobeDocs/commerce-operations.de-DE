---
title: 'MDVA-39043: Admin-Benutzende erhalten Fehler beim Hinzufügen eines Widgets zur CMS-Seite'
description: Der Patch MDVA-39043 behebt das Problem, dass Admin-Benutzende mit eingeschränktem Zugriff beim Hinzufügen des Widgets „Produkte“ zur CMS-Seite einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39043. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Admin Workspace, CMS, Products
role: Admin
exl-id: 82488249-cca3-4a28-bdc1-fa93a4c9dc2f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39043: Admin-Benutzende erhalten Fehler beim Hinzufügen eines Widgets zur CMS-Seite

Der Patch MDVA-39043 behebt das Problem, dass Admin-Benutzende mit eingeschränktem Zugriff beim Hinzufügen des Widgets „Produkte“ zur CMS-Seite einen Fehler erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39043. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Admin-Benutzende mit eingeschränktem Zugriff erhalten eine Fehlermeldung, wenn das Widget „Produkte“ zur CMS-Seite hinzugefügt wird.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Backend mit dem Admin an und haben Sie nur Zugriff auf die Bearbeitung von Inhalten.
1. Navigieren Sie **Inhalt** > **Seiten**.
1. Öffnen Sie eine beliebige Seite zur Bearbeitung.
1. Bearbeiten des Inhalts mit **Page Builder**.
1. Fügen Sie **Produkt**-Widget aus **Abschnitt „Inhalt hinzufügen** hinzu.
1. Klicken Sie **Konfigurieren** im **Produkt**-Widget.

<u>Erwartete Ergebnisse</u>:

Es wird kein Fehler angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird empfangen:

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
