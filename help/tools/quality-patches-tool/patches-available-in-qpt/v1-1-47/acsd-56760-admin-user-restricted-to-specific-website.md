---
title: 'ACSD-56760: Der Administrator ist auf eine bestimmte Website beschränkt und kann keine neuen Produkte sortieren oder hinzufügen'
description: Wenden Sie den Patch ACSD-56760 an, um das Adobe Commerce-Problem zu beheben, bei dem der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore über eine eigene Stammkategorie verfügt.
role: Admin
exl-id: 2d75164e-c463-4e1a-aa6f-f420dbe0aaeb
source-git-commit: 881d33089b15b78583e09b79e93a3f78f38bc2ca
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-56760: Der Administrator ist auf eine bestimmte Website beschränkt und kann keine neuen Produkte sortieren oder hinzufügen

Der Patch ACSD-56760 behebt das Problem, dass der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore über eine eigene Stammkategorie verfügt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.47 installiert ist. Die Patch-ID ist ACSD-56760. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8-beta1 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Administrator-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore über eine eigene Stammkategorie verfügt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie *2* Websites.
1. Erstellen Sie eine **[!UICONTROL restricted admin user]** mit Zugriff auf nur die Website *1*.
1. Melden Sie sich als **[!UICONTROL restricted admin user]** an und versuchen Sie, die Produktpositionen in einer Kategorie zu ändern.

*1*:

* *2* speichert.
* *2* Stammkategorien, jede Website, die dem eigenen Kategoriestamm zugewiesen ist.

*2*:

* *2* speichert.
* Beide Websites erhalten nur die Stammkategorie *1* .

<u>Erwartete Ergebnisse</u>:

* *1 Fall 1*: Der eingeschränkte Administrator sollte Produkte innerhalb der verfügbaren Kategorie sortieren können.
* *Fall 2*: Der eingeschränkte Administrator kann keine Produkte innerhalb der verfügbaren Kategorie sortieren, da sich dies auch auf den eingeschränkten Speicher auswirkt.

<u>Tatsächliche Ergebnisse</u>:

* *1 Fall 1*: Der eingeschränkte Administrator kann keine Produkte innerhalb der verfügbaren Kategorie sortieren.
* *2.1}: Der eingeschränkte Administrator kann Produkte innerhalb der verfügbaren Kategorie sortieren, was sich auf die eingeschränkten Geschäfte auswirkt.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
