---
title: 'ACSD-51666: Fehler „Die Sitzung ist abgelaufen, bitte melden Sie sich erneut an.“ Nach der Anmeldung'
description: Wenden Sie den Patch ACSD-51666 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler „Die Sitzung ist abgelaufen“ auftritt. Melden Sie sich erneut an.* Tritt nach dem Anmeldeversuch auf.
feature: Customers
role: Admin, Developer
exl-id: 8968b314-6625-45fa-9733-20560cca7089
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51666: Fehler *Die Sitzung ist abgelaufen, bitte erneut anmelden.* nach der Anmeldung

Der Patch ACSD-51666 behebt das Problem, dass der Fehler *Die Sitzung ist abgelaufen, bitte melden Sie sich erneut an.* tritt nach dem Anmeldeversuch auf. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.36 installiert ist. Die Patch-ID ist ACSD-51666. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Sie erhalten die Fehlermeldung *Die Sitzung ist abgelaufen, melden Sie sich erneut an.* beim Versuch, sich mit dem neuen Kennwort von einem Gerät aus anzumelden, nachdem das Kennwort auf einem anderen Gerät zurückgesetzt wurde. Dies geschieht nur, wenn auf der von einem benutzerdefinierten Modul hinzugefügten Seite eine zusätzliche Ajax-Anfrage vorhanden ist.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie ein benutzerdefiniertes Modul, das eine Ajax-Anfrage auf jeder Seite der Storefront hinzufügt.
1. Erstellen Sie ein neues Konto.
1. Melden Sie sich ab und gehen Sie zurück zur Anmeldeseite.
1. Öffnen Sie den Link *Kennwort vergessen* in einem anderen Browser und senden Sie die E *Mail zum Zurücksetzen des*.
1. Öffnen Sie die E-Mail zum Zurücksetzen des Kennworts im ersten Browser und legen Sie das neue Kennwort fest.
1. Versuchen Sie, sich im zweiten Browser anzumelden.

<u>Erwartete Ergebnisse</u>:

Sie können sich beim ersten Versuch erfolgreich anmelden.

<u>Tatsächliche Ergebnisse</u>:

* Sie sehen die *Die Sitzung ist abgelaufen, melden Sie sich erneut an.*.
* Sie sind nicht eingeloggt und werden nicht auf die Homepage weitergeleitet.
* Ihr zweiter Anmeldeversuch ist erfolgreich.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
