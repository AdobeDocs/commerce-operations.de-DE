---
title: 'ACSD-62872: Aktualisierungen planen falsch validiert'
description: Wenden Sie den Patch ACSD-62872 an, um das Adobe Commerce-Problem mit der eindeutigen Attributvalidierung zu beheben, bei dem geplante Aktualisierungen falsch validiert werden.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
exl-id: bd0d452b-aae3-4682-8a2c-471a7f8bf132
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%
---
# ACSD-62872: Aktualisierungen planen falsch validiert

Der Patch ACSD-62872 behebt das Problem der eindeutigen Attributvalidierung, bei der geplante Aktualisierungen falsch validiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-62872. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch wird für die Versionen 2.4.4 - 2.4.6-p8 in der Version 1.1.58 QPT als veraltet markiert.

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die geplante Aktualisierung eines benutzerdefinierten Attributs wird falsch validiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein benutzerdefiniertes Attribut für Kategorien.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Neue Kategorie erstellen.
1. Rufen Sie in derselben Kategorie den Abschnitt **[!UICONTROL Scheduled Updates]** auf.
1. Sie können zu jedem späteren Zeitpunkt ein neues Update für diese Kategorie einrichten.
1. Bevor Sie mit der geplanten Aktualisierung beginnen, versuchen Sie, die erstellte Zeitplanaktualisierung für die Kategorie zu bearbeiten.

<u>Erwartete Ergebnisse</u>:

Sollte in der Lage sein, die geplante Aktualisierung durchzuführen.

<u>Tatsächliche Ergebnisse</u>:

Ein Fehler wird ausgelöst: *Der Wert des Attributs „Benutzerdefiniertes Attribut“ ist nicht eindeutig. Legen Sie einen eindeutigen Wert fest und versuchen Sie es erneut.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
