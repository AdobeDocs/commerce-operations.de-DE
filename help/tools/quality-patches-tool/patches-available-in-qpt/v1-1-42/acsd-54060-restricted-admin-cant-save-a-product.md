---
title: "ACSD-54060: Eingeschränkte Administratoren können ein Produkt nicht speichern, wenn es einem anderen Produkt untergeordnet ist."
description: Wenden Sie den Patch ACSD-54060 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Administrator ein Produkt nicht speichern kann, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen ist.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-54060: Eingeschränkte Administratoren können ein Produkt nicht speichern, wenn es einem anderen Produkt untergeordnet ist

Der Patch ACSD-54060 behebt das Problem, dass ein eingeschränkter Administrator ein Produkt nicht speichern kann, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-54060. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein eingeschränkter Administrator kann ein Produkt nicht speichern, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es beiden Websites zu.
1. Erstellen Sie ein konfigurierbares Produkt mit dem einfachen Produkt als einzige Variante und weisen Sie das konfigurierbare Produkt nur der Standardwebsite zu.
1. Erstellen Sie einen Benutzer mit eingeschränktem Administratorstatus, der nur Zugriff auf die zweite Website hat.
1. Melden Sie sich als eingeschränkter Administrator an.
1. Versuchen Sie, den einfachen Produktnamen im zweiten Website-Bereich zu ändern.

<u>Erwartete Ergebnisse</u>:

Der eingeschränkte Administrator kann den Produktnamen ändern.

<u>Tatsächliche Ergebnisse</u>:

Es tritt ein Fehler auf: *Mehr Berechtigungen sind erforderlich, um dieses Element anzuzeigen*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
