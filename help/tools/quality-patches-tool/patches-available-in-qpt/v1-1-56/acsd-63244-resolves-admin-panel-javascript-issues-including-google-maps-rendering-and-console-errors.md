---
title: 'ACSD-63244: Beheben von JavaScript-Problemen im Admin-Bedienfeld, einschließlich  [!DNL Google Maps] - und Konsolenfehlern'
description: Mit dem Patch „ACSD-63244“ werden die verschiedenen JavaScript-Probleme im Admin-Bedienfeld behoben, einschließlich Problemen mit  [!DNL Google Maps] -Rendering und wiederkehrendem „Uncauth TypeError this“._each is not a function&grave; errors in der Browser-Konsole.
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
source-git-commit: 6b623811440238deee7a7fe859d887830f89782c
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-63244: Beheben von JavaScript-Problemen im Admin-Bedienfeld, einschließlich [!DNL Google Maps]-Rendering und Konsolenfehlern

Mit dem Patch ACSD-63244 werden die verschiedenen JavaScript-Probleme im Admin-Bedienfeld behoben, einschließlich Problemen mit der [!DNL Google Maps]-Wiedergabe und wiederkehrenden `Uncaught TypeError: this._each is not a function` in der Browser-Konsole. Dieser Patch ist ab dem [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 verfügbar. Die Patch-ID ist ACSD-63244. Das Problem wurde planmäßig in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4, 2.4.4-p9, 2.4.6-p7, 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

* Der `Uncaught TypeError: this._each is not a function` Fehler erscheint in der Browser-Konsole und stört die Admin-UI-Funktionalität.
* JavaScript-Fehler verhindert, dass [!DNL Google Maps] richtig gerendert wird.

<u>Schritte zur Reproduktion</u>:

1. Laden Sie die Admin-Benutzeroberfläche von Adobe Commerce.
1. Öffnen Sie die Browser-Konsole und führen Sie das folgende Skript aus:

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>Erwartete Ergebnisse</u>:

Die in der standardmäßigen JS-Bibliothek verfügbaren JavaScript-Funktionen werden korrekt und fehlerfrei ausgeführt.

<u>Tatsächliche Ergebnisse</u>:

JavaScript-Fehler werden in der Browser-Konsole angezeigt:

```
Uncaught TypeError: this._each is not a function
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
