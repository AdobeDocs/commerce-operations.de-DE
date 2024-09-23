---
title: "MDVA-41236: Es ist nicht möglich, bestehende geplante Updates für das Produkt zu erstellen oder zu bearbeiten."
description: Der Patch MDVA-41236 behebt das Problem, dass Benutzer nicht in der Lage sind, neue geplante Updates für das Produkt zu erstellen oder zu bearbeiten, wenn das "Enddatum"zuvor entfernt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41236. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Products, Staging
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-41236: Es können keine neuen geplanten Updates für das Produkt erstellt oder bearbeitet werden

Der Patch MDVA-41236 behebt das Problem, dass Benutzer nicht in der Lage sind, neue geplante Updates für das Produkt zu erstellen oder zu bearbeiten, wenn das &quot;Enddatum&quot;zuvor entfernt wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41236. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können keine neuen Zeitpläne erstellen oder vorhandene Zeitpläne für Produkte bearbeiten, wenn das Enddatum zuvor entfernt wurde.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt mit dem Status &quot;*disable*&quot;.
1. Fügen Sie eine geplante Aktualisierung hinzu, um dieses Produkt zu aktivieren.
   * Fügen Sie zukünftige Start- und Enddaten hinzu.
1. Bearbeiten Sie die geplante Aktualisierung, indem Sie das **Enddatum** entfernen.
1. Bearbeiten Sie den Zeitplan erneut und versuchen Sie, ein **Enddatum** hinzuzufügen. Ein Fehler tritt auf.
1. Aktualisieren Sie die Seite und navigieren Sie erneut zu **Geplantes Update bearbeiten**.
1. Klicken Sie auf **Aus Update entfernen** > **Aktualisieren löschen**.
1. Jetzt sollte das geplante Update nicht über der Seite zur Produktbearbeitung angezeigt werden.
1. Versuchen Sie, eine neue geplante Aktualisierung zu erstellen, die sich mit der vorherigen Dauer überschneidet.

<u>Erwartete Ergebnisse</u>:

* In Schritt 4 ist kein Fehler aufgetreten. Der Administrator kann die geplante Aktualisierung ohne Fehler aktualisieren, da der Zeitplan noch nicht aktiv ist.
* Der Administrator kann die vorherige Aktualisierung löschen und eine neue erstellen.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten die folgende Fehlermeldung:

*error: Zukünftige Aktualisierung ist bereits in diesem Zeitraum vorhanden. Legen Sie einen anderen Bereich fest und versuchen Sie es erneut.*


## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-) verfügbare Patches.
