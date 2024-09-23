---
title: "ACSD-54106: Korrigieren der türkischen Zeichensortierung in der Produktkategorie"
description: Wenden Sie den Patch ACSD-54106 an, um das Adobe Commerce-Problem zu beheben, bei dem die Sortierung von Kategorieprodukten nach Namen für türkische Akzentzeichen falsch ist.
feature: Categories, Products, Search
role: Admin
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-54106: Korrigieren der Zeichensortierung türkischer Akzentzeichen in der Produktkategorie

Der Patch ACSD-54106 behebt das Problem, dass die Sortierung von Kategorieprodukten nach Namen für türkische Akzentzeichen falsch ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.39 installiert ist. Die Patch-ID ist ACSD-54106. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Sortierung von Produkten in Kategorien nach Namen ist für türkische Zeichen mit Akzentzeichen nicht korrekt.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin-Bedienfeld an.
1. Erstellen Sie einfache Produkte mit dem Namen wie folgt und weisen Sie sie jeder Kategorie zu:

* Name A
* Name f
* Name D
* Ğ
* Name M
* Name Ö
* Name: Ü
* Name Y
* Name Z

1. Navigieren Sie zur Storefront und greifen Sie auf die Kategorie zu, die die Produkte enthält.
1. Ändern Sie die Sortierreihenfolge in &quot;*[!UICONTROL By Name]*&quot;.

<u>Erwartete Ergebnisse</u>:

Produkte werden in der folgenden Reihenfolge korrekt sortiert:

* Name A
* Name f
* Name D
* Ğ
* Name M
* Name Ö
* Name: Ü
* Name Y
* Name Z

<u>Tatsächliche Ergebnisse</u>:

Produkte werden in der folgenden Reihenfolge falsch sortiert:

* Name A
* Name D
* Name M
* Name Y
* Name Z
* Name f
* Name Ö
* Name: Ü
* Ğ

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
