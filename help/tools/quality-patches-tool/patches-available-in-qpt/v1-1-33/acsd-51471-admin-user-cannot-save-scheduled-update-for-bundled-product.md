---
title: 'ACSD-51471: Admin-Benutzer kann geplante Aktualisierungen für gebündeltes Produkt nicht speichern'
description: Wenden Sie den Patch ACSD-51471 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Administrator bzw. eine Administratorin keine geplante Aktualisierung für ein gebündeltes Produkt speichern kann, das ein einfaches Produkt mit einer geplanten Aktualisierung verwendet.
exl-id: d8134111-63f0-4476-a407-677bda52fa90
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-51471: Admin-Benutzer kann geplante Aktualisierungen für gebündeltes Produkt nicht speichern

Mit dem Patch ACSD-51471 wird das Problem behoben, dass ein Admin-Benutzer ein geplantes Update für ein gebündeltes Produkt, das ein einfaches Produkt mit einem geplanten Update verwendet, nicht speichern kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51471. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Admin-Benutzer können keine geplante Aktualisierung für ein gebündeltes Produkt speichern, das ein einfaches Produkt verwendet, das selbst eine geplante Aktualisierung hat.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Fügen Sie ein geplantes Update für das einfache Produkt mit nur *Startdatum* und ohne *Enddatum* hinzu.
1. Nachdem die Aktualisierung angewendet wurde, ändern Sie die SKU des Produkts.
1. Erstellen Sie ein gebündeltes Produkt und fügen Sie das in Schritt 1 erstellte einfache Produkt als untergeordnetes Produkt hinzu.
1. Erstellen Sie ein geplantes Update für das gebündelte Produkt, um das gebündelte Produkt zu aktivieren. Geben Sie sowohl *Startdatum* als auch *Enddatum* für die geplante Aktualisierung an.
1. Speichern Sie die geplante Aktualisierung.

<u>Erwartete Ergebnisse</u>:

Die geplante Aktualisierung wurde erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Beim Speichern der geplanten Aktualisierung tritt der folgende Fehler auf: *Das angeforderte Produkt existiert nicht. Überprüfen Sie das Produkt und versuchen Sie es erneut.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
