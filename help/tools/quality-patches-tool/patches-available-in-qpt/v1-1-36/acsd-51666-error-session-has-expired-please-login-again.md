---
title: '"ACSD-51666: Fehler "Die Sitzung ist abgelaufen, melden Sie sich bitte erneut an." nach der Anmeldung"'
description: Wenden Sie den Patch ACSD-51666 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler *Die Sitzung ist abgelaufen ist. Melden Sie sich bitte erneut an.* tritt auf, nachdem Sie sich angemeldet haben.
feature: Customers
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51666: Fehler *Die Sitzung ist abgelaufen. Melden Sie sich erneut an.* nach der Anmeldung

Der Patch ACSD-51666 behebt das Problem, dass der Fehler *Die Sitzung abgelaufen ist. Melden Sie sich bitte erneut an.* tritt auf, nachdem Sie versucht haben, sich anzumelden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.36 installiert ist. Die Patch-ID ist ACSD-51666. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Sie erhalten den Fehler *Die Sitzung ist abgelaufen. Melden Sie sich erneut an.* , wenn versucht wird, sich mit dem neuen Kennwort von einem Gerät aus anzumelden, nachdem das Kennwort auf einem anderen Gerät zurückgesetzt wurde. Dies geschieht nur, wenn eine zusätzliche Ajax-Anfrage auf der Seite vorhanden ist, die von einem benutzerdefinierten Modul hinzugefügt wird.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie ein benutzerdefiniertes Modul, das auf jeder Seite des Storefront eine Ajax-Anfrage hinzufügt.
1. Erstellen Sie ein neues Konto.
1. Melden Sie sich ab und gehen Sie zurück zur Anmeldeseite.
1. Öffnen Sie den Link &quot;*Kennwort vergessen*&quot;in einem anderen Browser und senden Sie die E-Mail &quot;*Kennwort zurücksetzen*&quot;.
1. Öffnen Sie die E-Mail zum Zurücksetzen des Kennworts im ersten Browser und legen Sie das neue Kennwort fest.
1. Versuchen Sie, sich im zweiten Browser anzumelden.

<u>Erwartete Ergebnisse</u>:

Sie können sich beim ersten Versuch erfolgreich anmelden.

<u>Tatsächliche Ergebnisse</u>:

* Sie sehen, dass die *Sitzung abgelaufen ist. Melden Sie sich erneut an.* -Fehler.
* Sie werden nicht angemeldet und zur Homepage weitergeleitet.
* Ihr zweiter Anmeldeversuch ist erfolgreich.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
