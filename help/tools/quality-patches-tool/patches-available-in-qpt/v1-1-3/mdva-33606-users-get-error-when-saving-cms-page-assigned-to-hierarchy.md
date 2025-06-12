---
title: 'MDVA-33606: Beim Speichern einer CMS-Seite, die einer Hierarchie zugewiesen ist, wird eine Fehlermeldung angezeigt'
description: Mit dem Patch MDVA-33606 wird das Problem behoben, dass beim Speichern einer CMS-Seite, die der Hierarchiestruktur zugewiesen ist, der Fehler *Eindeutige Einschränkungsverletzung gefunden* angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-33606. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: CMS
role: Admin
exl-id: 19aaa13f-7ee6-49bc-b1d9-c288dc93b951
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# MDVA-33606: Beim Speichern einer CMS-Seite, die einer Hierarchie zugewiesen ist, wird eine Fehlermeldung angezeigt

Der Patch MDVA-33606 löst das Problem, dass beim Speichern einer CMS *Seite, die der Hierarchiestruktur zugewiesen ist, der Fehler „eindeutige Einschränkungsverletzung gefunden* angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-33606. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Versuch, eine CMS-Seite zu speichern, die einer Hierarchiestruktur zugewiesen ist, erhalten Benutzerinnen und Benutzer die folgende Fehlermeldung: *Eindeutige Einschränkungsverletzung gefunden*.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue CMS-Seite. Legen Sie den Bereich auf Alle Store-Ansichten fest. Dies ist Ihre CMS-Seite 1.
1. Erstellen Sie eine neue Store-Ansicht. Dies ist Ihre Store-Ansicht 2.
1. Gehen Sie zu **Inhalt** > **Hierarchie** > Fügen Sie die CMS-Seite 1 zur Hierarchiestruktur hinzu.
1. Ändern Sie den Bereich in Store-Ansicht 2.
   * Deaktivieren Sie „Übergeordnete Knotenhierarchie verwenden“.
   * Fügen Sie CMS Page 1 zu diesem Bereich hinzu und speichern Sie ihn.
1. Ändern Sie nun den Bereich in Standardspeicheransicht.
   * Deaktivieren Sie „Übergeordnete Knotenhierarchie verwenden“.
   * Fügen Sie CMS Page 1 zu diesem Bereich hinzu und speichern Sie ihn.
1. Navigieren Sie **Inhalt** > **Seiten** > **Neue Seite hinzufügen**.
   * Geben Sie der Seite den Titel „Page 2“.
   * Weisen Sie im Abschnitt Seite in Websites den Ansichten „Alle Store“ und beiden Stores (Standard-Store-Ansicht und Store-Ansicht 2) zu und klicken Sie auf **Seite speichern**.
1. Öffnen Sie auf der CMS-Bearbeitungsseite die Registerkarte Hierarchie .
   * Weisen Sie Seite 2 dem Knoten „Store View 2“, dem Knoten „Default“ und dem Knoten „All Websites“ zu.

<u>Erwartete Ergebnisse</u>:

Sie können die CMS-Seite ohne Fehler allen drei Knoten zuweisen.

<u>Tatsächliche Ergebnisse</u>:

Es wird folgender Fehler angezeigt: *Eindeutige Einschränkungsverletzung gefunden*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [Überprüfen Sie mit dem Quality Patches Tool, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
