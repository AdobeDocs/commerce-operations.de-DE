---
title: 'MDVA-39605: Redis-Cache-TTL (Ablaufdatum) hat falschen Wert'
description: Der MDVA-39605 Patch löst das Problem, dass die Redis-Cache-TTL (Ablaufdatum) einen falschen Wert aufweist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-39605. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Cache, Console, Services
role: Admin
exl-id: 65f5d50a-e49e-4155-9d1a-3758f0c723a8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# MDVA-39605: Redis-Cache-TTL (Ablaufdatum) hat falschen Wert

Der MDVA-39605 Patch löst das Problem, dass die Redis-Cache-TTL (Ablaufdatum) einen falschen Wert aufweist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-39605. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Redis-Cache-TTL (Ablaufdatum) hat einen falschen Wert.

<u>Schritte zur Reproduktion</u>:

Um die Fehlerbehebung zu testen, leeren Sie den Cache und öffnen Sie ein konfigurierbares Produkt in der Storefront. Öffnen Sie dann ein Terminal (Konsole) und führen Sie die folgenden Schritte aus:

1. Führen Sie den Befehl `redis-cli` aus.
1. Führen Sie `KEYS "*PRICE"` aus (das Ergebnis sollte nur einen Schlüssel enthalten, z. B. `zc:ti:e54_PRICE`). Kopieren Sie den Schlüssel.
1. Führen Sie `SMEMBERS` aus, gefolgt vom Schlüssel aus dem vorherigen Schritt (zum Beispiel `SMEMBERS zc:ti:e54_PRICE`). Kopieren Sie einen beliebigen Schlüssel aus dem Ergebnis (beispielsweise e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Führen Sie `KEYS "*<key>"` mit dem Namen des Schlüssels aus dem vorherigen Schritt aus, um den vollständigen Schlüsselnamen abzurufen (z. B. `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Das Ergebnis sollte nur einen Schlüssel enthalten (z. B. `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Wie Sie vielleicht bemerken, ist der vollständige Schlüsselname einfach der Schlüsselname mit dem Präfix &quot;`zc:k:`&quot;. Kopieren Sie nun den vollständigen Schlüsselnamen.
1. Führen Sie `HGETALL` aus, gefolgt vom vollständigen Schlüsselnamen aus Schritt 4, um den Wert zu überprüfen. Der Wert sollte serialisierte Daten von zugehörigen Produkten eines zugehörigen konfigurierbaren Produkts enthalten.
1. Führen Sie `TTL` aus, gefolgt vom vollständigen Schlüsselnamen aus Schritt 4, um zu überprüfen, ob der Schlüssel ein Ablaufdatum hat. Das Ergebnis sollte von **-1** und **-2** abweichen und ungefähr 2592000 (30 Tage) sein. Obwohl die im Code festgelegte Gültigkeitsdauer ein Jahr beträgt, gilt für die in Adobe Commerce verwendete Redis-Bibliothek eine feste maximale Gültigkeitsdauer von 2592000s.

<u>Erwartete Ergebnisse</u>:

Ablaufdatum ist 2592000s

<u>Tatsächliche Ergebnisse</u>:

Das Ablauflimit ist auf **-1** oder **-2** festgelegt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
