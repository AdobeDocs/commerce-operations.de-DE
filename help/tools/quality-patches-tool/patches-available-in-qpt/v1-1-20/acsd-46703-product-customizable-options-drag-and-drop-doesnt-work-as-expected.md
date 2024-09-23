---
title: "ACSD-46703: Die Drag & Drop-Anpassung von Produkten funktioniert nicht."
description: Dieser Artikel bietet eine Lösung für das Problem, dass das Ziehen und Ablegen der anpassbaren Produktoptionen nicht wie erwartet funktioniert.
feature: Products
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-46703: Drag &amp; Drop zur Produktanpassung funktioniert nicht

Der Patch ACSD-46703 behebt das Problem, dass die anpassbaren Optionen (Drag &amp; Drop) des Produkts nicht wie erwartet funktionieren. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46703. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen Versionen des [Qualitätspatches-Tools] gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können die anpassbaren Optionen nicht von einer Seite auf eine andere ziehen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Fügen Sie dem einfachen Produkt anpassbare Optionen hinzu und stellen Sie sicher, dass Sie mehr als 20 Optionen hinzufügen, was zu einer Paginierung führt.
1. Versuchen Sie, eine anpassbare Option (per Drag &amp; Drop) innerhalb derselben Seite zu verschieben.
1. Versuchen Sie jetzt, eine anpassbare Option von Seite 2 auf Seite 1 zu verschieben.

<u>Erwartete Ergebnisse</u>:

* Sie können die anpassbaren Optionen per Drag-and-Drop von einer Seite auf eine andere ziehen.
* Sie können die Werte mithilfe der Drag-and-Drop-Funktion sortieren, auch für mehrere Seiten.

<u>Tatsächliche Ergebnisse</u>:

Mit der Drag &amp; Drop-Funktion können Sie keinen Wert auf eine andere Seite verschieben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [Tools für Qualitätsmuster > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im Handbuch zum Werkzeug für Qualitätsmuster.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) in unserer Support-Wissensdatenbank, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im Handbuch zum Werkzeug für Qualitätsmuster.
