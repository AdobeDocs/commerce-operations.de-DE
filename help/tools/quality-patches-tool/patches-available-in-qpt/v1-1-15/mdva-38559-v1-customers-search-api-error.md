---
title: 'MDVA-38559: /V1/Customers/search API gibt Fehler zurück'
description: Der Patch MDVA-38559 behebt das Problem, dass die API "/V1/Customers/search" einen Fehler für Kunden zurückgibt, die mehr als ein Abonnement haben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-38559. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben ist.
feature: REST, Search
role: Admin
exl-id: 6bcb65d0-1389-4090-b53c-8048bf64d8fb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# MDVA-38559: /V1/Customers/search API gibt Fehler zurück

Der Patch MDVA-38559 behebt das Problem, bei dem die `/V1/customers/search` -API einen Fehler für Kunden zurückgibt, die mehr als ein Abonnement haben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 installiert ist. Die Patch-ID lautet MDVA-38559. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben ist.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`/V1/customers/search` -API gibt einen Fehler für Kunden mit mehr als einem Abonnement zurück.

<u>Voraussetzungen</u>:

Der Adobe Commerce-Store verwendet mehr als eine Website.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Store** > **Konfiguration** > **Kunde** > **Kundenkonfiguration** > **Optionen für die Kontofreigabe** und wählen Sie **Global** aus.
1. Wechseln Sie zu **Kunden** > **Alle Kunden**, wählen Sie für jeden Kunden die Option **Bearbeiten** und wählen Sie dann **Newsletter** aus.
1. Abonnieren Sie einen Newsletter für mehr als eine Website und speichern Sie den Kunden.
1. Senden Sie die folgende Anfrage:

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>Erwartete Ergebnisse</u>:

Die Suchergebnisse des Kunden werden angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird in der Datei exception.log protokolliert: *Item (Magento\Customer\Model\Customer\Interceptor) mit der gleichen ID &quot;1&quot; ist bereits vorhanden.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
