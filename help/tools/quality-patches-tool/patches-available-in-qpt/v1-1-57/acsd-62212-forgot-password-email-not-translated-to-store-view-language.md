---
title: 'ACSD-62212: [!UICONTROL Forgot Password] E-Mail nicht in die Sprache der Store-Ansicht übersetzt'
description: Wenden Sie den Patch ACSD-62212 an, um das Adobe Commerce-Problem zu beheben, bei dem der Inhalt der *[!UICONTROL Forgot Password]*-E-Mail nicht in die Sprache der Shop-Ansicht übersetzt wird.
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
source-git-commit: 8f39f7838d5c98a1dcc584edf766393012ec8820
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212: *[!UICONTROL Forgot Password]* E-Mail nicht in die Sprache der Store-Ansicht übersetzt

Mit dem Patch ACSD-62212 wird das Problem behoben, dass der Inhalt der *[!UICONTROL Forgot Password]*-E-Mail nicht in die Sprache der Store-Ansicht übersetzt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62212. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Zurücksetzen des Kennworts über GraphQL in einer anderen Store-Ansicht als der registrierten entspricht der Link zum Zurücksetzen des Kennworts nicht der Store-Ansicht, von der aus er initiiert wurde.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine sekundäre Store-Ansicht unter dem *[!UICONTROL Main Website Store]*.
1. Wechseln Sie *[!UICONTROL Locale]* im Bereich für die sekundäre Store-Ansicht zu *[!UICONTROL French (France)]*.
1. Installieren Sie das französische Sprachpaket für Übersetzungen.
1. Kundenkonto erstellen.
1. Verwenden Sie die folgende GraphQL-Mutation mit *store*-Header mit dem Code der sekundären Store-Ansicht.

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. Überprüfen Sie die E-Mail.

<u>Erwartete Ergebnisse</u>:

* Die Sprache des Betreffs, des Links und des Inhalts der E-Mail stimmt mit dem Gebietsschema der Store-Ansicht überein.
* Die Anforderung zum Zurücksetzen des Kennworts wird von dem Store gesendet, in dem das Konto des Kunden tatsächlich registriert ist, unabhängig von der Store-Kopfzeile in der Anforderung.

<u>Tatsächliche Ergebnisse</u>:

In der E-Mail konnte Folgendes beobachtet werden:

* Der Link zum Zurücksetzen des Kennworts hat den Store-Code „default“.
* Das Thema ist auf Englisch.
* Der Inhalt ist auf Französisch.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
