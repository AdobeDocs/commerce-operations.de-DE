---
title: 'ACSD-56760: Admin-Benutzende sind auf eine bestimmte Website beschränkt und können keine Produkte sortieren oder hinzufügen'
description: Wenden Sie den Patch ACSD-56760 an, um das Adobe Commerce-Problem zu beheben, bei dem der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore eine eigene Stammkategorie hat.
role: Admin
exl-id: 2d75164e-c463-4e1a-aa6f-f420dbe0aaeb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-56760: Admin-Benutzende sind auf eine bestimmte Website beschränkt und können keine Produkte sortieren oder hinzufügen

Mit dem Patch ACSD-56760 wird das Problem behoben, dass der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore eine eigene Stammkategorie hat. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.47 installiert ist. Die Patch-ID ist ACSD-56760. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8-beta1 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Admin-Benutzer, der auf eine bestimmte Website beschränkt ist und keine neuen Produkte innerhalb einer Kategorie sortieren oder hinzufügen kann, falls der Webstore eine eigene Stammkategorie hat.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie *2*-Websites.
1. Erstellen Sie eine **[!UICONTROL restricted admin user]**, die nur Zugriff auf die *1*-Website hat.
1. Melden Sie sich als **[!UICONTROL restricted admin user]** an und versuchen Sie, die Produktpositionen in einer Kategorie zu ändern.

*Fall 1*:

* *2* Stores.
* *2* Stammkategorien, wobei jede Website ihrem eigenen Kategoriestamm zugewiesen ist.

*Fall 2*:

* *2* Stores.
* Beide Websites haben nur eine *1*-Stammkategorie.

<u>Erwartete Ergebnisse</u>:

* *Fall 1*: Der Admin mit Zugriffsbeschränkung sollte in der Lage sein, Produkte innerhalb der verfügbaren Kategorie zu sortieren.
* *Fall 2*: Der Admin mit Zugriffsbeschränkung kann Produkte nicht innerhalb der verfügbaren Kategorie sortieren, da dies auch den eingeschränkten Store betrifft.

<u>Tatsächliche Ergebnisse</u>:

* *Fall 1*: Der Administrator mit Zugriffsbeschränkung kann Produkte nicht innerhalb der verfügbaren Kategorie sortieren.
* *Fall 2*: Der eingeschränkte Administrator kann Produkte innerhalb der verfügbaren Kategorie sortieren, was sich auf die eingeschränkten Stores auswirkt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
