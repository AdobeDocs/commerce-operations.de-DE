---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in Version 1.1.42  [!DNL Quality Patches Tool]  Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 40db5196-0ba3-49c4-97b7-32f146c67f95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Überblick: [!DNL Quality Patches Tool] (QPT) v1.1.42

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.42 verfügbaren Patches behoben wurden.

QPT v1.1.42 enthält die folgenden Patches:

1. **ACSD-53658**: Es wird das Problem behoben, bei dem *[!UICONTROL Recently Viewed]* Produktdaten in der Store-Ansicht nicht ordnungsgemäß aktualisiert werden.
1. **ACSD-54626**: Es wurde das Problem behoben, dass keine neue Bestellregel (`createPurchaseOrderApprovalRule`) mit dem Attribut &quot;`NUMBER_OF_SKUS`&quot; über GraphQL erstellt werden kann.
1. **ACSD-53845**: Behebt das Problem der MySQL-Verbindungs-Zeitüberschreitung bei `consumer max_messages` = 0.
1. **ACSD-54890**: Behebt das Problem, dass `aggregate_sales_report_bestsellers_data` MySQL-Fehler verursacht, weil `/tmp` Festplatte nicht genügend Speicherplatz zur Verfügung steht.
1. **ACSD-55112**: Es wird das Problem behoben, dass die *[!UICONTROL Submit review]*-Schaltfläche mehrmals ohne [!DNL Google reCAPTCHA v3] Validierung angeklickt werden kann.
1. **ACSD-54264**: Es wurde das Problem behoben, dass die Fehlermeldung *Sie können das angeforderte Attribut nicht aktualisieren. Zeilenkennung: store_id* wird angezeigt, wenn ein Kunde versucht, mit einem verhandelbaren Angebot aus einer anderen Store-Ansicht auszuchecken.
1. **ACSD-54418**: Es wird ein Problem behoben, bei dem ein fester Rabattbetrag fälschlicherweise auf jedes untergeordnete Produkt des dynamisch berechneten Pakets angewendet wird.
1. **ACSD-55238**: Das Problem beim Speichern der leeren Produktmetabeschreibung wurde behoben.
1. **ACSD-54966**: Es wurde ein Problem behoben, bei dem ein Gutscheincode mit einer begrenzten Nutzung pro Kunde nicht wiederverwendet werden kann, wenn die vorherige Bestellung fehlgeschlagen ist.
1. **ACSD-54060**: Es wird ein Problem behoben, bei dem ein eingeschränkter Administrator ein Produkt nicht speichern kann, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Umfang zugewiesen wurde.
1. **ACSD-48910**: Es wird ein Problem behoben, bei dem ein gebündeltes Produkt, das mehreren Quellen zugewiesen ist, nach der Fakturierung und dem Versand einer Bestellung nicht mehr vorrätig ist, selbst wenn es eine Menge ungleich null aufweist.
1. **ACSD-55381**: Behebt einen internen Server-Fehler bei der Abfrage von `configurable_product_option_uid`- und `configurable_product_option_value_uid`-Feldern aus einem B2B-*[!UICONTROL Requisition list]* über GraphQL.
1. **ACSD-55628**: Fehlerkorrektur - Das Hochladen einer Datei auf dem Unternehmensregistrierungsformular und das Ersetzen einer Datei durch ein Kundenattribut in der Storefront wird korrigiert.

Navigieren Sie im Menü links zu einer bestimmten Patch-Seite.
