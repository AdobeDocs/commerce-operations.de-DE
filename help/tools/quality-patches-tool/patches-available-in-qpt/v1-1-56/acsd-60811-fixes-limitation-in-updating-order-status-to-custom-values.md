---
title: 'ACSD-60811: Korrigiert die Einschränkung bei der Aktualisierung des Bestellstatus auf benutzerdefinierte Werte'
description: Wenden Sie den Patch ACSD-60811 an, um das Adobe Commerce-Problem zu beheben, bei dem die Aktualisierung des Bestellstatus mit einem benutzerdefinierten Wert oder Kommentar nur möglich ist, wenn der aktuelle Status entweder „Verarbeitung läuft“ oder „Betrug“ ist.
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '394'
ht-degree: 0%
---
# ACSD-60811: Korrigiert die Einschränkung bei der Aktualisierung des Bestellstatus auf benutzerdefinierte Werte

Der Patch des ACSD-60811 behebt das Problem, dass das Aktualisieren des Bestellstatus mit einem benutzerdefinierten Wert oder Kommentar nur möglich ist, wenn der aktuelle Status entweder &quot;[!UICONTROL Processing]&quot; oder &quot;[!UICONTROL Suspected Fraud]&quot; ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-60811. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7. 2.4.7-p1, 2.4.7-p2, 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Aktualisieren des Bestellstatus mit einem benutzerdefinierten Wert oder Kommentar ist nur möglich, wenn der aktuelle Status entweder *Verarbeitung* oder *Betrug* ist. Der Bestellstatus bleibt unverändert, wenn ein neuer Status ausgewählt und gesendet wird.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Order Status]**, um einen benutzerdefinierten Bestellstatus im Admin-Bedienfeld zu erstellen.
1. Klicken Sie auf **[!UICONTROL Assign Status to State]** , um den benutzerdefinierten Status dem Bestellstatus zuzuweisen.
1. Ändern Sie den Bestellstatus auf der Seite „Bestellansicht“ im Admin-Bedienfeld.

<u>Erwartete Ergebnisse</u>:

Der Administrator sollte in der Lage sein, im Admin-Bedienfeld den Bestellstatus in einen benutzerdefinierten Bestellstatus zu ändern.

<u>Tatsächliche Ergebnisse</u>:

Der Bestellstatus bleibt unverändert, wenn ein neuer Bestellstatus ausgewählt und gesendet wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
