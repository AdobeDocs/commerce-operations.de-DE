---
title: 'Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool]  (QPT) v1.1.42 verfügbaren Patches behoben wurden.
feature: Tools and External Services
role: Admin, Developer
exl-id: 40db5196-0ba3-49c4-97b7-32f146c67f95
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Übersicht: [!DNL Quality Patches Tool] (QPT) v1.1.42

Dieser Unterabschnitt enthält eine detaillierte Beschreibung der Probleme, die durch die in [!DNL Quality Patches Tool] (QPT) v1.1.42 verfügbaren Patches behoben wurden.

QPT v1.1.42 umfasst die folgenden Patches:

1. **ACSD-53658**: Behebung des Problems, bei dem *[!UICONTROL Recently Viewed]* -Produktdaten in der Store-Ansicht nicht ordnungsgemäß aktualisiert wurden.
1. **ACSD-54626**: Behebung des Problems, bei dem Sie keine neue Bestellregel (`createPurchaseOrderApprovalRule`) mit dem Attribut `NUMBER_OF_SKUS` über GraphQL erstellen können.
1. **ACSD-53845**: Behebt das Problem mit dem MySQL-Verbindungstimeout, wenn `consumer max_messages` = 0 ist.
1. **ACSD-54890**: Behebung des Problems, bei dem `aggregate_sales_report_bestsellers_data` MySQL-Fehler verursacht, weil `/tmp` nicht genügend Speicherplatz vorhanden ist.
1. **ACSD-55112**: Behebung des Problems, bei dem die Schaltfläche *[!UICONTROL Submit review]* mehrmals ohne Validierung von [!DNL Google reCAPTCHA v3] angeklickt werden kann.
1. **ACSD-54264**: Behebung des Problems, bei dem die Fehlermeldung *Sie können das angeforderte Attribut nicht aktualisieren können. Zeilen-ID: store_id* wird angezeigt, wenn ein Kunde versucht, mit einem übertragbaren Angebot aus einer anderen Store-Ansicht auszuchecken.
1. **ACSD-54418**: Behebung des Problems, bei dem ein fester Rabatt fälschlicherweise auf jedes untergeordnete Produkt des dynamisch primierten Bundles angewendet wird.
1. **ACSD-55238**: Behebung des Problems beim Speichern der leeren Produktmeta-Beschreibung.
1. **ACSD-54966**: Behebung des Problems, bei dem ein Gutscheincode mit einer begrenzten Nutzung pro Kunde nicht wiederverwendet werden kann, wenn die vorherige Bestellung fehlgeschlagen ist.
1. **ACSD-54060**: Behebung des Problems, bei dem ein eingeschränkter Administrator ein Produkt nicht speichern kann, wenn es ein untergeordnetes Element eines anderen Produkts ist, das einem anderen Bereich zugewiesen ist.
1. **ACSD-48910**: Behebung des Problems, bei dem ein gebündeltes Produkt, das mehreren Quellen zugeordnet ist, nach dem Fakturieren und Versand einer Bestellung nicht mehr vorrätig ist, selbst wenn es eine Menge ungleich null hat.
1. **ACSD-55381**: Behebt einen internen Serverfehler bei der Abfrage von `configurable_product_option_uid` und `configurable_product_option_value_uid` Feldern von B2B *[!UICONTROL Requisition list]* über GraphQL.
1. **ACSD-55628**: Fehlerkorrektur - das Hochladen einer Datei auf das Registrierungsformular für das Unternehmen und das Ersetzen einer Datei für ein Kundenattribut auf der Storefront werden korrigiert.

Navigieren Sie über das Menü links zu einer bestimmten Patch-Seite.
