---
title: 'MDVA-41350: Ausnahme, wenn Admin Produkte außerhalb ihres Zugriffs hinzufügt'
description: Mit dem Patch MDVA-41350 wird das Problem behoben, dass ein Ausnahmefehler anstelle einer Benachrichtigung mit eingeschränktem Zugriff ausgelöst wird, wenn ein Administrator ein Produkt in der Reihenfolge nach SKU hinzufügt, auf das er keinen Zugriff hat. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-41350. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Admin Workspace, Products
role: Admin
exl-id: 4dc5ee5c-bd93-42e1-9c63-93ffb8e5f21c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-41350: Ausnahme, wenn Admin Produkte außerhalb ihres Zugriffs hinzufügt

Mit dem Patch MDVA-41350 wird das Problem behoben, dass ein Ausnahmefehler anstelle einer Benachrichtigung mit eingeschränktem Zugriff ausgelöst wird, wenn ein Administrator ein Produkt in der Reihenfolge nach SKU hinzufügt, auf das er keinen Zugriff hat. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-41350. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn ein Admin-Benutzer mit eingeschränktem Zugriff ein Produkt über eine SKU außerhalb seines Zugriffs in der Bestellung hinzufügt, tritt eine Ausnahme anstelle einer Meldung auf, die den Benutzer über seinen eingeschränkten Zugriff informiert.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Admin als Benutzer an, der nur Zugriff auf eine bestimmte Website hat.
1. Gehen Sie zu **Verkauf** > **Bestellungen** und klicken Sie auf **Neue Bestellung erstellen**.
1. Kunden- und Shop-Ansicht auswählen.
1. Klicken Sie auf **Produkte hinzufügen nach SKU**.
1. Suchen Sie nach einer SKU, die keiner Website zugewiesen ist oder der Website, auf die Sie Zugriff haben, nicht zugewiesen ist.
1. Klicken Sie **Zur Bestellung hinzufügen**.

<u>Erwartete Ergebnisse</u>:

Eine entsprechende Fehlermeldung wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Eine Ausnahme tritt auf.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
