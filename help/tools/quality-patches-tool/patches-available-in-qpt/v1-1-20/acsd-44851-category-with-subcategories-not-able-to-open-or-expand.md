---
title: "ACSD-44851: Kategorie mit Unterkategorien, die nicht geöffnet oder erweitert werden können"
description: Dieser Artikel bietet eine Lösung für das Problem, dass der Benutzer eine Kategorie mit Unterkategorien nicht öffnen oder erweitern kann.
feature: Categories
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-44851: Kategorie mit Unterkategorien, die nicht geöffnet oder erweitert werden können

Der Patch ACSD-44851 behebt das Problem, dass der Benutzer eine Kategorie mit Unterkategorien nicht öffnen oder erweitern kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID lautet ACSD-44851. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Benutzer kann eine Kategorie mit Unterkategorien nicht öffnen oder erweitern.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie in Adobe Commerce Admin einen Kategoriebaum mit zwei Stammkategorien und jeweils einigen Unterkategorien.
1. Öffnen Sie die Mobile-Ansicht/den Emulator oder verkleinern Sie die Fensterbreite, bis das Layout für Mobilgeräte verfügbar wird.
1. Öffnen Sie das Hauptmenü des Katalogs.
1. Versuchen Sie, die Stammkategorien zu erweitern.
1. Versuchen Sie, die Kategorie zu öffnen.

<u>Erwartete Ergebnisse</u>:

Auf das Menü kann zugegriffen werden.

<u>Tatsächliche Ergebnisse</u>:

Die zweite Ebene des Mobilmenüs wird nicht geöffnet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Tools für Qualitätsmuster > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im Handbuch zum Werkzeug für Qualitätsmuster.

* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch zum Werkzeug für Qualitätsmuster.
