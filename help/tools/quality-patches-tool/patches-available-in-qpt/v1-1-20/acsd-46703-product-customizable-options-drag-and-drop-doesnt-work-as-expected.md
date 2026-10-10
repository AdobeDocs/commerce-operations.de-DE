---
title: 'ACSD-46703: Drag-and-Drop der Produktanpassung funktioniert nicht'
description: Dieser Artikel bietet eine Lösung für den Fall, dass die anpassbaren Optionen zum Ziehen und Ablegen des Produkts nicht wie erwartet funktionieren.
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%
---
# ACSD-46703: Drag-and-Drop der Produktanpassung funktioniert nicht

Der Patch ACSD-46703 behebt das Problem, dass die anpassbaren Optionen des Produkts (Drag-and-Drop) nicht wie erwartet funktionieren. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20 installiert ist. Die Patch-ID ist ACSD-46703. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des [Quality Patches Tool] auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende können die anpassbaren Optionen nicht von einer Seite auf eine andere ziehen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Fügen Sie dem einfachen Produkt anpassbare Optionen hinzu und stellen Sie sicher, dass Sie über 20 Optionen hinzufügen, was zu einer Paginierung führt.
1. Versuchen Sie, eine anpassbare Option (Drag-and-Drop) innerhalb derselben Seite zu verschieben.
1. Versuchen Sie jetzt, eine anpassbare Option von Seite zwei auf Seite eins zu verschieben.

<u>Erwartete Ergebnisse</u>:

* Sie können die anpassbaren Optionen per Drag-and-Drop von einer Seite auf eine andere ziehen.
* Sie können die Werte mithilfe der Drag-and-Drop-Funktion sortieren, auch für mehrere Seiten.

<u>Tatsächliche Ergebnisse</u>:

Sie können mit der Drag-and-Drop-Funktion keinen Wert auf eine andere Seite verschieben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [Quality Patches Tools > Usage](/help/tools/quality-patches-tool/usage.md) im Handbuch zum Quality Patches Tool .
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
