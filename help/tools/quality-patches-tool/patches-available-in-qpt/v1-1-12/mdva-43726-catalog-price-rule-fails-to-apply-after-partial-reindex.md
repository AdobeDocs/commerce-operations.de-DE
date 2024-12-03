---
title: 'MDVA-43726: Katalogpreisregel wird nach partieller Neuindizierung nicht angewendet'
description: Der Patch MDVA-43726 behebt das Problem, dass die Katalogpreisregel, die auf einer Attributübereinstimmung auf Store-Ebene basiert, nach einer partiellen Neuindizierung nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43726. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
exl-id: db536749-eb89-4bb5-9c69-f448f74497b8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# MDVA-43726: Katalogpreisregel wird nach partieller Neuindizierung nicht angewendet

Der Patch MDVA-43726 behebt das Problem, dass die Katalogpreisregel, die auf einer Attributübereinstimmung auf Store-Ebene basiert, nach einer partiellen Neuindizierung nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-43726. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Katalogpreisregel, die auf der Attributübereinstimmung auf Store-Ebene basiert, wird nach einer partiellen Neuindizierung nicht angewendet.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie den Indexermodus fest, um planmäßig ausgeführt zu werden.
1. Erstellen Sie zwei konfigurierbare Produktattribute. Beispiel: Farbe (visuelles Muster) und Größe (Textmuster).
1. Erstellen Sie ein konfigurierbares Produkt mit beiden Attributen, die Sie in Schritt 2 erstellt haben.
1. Erstellen Sie nach dem Erstellen der Produkte ein Attribut vom Typ **Ja/Nein** und machen Sie es in den Regelbedingungen sichtbar.
1. Fügen Sie dieses Attribut zum standardmäßigen Attributsatz hinzu.
1. Erstellen Sie eine Katalogpreisregel, die angewendet werden soll, wenn dieses Attribut auf **Ja** festgelegt ist.
1. Öffnen Sie eines der einfachen Produkte, die sich auf das konfigurierbare Produkt beziehen.
1. Ändern Sie den Umfang, in dem die Ansicht gespeichert werden soll, und aktualisieren Sie den Attributwert auf **Ja**.
1. Führen Sie die `CRON` aus und überprüfen Sie den Preis auf der Vorderseite.
1. Führen Sie eine vollständige Neuindizierung durch. Nochmals, überprüfen Sie den Preis auf der Vorderseite.
1. Aktualisieren Sie die konfigurierbare Produktkategorie.
1. Führen Sie die `CRON` aus und überprüfen Sie den Preis erneut auf der Vorderseite.

<u>Erwartete Ergebnisse</u>:

Die Katalogregel wird korrekt ohne vollständige Neuindizierung mit inkrementellen Indizes angewendet.

<u>Tatsächliche Ergebnisse</u>:

Die Katalogregel gilt nicht ohne vollständige Neuindizierung.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
