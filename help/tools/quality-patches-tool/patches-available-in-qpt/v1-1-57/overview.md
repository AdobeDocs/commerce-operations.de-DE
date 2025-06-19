---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.57'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.57  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 3e252a71-f35f-4046-9353-169060451ffe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.57

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.57 verfügbaren Patches behoben wurden.

QPT v1.1.57 enthält die folgenden Patches:

1. **ACSD-57570**: Es wird ein Problem behoben, bei dem ein Admin-Benutzer mit Zugriffsrechten auf einen bestimmten Store nicht immer alle freigegebenen Kataloge sehen kann, denen die Produkte zugewiesen sind, oder Kunden sehen kann, die nicht speichern können, was zu Inkonsistenzen im System führt.
1. **ACSD-58325**: Es wird das Problem behoben, dass die Schaltfläche [!UICONTROL Import] auch nach einem Validierungsfehler verfügbar ist.
1. **ACSD-59083**: Es wird der Fehler behoben, bei dem einige Datenbankaktualisierungsvorgänge zu _Basistabelle oder Ansicht nicht gefunden_ führen, wenn die [!DNL mview] Aktualisierung gleichzeitig ausgeführt wird.
1. **ACSD-61622**: Es wurde ein Problem behoben, bei dem [!DNL FedEx] kontospezifischen Raten in der Antwort fehlen. ACSD-61622 ersetzt die Fehlerbehebung, die in [[!DNL FedEx] Migration der Versandmethodenintegration von zu [!DNL SOAP]  dokumentiert  [!DNL RESTful API]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api).
1. **ACSD-61895**: Es wird ein Problem behoben, bei dem die Kategorien [!DNL GraphQL] Abfrage Kategorien mit der Berechtigung *allow* zurückgibt, auch wenn die Stammkategorie nicht über *allow*-Berechtigung verfügt.
1. **ACSD-62212**: Es wird ein Problem behoben, bei dem der [!UICONTROL Forgot Password] E-Mail-Inhalt nicht in die Sprache der Store-Ansicht übersetzt wird.
1. **ACSD-62481**: Es wird ein Problem behoben, bei dem der Warenkorb des Kunden auch dann leer bleibt, wenn [!UICONTROL Persistence] aktiviert ist.
1. **ACSD-62629**: Es wird das Problem behoben, dass eine in [!UICONTROL Widgets] verwendete Produktliste die Kategoriebedingung nicht erfüllt.
1. **ACSD-62635**: Es wird das Problem behoben, dass Produkte, die zu mehreren Stores gehören, in der [!DNL GraphQL]-Produktabfrage nicht korrekt angezeigt werden.
1. **ACSD-62671**: Es wird ein Problem behoben, bei dem die [!DNL GraphQL] beim ersten Versuch keine aktuellen Adressinformationen zurückgibt.
1. **ACSD-62689**: Es wird das Problem behoben, dass Kundinnen und Kunden nach Tiefe 4 keine Kategorien in [!UICONTROL Related Product Rules] und [!UICONTROL Widgets] hinzufügen können.
1. **ACSD-62708**: Es wurde ein Problem behoben, bei dem die Schriftgröße [!DNL TinyMCE] 7-Editors in der Admin nach der Anwendung der Korrektur von [!UICONTROL ACP2E-3430] als [!UICONTROL pt] und nicht [!UICONTROL px] angezeigt wurde. Jetzt können Sie die Schriftgröße auch in [!UICONTROL px] anstelle von [!UICONTROL pt] festlegen.
1. **ACSD-62758**: Es wird das Problem behoben, dass Produktvideos auf der Seite mit den [!UICONTROL Configurable Product] nicht korrekt gerendert werden, wenn die URL ausgewählte Optionen enthält.
1. **ACSD-62951**: Es wird ein Problem behoben, bei dem die [!UICONTROL Credit Memo]-E-Mail gesendet wird, ohne Elemente und Gesamtwerte einzubeziehen.
1. **ACSD-62965**: Es wird ein Problem behoben, bei dem *Meldung „LocalizedException* nicht in der [!DNL GraphQL response] enthalten ist.
1. **ACSD-63286**: Es wird das Problem behoben, dass Produkte, die einem freigegebenen Katalog über die API zugewiesen sind, erst dann in der Storefront angezeigt werden, wenn eine manuelle Neuindizierung ausgeführt wird.
1. **ACSD-63326**: Es wird ein Problem behoben, bei dem der Administrator nach einer Bestellung über das Backend zu einer fehlerhaften Seite weitergeleitet wird.


Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
