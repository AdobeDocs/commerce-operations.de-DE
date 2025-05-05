---
title: 'MDVA-39153: Rabattbetrag wird bei der Neubestellung im Admin falsch berechnet'
description: Der Patch MDVA-39153 behebt das Problem, dass der Rabattbetrag bei der Neuanordnung in der Admin-Liste falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-39153. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39153: Rabattbetrag wird bei der Neubestellung im Admin falsch berechnet

Der Patch MDVA-39153 behebt das Problem, dass der Rabattbetrag bei der Neuanordnung in der Admin-Liste falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-39153. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Rabattbetrag wird bei der Neubestellung in der Admin falsch berechnet.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **Admin** > **Stores** > **Konfiguration** > **Verkauf** > **Steuern**.
1. Aktivieren Sie die Steuer für den Versand, indem Sie die Steuer im Warenkorb anzeigen.
1. Aktivieren und konfigurieren Sie die Versandmethode „Tabellenrate“ ($15).
1. Erstellen Sie eine Steuerregel für den integrierten Steuersatz (für CA).
1. Erstellen Sie eine Warenkorb-Preisregel mit einem festen Rabatt von 5 USD, der auf den gesamten Warenkorb und den Versandbetrag angewendet wird.
1. Fügen Sie ein Produkt mit einem Preis von $12 in den Warenkorb und gehen Sie zur Seite Warenkorb .
1. Wenden Sie den Rabatt auf den Warenkorb an.
1. Die Versandmethode im Abschnitt „Schätzungen“ auf „Pauschale“ setzen.
1. Gehen Sie durch den Checkout bis zu den Überprüfungsschritten (geben Sie die Bestellung nicht auf).
1. Gehen Sie auf die Homepage und dann zurück zum Warenkorb.
1. Ändern Sie die Versandart im Abschnitt „Schätzungen“ in „Tabellensatz“.

<u>Erwartete Ergebnisse</u>:

Der Rabatt bleibt gleich - $5.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt beträgt $6,31.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
