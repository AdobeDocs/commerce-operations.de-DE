---
title: 'ACSD-51471: Admin-Benutzer können geplante Updates für gebündelte Produkte nicht speichern'
description: Wenden Sie den Patch ACSD-51471 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Admin-Benutzer ein geplantes Update für ein gebündeltes Produkt, das ein einfaches Produkt mit geplantem Update verwendet, nicht speichern kann.
exl-id: d8134111-63f0-4476-a407-677bda52fa90
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-51471: Admin-Benutzer können geplante Updates für gebündelte Produkte nicht speichern

Der Patch ACSD-51471 behebt das Problem, dass ein Administrator ein geplantes Update für ein gebündeltes Produkt, das ein einfaches Produkt mit geplantem Update verwendet, nicht speichern kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51471. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Admin-Benutzer können keine geplante Aktualisierung für ein gebündeltes Produkt speichern, das ein einfaches Produkt verwendet, für das selbst eine geplante Aktualisierung geplant ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Fügen Sie eine geplante Aktualisierung für das einfache Produkt hinzu, für das nur das *Startdatum* und das keine *Enddatum* verwendet wurde.
1. Nachdem die Aktualisierung angewendet wurde, ändern Sie die SKU des Produkts.
1. Erstellen Sie ein gebündeltes Produkt und fügen Sie das in Schritt 1 erstellte einfache Produkt als untergeordnetes Produkt hinzu.
1. Erstellen Sie ein geplantes Update für das gebündelte Produkt, um das gebündelte Produkt zu aktivieren. Geben Sie sowohl *Startdatum* als auch *Enddatum* für die geplante Aktualisierung an.
1. Speichern Sie die geplante Aktualisierung.

<u>Erwartete Ergebnisse</u>:

Die geplante Aktualisierung wurde erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt beim Speichern der geplanten Aktualisierung auf: *Das angeforderte Produkt existiert nicht. Überprüfen Sie das Produkt und versuchen Sie es erneut.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
