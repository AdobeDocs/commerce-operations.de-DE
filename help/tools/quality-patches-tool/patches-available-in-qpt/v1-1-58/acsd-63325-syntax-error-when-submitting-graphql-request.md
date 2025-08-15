---
title: 'ACSD-63325: Syntaxfehler: Unerwarteter &lt;EOF&gt; Fehler beim Senden einer leeren  [!DNL GraphQL] '
description: Wenden Sie den ACSD-63325-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem beim Senden einer leeren - [!DNL GraphQL]  ein Syntaxfehler auftritt.
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325: Fehler „Syntaxfehler: Unerwarteter &lt; EOF >&quot; beim Senden einer leeren [!DNL GraphQL]

Mit dem Patch ACSD-63325 wird das Problem behoben, dass beim Senden einer leeren [!DNL GraphQL]-Anfrage der Fehler „Syntaxfehler: Unerwarteter &lt; EOF >&quot; und ein Nicht-200-Antwort-Code zurückgegeben wurden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-63325. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Senden einer leeren [!DNL GraphQL]-Anfrage tritt anstelle des Antwort-Codes 200 ein interner HTTP-Server-Fehler auf.

<u>Schritte zur Reproduktion</u>:

1. Leere GraphQL-Anfrage senden

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>Erwartete Ergebnisse</u>:

Der Antwort-Code für die Anfrage lautet 200.

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>Tatsächliche Ergebnisse</u>:

Ein interner 500-Server-Fehler tritt auf, wie dargestellt:

```
HTTP/1.1 500 Internal Server Error
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
