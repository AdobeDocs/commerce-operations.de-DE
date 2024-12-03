---
title: 'MDVA-41350: Ausnahme, wenn der Administrator Produkte außerhalb seines Zugriffs hinzufügt'
description: Der Patch MDVA-41350 behebt das Problem, bei dem anstelle einer eingeschränkten Zugriffsbenachrichtigung ein Ausnahmefehler ausgegeben wird, wenn ein Administrator ein Produkt in der Bestellung durch die SKU hinzufügt, das sich außerhalb seines Zugriffs befindet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-41350. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Admin Workspace, Products
role: Admin
exl-id: 4dc5ee5c-bd93-42e1-9c63-93ffb8e5f21c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-41350: Ausnahme, wenn der Administrator Produkte außerhalb seines Zugriffs hinzufügt

Der Patch MDVA-41350 behebt das Problem, bei dem anstelle einer eingeschränkten Zugriffsbenachrichtigung ein Ausnahmefehler ausgegeben wird, wenn ein Administrator ein Produkt in der Bestellung durch die SKU hinzufügt, das sich außerhalb seines Zugriffs befindet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-41350. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn ein Admin-Benutzer mit eingeschränktem Zugriff ein Produkt von SKU außerhalb seines Zugriffs in der Bestellung hinzufügt, tritt eine Ausnahme auf, anstatt dass der Benutzer über den eingeschränkten Zugriff benachrichtigt wird.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei Admin als Benutzer mit Zugriff auf nur eine bestimmte Website an.
1. Wechseln Sie zu **Verkauf** > **Bestellungen** und klicken Sie auf **Neue Bestellung erstellen**.
1. Wählen Sie einen Kunden und eine Store-Ansicht aus.
1. Klicken Sie auf **Produkte von SKU hinzufügen**.
1. Suchen Sie nach einer SKU, die keiner Website zugewiesen ist oder der Website nicht zugewiesen ist, auf die Sie Zugriff haben.
1. Klicken Sie auf **Zur Bestellung hinzufügen**.

<u>Erwartete Ergebnisse</u>:

Eine entsprechende Fehlermeldung wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Eine Ausnahme tritt auf.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
