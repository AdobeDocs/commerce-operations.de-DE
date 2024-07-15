---
title: '[!DNL Upgrade Compatibility Tool] Fehlermeldungen'
description: Erfahren Sie mehr über Fehlermeldungen, die bei der Verwendung von [!DNL Upgrade Compatibility Tool] in Ihrem Adobe Commerce-Projekt auftreten.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4105'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] Fehlermeldungen

{{commerce-only}}

Diese Fehlermeldungsreferenz enthält Informationen zu Fehlern, die beim Ausführen von [!DNL Upgrade Compatibility Tool] auftreten können.

Fehlermeldungen werden nach Ebene (kritische Probleme, Fehler und Warnungen) und Typ (Kerncode, benutzerdefinierter Code und GraphQL-Schemata) kategorisiert. Jeder Typ enthält die folgenden Informationen:

- **Fehlercode**: Die von Adobe Commerce zugewiesene Kennung für die Fehlermeldung.
- **Fehlerbeschreibung**: Eine Beschreibung, die die Fehlerursache zusammenfasst.
- **Fehlerempfehlung**: Falls zutreffend, bietet eine Anleitung zur Fehlerbehebung und Fehlerbehebung.

## Kritische Fragen

### Core Code

Diese Fehler werden gemeldet, wenn einige der Kerndateien fehlen oder nicht mit dem Original übereinstimmen.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 2001 | Die Kerndatei wurde nicht gefunden | Führen Sie den Befehl `composer install` aus dem Stammverzeichnis des Projekts aus. |
| 2002 | Die Kerndatei wurde geändert. | Führen Sie den Befehl `composer install` aus dem Stammverzeichnis des Projekts aus. |
| 2003 | Komponentenabhängigkeit ist nicht installiert | Fehlende Komponentenabhängigkeiten können zu Problemen führen. Wiederherstellen der Abhängigkeit durch Ausführen von `composer require package_name`. |
| 2005 | Core-Ordner wurde nicht gefunden | Führen Sie den Befehl `composer install` aus dem Stammverzeichnis des Projekts aus. |

{style="table-layout:auto"}

### Benutzerspezifischer Code

Kritische Fehler werden ausgelöst, wenn der benutzerspezifische Code auf Entitäten verweist, die nicht in der Adobe Commerce-Zielversion vorhanden sind. Diese Fehler werden auch gemeldet, wenn kritische Kodierungsstandards verletzt wurden.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 1110 | Instanziieren nicht vorhandener Adobe Commerce-Klasse/Benutzeroberfläche | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. Instanziieren nicht vorhandener Adobe Commerce-Klasse/-Schnittstelle. |
| 1111 | Erweitern von nicht vorhandener Adobe Commerce-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Die Vererbung ist keine empfohlene Methode zur Erweiterung der Adobe Commerce-Funktionalität. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. |
| 1112 | Importieren nicht vorhandener Adobe Commerce-Klasse | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. |
| 1113 | Nicht vorhandene Adobe Commerce-Klasse laden | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. |
| 1114 | Verwenden nicht vorhandener Adobe Commerce-Klasse | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. |
| 1214 | Verwenden nicht vorhandener Adobe Commerce-Konstante | Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1215 | Nicht vorhandene Adobe Commerce-Konstante überschreiben | Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1216 | Zuweisung nicht vorhandener Adobe Commerce-Konstante | Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1312 | Importierte nicht vorhandene Adobe Commerce-Benutzeroberfläche | Erwägen Sie, die Vererbung zu entfernen oder sie durch die im Bereich der Anpassung eingeführte Benutzeroberfläche zu ersetzen. |
| 1314 | Nicht vorhandene Adobe Commerce-Benutzeroberfläche verwendet | Erwägen Sie, die Vererbung zu entfernen oder sie durch die im Bereich der Anpassung eingeführte Benutzeroberfläche zu ersetzen. |
| 1317 | Übernommene nicht vorhandene Adobe Commerce-Benutzeroberfläche | Erwägen Sie, die Vererbung zu entfernen oder sie durch die im Bereich der Anpassung eingeführte Benutzeroberfläche zu ersetzen. |
| 1318 | Nicht vorhandene Adobe Commerce-Oberfläche wurde implementiert | Erwägen Sie, die Vererbung zu entfernen oder sie durch die im Bereich der Anpassung eingeführte Benutzeroberfläche zu ersetzen. |
| 1410 | Adobe Commerce-Methode ohne Aufruf | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. |
| 1514 | Verwenden nicht vorhandener Adobe Commerce-Eigenschaft | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. |
| 1515 | Nicht vorhandene Adobe Commerce-Eigenschaft überschreiben | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. |
| 1516 | Zuweisung nicht vorhandener Adobe Commerce-Eigenschaften | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. Aktualisieren Sie die Eigenschaftenzugriffsebene auf &quot;privat&quot;, wenn sie nur innerhalb einer einzelnen Klasse verwendet werden kann. |
| 5002 | Das öffnende PHP-Tag muss der erste Inhalt in der Datei sein. | Stellen Sie sicher, dass die Datei vor dem öffnenden PHP-Tag keinen Inhalt enthält. |
| 5003 | Funktion ist veraltet | Verwenden Sie einen Ersatz, der in der Fehlermeldung vorgeschlagen wird. Wenn die Nachricht keinen Ersatz vorschlägt, muss eine gründliche Überprüfung durchgeführt werden, um eine alternative Funktion oder Implementierung auszuwählen. |
| 5005 | PHP-Syntaxfehler | Der Code muss entsprechend den PHP-Syntaxstandards aktualisiert werden. |
| 5072 | Mögliche Magento 2-Designverletzung. Typische Magento 1.x-Konstruktion erkannt | Aktualisierung der Konstruktion auf Magento 2-Standards. |
| 5076 | Kann nicht im Namespace verwendet werden, da er seit PHP 7 reserviert ist | Ersetzen Sie das reservierte Wort im Namespace durch ein nicht reserviertes Schlüsselwort. |
| 5077 | Kann nicht als Klassenname verwendet werden, da er seit PHP 7 reserviert ist | Ersetzen Sie den reservierten Klassennamen durch einen nicht reservierten Namen. |

{style="table-layout:auto"}

### DB-Schema

Kritische Probleme mit DB-Schemas werden gemeldet, wenn entfernte Kerntabellen oder -spalten durch benutzerdefinierte Begrenzungen referenziert werden.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 7009 | Benutzerdefinierte Beschränkung bezieht sich auf eine Kerntabelle, die in der Zielversion entfernt wurde | Entfernen Sie die Einschränkungs- oder Aktualisierungsattribute referenceTable und referenceColumn |
| 7010 | Benutzerdefinierte Beschränkung bezieht sich auf eine Kernspalte, die in der Zielversion entfernt wurde | Entfernen Sie die Einschränkung oder aktualisieren Sie das Attribut referenceColumn |

{style="table-layout:auto"}

### GraphQL-Schema

Kritische Probleme mit dem GraphQL-Schema werden angezeigt, wenn die Schemaelemente nicht in der Zielversion vorhanden sind.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 3101 | Typ wurde entfernt | Liste aller Abfragen, die auf dieses Feld verweisen. Überprüfen Sie, ob diese Abfragen von der Implementierung der Anpassung verwendet werden. Aktualisieren Sie den Clientcode, um die geänderte Abfrageschnittstelle zu verarbeiten. |
| 3102 | Aus Vereinigung entfernter Typ | Wenn der Vereinigungstyp in der Implementierung der GraphQL-Anforderungserstellung oder der Antwortverarbeitung verwendet wird, muss er möglicherweise aktualisiert werden. |
| 3103 | Feld entfernt | Überprüfen Sie, ob in der Codebasis für die Anpassung auf das Feld verwiesen wird. Passen Sie die Implementierung an, um den neuen Feldtyp korrekt zu handhaben. |
| 3105 | Implementierte Oberfläche entfernt | Überprüfen Sie, ob der Typ, der die entfernte Oberfläche implementiert, bei der Anpassung verwendet wird. Die Implementierung muss möglicherweise aktualisiert werden, wenn sie auf die entfernte Oberfläche angewiesen ist. |
| 3106 | Wert aus Enum entfernt | Wenn der entfernte Enum-Wert in der Implementierung der GraphQL-Anforderungserstellung oder der Antwortverarbeitung verwendet wird, muss er möglicherweise aktualisiert werden. |
| 3107 | Argument entfernt | Überprüfen Sie, ob das Feld in der angepassten Codebasis verwendet wird. Entfernen Sie das -Argument für dieses Feld. |
| 3109 | Richtlinie aufgehoben | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Passen Sie die Implementierung an, um den Verweis auf die Richtlinie zu entfernen. |
| 3110 | Richtlinienargument entfernt | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Entfernen Sie das Argument der Anweisung. |
| 3111 | Richtlinie wiederholbar entfernt | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Passen Sie die Implementierung an, um die Änderungen an der Benutzeroberfläche zu handhaben. |
| 3112 | Richtlinienstandort entfernt | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Passen Sie die Implementierung an, um die Änderungen an der Benutzeroberfläche zu handhaben. |
| 3201 | Typ geändert | Liste aller Abfragen, die auf dieses Feld verweisen. Überprüfen Sie, ob diese Abfragen von der Implementierung der Anpassung verwendet werden. Aktualisieren Sie den Clientcode, um die geänderte Abfrageschnittstelle zu verarbeiten. |
| 3203 | Feld geändert | Überprüfen Sie, ob in der Codebasis für die Anpassung auf das Feld verwiesen wird. Passen Sie die Implementierung an, um den neuen Feldtyp korrekt zu handhaben. |
| 3207 | Argument geändert | Überprüfen Sie, ob das Feld in der angepassten Codebasis verwendet wird. Aktualisieren Sie den Argumenttyp für dieses Feld. |
| 3303 | Erforderliches Eingabefeld hinzugefügt | Das Feld sollte der Anfrage hinzugefügt werden, wenn die Abfrage einschließlich dieses Felds für die Anpassung verwendet wird. |
| 3307 | Erforderliches Argument hinzugefügt | Überprüfen Sie, ob das Feld in der angepassten Codebasis verwendet wird. Das neue erforderliche Argument sollte bei Verwendung des Felds angegeben werden. |
| 3310 | Erforderliches Richtlinienargument hinzugefügt | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Fügen Sie das Argument der Anweisung hinzu. |

{style="table-layout:auto"}

## Fehler

### Benutzerspezifischer Code

Benutzerspezifische Code-Fehler werden ausgelöst, wenn benutzerdefinierter Code die Adobe Commerce-Einstiegspunkte verwendet, die nicht als `@api` betrachtet/markiert werden. Das beibehalten Verhalten solcher Einstiegspunkte ist nicht garantiert. Die Anpassung sollte stattdessen auf `@api` Einstiegspunkten basieren. Die Funktionalität, die auf Nicht-API-Adobe Commerce-Code basiert, sollte nach der Aktualisierung getestet werden. Diese Fehler werden auch gemeldet, wenn wichtige Kodierungsstandards verletzt wurden.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 1104 | Verwenden der Nicht-API-Klasse, die die API-Oberfläche erbt | Klassen, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie, den Code so zu aktualisieren, dass er stattdessen auf die als `@api` markierte Schnittstelle angewiesen ist. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1121 | Erweitern von Nicht-Adobe Commerce-API-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Die Vererbung ist keine empfohlene Methode zur Erweiterung der Adobe Commerce-Funktionalität. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. |
| 1122 | Importieren der Nicht-Adobe Commerce-API-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1123 | Nicht-Adobe Commerce-API-Klasse laden | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1124 | Verwenden der Nicht-Adobe Commerce-API-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1224 | Nicht-Adobe Commerce-API-Konstante verwenden | Konstanten, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1225 | Nicht-Adobe Commerce-API-Konstante überschreiben | Konstanten, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1226 | Zuweisung einer Nicht-Adobe Commerce-API-Konstante | Konstanten, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1322 | Importierte Nicht-Adobe Commerce-API-Benutzeroberfläche | Schnittstellen, die nicht als `@api` markiert sind, können geändert werden. Ziehen Sie in Erwägung, diese Vererbung zu entfernen oder durch Vererbung aus der Adobe Commerce-Oberfläche zu ersetzen, die als `@api` markiert ist, oder eine Schnittstelle, die im Bereich des Anpassungscodes eingeführt wurde. |
| 1324 | Nicht-Adobe Commerce-API-Benutzeroberfläche verwendet | Schnittstellen, die nicht als `@api` markiert sind, können geändert werden. Ziehen Sie in Erwägung, diese Vererbung zu entfernen oder durch Vererbung aus der Adobe Commerce-Oberfläche zu ersetzen, die als `@api` markiert ist, oder eine Schnittstelle, die im Bereich des Anpassungscodes eingeführt wurde. |
| 1327 | Übernommene Nicht-Adobe Commerce-API-Benutzeroberfläche | Konstanten, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1328 | Implementierte Nicht-Adobe Commerce-API-Benutzeroberfläche | Schnittstellen, die nicht als `@api` markiert sind, können geändert werden. Ziehen Sie in Erwägung, diese Vererbung zu entfernen oder durch Vererbung aus der Adobe Commerce-Oberfläche zu ersetzen, die als `@api` markiert ist, oder eine Schnittstelle, die im Bereich des Anpassungscodes eingeführt wurde. |
| 1420 | Instanziieren der Nicht-Adobe Commerce-API-Klasse/-Oberfläche | Klassen, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie, den Code so zu aktualisieren, dass er stattdessen auf die als `@api` markierte Schnittstelle angewiesen ist. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. Die empfohlene Methode zum Abrufen einer Instanz der Klasse ist auch die Verwendung von ID. Erwägen Sie die Verwendung einer Factory , wenn eine neue Instanz der Klasse erforderlich ist. |
| 1428 | Mögliche Abhängigkeit von Implementierungsdetails. | Klassen, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie, den Code so zu aktualisieren, dass er stattdessen auf die als `@api` markierte Schnittstelle angewiesen ist. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1429 | Nicht-Adobe Commerce-API-Methoden aufrufen | Methoden, die nicht als `@api` gekennzeichnet sind oder nicht innerhalb der API-Klasse/-Schnittstelle deklariert sind, können geändert werden. Selbst wenn die Schnittstelle der Methode in der neuen Version nicht aktualisiert wird, kann ihr Verhalten oder ihre Ausgabe unterschiedlich sein. Erwägen Sie, sich auf eine Schnittstellenmethode zu verlassen. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1449 | Aufruf der Nicht-Schnittstelle-Methode (in der Implementierung vorhanden) | Methoden, die nicht in der Benutzeroberfläche deklariert werden, können geändert werden. Erwägen Sie, sich auf eine Schnittstellenmethode zu verlassen. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1524 | Verwenden der Nicht-Adobe Commerce-API-Eigenschaft | Die Werte der Eigenschaften, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie stattdessen die Verwendung der API-Schnittstellenmethode . |
| 1525 | Nicht-Adobe Commerce-API-Eigenschaft überschreiben | Die Werte der Eigenschaften, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie stattdessen die Verwendung der API-Schnittstellenmethode . |
| 1526 | Zuweisung einer Nicht-Adobe Commerce-API-Eigenschaft | Die Werte der Eigenschaften, die nicht als `@api` markiert sind, können geändert werden. Erwägen Sie stattdessen die Verwendung der API-Schnittstellenmethode . |
| 5004 | Funktion ohne -Argument ist veraltet | Übergeben Sie die Eingabe, um als erstes Argument der Funktion zu validieren. |
| 5007 | Von der Verwendung bestimmter Funktionen wird abgeraten | Vermeiden Sie die Verwendung dieser Funktionen. |
| 5009 | Vorlagenanweisungen dürfen keine Methoden aufrufen. Nur Zugriff auf skalare Arrays ist zulässig | Entfernen Sie Methodenaufrufe aus der Vorlage. |
| 5010 | Kommentarblock der Vorlage `@vars` enthält ungültiges JSON | Fehlerbehebung für ungültige JSON. |
| 5011 | Kommentarblock der Vorlage `@vars` enthält ungültige Bezeichnung | Fehlerbehebung für ungültige Bezeichnung. |
| 5012 | Dem Kommentarblock der Vorlage `@vars` fehlt eine in der Vorlage verwendete Variable | Fügen Sie dem Kommentarblock @vars eine fehlende Variable hinzu. |
| 5013 | Vermeiden Sie die Verwendung eines sich selbst schließenden Tags mit einem nicht void HTML-Element | Verwenden Sie stattdessen das Tag close . |
| 5014 | Das Attribut `"active"` ist veraltet. | Die Liste der aktiven Module wird in der Bereitstellungskonfiguration definiert. |
| 5015 | Der Knoten `<param>` ist veraltet. | Verwenden Sie stattdessen `<argument name="..." xsi:type="...">` . |
| 5016 | Der Knoten `<instance>` ist veraltet. | Verwenden Sie stattdessen `<argument name="..." xsi:type="object">` . |
| 5017 | Der Knoten `<array>` ist veraltet. | Verwenden Sie stattdessen `<argument name="..." xsi:type="array">` . |
| 5018 | Der Knoten `<item key="...">` ist veraltet. | Verwenden Sie stattdessen `<item name="..." xsi:type="...">` . |
| 5019 | Der Knoten `<value>` ist veraltet. | Geben Sie stattdessen den tatsächlichen Wert als Textliteral an. |
| 5020 | Veralteter Knoten: `<supported_blocks>` | Wird durch `<supported_containers>` ersetzt. |
| 5021 | Veralteter Knoten: `<block_name>` | Wird durch `<container_name>` ersetzt. |
| 5022 | Fabrikname erkannt | Widget-Typ sollte nicht mit / beginnen. |
| 5023 | Veraltete ACL-Struktur in Zeile erkannt | Überprüfen Sie lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Obsolete Menüstruktur in Zeile erkannt | Überprüfen Sie app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Veraltete Systemkonfigurationsstruktur in Datei erkannt | Überprüfen Sie app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Attribut vom Typ `"text/javascript"` nicht verwenden | Verwenden Sie nur öffentliche Mitglieder. |
| 5028 | Der Zugriff auf geschützte und private Mitglieder der `Block`-Klasse ist in den phtml-Vorlagen veraltet. | Verwenden Sie nur öffentliche Mitglieder. |
| 5031 | Enthält veraltete Methode | Verwenden Sie stattdessen die Methode `getConnection()` . |
| 5042 | Falsches Format der PHP-Klassenreferenz | Vergewissern Sie sich, dass nur mit Binnenmajuskeln (camelCased letters, numbers) und ohne vorangestellten Schrägstrich auf die Klasse verwiesen wird. |
| 5043 | Falsches Format der Modulreferenz | Vergewissern Sie sich, dass nur mit Buchstaben, Zahlen, Unterstrichen und einem vorangestellten Schrägstrich auf das Modul verwiesen wird. |
| 5044 | Klasse `Zend_Db_Select` ist eingeschränkt | Empfohlene Ersetzung: `\Magento\Framework\DB\Select`. |
| 5045 | Klasse `Zend_Db_Adapter_Pdo_Mysql` ist eingeschränkt | Empfohlene Ersetzung: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Klasse `Magento\Framework\Serialize\Serializer\Serialize` ist eingeschränkt | Empfohlene Ersetzung: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Klasse `ArrayObject` ist eingeschränkt | Empfohlene Ersetzung: Benutzerdefinierte Klasse, erweitert von `ArrayObject` durch überschriebene Serialize-/Deserialize-Methoden. |
| 5048 | Klasse `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` ist eingeschränkt | Empfohlener Ersatz: Factory, die eine benutzerdefinierte Klasse erstellt, erweitert von `ArrayObject` durch überschriebene Serialize-/Deserialize-Methoden. |
| 5050 | Der referenzierte Block wird entfernt | Entfernen Sie den Verweis auf den Block. |
| 5051 | `output="toHtml"` ist veraltet | Verwenden Sie `output="1"`. |
| 5052 | Die Klasse &quot;`\Magento\Framework\View\Element\Text\ListText`&quot; sollte nicht mehr im Layout verwendet werden | Entfernen Sie die Klasse `\Magento\Framework\View\Element\Text\ListText` aus dem Layout. |
| 5053 | Aufruf der Methode über Layout-Anweisung `<action>` ist nicht zulässig | Vermeiden Sie die Verwendung einer Verstoßmethode in `<action>`. |
| 5054 | `helper` Attribut enthält `/` | Entfernen Sie `/` aus dem Helper-Attribut. |
| 5055 | `helper` Attribut enthält nicht `::` | Fügen Sie `::` zum Helper-Attribut hinzu. |
| 5056 | Installationsskripte sind veraltet | Verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml des Moduls. |
| 5057 | InstallSchema-Skripte sind veraltet | Verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml des Moduls. |
| 5058 | InstallData-Skripte sind veraltet | Verwenden Sie den Datenpatches-Ansatz im Setup/Patch/Data-Verzeichnis des Moduls. |
| 5059 | Installationsskripte sind veraltet | Erstellen Sie eine Klasse InstallData im Ordner Setup des Moduls. |
| 5060 | Aktualisierungsskripte sind veraltet | Verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml des Moduls. |
| 5061 | UpgradeSchema-Skripte sind veraltet | Verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml des Moduls. |
| 5062 | UpgradeData-Skripte sind veraltet | Verwenden Sie den Datenpatches-Ansatz im Setup/Patch/Data-Verzeichnis des Moduls. |
| 5063 | Aktualisierungsskripte sind veraltet | Verwenden Sie den Datenpatches-Ansatz im Setup/Patch/Data-Verzeichnis des Moduls. |
| 5064 | Wiederkehrende Skripte sind veraltet | Erstellen Sie die Klasse Recurring im Ordner Setup des Moduls. |
| 5065 | &#39;data&#39; befindet sich in einem ungültigen Verzeichnis. | Erstellen Sie einen Daten-Patch im Ordner Setup/Patch/Data des Moduls für Datenaktualisierungen oder verwenden Sie den deklarativen Schema-Ansatz in der Datei etc/db_schema.xml des Moduls für Schemaänderungen. |
| 5066 | &#39;sql&#39; befindet sich in einem ungültigen Verzeichnis. | Erstellen Sie einen Daten-Patch im Ordner Setup/Patch/Data des Moduls für Datenaktualisierungen oder verwenden Sie den deklarativen Schema-Ansatz in der Datei etc/db_schema.xml des Moduls für Schemaänderungen. |
| 5067 | Von XPath identifizierte Knoten sind veraltet | Die veraltete XML, die im Fehler angegeben wurde, sollte aktualisiert werden. Befolgen Sie die Vorschläge aus der Fehlermeldung. |
| 5068 | Direktive `{{htmlescape}}` ist veraltet | Verwenden Sie stattdessen `{{var}}` . |
| 5069 | Direktive `{{escapehtml}}` ist veraltet | Verwenden Sie stattdessen `{{var}}` . |
| 5070 | Der dritte Parameter wird für `getChildHtml()` nicht mehr benötigt | Entfernen Sie den dritten Parameter aus dem Aufruf an `getChildHtml()`. |
| 5071 | 4. Parameter wird für `getChildHtml()` nicht mehr benötigt | Entfernen Sie den vierten Parameter aus dem Aufruf von `getChildHtml()`. |
| 5073 | Ältere Tabellennamen mit Schrägstrich müssen auf direkte Tabellennamen fixiert sein | Verwenden Sie stattdessen den direkten Tabellennamen. |
| 5075 | Anwendungsmodule sollten keine Klassen aus Testmodulen verwenden | Entfernen Sie die Verwendung von Klassen aus Testmodulen. |
| 5078 | Klasse muss im Konstruktor angefordert werden, sonst kann Compiler diese Klassen nicht finden und generieren | Klasse zum Konstruktor hinzufügen. |
| 5079 | Von der Verwendung von Variablen der var-Klasse wird abgeraten | Vermeiden Sie die Verwendung von &quot;var&quot;zum Deklarieren von Klassenvariablen. |
| 5080 | Mögliche SQL-Rohanweisung erkannt | Verwenden Sie stattdessen Repositorys oder Daten-Patches. |
| 5081 | Von der Verwendung von Helfern in Vorlagen wird abgeraten | Verwenden Sie stattdessen ViewModel . |
| 5082 | Die Verwendung von $this in Vorlagen wird nicht mehr unterstützt | Verwenden Sie stattdessen $block . |
| 5083 | Konstanten sind nicht als erstes Argument der Übersetzungsfunktion zulässig | Verwenden Sie stattdessen das Zeichenfolgenliteral. |
| 5085 | Von der Verwendung bestimmter Funktionen wird abgeraten | Verwenden Sie stattdessen die alternative Funktion, die für die Nachricht empfohlen wird. |
| 5087 | Kompatibilitätsproblem mit PHP-Querversionen | Befolgen Sie die Vorschläge der Nachricht und überprüfen Sie das [Migrationshandbuch](https://www.php.net/manual/en/migration81.php). |
| 5088 | Optionale Parameter, die nach erforderlichen gefunden werden | Verschieben Sie erforderliche Parameter nach optionalen. |
| 5089 | Sichtbarkeit der Methode `final private` gefunden | Ändern Sie die Sichtbarkeit der Methode von `final private` in nur `private`. |
| 5090 | Magische Methode `__set_state` ist nicht als `static` definiert | Magische Methode `__set_state` muss als `static` definiert sein. |
| 5091 | Klasse mit der Methode `__toString()` , die nicht von der Oberfläche von `Stringable` erbt | Fügen Sie die `Stringable` -Schnittstelle zur Klasse mit der `__toString()` -Methode hinzu. |
| 5092 | `is_resource()` -Methode für Funktionen, die jetzt Objekt zurückgeben | Ändern Sie `is_resource()` in `instanceof` Objekt. |
| 6001 | `jQuery.andSelf()` entfernt | Verwenden Sie `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` und `$.unbind` werden nicht mehr unterstützt | Verwenden Sie stattdessen `$.on` und `$.off`. |
| 6003 | Die jQuery-Methode zum Abonnieren von Ereignissen ist veraltet und sollte nicht verwendet werden | Verwenden Sie stattdessen die Methode `.on("event name", fn)` , um dieses Ereignis zu abonnieren. |
| 6003 | Die jQuery-Methode zum Trigger-Ereignis ist veraltet und sollte nicht verwendet werden | Verwenden Sie stattdessen die Methode `.trigger("event name")` , um dieses Ereignis Trigger. |
| 6004 | jQuery `$.delegate` und `$.undelegate` werden nicht mehr unterstützt | Verwenden Sie stattdessen `$.on` und `$.off`. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) wurde entfernt | Verwenden Sie stattdessen (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` entfernt | Verwenden Sie `jQuery.length`. |
| 6007 | `jQuery.trim` ist veraltet | Verwenden Sie `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, &quot;inlite&quot;-Design, &quot;mobile&quot;Design, &quot;modernes&quot;Design) entfernt | Aktualisieren Sie den Code, um mit tinymce5 kompatibel zu sein. |
| 6009 | `jQuery.isFunction()` ist veraltet | In den meisten Fällen kann sie durch [typeof x === &quot;function&quot;] ersetzt werden. |
| 6009 | `jQuery.type()` ist veraltet | Ersetzen Sie sie durch eine entsprechende Typüberprüfung wie [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` ist veraltet | Verwenden Sie stattdessen die native Array.isArray -Methode. |
| 6009 | `jQuery.parseJSON()` ist veraltet | Um JSON-Zeichenfolgen zu analysieren, verwenden Sie stattdessen die native Methode JSON.parse . |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) veraltet ist | Verwenden Sie stattdessen jQuery.expr.pseudos . |

{style="table-layout:auto"}

### DB-Schema

DB-Schemafehler werden ausgelöst, wenn Datenbanktabellen, -spalten, -indizes oder -begrenzungen, die in der Adobe Commerce-Zielversion hinzugefügt oder entfernt werden, zu Konflikten mit dem benutzerdefinierten Datenbankschema führen können.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 7001 | Die Zielversion führt eine Tabelle mit demselben Namen wie eine Tabelle ein, die von einem benutzerdefinierten Modul deklariert wurde | Verwenden Sie die neue Kerntabelle (falls zutreffend) oder benennen Sie die benutzerdefinierte Tabelle um |
| 7002 | Die Kerntabelle, die durch ein benutzerdefiniertes Modul erweitert wird, wurde in der Zielversion entfernt | Alle entfernten Kerntabellenverweise sollten aus der Codebase entfernt werden |
| 7003 | Mit der Zielversion wird eine Spalte mit demselben Namen wie eine von einem benutzerdefinierten Modul deklarierte Spalte eingefügt | Verwenden Sie die neue Kernspalte (falls zutreffend) oder benennen Sie die benutzerdefinierte Spalte um. |
| 7004 | Die Kernspalte, die durch ein benutzerdefiniertes Modul erweitert wurde, wurde in der Zielversion entfernt | Alle entfernten Kernspaltenverweise sollten aus der Codebase entfernt werden |
| 7005 | Die Zielkernversion führt einen Index mit derselben referenceId ein, der von einem benutzerdefinierten Modul deklariert wurde | Entfernen (bei Duplizierung des eingeführten Kernindex) oder Umbenennen des benutzerdefinierten Index |
| 7006 | Der von einem benutzerdefinierten Modul erweiterte Core-Index wurde in der Zielversion entfernt | Alle entfernten Core-Indexverweise sollten aus der Codebase entfernt werden |
| 7007 | Die Ziel-Core-Version führt eine Beschränkung mit demselben Namen wie eine von einem benutzerdefinierten Modul deklarierte Beschränkung ein | Entfernen (bei Duplizierung der eingeführten Kernbegrenzung) oder Umbenennen der benutzerdefinierten Beschränkung |
| 7008 | Die durch ein benutzerdefiniertes Modul erweiterte Kernbeschränkung wurde in der Zielversion entfernt | Verwenden Sie die neue Kernbeschränkung (falls zutreffend) oder benennen Sie die benutzerdefinierte Einschränkung um. |

{style="table-layout:auto"}

## Warnungen

### Core Code

Diese Warnungen werden bei geringfügigen Inkonsistenzen in der Core-Codebase gemeldet.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 2004 | Variantenabweichung der Komponentenabhängigkeiten | Das Problem weist darauf hin, dass die Komponentenabhängigkeitsversion in etalon und dem eigentlichen Projekt unterschiedlich ist. Aktualisieren Sie die Abhängigkeit durch Ausführen von `composer update <package_name>`. |

{style="table-layout:auto"}

### Benutzerspezifischer Code

Wenn Verweise auf veralteten Code erkannt werden, werden benutzerdefinierte Code-Warnungen ausgelöst. Solche Verweise sollten durch die unterstützten Erweiterungspunkte ersetzt werden. Achten Sie bei Empfehlungen auf die Anmerkung `@see` des veralteten Elements. Diese Fehler werden auch gemeldet, wenn kleinere Kodierungsstandards verletzt wurden.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 1131 | Erweitern von der Adobe Commerce ``@deprecated``-Klasse | Die erweiterte Klasse wird in den kommenden Versionen entfernt. Die Vererbung ist keine empfohlene Methode zur Erweiterung der Adobe Commerce-Funktionalität. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api` gekennzeichnet ist. |
| 1132 | Adobe Commerce `@deprecated`-Klasse importieren | Die erweiterte Klasse wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung der als `@api` markierten Adobe Commerce-Klasse. |
| 1133 | Laden der Adobe Commerce `@deprecated`-Klasse | Die erweiterte Klasse wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung der als `@api` markierten Adobe Commerce-Klasse. |
| 1134 | Verwenden der Adobe Commerce `@deprecated`-Klasse | Die erweiterte Klasse wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung der als `@api` markierten Adobe Commerce-Klasse. |
| 1234 | Adobe Commerce `@deprecated`-Konstante verwenden | Die veraltete Konstante wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung einer Konstante, die als `@api` oder eine private Konstante in Ihrer Implementierung markiert ist. |
| 1235 | Überschreiben der Adobe Commerce `@deprecated`-Konstante | Die veraltete Konstante wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung einer Konstante, die als `@api` oder eine private Konstante in Ihrer Implementierung markiert ist. |
| 1236 | Zuweisung der Adobe Commerce `@deprecated`-Konstante | Die veraltete Konstante wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung einer Konstante, die als `@api` oder eine private Konstante in Ihrer Implementierung markiert ist. |
| 1332 | Importierte Adobe Commerce `@deprecated`-Benutzeroberfläche | Die veraltete Benutzeroberfläche wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung einer Schnittstelle oder Klasse, die als `@api` markiert ist. |
| 1334 | Verwendete Adobe Commerce `@deprecated`-Benutzeroberfläche | Die veraltete Benutzeroberfläche wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung einer Schnittstelle oder Klasse, die als `@api` markiert ist. |
| 1337 | Von der Adobe Commerce `@deprecated`-Oberfläche übernommen | Die veraltete Benutzeroberfläche wird in den kommenden Versionen entfernt. Erwägen Sie, die Vererbung der Oberfläche zu entfernen, indem Sie stattdessen eine als `@api` markierte Schnittstelle oder eine in Ihrer Implementierung eingeführte Schnittstelle verwenden. |
| 1338 | Implementierung der Adobe Commerce `@deprecated`-Benutzeroberfläche | Die veraltete Benutzeroberfläche wird in den kommenden Versionen entfernt. Erwägen Sie, die Vererbung der Oberfläche zu entfernen, indem Sie stattdessen eine als `@api` markierte Schnittstelle oder eine in Ihrer Implementierung eingeführte Schnittstelle verwenden. |
| 1430 | Aufruf nicht deklarierte Datenobjektmethode | Die nicht deklarierten magischen Methoden können sich ändern. Erwägen Sie stattdessen die Verwendung von Oberflächenmethoden . |
| 1439 | Adobe Commerce `@deprecated`-Methode aufrufen | Die veraltete Methode wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen, sich auf Methoden zu verlassen, die in API-Schnittstellen deklariert sind. |
| 1440 | Methodenunterschrift stimmt nicht überein | Ein Aufruf oder eine Überschreibung der Kernmethode wird mit Parametern, Argumenten oder Rückgabetyp erkannt, die nicht mit der Methodensignatur übereinstimmen. |
| 1534 | Verwenden der Adobe Commerce `@deprecated`-Eigenschaft | Die veraltete Methode wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen, sich auf Methoden zu verlassen, die in API-Schnittstellen deklariert sind. |
| 1535 | Überschreiben der Adobe Commerce `@deprecated`-Eigenschaft | Die veraltete Eigenschaft wird in den kommenden Versionen entfernt. Ziehen Sie stattdessen die Verwendung von Methoden in Betracht, die in API-Schnittstellen deklariert wurden, oder die Verwendung einer privaten Eigenschaft in Ihrer Implementierung. |
| 1536 | Zuweisung der Adobe Commerce `@deprecated`-Eigenschaft | Die veraltete Methode wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen, sich auf Methoden zu verlassen, die in API-Schnittstellen deklariert sind. |
| 5006 | Proxys und Abfänger dürfen in Konstruktoren niemals explizit angefordert werden | Die ursprüngliche Klasse sollte als Typ des Konstruktorparameters deklariert werden. Die Interceptor/Proxy-Klasse wird von der Implementierung der Framework-Abhängigkeitsinjektion übergeben. |
| 5074 | Verwendung der veralteten Methode `getResource()` zum (Speichern/Laden/Löschen) erkannter Daten. | Verwenden Sie stattdessen ein Repository. |
| 5086 | Sichtbarkeit wird nicht auf einer Konstante deklariert | Deklarieren Sie die Sichtbarkeit für alle Konstanten. |

{style="table-layout:auto"}

### GraphQL-Schema

GraphQL-Schemawarnungen werden ausgelöst, wenn die zusätzlichen Elemente in der neuen Version zum Schema hinzugefügt werden. Es wird empfohlen, die Implementierung zu überprüfen, um zu sehen, ob sie für Anfragen verwendet werden sollten.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 3206 | Standardwert des Arguments geändert | Wenn die Abfrage bei der Anpassung verwendet wird, muss der Argumentwert möglicherweise explizit angegeben werden. |
| 3302 | Typ hinzugefügt zur Vereinigung | Der Typ wurde der Vereinigung hinzugefügt. Überprüfen Sie die Implementierung, die das Ergebnis der Abfrage verarbeitet, die diesen Vereinigungstyp zurückgibt, und stellen Sie sicher, dass sie den hinzugefügten Typ verarbeiten kann. |
| 3304 | Optionales Eingabefeld hinzugefügt | Optionales Eingabefeld hinzugefügt. Überprüfen Sie die Implementierung, um sicherzustellen. |
| 3305 | Implementierte Benutzeroberfläche hinzugefügt | Das Feld kann weitere Informationen akzeptieren/bereitstellen, die in der Implementierung berücksichtigt werden können. |
| 3306 | Wert zu Enum hinzugefügt | Ein Wert wurde zu einer -Enumeration hinzugefügt. Wenn Clients eine switch -Anweisung zum Wert der Enum enthalten und keinen Standardfall enthalten, kann diese Änderung zu unerwartetem Verhalten führen. |
| 3308 | Optionales Argument hinzugefügt | Wenn die Abfrage bei der Anpassung ein neues Argument verwendet, muss es möglicherweise der Anfrage hinzugefügt werden. |

{style="table-layout:auto"}
