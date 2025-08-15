---
title: '[!DNL Upgrade Compatibility Tool] Fehlermeldungen'
description: Erfahren Sie mehr über Fehlermeldungen, die bei Verwendung von  [!DNL Upgrade Compatibility Tool]  in Ihrem Adobe Commerce-Projekt auftreten.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4105'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] Fehlermeldungen

{{commerce-only}}

Diese Fehlermeldungsreferenz enthält Informationen zu Fehlern, die beim Ausführen der [!DNL Upgrade Compatibility Tool] auftreten können.

Fehlermeldungen werden nach Ebene (kritische Probleme, Fehler und Warnungen) und Typ (Kern-Code, benutzerdefinierter Code und GraphQL-Schemata) kategorisiert. Jeder Typ enthält die folgenden Informationen:

- **Fehlercode**: Die von Adobe Commerce zugewiesene Kennung für die Fehlermeldung.
- **Fehlerbeschreibung**: Eine Beschreibung, die die Ursache des Fehlers zusammenfasst.
- **Vorgeschlagene Fehleraktion**: Bietet gegebenenfalls Anleitungen zur Fehlerbehebung und Fehlerbehebung.

## Kritische Probleme

### Kerncode

Diese Fehler werden gemeldet, wenn einige der Kerndateien fehlen oder nicht mit dem Original übereinstimmen.

| Fehlercode | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 2001 | Kerndatei wurde nicht gefunden | Führen Sie den `composer install` Befehl im Stammverzeichnis des Projekts aus. |
| 2002 | Kerndatei wurde geändert | Führen Sie den `composer install` Befehl im Stammverzeichnis des Projekts aus. |
| 2003 | Composer-Abhängigkeit ist nicht installiert | Fehlende Komponentenabhängigkeiten können möglicherweise zu Problemen führen. Stellen Sie die Abhängigkeit durch Ausführen von `composer require package_name` wieder her. |
| 2005 | Kernordner wurde nicht gefunden | Führen Sie den `composer install` Befehl im Stammverzeichnis des Projekts aus. |

{style="table-layout:auto"}

### Benutzerdefinierter Code

Kritische Fehler treten auf, wenn der benutzerdefinierte Code auf Entitäten verweist, die in der Adobe Commerce-Zielversion nicht vorhanden sind. Diese Fehler werden auch gemeldet, wenn kritische Codierungsstandards verletzt wurden.

| Fehlercode | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 1110 | Instanziieren einer nicht vorhandenen Adobe Commerce-Klasse/-Schnittstelle | Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. Instanziieren einer nicht vorhandenen Adobe Commerce-Klasse/-Schnittstelle. |
| 1111 | Erweitern von nicht vorhandener Adobe Commerce-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebasis vorhanden. Die Vererbung ist keine empfohlene Methode zur Erweiterung der Adobe Commerce-Funktionalität. Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. |
| 1112 | Nicht vorhandene Adobe Commerce-Klasse importieren | Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. |
| 1113 | Nicht vorhandene Adobe Commerce-Klasse wird geladen | Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. |
| 1114 | Verwenden einer nicht vorhandenen Adobe Commerce-Klasse | Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. |
| 1214 | Verwenden einer nicht vorhandenen Adobe Commerce-Konstante | Stattdessen sollte eine private Konstante des erforderlichen Werts im benutzerdefinierten Code eingeführt und verwendet werden. |
| 1215 | Überschreiben nicht vorhandener Adobe Commerce-Konstanten | Stattdessen sollte eine private Konstante des erforderlichen Werts im benutzerdefinierten Code eingeführt und verwendet werden. |
| 1216 | Zuweisung einer nicht vorhandenen Adobe Commerce-Konstante | Stattdessen sollte eine private Konstante des erforderlichen Werts im benutzerdefinierten Code eingeführt und verwendet werden. |
| 1312 | Nicht vorhandene Adobe Commerce-Benutzeroberfläche importiert | Erwägen Sie, die Vererbung zu entfernen oder durch die im Rahmen der Anpassung eingeführte Schnittstelle zu ersetzen. |
| 1314 | Nicht vorhandene Adobe Commerce-Benutzeroberfläche verwendet | Erwägen Sie, die Vererbung zu entfernen oder durch die im Rahmen der Anpassung eingeführte Schnittstelle zu ersetzen. |
| 1317 | Vererbte nicht vorhandene Adobe Commerce-Schnittstelle | Erwägen Sie, die Vererbung zu entfernen oder durch die im Rahmen der Anpassung eingeführte Schnittstelle zu ersetzen. |
| 1318 | Implementierte nicht vorhandene Adobe Commerce-Schnittstelle | Erwägen Sie, die Vererbung zu entfernen oder durch die im Rahmen der Anpassung eingeführte Schnittstelle zu ersetzen. |
| 1410 | Aufrufen der nicht vorhandenen Adobe Commerce-Methode | Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. |
| 1514 | Verwenden einer nicht vorhandenen Adobe Commerce-Eigenschaft | Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. |
| 1515 | Nicht vorhandene Adobe Commerce-Eigenschaft überschreiben | Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. |
| 1516 | Zuweisung einer nicht vorhandenen Adobe Commerce-Eigenschaft | Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. Aktualisieren Sie die Zugriffsebene der Eigenschaft auf „Privat“, wenn sie nur innerhalb einer einzelnen Klasse verwendet werden kann. |
| 5002 | Das PHP-Starttag muss der erste Inhalt in der Datei sein | Stellen Sie sicher, dass vor dem PHP-Öffnungstag kein Inhalt in der Datei vorhanden ist. |
| 5003 | Funktion ist veraltet | Verwenden Sie einen in der Fehlermeldung vorgeschlagenen Ersatz. Wenn die Meldung keinen Ersatz vorschlägt, ist eine eingehende Überprüfung erforderlich, um eine alternative Funktion oder Implementierung auszuwählen. |
| 5005 | PHP-Syntaxfehler | Der Code muss aktualisiert werden, um den PHP-Syntaxstandards zu entsprechen. |
| 5072 | Mögliche Designverletzung durch Magento 2. Typische Magento 1.x-Konstruktion erkannt | Aktualisieren Sie die Konstruktion entsprechend den Magento 2-Standards. |
| 5076 | Kann im Namespace nicht verwendet werden, da er seit PHP 7 reserviert ist | Ersetzen Sie das reservierte Wort im Namespace durch ein nicht reserviertes Keyword. |
| 5077 | Kann nicht als Klassenname verwendet werden, da er seit PHP 7 reserviert ist | Ersetzen Sie den reservierten Klassennamen durch einen nicht reservierten Namen. |

{style="table-layout:auto"}

### DB-Schema

Wichtige Probleme mit dem DB-Schema werden gemeldet, wenn entfernte Kerntabellen oder -spalten durch benutzerdefinierte Einschränkungen referenziert werden.

| Fehlercode | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 7009 | Benutzerdefinierte Einschränkung verweist auf eine Kerntabelle, die in der Zielversion entfernt wurde | Entfernen Sie die Einschränkung oder aktualisieren Sie die Attribute referenceTable und referenceColumn |
| 7010 | Benutzerdefinierte Einschränkung verweist auf eine Kernspalte, die in der Zielversion entfernt wurde | Entfernen Sie die Einschränkung oder aktualisieren Sie das referenceColumn-Attribut |

{style="table-layout:auto"}

### GraphQL-Schema

GraphQL-Schemakritische Probleme treten auf, wenn die Schemaelemente in der Zielversion nicht vorhanden sind.

| Fehlercode | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 3101 | Typ wurde entfernt | Listet alle Abfragen auf, die auf dieses Feld verweisen. Überprüfen Sie, ob diese Abfragen von der Anpassungsimplementierung verwendet werden. Aktualisieren Sie den Client-Code, um die geänderte Abfrageschnittstelle zu verarbeiten. |
| 3102 | Aus Vereinigung entfernter Typ | Wenn der Vereinigungstyp beim Erstellen einer GraphQL-Anfrage oder bei der Implementierung der Antwortverarbeitung verwendet wird, muss er möglicherweise aktualisiert werden. |
| 3103 | Feld entfernt | Überprüfen Sie, ob das Feld in der Anpassungs-Code-Basis referenziert wird. Passen Sie die Implementierung an, um den neuen Feldtyp korrekt zu verarbeiten. |
| 3105 | Implementierte Schnittstelle entfernt | Überprüfen Sie, ob bei der Anpassung der Typ verwendet wird, der die entfernte Schnittstelle implementiert. Die Implementierung muss möglicherweise aktualisiert werden, wenn sie auf die entfernte Schnittstelle angewiesen ist. |
| 3106 | Aus der Aufzählung entfernter Wert | Wenn der entfernte Enum-Wert in der Implementierung der GraphQL-Anfrage zum Aufbau oder zur Antwortverarbeitung verwendet wird, muss er möglicherweise aktualisiert werden. |
| 3107 | Argument entfernt | Überprüfen Sie, ob das Feld in der Anpassungs-Code-Basis verwendet wird. Das Argument für dieses Feld entfernen. |
| 3109 | Richtlinie entfernt | Überprüfen Sie, ob die -Anweisung in der Anpassungs-Code-Basis verwendet wird. Anpassung der Umsetzung, um den Verweis auf die Richtlinie zu entfernen. |
| 3110 | Richtlinienargument entfernt | Überprüfen Sie, ob die -Anweisung in der Anpassungs-Code-Basis verwendet wird. Entfernen Sie das Argument der Direktive. |
| 3111 | Anweisung wiederholbar entfernt | Überprüfen Sie, ob die -Anweisung in der Anpassungs-Code-Basis verwendet wird. Passen Sie die Implementierung an, um die Änderungen an der Benutzeroberfläche zu verarbeiten. |
| 3112 | Richtlinienspeicherort entfernt | Überprüfen Sie, ob die -Anweisung in der Anpassungs-Code-Basis verwendet wird. Passen Sie die Implementierung an, um die Änderungen an der Benutzeroberfläche zu verarbeiten. |
| 3201 | Typ wurde geändert | Listet alle Abfragen auf, die auf dieses Feld verweisen. Überprüfen Sie, ob diese Abfragen von der Anpassungsimplementierung verwendet werden. Aktualisieren Sie den Client-Code, um die geänderte Abfrageschnittstelle zu verarbeiten. |
| 3203 | Feldtyp geändert | Überprüfen Sie, ob das Feld in der Anpassungs-Code-Basis referenziert wird. Passen Sie die Implementierung an, um den neuen Feldtyp korrekt zu verarbeiten. |
| 3207 | Argumentart geändert | Überprüfen Sie, ob das Feld in der Anpassungs-Code-Basis verwendet wird. Aktualisieren Sie den Argumenttyp für dieses Feld. |
| 3303 | Erforderliches Eingabefeld hinzugefügt | Das Feld sollte der Anfrage hinzugefügt werden, wenn die Abfrage einschließlich dieses Felds für die Anpassung verwendet wird. |
| 3307 | Erforderliches Argument hinzugefügt | Überprüfen Sie, ob das Feld in der Anpassungs-Code-Basis verwendet wird. Das neue erforderliche Argument sollte bei Verwendung des Felds angegeben werden. |
| 3310 | Erforderliches Richtlinienargument hinzugefügt | Überprüfen Sie, ob die -Anweisung in der Anpassungs-Code-Basis verwendet wird. Fügen Sie das Argument der Anweisung hinzu. |

{style="table-layout:auto"}

## Fehler

### Benutzerdefinierter Code

Fehler mit benutzerdefiniertem Code werden ausgelöst, wenn benutzerdefinierter Code die Adobe Commerce-Einstiegspunkte verwendet, die nicht als `@api` betrachtet/markiert sind. Das beibehaltene Verhalten solcher Einsprungspunkte ist nicht garantiert. Die Anpassung sollte stattdessen auf `@api` Einstiegspunkten basieren. Die Funktion, die auf Nicht-API-Adobe Commerce-Code basiert, sollte nach dem Upgrade getestet werden. Diese Fehler werden auch gemeldet, wenn wichtige Codierungsstandards verletzt wurden.

| Fehlercode | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 1104 | Verwenden einer Nicht-API-Klasse, die die API-Schnittstelle erbt | Klassen, die nicht als `@api` gekennzeichnet sind, können geändert werden. Aktualisieren Sie den Code ggf. so, dass stattdessen die als `@api` markierte Schnittstelle verwendet wird. Andernfalls sollten die Funktionen, die sich auf diese Implementierung stützen, nach dem Upgrade getestet werden. |
| 1121 | Erweitern von einer Nicht-Adobe Commerce-API-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebasis vorhanden. Die Vererbung ist keine empfohlene Methode zur Erweiterung der Adobe Commerce-Funktionalität. Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. |
| 1122 | Importieren einer Nicht-Adobe Commerce-API-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebasis vorhanden. Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. Andernfalls sollten die Funktionen, die sich auf diese Implementierung stützen, nach dem Upgrade getestet werden. |
| 1123 | Nicht-Adobe Commerce-API-Klasse wird geladen | Die erweiterte Klasse ist nicht mehr in der Codebasis vorhanden. Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. Andernfalls sollten die Funktionen, die sich auf diese Implementierung stützen, nach dem Upgrade getestet werden. |
| 1124 | Verwenden einer Nicht-Adobe Commerce-API-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebasis vorhanden. Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. Andernfalls sollten die Funktionen, die sich auf diese Implementierung stützen, nach dem Upgrade getestet werden. |
| 1224 | Verwenden von Nicht-Adobe Commerce-API-Konstanten | Konstanten, die nicht als `@api` gekennzeichnet sind, können geändert werden. Stattdessen sollte eine private Konstante des erforderlichen Werts im benutzerdefinierten Code eingeführt und verwendet werden. |
| 1225 | Überschreiben von Nicht-Adobe Commerce-API-Konstanten | Konstanten, die nicht als `@api` gekennzeichnet sind, können geändert werden. Stattdessen sollte eine private Konstante des erforderlichen Werts im benutzerdefinierten Code eingeführt und verwendet werden. |
| 1226 | Zuweisung einer Nicht-Adobe Commerce-API-Konstante | Konstanten, die nicht als `@api` gekennzeichnet sind, können geändert werden. Stattdessen sollte eine private Konstante des erforderlichen Werts im benutzerdefinierten Code eingeführt und verwendet werden. |
| 1322 | Importierte Nicht-Adobe Commerce-API-Schnittstelle | Schnittstellen, die nicht als `@api` gekennzeichnet sind, können geändert werden. Erwägen Sie, diese Vererbung zu entfernen oder durch eine Vererbung von der als `@api` markierten Adobe Commerce-Schnittstelle oder einer im Umfang des Anpassungscodes eingeführten Schnittstelle zu ersetzen. |
| 1324 | Verwendete Nicht-Adobe Commerce-API-Schnittstelle | Schnittstellen, die nicht als `@api` gekennzeichnet sind, können geändert werden. Erwägen Sie, diese Vererbung zu entfernen oder durch eine Vererbung von der als `@api` markierten Adobe Commerce-Schnittstelle oder einer im Umfang des Anpassungscodes eingeführten Schnittstelle zu ersetzen. |
| 1327 | Vererbte Nicht-Adobe Commerce-API-Schnittstelle | Konstanten, die nicht als `@api` gekennzeichnet sind, können geändert werden. Stattdessen sollte eine private Konstante des erforderlichen Werts im benutzerdefinierten Code eingeführt und verwendet werden. |
| 1328 | Implementierte Nicht-Adobe Commerce-API-Schnittstelle | Schnittstellen, die nicht als `@api` gekennzeichnet sind, können geändert werden. Erwägen Sie, diese Vererbung zu entfernen oder durch eine Vererbung von der als `@api` markierten Adobe Commerce-Schnittstelle oder einer im Umfang des Anpassungscodes eingeführten Schnittstelle zu ersetzen. |
| 1420 | Instanziieren einer Nicht-Adobe Commerce-API-Klasse/-Schnittstelle | Klassen, die nicht als `@api` gekennzeichnet sind, können geändert werden. Aktualisieren Sie den Code ggf. so, dass stattdessen die als `@api` markierte Schnittstelle verwendet wird. Andernfalls sollten die Funktionen, die sich auf diese Implementierung stützen, nach dem Upgrade getestet werden. Die empfohlene Methode zum Abrufen einer Instanz der -Klasse ist auch die Verwendung von ID. Erwägen Sie die Verwendung einer Factory, wenn eine neue Instanz der Klasse erforderlich ist. |
| 1428 | Mögliche Abhängigkeit von Implementierungsdetails. | Klassen, die nicht als `@api` gekennzeichnet sind, können geändert werden. Aktualisieren Sie den Code ggf. so, dass stattdessen die als `@api` markierte Schnittstelle verwendet wird. Andernfalls sollten die Funktionen, die sich auf diese Implementierung stützen, nach dem Upgrade getestet werden. |
| 1429 | Aufrufen von Nicht-Adobe Commerce-API-Methoden | Methoden, die nicht als `@api` gekennzeichnet oder nicht in der API-Klasse/-Schnittstelle deklariert sind, können geändert werden. Selbst wenn die Schnittstelle der Methode in der neuen Version nicht aktualisiert wird, kann ihr Verhalten oder ihre Ausgabe unterschiedlich sein. Erwägen Sie, sich auf eine Schnittstellenmethode zu verlassen. Andernfalls sollten die Funktionen, die sich auf diese Implementierung stützen, nach dem Upgrade getestet werden. |
| 1449 | Aufruf der Nicht-Schnittstellenmethode (die in der Implementierung vorhanden ist) | Methoden, die nicht in der Schnittstelle deklariert sind, können geändert werden. Erwägen Sie, sich auf eine Schnittstellenmethode zu verlassen. Andernfalls sollten die Funktionen, die sich auf diese Implementierung stützen, nach dem Upgrade getestet werden. |
| 1524 | Verwenden einer Nicht-Adobe Commerce-API-Eigenschaft | Werte der Eigenschaften, die nicht als `@api` gekennzeichnet sind, können geändert werden. Stattdessen sollte die API-Schnittstellenmethode verwendet werden. |
| 1525 | Überschreiben der Nicht-Adobe Commerce-API-Eigenschaft | Werte der Eigenschaften, die nicht als `@api` gekennzeichnet sind, können geändert werden. Stattdessen sollte die API-Schnittstellenmethode verwendet werden. |
| 1526 | Zuweisung einer Nicht-Adobe Commerce-API-Eigenschaft | Werte der Eigenschaften, die nicht als `@api` gekennzeichnet sind, können geändert werden. Stattdessen sollte die API-Schnittstellenmethode verwendet werden. |
| 5004 | Funktion ohne Argument wird nicht mehr unterstützt | Übergeben Sie die zu validierende Eingabe als erstes Argument der Funktion. |
| 5007 | Von der Verwendung bestimmter Funktionen wird abgeraten | Diese Funktionen sollten nicht verwendet werden. |
| 5009 | Vorlagenrichtlinien dürfen keine Methoden aufrufen. Nur Zugriff auf skalare Arrays ist zulässig | Entfernen Sie Methodenaufrufe aus der Vorlage. |
| 5010 | Vorlagen- `@vars` Kommentarblock enthält ungültige JSON-Dateien | Korrigieren Sie ungültige JSON. |
| 5011 | Vorlage `@vars` Kommentarblock enthält ungültige Beschriftung | Ungültige Kennzeichnung korrigieren. |
| 5012 | Im Vorlagenkommentarblock `@vars` fehlt eine in der Vorlage verwendete Variable | Fügen Sie @vars Kommentarblock die fehlende Variable hinzu. |
| 5013 | Verwenden Sie kein selbstschließendes Tag mit einem HTML-Element ohne Leerzeichen | Verwenden Sie stattdessen Tag schließen . |
| 5014 | Das `"active"` ist veraltet | Die Liste der aktiven Module wird in der Bereitstellungskonfiguration definiert. |
| 5015 | Der `<param>` ist veraltet | Verwenden Sie stattdessen `<argument name="..." xsi:type="...">` . |
| 5016 | Der `<instance>` ist veraltet | Verwenden Sie stattdessen `<argument name="..." xsi:type="object">` . |
| 5017 | Der `<array>` ist veraltet | Verwenden Sie stattdessen `<argument name="..." xsi:type="array">` . |
| 5018 | Der `<item key="...">` ist veraltet | Verwenden Sie stattdessen `<item name="..." xsi:type="...">` . |
| 5019 | Der `<value>` ist veraltet | Geben Sie stattdessen den tatsächlichen Wert als Textliteral an. |
| 5020 | Veralteter Knoten: `<supported_blocks>` | Durch `<supported_containers>` zu ersetzen. |
| 5021 | Veralteter Knoten: `<block_name>` | Durch `<container_name>` zu ersetzen. |
| 5022 | Factory-Name erkannt | Der Widget-Typ sollte nicht mit / beginnen. |
| 5023 | In der Zeile wurde eine veraltete ACL-Struktur erkannt. | Überprüfen Sie lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | In Zeile wurde eine veraltete Menüstruktur erkannt | Überprüfen Sie app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | In der Datei wurde eine veraltete Systemkonfigurationsstruktur erkannt. | Überprüfen Sie app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | `"text/javascript"` Typ-Attribut nicht verwenden | Nur öffentliche Member verwenden. |
| 5028 | Der Zugriff auf geschützte und private Member `Block` Klasse ist in HTML-Vorlagen veraltet | Nur öffentliche Member verwenden. |
| 5031 | Enthält veraltete Methode | Verwenden Sie stattdessen `getConnection()` Methode . |
| 5042 | Falsches Format der PHP-Klassenreferenz | Vergewissern Sie sich, dass auf die Klasse nur mit Binnenbuchstaben, Zahlen und keinem Schrägstrich verwiesen wird. |
| 5043 | Falsches Format der Modulreferenz | Überprüfen Sie, ob das Modul nur mit Buchstaben, Zahlen, Unterstrichen und ohne vorangestellten Schrägstrich referenziert wird. |
| 5044 | Klasse `Zend_Db_Select` ist eingeschränkt | Vorgeschlagene Ersetzung: `\Magento\Framework\DB\Select`. |
| 5045 | Klasse `Zend_Db_Adapter_Pdo_Mysql` ist eingeschränkt | Vorgeschlagene Ersetzung: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Klasse `Magento\Framework\Serialize\Serializer\Serialize` ist eingeschränkt | Vorgeschlagene Ersetzung: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Klasse `ArrayObject` ist eingeschränkt | Empfohlene Ersetzung: Benutzerdefinierte Klasse, erweitert von `ArrayObject` mit überschriebenen serialize/unserialize-Methoden. |
| 5048 | Klasse `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` ist eingeschränkt | Empfohlene Ersetzung: Factory, die eine benutzerdefinierte Klasse erstellt, die durch `ArrayObject` mit überschriebenen serialize/serialize-Methoden erweitert wurde. |
| 5050 | Der referenzierte Block wird entfernt | Verweis auf Block entfernen. |
| 5051 | `output="toHtml"` ist veraltet | `output="1"` verwenden. |
| 5052 | Die Klasse `\Magento\Framework\View\Element\Text\ListText` sollte nicht mehr im Layout verwendet werden | Entfernen Sie die Klasse `\Magento\Framework\View\Element\Text\ListText` aus dem Layout. |
| 5053 | Aufruf der Methode über Layout-Anweisung `<action>` ist nicht zulässig | Vermeiden Sie die Verwendung einer fehlerhaften Methode in `<action>`. |
| 5054 | `helper` Attribut enthält `/` | Entfernen Sie `/` aus dem Hilfsattribut. |
| 5055 | `helper` Attribut enthält keine `::` | Fügen Sie `::` zum Helper-Attribut hinzu. |
| 5056 | Installationsskripte sind veraltet | Verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml von module\. |
| 5057 | InstallSchema-Skripte sind veraltet | Verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml von module\. |
| 5058 | InstallData-Skripte sind veraltet | Verwenden Sie den Ansatz „Daten-Patches“ im Verzeichnis Setup/Patch/Data des Moduls. |
| 5059 | Installationsskripte sind veraltet | Erstellen Sie eine Klasse InstallData im Setup-Ordner des Moduls. |
| 5060 | Upgrade-Skripte sind veraltet | Verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml von module\. |
| 5061 | UpgradeSchema-Skripte sind veraltet | Verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml von module\. |
| 5062 | UpgradeData-Skripte sind veraltet | Verwenden Sie den Ansatz „Daten-Patches“ im Verzeichnis Setup/Patch/Data des Moduls. |
| 5063 | Upgrade-Skripte sind veraltet | Verwenden Sie den Ansatz „Daten-Patches“ im Verzeichnis Setup/Patch/Data des Moduls. |
| 5064 | Wiederkehrende Skripte sind veraltet | Erstellen Sie eine wiederkehrende Klasse im Setup-Ordner des Moduls. |
| 5065 | &#39;Daten&#39; befindet sich in einem ungültigen Verzeichnis | Erstellen Sie einen Daten-Patch im Ordner Setup/Patch/Data des Moduls für Daten-Upgrades oder verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml des Moduls für Schemaänderungen. |
| 5066 | &#39;SQL&#39; befindet sich in einem ungültigen Verzeichnis | Erstellen Sie einen Daten-Patch im Ordner Setup/Patch/Data des Moduls für Daten-Upgrades oder verwenden Sie den deklarativen Schemaansatz in der Datei etc/db_schema.xml des Moduls für Schemaänderungen. |
| 5067 | Durch XPath identifizierte Knoten sind veraltet | Veraltete XML, auf die in dem Fehler hingewiesen wurde, sollte aktualisiert werden. Befolgen Sie die Vorschläge aus der Fehlermeldung. |
| 5068 | Die Richtlinie `{{htmlescape}}` ist überholt | Verwenden Sie stattdessen `{{var}}` . |
| 5069 | Die Richtlinie `{{escapehtml}}` ist überholt | Verwenden Sie stattdessen `{{var}}` . |
| 5070 | &#x200B;3. Parameter wird für `getChildHtml()` nicht mehr benötigt | Entfernen Sie den dritten Parameter aus dem Aufruf an `getChildHtml()`. |
| 5071 | &#x200B;4. Parameter wird für `getChildHtml()` nicht mehr benötigt | Entfernen Sie den 4. Parameter aus dem Aufruf an `getChildHtml()`. |
| 5073 | Alte Tabellennamen mit Schrägstrich müssen auf direkte Tabellennamen korrigiert werden | Verwenden Sie stattdessen den direkten Tabellennamen. |
| 5075 | Anwendungsmodule sollten keine Klassen aus Testmodulen verwenden | Entfernen Sie die Verwendung von Klassen aus Testmodulen. |
| 5078 | Die Klasse muss im Konstruktor angefordert werden, andernfalls kann der Compiler diese Klassen nicht finden und generieren | Fügen Sie dem Konstruktor eine Klasse hinzu. |
| 5079 | Von der Verwendung von Variablen der Var-Klasse wird abgeraten | Vermeiden Sie die Verwendung von „var“ zur Deklaration von Klassenvariablen. |
| 5080 | Mögliche SQL-Rohanweisung erkannt | Verwenden Sie stattdessen Repositorys oder Daten-Patches . |
| 5081 | Von der Verwendung von Helfern in Vorlagen wird abgeraten | Verwenden Sie stattdessen ViewModel . |
| 5082 | Die Verwendung von $this in Vorlagen wird nicht mehr unterstützt | Stattdessen $block verwenden. |
| 5083 | Konstanten sind nicht als erstes Argument der Übersetzungsfunktion zulässig | Verwenden Sie stattdessen das Zeichenfolgenliteral. |
| 5085 | Von der Verwendung bestimmter Funktionen wird abgeraten | Verwenden Sie stattdessen die in der Nachricht empfohlene alternative Funktion. |
| 5087 | Problem mit der Versionsübergreifenden PHP-Kompatibilität | Befolgen Sie die Vorschläge aus der Nachricht und überprüfen Sie das [Migrationshandbuch](https://www.php.net/manual/en/migration81.php). |
| 5088 | Optionale Parameter nach den erforderlichen | Erforderliche Parameter nach optionalen Parametern verschieben. |
| 5089 | Sichtbarkeit der Methode `final private` gefunden | Ändern Sie die Sichtbarkeit der Methode von `final private` in nur `private`. |
| 5090 | Die magische Methode `__set_state` ist nicht als `static` definiert | Die magische Methode `__set_state` muss als `static` definiert werden. |
| 5091 | Klasse mit `__toString()` Methode erbt nicht von `Stringable` Schnittstelle | Fügen Sie mit `Stringable` Methode `__toString()` Schnittstelle zur Klasse hinzu. |
| 5092 | `is_resource()` Methode, die für Funktionen verwendet wird, die jetzt Object zurückgeben | Ändern Sie `is_resource()` in `instanceof` -Objekt. |
| 6001 | `jQuery.andSelf()` entfernt | `jQuery.addBack()` verwenden. |
| 6002 | jQuery `$.bind` und `$.unbind` sind veraltet | Verwenden Sie stattdessen `$.on` und `$.off`. |
| 6003 | Die jQuery-Methode zum Abonnieren des Ereignisses ist veraltet und sollte nicht verwendet werden | Verwenden Sie stattdessen `.on("event name", fn)` -Methode, um dieses Ereignis zu abonnieren. |
| 6003 | jQuery-Methode für Trigger-Ereignis ist veraltet und sollte nicht verwendet werden | Verwenden Sie stattdessen `.trigger("event name")` -Methode, um dieses Ereignis in einen Trigger aufzunehmen. |
| 6004 | jQuery `$.delegate` und `$.undelegate` sind veraltet | Verwenden Sie stattdessen `$.on` und `$.off`. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) wurde entfernt | Verwenden Sie stattdessen (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` entfernt | `jQuery.length` verwenden. |
| 6007 | `jQuery.trim` ist veraltet | `String.prototype.trim` verwenden. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, Design „inlite“, Design „mobile“, Design „modern„) wird entfernt | Code aktualisieren, um mit tinymce5 kompatibel zu sein. |
| 6009 | `jQuery.isFunction()` ist veraltet | In den meisten Fällen kann sie durch &quot;[ x === „Funktion“ ersetzt ]. |
| 6009 | `jQuery.type()` ist veraltet | Ersetzen Sie durch eine entsprechende Typprüfung wie [type of x === „function“]. |
| 6009 | `jQuery.isArray()` ist veraltet | Verwenden Sie stattdessen die native Array.isArray-Methode. |
| 6009 | `jQuery.parseJSON()` ist veraltet | Verwenden Sie zum Analysieren von JSON-Zeichenfolgen stattdessen die native Methode JSON.parse . |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) ist veraltet | Verwenden Sie stattdessen jQuery.expr.pseudo. |

{style="table-layout:auto"}

### DB-Schema

DB-Schemafehler werden ausgelöst, wenn die Datenbanktabellen, -spalten, -indizes oder -einschränkungen, die in der Zielversion von Adobe Commerce hinzugefügt oder entfernt wurden, zu Konflikten mit dem benutzerdefinierten Datenbankschema führen können.

| Fehlercode | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 7001 | Die Ziel-Kernversion führt eine Tabelle mit demselben Namen ein wie eine Tabelle, die durch ein benutzerdefiniertes Modul deklariert wurde | Verwenden Sie die neue Kerntabelle (falls zutreffend) oder benennen Sie die benutzerdefinierte Tabelle um. |
| 7002 | Die Kerntabelle, die durch ein benutzerdefiniertes Modul erweitert wird, wurde in der Zielversion entfernt | Alle entfernten Haupttabellenverweise sollten aus der Codebasis entfernt werden |
| 7003 | Die Ziel-Kernversion führt eine Spalte mit demselben Namen ein wie eine Spalte, die von einem benutzerdefinierten Modul deklariert wurde | Verwenden Sie die neue Kernspalte (falls zutreffend) oder benennen Sie die benutzerdefinierte Spalte um. |
| 7004 | Die Kernspalte, die durch ein benutzerdefiniertes Modul erweitert wird, wurde in der Zielversion entfernt | Alle entfernten Kernspaltenverweise sollten aus der Code-Basis entfernt werden |
| 7005 | Die Ziel-Kernversion führt einen Index mit derselben referenceId ein wie ein von einem benutzerdefinierten Modul deklarierter Index | Entfernen Sie (falls doppelt vorhanden) oder benennen Sie den benutzerdefinierten Index um. |
| 7006 | Der durch ein benutzerdefiniertes Modul erweiterte Kernindex wurde in der Zielversion entfernt | Alle entfernten Kernindexverweise sollten aus der Codebasis entfernt werden |
| 7007 | Die Ziel-Kernversion führt eine Einschränkung ein, die denselben Namen wie eine von einem benutzerdefinierten Modul deklarierte Einschränkung hat | Entfernen Sie (falls doppelt vorhanden) oder benennen Sie die benutzerdefinierte Einschränkung um. |
| 7008 | Die durch ein benutzerdefiniertes Modul erweiterte Kernbeschränkung wurde in der Zielversion entfernt | Verwenden Sie die neue Kernbeschränkung (falls zutreffend) oder benennen Sie die benutzerdefinierte Beschränkung um |

{style="table-layout:auto"}

## Warnungen

### Kerncode

Diese Warnungen werden gemeldet, wenn kleinere Inkonsistenzen in der Code-Basis des Kerns vorliegen.

| Fehlercode | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 2004 | Composer-Abhängigkeitsversionen stimmen nicht überein | Das Problem zeigt an, dass die Composer-Abhängigkeitsversion in Metalon und das tatsächliche Projekt unterschiedlich sind. Aktualisieren Sie die Abhängigkeit, indem Sie `composer update <package_name>` ausführen. |

{style="table-layout:auto"}

### Benutzerdefinierter Code

Warnhinweise für benutzerspezifischen Code werden ausgelöst, wenn Verweise auf veralteten Code erkannt werden. Solche Verweise sollten durch die unterstützten Erweiterungspunkte ersetzt werden. Achten Sie bei Empfehlungen auf die `@see` Anmerkung veralteter Elemente. Diese Fehler werden auch gemeldet, wenn kleinere Codierungsstandards verletzt wurden.

| Fehlercode | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 1131 | Erweitern von der Adobe Commerce-``@deprecated`` | Die erweiterte Klasse wird in kommenden Versionen entfernt. Die Vererbung ist keine empfohlene Methode zur Erweiterung der Adobe Commerce-Funktionalität. Aktualisieren Sie den Code, um eine als `@api` markierte Klasse zu verwenden. |
| 1132 | Adobe Commerce `@deprecated`-Klasse importieren | Die erweiterte Klasse wird in kommenden Versionen entfernt. Sie sollten stattdessen die als `@api` markierte Adobe Commerce-Klasse verwenden. |
| 1133 | Adobe Commerce `@deprecated`-Klasse wird geladen | Die erweiterte Klasse wird in kommenden Versionen entfernt. Sie sollten stattdessen die als `@api` markierte Adobe Commerce-Klasse verwenden. |
| 1134 | Verwenden der Adobe Commerce-`@deprecated` | Die erweiterte Klasse wird in kommenden Versionen entfernt. Sie sollten stattdessen die als `@api` markierte Adobe Commerce-Klasse verwenden. |
| 1234 | Verwenden der Adobe Commerce`@deprecated`Konstante | Die veraltete Konstante wird in kommenden Versionen entfernt. Verwenden Sie stattdessen eine Konstante, die als `@api` markiert ist, oder eine private Konstante in Ihrer Implementierung. |
| 1235 | Überschreiben der Adobe Commerce`@deprecated`Konstante | Die veraltete Konstante wird in kommenden Versionen entfernt. Verwenden Sie stattdessen eine Konstante, die als `@api` markiert ist, oder eine private Konstante in Ihrer Implementierung. |
| 1236 | Zuweisung von Adobe Commerce `@deprecated` Konstante | Die veraltete Konstante wird in kommenden Versionen entfernt. Verwenden Sie stattdessen eine Konstante, die als `@api` markiert ist, oder eine private Konstante in Ihrer Implementierung. |
| 1332 | Importierte Adobe Commerce-`@deprecated` | Die veraltete Benutzeroberfläche wird in kommenden Versionen entfernt. Verwenden Sie stattdessen eine Schnittstelle oder Klasse, die als `@api` gekennzeichnet ist. |
| 1334 | Verwendete Adobe Commerce`@deprecated`Benutzeroberfläche | Die veraltete Benutzeroberfläche wird in kommenden Versionen entfernt. Verwenden Sie stattdessen eine Schnittstelle oder Klasse, die als `@api` gekennzeichnet ist. |
| 1337 | Von der Adobe Commerce-`@deprecated` geerbt | Die veraltete Benutzeroberfläche wird in kommenden Versionen entfernt. Erwägen Sie, die Schnittstellenvererbung zu entfernen, indem Sie stattdessen eine als `@api` markierte Schnittstelle oder eine innerhalb Ihrer Implementierung eingeführte Schnittstelle verwenden. |
| 1338 | Implementierte Adobe Commerce-`@deprecated` | Die veraltete Benutzeroberfläche wird in kommenden Versionen entfernt. Erwägen Sie, die Schnittstellenvererbung zu entfernen, indem Sie stattdessen eine als `@api` markierte Schnittstelle oder eine innerhalb Ihrer Implementierung eingeführte Schnittstelle verwenden. |
| 1430 | Aufruf der Methode des nicht deklarierten Datenobjekts | Die magischen Methoden, die nicht deklariert werden, können geändert werden. Stattdessen sollten Sie sich auf Schnittstellenmethoden verlassen. |
| 1439 | Adobe Commerce-`@deprecated` aufrufen | Die veraltete Methode wird in kommenden Versionen entfernt. Stattdessen sollten Sie sich auf Methoden verlassen, die in API-Schnittstellen deklariert wurden. |
| 1440 | Fehlende Übereinstimmung bei Methodensignatur | Ein Aufruf oder eine Überschreibung der Kernmethode wird mit Parametern, Argumenten oder Rückgabetypen erkannt, die nicht mit der Methodensignatur übereinstimmen. |
| 1534 | Verwenden der Adobe Commerce `@deprecated`-Eigenschaft | Die veraltete Methode wird in kommenden Versionen entfernt. Stattdessen sollten Sie sich auf Methoden verlassen, die in API-Schnittstellen deklariert wurden. |
| 1535 | Überschreiben der Adobe Commerce `@deprecated`-Eigenschaft | Die veraltete Eigenschaft wird in kommenden Versionen entfernt. Erwägen Sie stattdessen, sich auf Methoden zu verlassen, die in API-Schnittstellen deklariert sind, oder stattdessen eine private Eigenschaft in Ihrer Implementierung zu verwenden. |
| 1536 | Zuweisung der `@deprecated` Adobe Commerce | Die veraltete Methode wird in kommenden Versionen entfernt. Stattdessen sollten Sie sich auf Methoden verlassen, die in API-Schnittstellen deklariert wurden. |
| 5006 | Proxys und Interceptoren DÜRFEN in Konstruktoren niemals explizit angefordert werden | Die ursprüngliche Klasse sollte als Typ des Konstruktorparameters deklariert werden. Die Interceptor/Proxy-Klasse wird von der Framework-Abhängigkeitsinjektionsimplementierung übergeben. |
| 5074 | Verwendung der veralteten Methode `getResource()` zum Speichern/Laden/Löschen von Daten erkannt. | Verwenden Sie stattdessen ein Repository. |
| 5086 | Sichtbarkeit wird nicht auf einer Konstanten deklariert | Sichtbarkeit für alle Konstanten deklarieren. |

{style="table-layout:auto"}

### GraphQL-Schema

GraphQL-Schemawarnungen werden ausgelöst, wenn die zusätzlichen Elemente in der neuen Version zum Schema hinzugefügt werden. Es wird empfohlen, die Implementierung zu überprüfen, um festzustellen, ob sie für Anfragen verwendet werden sollten.

| Fehlercode | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 3206 | Standardwert des Arguments geändert | Wenn die Abfrage bei der Anpassung verwendet wird, muss der Argumentwert möglicherweise explizit angegeben werden. |
| 3302 | Typ zur Vereinigung hinzugefügt | Der Typ wurde der Vereinigung hinzugefügt. Überprüfen Sie, ob die Implementierung das Ergebnis der Abfrage verarbeitet, die diesen Vereinigungstyp zurückgibt, und stellen Sie sicher, dass sie den hinzugefügten Typ verarbeiten kann. |
| 3304 | Optionales Eingabefeld hinzugefügt | Optionales Eingabefeld hinzugefügt. Überprüfen Sie die Implementierung, um sicherzustellen. |
| 3305 | Implementierte Schnittstelle hinzugefügt | Das Feld kann weitere Informationen akzeptieren/bereitstellen, die bei der Implementierung berücksichtigt werden können. |
| 3306 | Zu Aufzählung hinzugefügter Wert | Einer Aufzählung wurde ein Wert hinzugefügt. Wenn Clients eine switch-Anweisung für den -Wert der Aufzählung enthalten und keinen Standardfall enthalten, kann diese Änderung zu unerwartetem Verhalten führen. |
| 3308 | Optionales Argument hinzugefügt | Wenn die Abfrage in der Anpassung ein neues Argument verwendet, muss sie möglicherweise zur Anfrage hinzugefügt werden. |

{style="table-layout:auto"}
