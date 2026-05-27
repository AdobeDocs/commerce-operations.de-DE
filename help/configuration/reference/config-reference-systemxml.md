---
title: System.Xml-Referenz
description: Erfahren Sie, wie die Datei „system.xml“ die Konfiguration von Adobe Commerce-Anwendungen verwaltet. Lernen Sie die Systemkonfigurationsverwaltung, die XML-Struktur und Implementierungstechniken kennen.
feature: Configuration, System
badge: label="Ein Beitrag von David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '2740'
ht-degree: 0%

---

# System.Xml-Referenz

Mit der `system.xml` können Sie die Commerce-Systemkonfiguration verwalten. Verwenden Sie dieses Thema als allgemeine Referenz für die `system.xml`. Die `system.xml` befindet sich unter `etc/adminhtml/system.xml` in einer bestimmten Commerce 2-Erweiterung.

Das folgende Codefragment zeigt das bloße Skelett der Datei:

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>Wenn Sie eine sofortige *XSD-Validierung in Ihrer IDE wünschen, können Sie `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>` ausführen.

## Registerkarten // Abschnitte // Gruppen // Felder

In der `system.xml`-Datei können vier verschiedene Typen von Entitäten definiert werden, die miteinander verknüpft sind. Im folgenden Abschnitt wird die Beziehung zwischen Registerkarten, Abschnitten, Gruppen und Feldern beschrieben. Der folgende Screenshot zeigt die Commerce 2-Systemkonfiguration im Admin-Backend.
Die roten Quadrate kennzeichnen die verschiedenen Typen, die in der `system.xml` definiert sind:

![Screenshot mit einem konfigurierten Abschnitt in „Admin“.](../../assets/configuration/magento2-system-configuration.png)

Registerkarten werden verwendet, um verschiedene Konfigurationsbereiche semantisch aufzuteilen. Jede Registerkarte kann einen oder mehrere Abschnitte enthalten, die auch als Untermenüs referenziert werden können. Ein Abschnitt enthält eine oder mehrere Gruppen.
Jede Gruppe listet ein oder mehrere Felder auf. Sie können auch eine Gruppe verwenden, um eine allgemeine Beschreibung für die folgenden Felder hinzuzufügen. Wie bereits erwähnt, kann jede Gruppe ein oder mehrere Felder enthalten. Felder sind die kleinste Entität
im Systemkonfigurationskontext.

## Registerkarten

Ein `<tab>`-Tag verweist entweder auf eine vorhandene oder eine neue Registerkarte in der Systemkonfiguration.

### Attributverweis für Registerkarte

Ein `<tab>`-Tag kann die folgenden Attribute aufweisen:

| Attribut | Beschreibung | Typ | Erforderlich |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Definiert die Kennung, die für den Verweis auf den Abschnitt verwendet wird. | `typeId` | required |
| `translate` | Definiert das Feld, das übersetzbar sein soll. Geben Sie `label` an, um die Bezeichnung übersetzbar zu machen. | `string` | fakultativ |
| `sortOrder` | Definiert die Sortierreihenfolge der Sektion. Hohe Zahlen schieben den Abschnitt an das Ende der Seite; niedrige Zahlen drücken den Abschnitt an das Ende. | `float` | fakultativ |
| `class` | Fügt dem gerenderten HTML-Element der Registerkarte eine definierte CSS-Klasse hinzu. | `string` | fakultativ |

### Tab-Knotenreferenz

Ein `<tab>`-Tag kann das folgende untergeordnete Element haben:

| Knoten | Beschreibung | Typ |
|---------|------------------------------------------------------|----------|
| `label` | Definiert die Bezeichnung, die im Frontend angezeigt wird. | `string` |

### Beispiel: Erstellen einer Registerkarte

Das folgende Codefragment veranschaulicht die Erstellung einer neuen Registerkarte mit Beispieldaten.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

Der obige Ausschnitt erstellt eine neue Registerkarte mit der `A_UNIQUE_ID`. Da das `translate`-Attribut definiert ist und auf die Beschriftung verweist, ist der `label`-Knoten übersetzbar. Während des Renderings wird die CSS-Klasse `a-custom-css-class-to-style-this-tab` auf das HTML-Element angewendet, das für diese Registerkarte erstellt wurde.
Das `sortOrder`-Attribut mit dem Wert `10` definiert die Position der Registerkarte in der Liste aller Registerkarten, wenn sie gerendert wird.

## Abschnitte

Ein `<section>`-Tag verweist entweder auf einen vorhandenen oder einen neuen Abschnitt in der Systemkonfiguration.

### Abschnittsattributverweis

Ein `<section>`-Tag kann die folgenden Attribute aufweisen:

| Attribut | Beschreibung | Typ | Erforderlich |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definiert die Kennung, die für den Verweis auf den Abschnitt verwendet wird. | `typeId` | required |
| `translate` | Definiert das Feld, das übersetzbar sein soll. Geben Sie `label` an, um die Bezeichnung übersetzbar zu machen. | `string` | fakultativ |
| `type` | Definiert den Eingabetyp des gerenderten HTML-Elements. Die Standardeinstellung ist `text`. | `string` | fakultativ |
| `sortOrder` | Definiert die Sortierreihenfolge der Sektion. Hohe Zahlen schieben den Abschnitt an das Ende der Seite; niedrige Zahlen drücken den Abschnitt an das Ende. | `float` | fakultativ |
| `showInDefault` | Definiert, ob der Abschnitt im Standardkonfigurationsbereich angezeigt wird. Geben Sie an, `1` der Abschnitt angezeigt werden soll und `0` der Abschnitt ausgeblendet werden soll. | `int` | fakultativ |
| `showInStore` | Definiert, ob der Abschnitt auf Store-Ebene angezeigt wird. Geben Sie an, `1` der Abschnitt angezeigt werden soll und `0` der Abschnitt ausgeblendet werden soll. | `int` | fakultativ |
| `showInWebsite` | Definiert, ob der Abschnitt auf Website-Ebene angezeigt wird. Geben Sie an, `1` der Abschnitt angezeigt werden soll und `0` der Abschnitt ausgeblendet werden soll. | `int` | fakultativ |
| `canRestore` | Definiert, ob der Abschnitt auf den Standard zurückgesetzt werden kann. | `int` | fakultativ |
| `advanced` | Veraltet seit 100.0.2. | `bool` | fakultativ |
| `extends` | Indem Sie eine Kennung für einen anderen Abschnitt angeben, erweitert der Inhalt dieses Knotens den referenzierten Abschnitt. | `string` | fakultativ |

### Knotenreferenz des Abschnitts

Ein `<section>`-Tag kann die folgenden untergeordneten Elemente aufweisen:

| Knoten | Beschreibung | Typ |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Definiert die Bezeichnung, die im Frontend angezeigt wird. | `string` |
| `class` | Fügt eine definierte CSS-Klasse zum gerenderten HTML-Element des Abschnitts hinzu. | `string` |
| `tab` | Verweist auf die zugehörige Registerkarte. Erwartet die ID der Registerkarte. | `typeTabId` |
| `header_css` | Zum Zeitpunkt dieses Schreibens weder verwendet noch ausgewertet. | `string` |
| `resource` | Verweist auf eine ACL-Ressource, um Berechtigungseinstellungen für diesen Abschnitt bereitzustellen. | `typeAclResourceId` |
| `group` | Eine oder mehrere Untergruppen definieren. | `typeGroup` |
| `frontend_model` | Gibt ein anderes Frontend-Modell an, um das Rendering zu ändern und die Ausgabe zu ändern. | `typeModel` |
| `include` | Wird verwendet, um zusätzliche `system_include.xsd` kompatible Dateien einzuschließen. Wird in der Regel zum Strukturieren großer `system.xml` verwendet. | `includeType` |

### Beispiel: Abschnitt erstellen und einer Registerkarte zuweisen

Das folgende Codefragment veranschaulicht die grundlegende Verwendung beim Erstellen eines neuen Abschnitts.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

Der oben beschriebene Abschnitt definiert die ID `A_UNIQUE_SECTION_ID`, ist in der Standardkonfigurationsansicht und in einem Store-Kontext sichtbar. Der `label`-Knoten ist übersetzbar. Der Abschnitt ist mit der Registerkarte mit der ID `A_UNIQUE_ID` verknüpft. Der Abschnitt kann nur von Benutzern aufgerufen werden, die über die in der ACL-`VENDOR_MODULE::path_to_the_acl_resource` definierten Berechtigungen verfügen.

## Gruppen

Der `<group>`-Tag wird verwendet, um Felder zu gruppieren.

### Gruppenattributverweis

Ein `<group>`-Tag kann die folgenden Attribute aufweisen:

| Attribut | Beschreibung | Typ | Erforderlich |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definiert die Kennung, die für den Verweis auf die Gruppe verwendet wird. | `typeId` | required |
| `translate` | Definiert die Felder, die übersetzbar sein sollen. Geben Sie `label` an, um die Bezeichnung übersetzbar zu machen. Mehrere Felder sollten durch ein Leerzeichen getrennt werden. | `string` | fakultativ |
| `type` | Definiert den Eingabetyp des gerenderten HTML-Elements. Die Standardeinstellung ist `text`. | `string` | fakultativ |
| `sortOrder` | Definiert die Sortierreihenfolge der Sektion. Hohe Zahlen schieben den Abschnitt an das Ende der Seite; niedrige Zahlen drücken den Abschnitt an das Ende. | `float` | fakultativ |
| `showInDefault` | Definiert, ob die Gruppe im Standardkonfigurationsbereich angezeigt wird. Geben Sie an, `1` die Gruppe angezeigt werden soll und `0` die Gruppe ausgeblendet werden soll. | `int` | fakultativ |
| `showInStore` | Legt fest, ob die Gruppe auf Store-Ebene angezeigt wird Geben Sie an, `1` die Gruppe angezeigt werden soll und `0` die Gruppe ausgeblendet werden soll. | `int` | fakultativ |
| `showInWebsite` | Definiert, ob die Gruppe auf Website-Ebene angezeigt wird. Geben Sie an, `1` die Gruppe angezeigt werden soll und `0` die Gruppe ausgeblendet werden soll. | `int` | fakultativ |
| `canRestore` | Legt fest, ob die Gruppe auf den Standard zurückgesetzt werden kann. | `int` | fakultativ |
| `advanced` | Veraltet seit 100.0.2. | `bool` | fakultativ |
| `extends` | Durch Angabe einer Kennung für eine andere Gruppe erweitert der Inhalt dieses Knotens den referenzierten Abschnitt. | `string` | fakultativ |

### Gruppenknoten-Referenz

Ein `<group>`-Tag kann die folgenden untergeordneten Elemente aufweisen:

| Knoten | Beschreibung | Typ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Definiert die Bezeichnung, die im Frontend angezeigt wird. | `string` |
| `fieldset_css` | Fügt einer Feldergruppe eine oder mehrere CSS-Klassen hinzu. | `string` |
| `frontend_model` | Gibt ein anderes Frontend-Modell an, um das Rendering zu ändern und die Ausgabe zu ändern. | `typeModel` |
| `clone_model` | Gibt ein bestimmtes Modell zum Klonen von Feldern an. | `typeModel` |
| `clone_fields` | Klonen von Feldern aktiviert oder deaktiviert. | `int` |
| `help_url` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `more_url` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `demo_link` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `comment` | Fügt unterhalb der Gruppenbeschriftung einen Kommentar ein. Durch Verwendung von `<![CDATA[//]]>` kann HTML angewendet werden. | `string` |
| `hide_in_single_store_mode` | Gibt an, ob die Gruppe im Einzelspeichermodus angezeigt werden soll. `1` blendet die Gruppe aus, `0` zeigt die Gruppe an. | `int` |
| `field` | Definieren Sie ein oder mehrere Felder, die unter dieser Gruppe verfügbar sein sollen. | `field` |
| `group` | Eine oder mehrere Untergruppen definieren. | `unbounded` |
| `depends` | Kann verwendet werden, um Abhängigkeiten von anderen Feldern zu deklarieren. Wird verwendet, um bestimmte Felder/Gruppen nur anzuzeigen, wenn ein bestimmtes Feld einen Wert von `1` hat. Dieser Knoten erwartet eine `section/group/field` Zeichenfolge. | `depends` |
| `attribute` | Benutzerdefinierte Attribute können von Frontend-Modellen verwendet werden. Wird in der Regel verwendet, um ein bestimmtes Frontend-Modell dynamischer zu machen. | `attribute` |
| `include` | Wird verwendet, um zusätzliche `system_include.xsd` kompatible Dateien einzuschließen. Wird in der Regel zum Strukturieren großer `system.xml` verwendet. | `includeType` |

>[!WARNING]
>
>Die Knoten `more_url`, `demo_url` und `help_url` werden durch ein PayPal-Frontend-Modell definiert, das nur einmal verwendet wird. Diese Knoten sind nicht wiederverwendbar.

### Beispiel: Erstellen einer Gruppe für einen bestimmten Abschnitt

Das folgende Codefragment veranschaulicht die grundlegende Verwendung beim Erstellen einer neuen Gruppe.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

Die oben beschriebene Gruppe definiert die ID `A_UNIQUE_GROUP_ID` und ist in der Standardkonfigurationsansicht und in einem Store-Kontext sichtbar. Sowohl die `label` als auch die `comment` werden als übersetzbar markiert.

## Felder

Der `<field>`-Tag wird innerhalb von `<group>`-Tags verwendet, um bestimmte Konfigurationswerte zu definieren.

### Feldattributverweis

Ein `<field>`-Tag kann die folgenden Attribute aufweisen:

| Attribut | Beschreibung | Typ | Erforderlich |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definiert die Kennung, die für den Verweis auf das Feld verwendet wird. | `typeId` | required |
| `translate` | Definiert die Felder, die übersetzbar sein sollen. Geben Sie `label` an, um die Bezeichnung übersetzbar zu machen. Mehrere Felder sollten durch ein Leerzeichen getrennt werden. | `string` | fakultativ |
| `type` | Definiert den Eingabetyp des gerenderten HTML-Elements. Die Standardeinstellung ist `text`. | `string` | fakultativ |
| `sortOrder` | Definiert die Sortierreihenfolge der Sektion. Hohe Zahlen schieben den Abschnitt an das Ende der Seite; niedrige Zahlen drücken den Abschnitt an das Ende. | `float` | fakultativ |
| `showInDefault` | Definiert, ob das Feld im Standardkonfigurationsbereich angezeigt wird. Geben Sie an, `1` das Feld angezeigt werden soll und `0` das Feld ausgeblendet werden soll. | `int` | fakultativ |
| `showInStore` | Definiert, ob das Feld auf Store-Ebene angezeigt wird. Geben Sie an, `1` das Feld angezeigt werden soll und `0` das Feld ausgeblendet werden soll. | `int` | fakultativ |
| `showInWebsite` | Definiert, ob das Feld auf Website-Ebene angezeigt wird. Geben Sie an, `1` das Feld angezeigt werden soll und `0` das Feld ausgeblendet werden soll. | `int` | fakultativ |
| `canRestore` | Legt fest, ob das Feld auf den Standard zurückgesetzt werden kann. | `int` | fakultativ |
| `advanced` | Veraltet seit 100.0.2. | `bool` | fakultativ |
| `extends` | Indem Sie eine Kennung für ein anderes Feld angeben, erweitert der Inhalt dieses Knotens den referenzierten Abschnitt. | `string` | fakultativ |

### Feldtyp-Referenz

Ein `<field>`-Tag kann die folgenden Werte für das `type=""` haben:

| Typ | Beschreibung |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Standardmäßiges, einzeiliges Textfeld |
| `textarea` | Textblock |
| `select` | Normales Dropdown-Menü, erfordert möglicherweise ein benutzerdefiniertes `source_model`. Wird auch für `Yes/No` Auswahlen verwendet. Ein Beispiel finden Sie unter `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` . |
| `multiselect` | Wie `select`, aber mehrere Optionen sind gültig. |
| `button` | Eine Schaltfläche, die ein sofortiges Ereignis Trigger. Erfordert ein benutzerdefiniertes Frontend-Modell, um den Schaltflächentext und die Aktion zu definieren. Ein Beispiel finden Sie unter `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` . |
| `obscure` | Ein Textfeld mit dem Wert verschlüsselt und als `****` angezeigt. Wenn Sie den Typ mithilfe von „Element überprüfen“ im Browser ändern, wird der Wert nicht angezeigt. |
| `password` | Wie `obscure`, mit der Ausnahme, dass der ausgeblendete Wert nicht verschlüsselt ist, und das erzwungene Ändern des Typs mit „Element überprüfen“ im Browser zeigt den Wert nicht an. |
| `file` | Ermöglicht das Hochladen einer Datei zur Verarbeitung. |
| `label` | Zeigt eine Beschriftung anstelle eines bearbeitbaren Felds an. Verwenden Sie diesen Typ, wenn ein Feld nur für bestimmte Bereiche bearbeitbar ist, z. B. nur auf Store-Ansichtsebene. |
| `time` | Zum Einstellen der Zeit können Sie drei Dropdown-Menüs verwenden: Stunde, Minute und Sekunde. |
| `allowspecific` | Eine Mehrfachauswahl-Liste spezifischer Länder. Erfordert eine `source_model` wie `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | Ermöglicht das Hochladen eines Bildes. |
| `note` | Ermöglicht das Hinzufügen einer informativen Anmerkung zur Seite. Dieser Typ erfordert eine `frontend_model` zum Rendern der Anmerkung. |

Es ist auch möglich, einen benutzerdefinierten Feldtyp zu erstellen. Dies geschieht häufig, wenn eine spezielle Schaltfläche mit einer Aktion erforderlich ist. Dazu sind zwei Hauptelemente erforderlich:

- Erstellen eines Bausteins im `adminhtml`
- Festlegen des `type=""` auf den Pfad zu diesem Block

Für den Block selbst sind mindestens eine `__construct` und eine `getElementHtml()` erforderlich. Die [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) ist ein einfaches Beispiel für einen benutzerdefinierten Typ.

Beispielsweise ist im Modul OfflineShipping die Schaltfläche Exportieren in `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` definiert und die Felddefinition sieht wie folgt aus:

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Knotenreferenz des Feldes

Ein `<field>`-Tag kann die folgenden untergeordneten Elemente aufweisen:

| Knoten | Beschreibung | Typ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Definiert die Bezeichnung, die im Frontend angezeigt wird. | `string` |
| `comment` | Fügt unter der Feldbezeichnung einen Kommentar hinzu. Durch Verwendung von `<![CDATA[//]]>` kann HTML angewendet werden. | `string` |
| `tooltip` | Ein weiteres mögliches Frontend-Element, das zur Beschreibung der Bedeutung dieses Felds verwendet werden kann. Wird als kleines Symbol neben dem Feld angezeigt. | `string` |
| `hint` | Zeigt zusätzliche Informationen an. Nur mit bestimmten `frontend_model` verfügbar. | `string` |
| `frontend_class` | Fügt eine definierte CSS-Klasse zum gerenderten HTML-Element des Abschnitts hinzu. | `string` |
| `frontend_model` | Gibt ein anderes Frontend-Modell an, um das Rendering zu ändern und die Ausgabe zu ändern. | `typeModel` |
| `backend_model` | Gibt ein anderes Backend-Modell zum Ändern der konfigurierten Werte an. | `typeModel` |
| `source_model` | Gibt ein anderes Quellmodell an, das einen bestimmten Satz von Werten bereitstellt. | `typeModel` |
| `config_path` | Kann verwendet werden, um den allgemeinen Konfigurationspfad eines Felds zu überschreiben. | `typeConfigPath` |
| `validate` | Definieren Sie verschiedene Validierungsregeln (durch Leerzeichen getrennt). Eine vollständige Referenzliste der verfügbaren Validierungsregeln finden Sie unten. | `string` |
| `can_be_empty` | Wird verwendet, wenn `type` `multiselect` wird, um anzugeben, dass ein Feld leer sein kann. | `int` |
| `if_module_enabled` | Wird verwendet, um ein Feld nur anzuzeigen, wenn ein bestimmtes Modul aktiviert ist. | `typeModule` |
| `base_url` | Wird zusammen mit `upload_dir` für Datei-Uploads verwendet. | `typeUrl` |
| `upload_dir` | Geben Sie einen Zielordner für Uploads an. Dieser Knoten verfügt über zusätzliche Attribute und Knoten. Schlagen Sie sie nach, bevor Sie dies verwenden. | `typeUploadDir` |
| `button_url` | Zeigt eine Schaltfläche an, wenn `button_url` und `button_label` angegeben sind. Wird normalerweise in Kombination mit einem benutzerdefinierten Frontend-Modell verwendet. | `typeUrl` |
| `button_label` | Zeigt eine Schaltfläche an, wenn `button_label` und `button_url` angegeben sind. Wird normalerweise in Kombination mit einem benutzerdefinierten Frontend-Modell verwendet. | `string` |
| `more_url` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `demo_url` | Nicht erweiterbar. Siehe unten. | `typeUrl` |
| `hide_in_single_store_mode` | Gibt an, ob die Gruppe im Einzelspeichermodus angezeigt werden soll. `1` blendet die Gruppe aus, `0` zeigt die Gruppe an. | `int` |
| `options` | Nicht verwendet. Möglicherweise veraltet. | `complexType` |
| `depends` | Kann verwendet werden, um Abhängigkeiten zu anderen Feldern zu deklarieren. Wird verwendet, um nur bestimmte Felder/Gruppen anzuzeigen, wenn ein bestimmtes Feld den Wert `1` hat. Dieser Knoten erwartet eine `section/group/field` Zeichenfolge. | `complexType` |
| `attribute` | Benutzerdefinierte Attribute können von Frontend-Modellen verwendet werden. Wird in der Regel verwendet, um ein bestimmtes Frontend-Modell dynamischer zu machen. | `complexType` |
| `requires` | Nicht erweiterbar. Siehe unten. | `complexType` |

>[!WARNING]
>
>Die Knoten `more_url`, `demo_url`, `requires` und `options` werden durch ein anderes Kernzahlungsmodell definiert und nur einmal verwendet. Diese Knoten sind nicht wiederverwendbar.

### Beispiel: Zwei Felder in einer bestimmten Gruppe erstellen

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

Im obigen Beispiel werden zwei Felder erstellt, die standardmäßig und in der Store-Ansicht beide sichtbar/konfigurierbar sind. Beide Felder enthalten einen Kommentar und eine QuickInfo, um dem Benutzer den Zweck zu beschreiben. Der `label`-Knoten ist übersetzbar.
Das Feld mit der Kennung `ANOTHER_UNIQUE_FIELD_ID` ist sichtbar, wenn das angegebene Modul in der `if_module_enabled` global aktiviert ist. Das Feld validiert seinen Wert auch anhand der Regeln `required-entry` und `no-whitespace`.
Das Feld mit dem Bezeichner `A_UNIQUE_FIELD_ID` definiert ein anderes Quellmodell, das die Werte `Yes` und `No`.

### Allgemeine Quellmodelle

Die folgenden Quellmodelle werden vom Commerce 2 Core bereitgestellt. Im Allgemeinen gibt es viele weitere Quellmodelle. In der folgenden Liste werden die häufigsten beschrieben. Beachten Sie, dass bei diesen Quellmodellen das Feldattribut `type` auf `select` gesetzt werden muss, damit es ordnungsgemäß funktioniert.

| Source-Modell | Beschreibung |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Stellt die Werte `Yes`, `No` und `Specified` bereit. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Stellt die Werte `Enable`, `Disable`. Speichert die Werte als `0` und `1` in der Datenbank. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Stellt die Werte `1 Hour`, `2 Hours`, `6 Hours`, `12 Hours` und `24 Hours` bereit. Werte werden als Ganzzahlen gespeichert. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Stellt die Werte für das Zeitformat bereit (12 h/24 h). |
| `Magento\Cron\Model\Config\Source\Frequency` | Stellt die Werte `Daily`, `Weekly` und `Monthly` bereit. Werte werden in der Datenbank als `D`, `W` und `M` gespeichert. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Stellt die Werte für einen 2-Buchstaben-Code einer bestimmten Sprache im ISO 639-1-Format bereit (z. B. en). |
| `Magento\Config\Model\Config\Source\Locale` | Stellt die Werte ähnlich den oben genannten bereit, bezieht sich jedoch auf einen Gebietsschema-Code (z. B. en_US). |

### Feldüberprüfung

Einem Feld können eine oder mehrere Validierungsklassen zugewiesen sein, um sicherzustellen, dass die Eingabe des Benutzers die Anforderungen der Erweiterung erfüllt. Validierungsregeln können mit dem `<validate>`-Tag angewendet werden.
Im folgenden Beispiel wird ein Feld validiert und es werden mehrere verschiedene Validierungsregeln hinzugefügt.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

Die folgenden Validierungsregeln sind verfügbar:

| Regel | Beschreibung |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | Erlaubt nur Buchstaben, Zahlen, Leerzeichen oder Unterstriche. |
| `integer` | Ermöglicht eine positive oder negative ganze Zahl. |
| `ipv4` | Ermöglicht eine gültige IP-v4-Adresse. |
| `ipv6` | Ermöglicht eine gültige IP-v6-Adresse. |
| `letters-only` | Nur Briefe zulässig. Beispiel: `abcABC`. |
| `letters-with-basic-punc` | Erlaubt nur Buchstaben oder Satzzeichen.<br>Muss den folgenden Ausdruck übergeben: `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | Ermöglicht eine Mobiltelefonnummer (GB). |
| `no-marginal-whitespace` | Blendet Leerzeichen am Anfang oder Ende des Werts aus. |
| `no-whitespace` | Unzulässige Leerzeichen. |
| `phoneUK` | Ermöglicht eine Telefonnummer (GB). |
| `phoneUS` | Ermöglicht eine Telefonnummer (US). |
| `required-entry` | Lässt einen leeren Wert nicht zu (gleichwertige Validierung wie `validate-no-empty`).<br>Validierungsfehlermeldung: „Dies ist ein erforderliches Feld.“ |
| `time` | Ermöglicht eine gültige Zeit im 24-Stunden-Format zwischen 00 :00 23 :59. Zum Beispiel `15`, `15:05` oder `15:05:48`. |
| `time12h` | Ermöglicht eine gültige Zeit im 12-Stunden-Format zwischen 12 :00 und 23:59:59 Uhr. Beispiel: `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | Ermöglicht 7 oder mehr Zeichen, sowohl numerische als auch alphabetische Zeichen. |
| `validate-alphanum-with-spaces` | Ermöglicht die Verwendung von Buchstaben (a-z oder A-Z), Zahlen (0-9) oder Leerzeichen. |
| `validate-clean-url` | Ermöglicht eine gültige URL. Beispiel: `https://www.example.com` oder `www.example.com`. |
| `validate-currency-dollar` | Ermöglicht einen gültigen (Dollar-)Betrag. Beispiel: 100,00 $. |
| `validate-data` | Ermöglicht die Verwendung von Buchstaben (a-z oder A-Z), Zahlen (0-9) oder Unterstrichen (\_).<br>Das erste Zeichen muss ein Buchstabe sein.<br>(Muss mit Ausdruck übereinstimmen: `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>Meldung zu Validierungsfehlern: „Verwenden Sie nur Buchstaben (a-z oder A-Z), Zahlen (0-9) oder Unterstriche (\_) in diesem Feld. Das erste Zeichen sollte ein Buchstabe sein.“ |
| `validate-date-au` | Erzwingt das folgende Datumsformat: TT/MM/JJJJ. Zum Beispiel 17/03/2006 für den 17. März 2006. |
| `validate-email` | Ermöglicht eine gültige E-Mail-Adresse. Beispiel: johndoe@domain.com. |
| `validate-emailSender` | Ermöglicht eine gültige E-Mail-Adresse. Beispiel: johndoe@domain.com. |
| `validate-fax` | Ermöglicht eine gültige Faxnummer. Beispiel: 123-456-7890. |
| `validate-no-empty` | Lässt einen leeren Wert nicht zu (gleichwertige Validierung wie `requried-entry`).<br>Validierungsfehlermeldung: „Leerer Wert“. |
| `validate-no-html-tags` | Die Verwendung von HTML-Tags ist nicht zulässig. |
| `validate-password` | Lässt 6 oder mehr Zeichen zu. Führende und nachfolgende Leerzeichen werden ignoriert. |
| `validate-phoneLax` | Ermöglicht eine gültige Telefonnummer. Zum Beispiel (123) 456-7890 oder 123-456-7890. |
| `validate-phoneStrict` | Ermöglicht eine gültige Telefonnummer. Zum Beispiel (123) 456-7890 oder 123-456-7890. |
| `validate-select` | Erzwingt, dass die ausgewählte Option keinen `null`, keinen Zeichenfolgenwert von `none` oder keine Zeichenfolgenlänge von 0 aufweist. |
| `validate-ssn` | Ermöglicht eine gültige (US-)Sozialversicherungsnummer. Beispiel: 123-45-6789. |
| `validate-street` | Ermöglicht die Verwendung von Buchstaben (a-z oder A-Z), Zahlen (0-9), Leerzeichen und nur &quot;#&quot;. |
| `validate-url` | Ermöglicht eine gültige URL. Protokoll ist erforderlich (http://, https:// oder ftp://). |
| `validate-xml-identifier` | Ermöglicht eine gültige XML-Kennung. Beispiel: something_1, block5, id-4. |
| `validate-zip-us` | Ermöglicht eine gültige (US-)Postleitzahl. Beispiel: 90602 oder 90602-1234. |
| `vinUS` | Ermöglicht den Wert der (US-)Fahrzeugidentifizierungsnummer (FIN). |

### Standardwerte

Standardwerte für Felder können in der `etc/config.xml` des Moduls festgelegt werden, indem der Standardwert im `section/group/field_ID` angegeben wird.

#### Beispiel: Standardwert für `ANOTHER_UNIQUE_FIELD_ID` festlegen (Standardbereich)

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### Beispiel: Standardwert für `ANOTHER_UNIQUE_FIELD_ID` festlegen (Website-Umfang)

Geben Sie mithilfe des `websites`-Tags den Standardwert für eine bestimmte Website an.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
