---
title: 'MDVA-42269: Administratorbenutzer kann sich aufgrund des Fehlers „TypeError“ nicht bei Admin anmelden'
description: Der Patch MDVA-42269 behebt das Problem, dass sich Admin-Benutzer aufgrund von TypeError nicht bei Admin anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 installiert ist.  Die Patch-ID lautet MDVA-42269.  Das neueste Patch-Update ist in QPT 1.1.15. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Admin Workspace
role: Admin
exl-id: 42ad4bb5-950f-476d-bf55-931b38bcb937
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-42269: Administratorbenutzer kann sich aufgrund des Fehlers „TypeError“ nicht bei Admin anmelden

Der Patch MDVA-42269 behebt das Problem, dass sich Admin-Benutzer aufgrund von TypeError nicht bei Admin anmelden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 installiert ist.  Die Patch-ID lautet MDVA-42269.  Das neueste Patch-Update ist in QPT 1.1.15. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1, 2.3.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Administratorbenutzer können sich aufgrund des folgenden Fehlers nicht bei Admin anmelden: *TypeError: strtotime() erwartet, dass Parameter 1 eine Zeichenfolge ist, null angegeben.*

<u>Schritte zur Reproduktion</u>:

Melden Sie sich bei Commerce Admin an.

<u>Erwartete Ergebnisse</u>:

Der Administrator kann sich mit dem richtigen Benutzernamen und Kennwort anmelden.

<u>Tatsächliche Ergebnisse</u>:

Der Administrator kann sich nicht anmelden. Der folgende Fehler wird protokolliert: *TypeError: strtotime() erwartet, dass Parameter 1 eine Zeichenfolge ist, null angegeben.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
