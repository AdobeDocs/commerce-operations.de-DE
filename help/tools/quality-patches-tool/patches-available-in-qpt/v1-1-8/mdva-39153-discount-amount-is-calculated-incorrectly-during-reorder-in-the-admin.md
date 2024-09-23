---
title: "MDVA-39153: Rabattbetrag wird bei der Neubestellung in der Admin-Konsole falsch berechnet"
description: Der Patch MDVA-39153 behebt das Problem, dass der Rabattbetrag bei der Neubestellung in der Admin-Konsole falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-39153. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39153: Der Rabattbetrag wird bei der Neubestellung in der Admin-Konsole falsch berechnet

Der Patch MDVA-39153 behebt das Problem, dass der Rabattbetrag bei der Neubestellung in der Admin-Konsole falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-39153. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Rabattbetrag wird bei der Neuanordnung in der Admin-Konsole falsch berechnet.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu &quot;**Admin**&quot;> &quot;**Geschäfte**&quot;> &quot;**Konfiguration**&quot;> &quot;**Verkauf**&quot;> &quot;**Steuern**&quot;.
1. Schalten Sie die Steuer für den Versand ein, die die Steuer im Warenkorb anzeigt.
1. Aktivieren und konfigurieren Sie die Versandmethode Tabellenrate ($15).
1. Erstellen Sie eine Steuerregel für den integrierten Steuersatz (für CA).
1. Erstellen Sie eine Preisregel für den Warenkorb mit einem festgelegten Rabatt von 5 USD, der auf den gesamten Warenkorb und den Versandbetrag angewendet wird.
1. Fügen Sie dem Warenkorb ein Produkt mit einem Preis von 12 USD hinzu und rufen Sie die Seite Warenkorb auf.
1. Wenden Sie den Rabatt auf den Warenkorb an.
1. Setzen Sie die Versandmethode im Abschnitt &quot;Schätzungen&quot;auf &quot;Pauschalpreis&quot;.
1. Fahren Sie mit dem Checkout bis zum Review-Schritte fort (platzieren Sie die Bestellung nicht).
1. Gehen Sie zur Homepage und gehen Sie dann zurück zum Warenkorb.
1. Ändern Sie die Versandmethode im Abschnitt &quot;Schätzungen&quot;in &quot;Tabellenrate&quot;.

<u>Erwartete Ergebnisse</u>:

Der Rabatt bleibt gleich - 5 USD.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt beträgt 6,31 USD.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
