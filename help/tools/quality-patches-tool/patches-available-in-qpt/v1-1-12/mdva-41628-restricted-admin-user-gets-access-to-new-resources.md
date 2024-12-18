---
title: 'MDVA-41628: Administratoren mit eingeschränkter Zugriffsberechtigung erhalten Zugriff auf neue Ressourcen'
description: Mit dem Patch MDVA-41628 wird das Problem behoben, dass Administratoren mit eingeschränkten Berechtigungen auf die neuen Ressourcen zugreifen können, wenn neue Module hinzugefügt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41628. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Admin Workspace
role: Admin
exl-id: 774a4329-fa1f-4cca-aa97-1b8ef03c11d1
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-41628: Administratoren mit eingeschränkter Zugriffsberechtigung erhalten Zugriff auf neue Ressourcen

Mit dem Patch MDVA-41628 wird das Problem behoben, dass Administratoren mit eingeschränkten Berechtigungen auf die neuen Ressourcen zugreifen können, wenn neue Module hinzugefügt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-41628. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Administratoren mit beschränkten Zugangsrechten können auf die neuen Ressourcen zugreifen, wenn neue Module hinzugefügt werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Administratorrolle mit eingeschränkten Ressourcen.
1. Erstellen Sie unter der in Schritt 1 erstellten Rolle einen neuen Admin-Benutzer.
1. Installieren und aktivieren Sie das benutzerdefinierte Modul , das einen neuen Satz von Menüelementen zusammen mit ACL-Ressourcen erstellt.
1. Melden Sie sich mit dem neu erstellten Admin-Benutzer an.

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer mit eingeschränktem Zugriff kann nicht auf die neu erstellten Menüelemente zugreifen.

<u>Tatsächliche Ergebnisse</u>:

Der eingeschränkte Admin-Benutzer kann auf die neuen Menüelemente zugreifen, auch wenn die neuen Ressourcen nicht der Benutzerrolle zugewiesen sind.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
