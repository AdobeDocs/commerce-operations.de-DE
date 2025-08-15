---
title: 'ACSD-65254: E-Mail-Benachrichtigung wird nach der Aktualisierung der Kunden-E-Mail über updateCustomerEmail. [!DNL GraphQL]  nicht gesendet'
description: Wenden Sie den Patch von ACSD-65254 an, um das Adobe Commerce-Problem zu beheben, bei dem E-Mail-Benachrichtigungen an Kunden gesendet wurden, nachdem sie ihre E-Mail-Adressen in ihren Konten mit der Mutation updateCustomerEmail [!DNL GraphQL]  aktualisiert hatten.
feature: GraphQL, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: a97daceb-98f6-4bb8-9847-692af700c0fd
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-65254: E-Mail-Benachrichtigung wird nach der Aktualisierung der Kunden-E-Mail über `updateCustomerEmail` [!DNL GraphQL] Mutation nicht gesendet

Mit dem Patch ACSD-65254 wird das Problem behoben, dass keine E-Mail-Benachrichtigungen an Kunden gesendet wurden, nachdem ihre E-Mail-Adressen in ihren Konten mithilfe der `updateCustomerEmail`-[!DNL GraphQL]-Mutation aktualisiert wurden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 installiert ist. Die Patch-ID ist ACSD-65254. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

E-Mail-Benachrichtigungen wurden nicht an Kundinnen und Kunden gesendet, nachdem sie ihre E-Mail-Adressen mithilfe der `updateCustomerEmail` [!DNL GraphQL]-Mutation aktualisiert hatten.

<u>Schritte zur Reproduktion</u>:

1. Benutzer mithilfe der folgenden Mutation erstellen:

   ```
   mutation {
   	    createCustomer(
   		    input: {
   			    firstname: "Test"
   			    lastname: "User"
   			    email: "test@test.com"
   			    password: "Admin@123"
   			    is_subscribed: true
   		    }
   	    ) {
   		    customer {
   			    created_at
   		    }
   	    }
   }
   ```

1. Generieren Sie ein Token für den zuvor erstellten Benutzer und verwenden Sie es als Bearer-Token:

   ```
   mutation {
   generateCustomerToken(email: "test@test.com", password: "Admin@123") {
   	    token
   }
   }
   ```

1. Versuchen Sie, die E-Mail für den zuvor erstellten Benutzer mithilfe des zuletzt erstellten Bearer-Tokens zu aktualisieren:

   ```
   mutation {
   	    updateCustomerEmail(email: "test+updated@test.com", password: "Admin@123") {
   		    customer {
   			    email
   		    }
   	    }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Kunden sollten E-Mail-Benachrichtigungen erhalten, nachdem sie die E-Mail-Adressen in ihren Konten aktualisiert haben.

<u>Tatsächliche Ergebnisse</u>:

An die neue Adresse wird nur eine Abonnement-E-Mail gesendet. Die Bestätigungs-E-Mail für die E-Mail-Adressänderung wird nicht gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
