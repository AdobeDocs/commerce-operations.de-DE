---
title: "ACSD-60788: Benutzerdefinierte Skripte für [!DNL Google Tag Manager] werden aufgrund von CSP-Fehlern nicht ausgeführt."
description: Wenden Sie den Patch ACSD-60788 an, um das Adobe Commerce-Problem zu beheben, bei dem benutzerdefinierte Skripte für [!DNL Google Tag Manager] aufgrund von CSP-Fehlern (Content Security Policy) nicht ausgeführt werden.
feature: Security
role: Admin, Developer
source-git-commit: d1c643da36a200c6fb0a17139b12b6b91d9568e1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788: Benutzerdefinierte Skripte für [!DNL Google Tag Manager] werden aufgrund von Fehlern bei der Inhaltssicherheitsrichtlinie nicht ausgeführt

Der Patch ACSD-60788 behebt das Problem, dass benutzerdefinierte Skripte für [!DNL Google Tag Manager] aufgrund von Fehlern in der Inhaltssicherheitsrichtlinie nicht ausgeführt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-60788. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzerdefinierte Skripte für [!DNL Google Tag Manager] werden aufgrund von CSP-Fehlern (Content Security Policy) nicht ausgeführt.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie die Variable *[!DNL Google Tag Manager]* ein.
1. Richten Sie das Tag *[!DNL Google Tag Manager]* Benutzerdefiniertes HTML ein.
1. Fügen Sie den folgenden JavaScript-Code im ersten Tag ein:

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. Leeren Sie Caches nach dem Einrichten des *GTM*.
1. Öffnen Sie die Entwicklerkonsole in Ihrem Browser.
1. Öffnen Sie die Startseite.

<u>Erwartete Ergebnisse</u>:

Die Browser-Entwicklungskonsole zeigt *Nonce aus einfachen JS (Zufallszeichen)* an.

<u>Tatsächliche Ergebnisse</u>:

Die Browser-Entwicklungskonsole zeigt *Nonce von einfachem JS undefined* an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
