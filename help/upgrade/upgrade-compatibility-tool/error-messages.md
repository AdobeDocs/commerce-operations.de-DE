---
title: '"[!DNL Upgrade Compatibility Tool] Fehlermeldungen"'
description: Erfahren Sie mehr über Fehlermeldungen, die bei der Verwendung der [!DNL Upgrade Compatibility Tool] in Ihrem Adobe Commerce-Projekt.
source-git-commit: d62299d23d73b8566ed1c9b9739ca59fb0535d6f
workflow-type: tm+mt
source-wordcount: '3756'
ht-degree: 4%

---


# [!DNL Upgrade Compatibility Tool] Fehlermeldungen

{{commerce-only}

Diese Fehlernachrichten-Referenz enthält Informationen zu Fehlern, die beim Ausführen der [!DNL Upgrade Compatibility Tool].

Fehlermeldungen werden nach Ebene (kritische Probleme, Fehler und Warnungen) und Typ (Kerncode, benutzerspezifischer Code und GraphQL-Schemas) kategorisiert. Jeder Typ enthält die folgenden Informationen:

- **Fehler-Code**: Die Adobe Commerce hat die Kennung für die Fehlermeldung zugewiesen.
- **Fehlerbeschreibung**: Eine Beschreibung, die die Fehlerursache zusammenfasst.
- **Fehlerempfehlung für Aktion**: Enthält ggf. Anleitungen zur Fehlerbehebung und Fehlerbehebung.

## Kritische Fragen

### Core Code

Diese Fehler werden gemeldet, wenn einige der Kerndateien fehlen oder nicht mit dem Original übereinstimmen.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 2001 | Die Kerndatei wurde nicht gefunden | Führen Sie die `composer install` aus dem Stammverzeichnis des Projekts. |
| 2002 | Core-Datei wurde geändert | Führen Sie die `composer install` aus dem Stammverzeichnis des Projekts. |
| 2003 | Komponentenabhängigkeit ist nicht installiert | Fehlende Komponentenabhängigkeiten können zu Problemen führen. Wiederherstellen der Abhängigkeit durch Ausführen `composer require package_name`. |
| 2005 | Core-Ordner wurde nicht gefunden | Führen Sie die `composer install` aus dem Stammverzeichnis des Projekts. |

{style=&quot;table-layout:auto&quot;}

### Benutzerspezifischer Code

Kritische Fehler werden ausgelöst, wenn der benutzerspezifische Code auf Entitäten verweist, die nicht in der Adobe Commerce-Zielversion vorhanden sind. Diese Fehler werden auch gemeldet, wenn kritische Kodierungsstandards verletzt wurden.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 1110 | Instanziieren nicht vorhandener Adobe Commerce-Klasse/Benutzeroberfläche | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. Instanziieren nicht vorhandener Adobe Commerce-Klasse/-Schnittstelle. |
| 1111 | Erweitern von nicht vorhandener Adobe Commerce-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Die Vererbung ist keine empfohlene Methode zur Erweiterung der Adobe Commerce-Funktionalität. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. |
| 1112 | Importieren nicht vorhandener Adobe Commerce-Klasse | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. |
| 1113 | Nicht vorhandene Adobe Commerce-Klasse laden | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. |
| 1114 | Verwenden nicht vorhandener Adobe Commerce-Klasse | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. |
| 1214 | Verwenden nicht vorhandener Adobe Commerce-Konstante | Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1215 | Nicht vorhandene Adobe Commerce-Konstante überschreiben | Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1216 | Zuweisung nicht vorhandener Adobe Commerce-Konstante | Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1312 | Importierte nicht vorhandene Adobe Commerce-Benutzeroberfläche | Erwägen Sie, die Vererbung zu entfernen oder sie durch die im Bereich der Anpassung eingeführte Benutzeroberfläche zu ersetzen. |
| 1314 | Nicht vorhandene Adobe Commerce-Benutzeroberfläche verwendet | Erwägen Sie, die Vererbung zu entfernen oder sie durch die im Bereich der Anpassung eingeführte Benutzeroberfläche zu ersetzen. |
| 1317 | Übernommene nicht vorhandene Adobe Commerce-Benutzeroberfläche | Erwägen Sie, die Vererbung zu entfernen oder sie durch die im Bereich der Anpassung eingeführte Benutzeroberfläche zu ersetzen. |
| 1318 | Nicht vorhandene Adobe Commerce-Oberfläche wurde implementiert | Erwägen Sie, die Vererbung zu entfernen oder sie durch die im Bereich der Anpassung eingeführte Benutzeroberfläche zu ersetzen. |
| 1410 | Nicht vorhandene Adobe Commerce-Methode aufrufen | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. |
| 1514 | Verwenden nicht vorhandener Adobe Commerce-Eigenschaft | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. |
| 1515 | Nicht vorhandene Adobe Commerce-Eigenschaft überschreiben | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. |
| 1516 | Zuweisung nicht vorhandener Adobe Commerce-Eigenschaften | Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. Aktualisieren Sie die Eigenschaftenzugriffsebene auf &quot;privat&quot;, wenn sie nur innerhalb einer einzelnen Klasse verwendet werden kann. |
| 5002 | Das öffnende PHP-Tag muss der erste Inhalt in der Datei sein. | Stellen Sie sicher, dass die Datei vor dem öffnenden PHP-Tag keinen Inhalt enthält. |
| 5003 | Funktion ist veraltet | Verwenden Sie einen Ersatz, der in der Fehlermeldung vorgeschlagen wird. Wenn die Nachricht keinen Ersatz vorschlägt, muss eine gründliche Überprüfung durchgeführt werden, um eine alternative Funktion oder Implementierung auszuwählen. |
| 5005 | PHP-Syntaxfehler | Der Code muss entsprechend den PHP-Syntaxstandards aktualisiert werden. |
| 5072 | Mögliche Verletzung des Designs in Magento 2. Typische Konstruktion von Magento 1.x erkannt | Aktualisierung der Konstruktion auf Magento 2-Standards. |
| 5076 | Kann nicht im Namespace verwendet werden, da er seit PHP 7 reserviert ist | Ersetzen Sie das reservierte Wort im Namespace durch ein nicht reserviertes Schlüsselwort. |
| 5077 | Kann nicht als Klassenname verwendet werden, da er seit PHP 7 reserviert ist | Ersetzen Sie den reservierten Klassennamen durch einen nicht reservierten Namen. |

{style=&quot;table-layout:auto&quot;}

### GraphQL-Schema

GraphQL-Schema-kritische Probleme werden ausgelöst, wenn die Schemaelemente nicht in der Zielversion vorhanden sind.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 3101 | Typ wurde entfernt | Listen Sie alle Abfragen auf, die auf dieses Feld verweisen. Überprüfen Sie, ob diese Abfragen von der Implementierung der Anpassung verwendet werden. Aktualisieren Sie den Clientcode, um die geänderte Abfrageschnittstelle zu verarbeiten. |
| 3102 | Aus Vereinigung entfernter Typ | Wenn der Vereinigungstyp in der Implementierung des GraphQL-Anforderungskonstrukts oder der Antwortverarbeitung verwendet wird, muss er möglicherweise aktualisiert werden. |
| 3103 | Feld entfernt | Überprüfen Sie, ob in der Codebasis für die Anpassung auf das Feld verwiesen wird. Passen Sie die Implementierung an, um den neuen Feldtyp korrekt zu handhaben. |
| 3105 | Implementierte Oberfläche entfernt | Überprüfen Sie, ob der Typ, der die entfernte Oberfläche implementiert, bei der Anpassung verwendet wird. Die Implementierung muss möglicherweise aktualisiert werden, wenn sie auf die entfernte Oberfläche angewiesen ist. |
| 3106 | Wert aus Enum entfernt | Wenn der entfernte Enum-Wert in der GraphQL-Anforderungskonstruktions- oder Antwortverarbeitungs-Implementierung verwendet wird, muss er möglicherweise aktualisiert werden. |
| 3107 | Argument entfernt | Überprüfen Sie, ob das Feld in der angepassten Codebasis verwendet wird. Entfernen Sie das -Argument für dieses Feld. |
| 3109 | Richtlinie aufgehoben | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Passen Sie die Implementierung an, um den Verweis auf die Richtlinie zu entfernen. |
| 3110 | Richtlinienargument entfernt | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Entfernen Sie das Argument der Anweisung. |
| 3111 | Richtlinie wiederholbar entfernt | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Passen Sie die Implementierung an, um die Änderungen an der Benutzeroberfläche zu handhaben. |
| 3112 | Richtlinienstandort entfernt | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Passen Sie die Implementierung an, um die Änderungen an der Benutzeroberfläche zu handhaben. |
| 3201 | Typ geändert | Listen Sie alle Abfragen auf, die auf dieses Feld verweisen. Überprüfen Sie, ob diese Abfragen von der Implementierung der Anpassung verwendet werden. Aktualisieren Sie den Clientcode, um die geänderte Abfrageschnittstelle zu verarbeiten. |
| 3203 | Feld geändert | Überprüfen Sie, ob in der Codebasis für die Anpassung auf das Feld verwiesen wird. Passen Sie die Implementierung an, um den neuen Feldtyp korrekt zu handhaben. |
| 3207 | Argument geändert | Überprüfen Sie, ob das Feld in der angepassten Codebasis verwendet wird. Aktualisieren Sie den Argumenttyp für dieses Feld. |
| 3303 | Erforderliches Eingabefeld hinzugefügt | Das Feld sollte der Anfrage hinzugefügt werden, wenn die Abfrage einschließlich dieses Felds für die Anpassung verwendet wird. |
| 3307 | Erforderliches Argument hinzugefügt | Überprüfen Sie, ob das Feld in der angepassten Codebasis verwendet wird. Das neue erforderliche Argument sollte bei Verwendung des Felds angegeben werden. |
| 3310 | Erforderliches Richtlinienargument hinzugefügt | Überprüfen Sie, ob die Anweisung in der Codebasis für die Anpassung verwendet wird. Fügen Sie das Argument der Anweisung hinzu. |

{style=&quot;table-layout:auto&quot;}

## Fehler

### Benutzerspezifischer Code

Benutzerdefinierte Code-Fehler werden ausgelöst, wenn benutzerdefinierter Code die Adobe Commerce-Einstiegspunkte verwendet, die nicht als `@api`. Das Verhalten solcher Einstiegspunkte ist nicht garantiert. Die Anpassung sollte sich auf `@api` Einstiegspunkte. Die Funktionalität, die auf Nicht-API-Adobe Commerce-Code basiert, sollte nach der Aktualisierung getestet werden. Diese Fehler werden auch gemeldet, wenn wichtige Kodierungsstandards verletzt wurden.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 1104 | Verwenden der Nicht-API-Klasse, die die API-Oberfläche erbt | Klassen, die nicht als `@api` geändert werden. Erwägen Sie, den Code zu aktualisieren, um sich auf die als `@api` anstatt. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1121 | Erweitern von Nicht-Adobe Commerce-API-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Die Vererbung ist keine empfohlene Methode zur Erweiterung der Adobe Commerce-Funktionalität. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. |
| 1122 | Importieren der Nicht-Adobe Commerce-API-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1123 | Nicht-Adobe Commerce-API-Klasse laden | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1124 | Verwenden der Nicht-Adobe Commerce-API-Klasse | Die erweiterte Klasse ist nicht mehr in der Codebase vorhanden. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1224 | Nicht-Adobe Commerce-API-Konstante verwenden | Konstanten, die nicht als `@api` geändert werden. Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1225 | Nicht-Adobe Commerce-API-Konstante überschreiben | Konstanten, die nicht als `@api` geändert werden. Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1226 | Zuweisung einer Nicht-Adobe Commerce-API-Konstante | Konstanten, die nicht als `@api` geändert werden. Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1322 | Importierte Nicht-Adobe Commerce-API-Benutzeroberfläche | Schnittstellen, die nicht als `@api` geändert werden. Erwägen Sie, diese Vererbung zu entfernen oder sie durch Vererbung aus der Adobe Commerce-Oberfläche zu ersetzen, die als `@api` oder eine Schnittstelle, die im Bereich des Anpassungscodes eingeführt wurde. |
| 1324 | Nicht-Adobe Commerce-API-Benutzeroberfläche verwendet | Schnittstellen, die nicht als `@api` geändert werden. Erwägen Sie, diese Vererbung zu entfernen oder sie durch Vererbung aus der Adobe Commerce-Oberfläche zu ersetzen, die als `@api` oder eine Schnittstelle, die im Bereich des Anpassungscodes eingeführt wurde. |
| 1327 | Übernommene Nicht-Adobe Commerce-API-Benutzeroberfläche | Konstanten, die nicht als `@api` geändert werden. Erwägen Sie stattdessen die Einführung und Verwendung einer privaten Konstante des erforderlichen Werts im benutzerspezifischen Code. |
| 1328 | Implementierte Nicht-Adobe Commerce-API-Benutzeroberfläche | Schnittstellen, die nicht als `@api` geändert werden. Erwägen Sie, diese Vererbung zu entfernen oder sie durch Vererbung aus der Adobe Commerce-Oberfläche zu ersetzen, die als `@api` oder eine Schnittstelle, die im Bereich des Anpassungscodes eingeführt wurde. |
| 1420 | Instanziieren der Nicht-Adobe Commerce-API-Klasse/-Oberfläche | Klassen, die nicht als `@api` geändert werden. Erwägen Sie, den Code zu aktualisieren, um sich auf die als `@api` anstatt. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. Die empfohlene Methode zum Abrufen einer Instanz der Klasse ist auch die Verwendung von ID. Erwägen Sie die Verwendung einer Factory , wenn eine neue Instanz der Klasse erforderlich ist. |
| 1428 | Mögliche Abhängigkeit von Implementierungsdetails. | Klassen, die nicht als `@api` geändert werden. Erwägen Sie, den Code zu aktualisieren, um sich auf die als `@api` anstatt. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1429 | Nicht-Adobe Commerce-API-Methoden aufrufen | Methoden, die nicht als `@api` oder nicht innerhalb der API-Klasse/-Schnittstelle deklariert werden, kann geändert werden. Selbst wenn die Schnittstelle der Methode in der neuen Version nicht aktualisiert wird, kann ihr Verhalten oder ihre Ausgabe unterschiedlich sein. Erwägen Sie, sich auf eine Schnittstellenmethode zu verlassen. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1449 | Aufruf der Nicht-Schnittstelle-Methode (in der Implementierung vorhanden) | Methoden, die nicht in der Benutzeroberfläche deklariert werden, können geändert werden. Erwägen Sie, sich auf eine Schnittstellenmethode zu verlassen. Andernfalls sollte die Funktionalität, die auf diese Implementierung angewiesen ist, nach der Aktualisierung getestet werden. |
| 1524 | Verwenden der Nicht-Adobe Commerce-API-Eigenschaft | Werte der Eigenschaften, die nicht als `@api` geändert werden. Erwägen Sie stattdessen die Verwendung der API-Schnittstellenmethode . |
| 1525 | Nicht-Adobe Commerce-API-Eigenschaft überschreiben | Werte der Eigenschaften, die nicht als `@api` geändert werden. Erwägen Sie stattdessen die Verwendung der API-Schnittstellenmethode . |
| 1526 | Zuweisung einer Nicht-Adobe Commerce-API-Eigenschaft | Werte der Eigenschaften, die nicht als `@api` geändert werden. Erwägen Sie stattdessen die Verwendung der API-Schnittstellenmethode . |
| 5004 | Funktion ohne -Argument ist veraltet | Übergeben Sie die Eingabe, um als erstes Argument der Funktion zu validieren. |
| 5007 | Von der Verwendung bestimmter Funktionen wird abgeraten | Vermeiden Sie die Verwendung dieser Funktionen. |
| 5009 | Vorlagenanweisungen dürfen keine Methoden aufrufen. Nur Zugriff auf skalare Arrays ist zulässig | Entfernen Sie Methodenaufrufe aus der Vorlage. |
| 5010 | Vorlage `@vars` Kommentarblock enthält ungültige JSON-Datei | Fehlerbehebung für ungültige JSON. |
| 5011 | Vorlage `@vars` Kommentarblock enthält ungültige Bezeichnung | Fehlerbehebung für ungültige Bezeichnung. |
| 5012 | Vorlage `@vars` Dem Kommentarblock fehlt eine in der Vorlage verwendete Variable. | Fügen Sie dem Kommentarblock @vars eine fehlende Variable hinzu. |
| 5013 | Vermeiden Sie die Verwendung eines sich selbst schließenden Tags mit einem nicht void HTML-Element | Verwenden Sie stattdessen das Tag close . |
| 5014 | Die `"active"` -Attribut ist veraltet | Die Liste der aktiven Module wird in der Bereitstellungskonfiguration definiert. |
| 5015 | Die `<param>` Knoten ist veraltet | Verwendung `<argument name="..." xsi:type="...">` anstatt. |
| 5016 | Die `<instance>` Knoten ist veraltet | Verwendung `<argument name="..." xsi:type="object">` anstatt. |
| 5017 | Die `<array>` Knoten ist veraltet | Verwendung `<argument name="..." xsi:type="array">` anstatt. |
| 5018 | Die `<item key="...">` Knoten ist veraltet | Verwendung `<item name="..." xsi:type="...">` anstatt. |
| 5019 | Die `<value>` Knoten ist veraltet | Geben Sie stattdessen den tatsächlichen Wert als Textliteral an. |
| 5020 | Veralteter Knoten: `<supported_blocks>` | Zu ersetzen durch `<supported_containers>`. |
| 5021 | Veralteter Knoten: `<block_name>` | Zu ersetzen durch `<container_name>`. |
| 5022 | Fabrikname erkannt | Widget-Typ sollte nicht mit / beginnen. |
| 5023 | Veraltete ACL-Struktur in Zeile erkannt | Überprüfen Sie lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Obsolete Menüstruktur in Zeile erkannt | Überprüfen Sie app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | In der Datei erkannte veraltete Systemkonfigurationsstruktur | Überprüfen Sie app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Nicht anwenden `"text/javascript"` type attribute | Verwenden Sie nur öffentliche Mitglieder. |
| 5028 | Zugang zu geschützten und privaten Mitgliedern `Block` -Klasse ist in PHP-Vorlagen veraltet | Verwenden Sie nur öffentliche Mitglieder. |
| 5031 | Enthält veraltete Methode | Verwendung `getConnection()` -Methode. |
| 5042 | Falsches Format der PHP-Klassenreferenz | Vergewissern Sie sich, dass nur mit Binnenmajuskeln (camelCased letters, numbers) und ohne vorangestellten Schrägstrich auf die Klasse verwiesen wird. |
| 5043 | Falsches Format der Modulreferenz | Vergewissern Sie sich, dass nur mit Buchstaben, Zahlen, Unterstrichen und einem vorangestellten Schrägstrich auf das Modul verwiesen wird. |
| 5044 | Klasse `Zend_Db_Select` ist eingeschränkt | Vorgeschlagene Ersetzung: `\Magento\Framework\DB\Select`. |
| 5045 | Klasse `Zend_Db_Adapter_Pdo_Mysql` ist eingeschränkt | Vorgeschlagene Ersetzung: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Klasse `Magento\Framework\Serialize\Serializer\Serialize` ist eingeschränkt | Vorgeschlagene Ersetzung: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Klasse `ArrayObject` ist eingeschränkt | Vorgeschlagene Ersetzung: Benutzerdefinierte Klasse, erweitert von `ArrayObject` mit überschriebenen Serialisierungs-/Deserialisierungs-Methoden. |
| 5048 | Klasse `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` ist eingeschränkt | Vorgeschlagene Ersetzung: Factory, die eine benutzerdefinierte Klasse erstellt, erweitert von `ArrayObject` mit überschriebenen Serialisierungs-/Deserialisierungs-Methoden. |
| 5050 | Der referenzierte Block wird entfernt | Entfernen Sie den Verweis auf den Block. |
| 5051 | `output="toHtml"` ist veraltet | Verwendung `output="1"`. |
| 5052 | Die Klasse `\Magento\Framework\View\Element\Text\ListText` sollte nicht mehr im Layout verwendet werden | Klasse entfernen `\Magento\Framework\View\Element\Text\ListText` aus dem Layout. |
| 5053 | Methodenaufruf über Layoutanweisung `<action>` ist nicht erlaubt | Vermeiden Sie die Anwendung einer Verstoßmethode in `<action>`. |
| 5054 | `helper` attribute contains `/` | Entfernen `/` vom Helper-Attribut. |
| 5055 | `helper` Attribut enthält nicht `::` | Hinzufügen `::` zum Helper-Attribut. |
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
| 5068 | Richtlinie `{{htmlescape}}` ist veraltet | Verwendung `{{var}}` anstatt. |
| 5069 | Richtlinie `{{escapehtml}}` ist veraltet | Verwendung `{{var}}` anstatt. |
| 5070 | Dritter Parameter ist nicht mehr erforderlich für `getChildHtml()` | Entfernen des dritten Parameters aus dem Aufruf an `getChildHtml()`. |
| 5071 | Der 4. Parameter ist nicht mehr erforderlich für `getChildHtml()` | 4. Parameter aus Aufruf von entfernen `getChildHtml()`. |
| 5073 | Ältere Tabellennamen mit Schrägstrich müssen auf direkte Tabellennamen fixiert sein | Verwenden Sie stattdessen den direkten Tabellennamen. |
| 5075 | Anwendungsmodule sollten keine Klassen aus Testmodulen verwenden | Entfernen Sie die Verwendung von Klassen aus Testmodulen. |
| 5078 | Klasse muss im Konstruktor angefordert werden, sonst kann Compiler diese Klassen nicht finden und generieren | Klasse zum Konstruktor hinzufügen. |
| 5079 | Von der Verwendung von Variablen der var-Klasse wird abgeraten | Vermeiden Sie die Verwendung von &quot;var&quot;zum Deklarieren von Klassenvariablen. |
| 5080 | Mögliche SQL-Rohanweisung erkannt | Verwenden Sie stattdessen Repositorys oder Daten-Patches. |
| 5081 | Von der Verwendung von Helfern in Vorlagen wird abgeraten | Verwenden Sie stattdessen ViewModel . |
| 5082 | Die Verwendung von $this in Vorlagen wird nicht mehr unterstützt | Verwenden Sie stattdessen $block . |
| 5083 | Konstanten sind nicht als erstes Argument der Übersetzungsfunktion zulässig | Verwenden Sie stattdessen das Zeichenfolgenliteral. |
| 5085 | Von der Verwendung bestimmter Funktionen wird abgeraten | Verwenden Sie stattdessen die alternative Funktion, die für die Nachricht empfohlen wird. |
| 5087 | Kompatibilitätsproblem mit PHP-Querversionen | Befolgen Sie die Vorschläge der Nachricht und überprüfen Sie die [Migrationshandbuch](https://www.php.net/manual/en/migration81.php). |
| 5088 | Optionale Parameter gefunden nach erforderlichen | Verschieben Sie erforderliche Parameter nach optionalen. |
| 5089 | Sichtbarkeit der Methoden `final private` found | Sichtbarkeit der Methode ändern von `final private` nur `private`. |
| 5090 | Magische Methode `__set_state` nicht definiert als `static` | Magische Methode `__set_state` muss definiert werden als `static`. |
| 5091 | Klasse mit `__toString()` Methode, die nicht von `Stringable` Benutzeroberfläche | Hinzufügen `Stringable` Schnittstelle zur Klasse mit `__toString()` -Methode. |
| 5092 | `is_resource()` -Methode für Funktionen, die jetzt Objekt zurückgeben | Änderung `is_resource()` nach `instanceof` Objekt. |
| 6001 | `jQuery.andSelf()` entfernt | Verwendung `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` und `$.unbind` veraltet sind | Verwendung `$.on` und `$.off` anstatt. |
| 6003 | Die jQuery-Methode zum Abonnieren von Ereignissen ist veraltet und sollte nicht verwendet werden | Verwendung `.on("event name", fn)` -Methode verwenden, um dieses Ereignis zu abonnieren. |
| 6003 | Die jQuery-Methode zum Trigger-Ereignis ist veraltet und sollte nicht verwendet werden | Verwendung `.trigger("event name")` -Methode verwenden, um dieses Ereignis Trigger. |
| 6004 | jQuery `$.delegate` und `$.undelegate` veraltet sind | Verwendung `$.on` und `$.off` anstatt. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) wurde entfernt | Verwenden Sie (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` entfernt | Verwendung `jQuery.length`. |
| 6007 | `jQuery.trim` veraltet ist | Verwendung `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, &quot;inlite&quot;-Design, &quot;mobile&quot;-Design, &quot;moderne&quot; Design) entfernt | Aktualisieren Sie den Code, um mit tinymce5 kompatibel zu sein. |
| 6009 | `jQuery.isFunction()` veraltet ist | In den meisten Fällen kann sie durch [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.type()` veraltet ist | Ersetzen Sie durch eine entsprechende Typprüfung, wie [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` veraltet ist | Verwenden Sie stattdessen die native Array.isArray -Methode. |
| 6009 | `jQuery.parseJSON()` veraltet ist | Um JSON-Zeichenfolgen zu analysieren, verwenden Sie stattdessen die native Methode JSON.parse . |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) ist veraltet | Verwenden Sie stattdessen jQuery.expr.pseudos . |

{style=&quot;table-layout:auto&quot;}

## Warnungen

### Core Code

Diese Warnungen werden bei geringfügigen Inkonsistenzen in der Core-Codebase gemeldet.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 2004 | Variantenabweichung der Komponentenabhängigkeiten | Das Problem weist darauf hin, dass die Komponentenabhängigkeitsversion in etalon und dem eigentlichen Projekt unterschiedlich ist. Aktualisieren der Abhängigkeit durch Ausführen `composer update <package_name>`. |

{style=&quot;table-layout:auto&quot;}

### Benutzerspezifischer Code

Wenn Verweise auf veralteten Code erkannt werden, werden benutzerdefinierte Code-Warnungen ausgelöst. Solche Verweise sollten durch die unterstützten Erweiterungspunkte ersetzt werden. Beachten Sie die `@see` Anmerkung des veralteten Elements für Empfehlungen. Diese Fehler werden auch gemeldet, wenn kleinere Kodierungsstandards verletzt wurden.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 1131 | Aus Adobe Commerce erweitern ``@deprecated`` class | Die erweiterte Klasse wird in den kommenden Versionen entfernt. Die Vererbung ist keine empfohlene Methode zur Erweiterung der Adobe Commerce-Funktionalität. Aktualisieren Sie den Code, um eine Klasse zu verwenden, die als `@api`. |
| 1132 | Adobe Commerce importieren `@deprecated` class | Die erweiterte Klasse wird in den kommenden Versionen entfernt. Erwägen Sie die Verwendung der Adobe Commerce-Klasse, die als `@api` anstatt. |
| 1133 | Laden von Adobe Commerce `@deprecated` class | Die erweiterte Klasse wird in den kommenden Versionen entfernt. Erwägen Sie die Verwendung der Adobe Commerce-Klasse, die als `@api` anstatt. |
| 1134 | Verwenden von Adobe Commerce `@deprecated` class | Die erweiterte Klasse wird in den kommenden Versionen entfernt. Erwägen Sie die Verwendung der Adobe Commerce-Klasse, die als `@api` anstatt. |
| 1234 | Verwenden von Adobe Commerce `@deprecated` Konstante | Die veraltete Konstante wird in den kommenden Versionen entfernt. Erwägen Sie die Verwendung einer Konstante, die als `@api` oder eine private Konstante innerhalb Ihrer Implementierung verwenden. |
| 1235 | Überschreiben von Adobe Commerce `@deprecated` Konstante | Die veraltete Konstante wird in den kommenden Versionen entfernt. Erwägen Sie die Verwendung einer Konstante, die als `@api` oder eine private Konstante innerhalb Ihrer Implementierung verwenden. |
| 1236 | Zuweisung von Adobe Commerce `@deprecated` Konstante | Die veraltete Konstante wird in den kommenden Versionen entfernt. Erwägen Sie die Verwendung einer Konstante, die als `@api` oder eine private Konstante innerhalb Ihrer Implementierung verwenden. |
| 1332 | Importierte Adobe Commerce `@deprecated` Benutzeroberfläche | Die veraltete Benutzeroberfläche wird in den kommenden Versionen entfernt. Erwägen Sie die Verwendung einer Schnittstelle oder Klasse, die als `@api` anstatt. |
| 1334 | Verwendeter Adobe Commerce `@deprecated` Benutzeroberfläche | Die veraltete Benutzeroberfläche wird in den kommenden Versionen entfernt. Erwägen Sie die Verwendung einer Schnittstelle oder Klasse, die als `@api` anstatt. |
| 1337 | Von Adobe Commerce übernommen `@deprecated` Benutzeroberfläche | Die veraltete Benutzeroberfläche wird in den kommenden Versionen entfernt. Erwägen Sie das Entfernen der Vererbung der Benutzeroberfläche mithilfe einer Schnittstelle, die als `@api` oder eine in Ihrer Implementierung eingeführte Schnittstelle. |
| 1338 | Implementierte Adobe Commerce `@deprecated` Benutzeroberfläche | Die veraltete Benutzeroberfläche wird in den kommenden Versionen entfernt. Erwägen Sie das Entfernen der Vererbung der Benutzeroberfläche mithilfe einer Schnittstelle, die als `@api` oder eine in Ihrer Implementierung eingeführte Schnittstelle. |
| 1430 | Aufruf nicht deklarierte Datenobjektmethode | Die nicht deklarierten magischen Methoden können sich ändern. Erwägen Sie stattdessen die Verwendung von Oberflächenmethoden . |
| 1439 | Adobe Commerce aufrufen `@deprecated` method | Die veraltete Methode wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung von Methoden, die in API-Schnittstellen deklariert sind. |
| 1534 | Verwenden von Adobe Commerce `@deprecated` property | Die veraltete Methode wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung von Methoden, die in API-Schnittstellen deklariert sind. |
| 1535 | Überschreiben von Adobe Commerce `@deprecated` property | Die veraltete Eigenschaft wird in den kommenden Versionen entfernt. Ziehen Sie stattdessen die Verwendung von Methoden in Betracht, die in API-Schnittstellen deklariert wurden, oder die Verwendung einer privaten Eigenschaft in Ihrer Implementierung. |
| 1536 | Zuweisung von Adobe Commerce `@deprecated` property | Die veraltete Methode wird in den kommenden Versionen entfernt. Erwägen Sie stattdessen die Verwendung von Methoden, die in API-Schnittstellen deklariert sind. |
| 5006 | Proxys und Abfänger dürfen in Konstruktoren niemals explizit angefordert werden | Die ursprüngliche Klasse sollte als Typ des Konstruktorparameters deklariert werden. Die Interceptor/Proxy-Klasse wird von der Implementierung der Framework-Abhängigkeitsinjektion übergeben. |
| 5074 | Verwendung veralteter Methoden `getResource()` , um erkannte Daten zu speichern/zu laden/zu löschen. | Verwenden Sie stattdessen ein Repository. |
| 5086 | Sichtbarkeit wird nicht auf einer Konstante deklariert | Deklarieren Sie die Sichtbarkeit für alle Konstanten. |

{style=&quot;table-layout:auto&quot;}

### GraphQL-Schema

GraphQL-Schema-Warnungen werden ausgelöst, wenn die zusätzlichen Elemente in der neuen Version zum Schema hinzugefügt werden. Es wird empfohlen, die Implementierung zu überprüfen, um zu sehen, ob sie für Anfragen verwendet werden sollten.

| Fehler-Code | Fehlerbeschreibung | Vorgeschlagene Aktion |
| --- | --- | --- |
| 3206 | Argument Standardwert geändert | Wenn die Abfrage bei der Anpassung verwendet wird, muss der Argumentwert möglicherweise explizit angegeben werden. |
| 3302 | Typ hinzugefügt zur Vereinigung | Der Typ wurde der Vereinigung hinzugefügt. Überprüfen Sie die Implementierung, die das Ergebnis der Abfrage verarbeitet, die diesen Vereinigungstyp zurückgibt, und stellen Sie sicher, dass sie den hinzugefügten Typ verarbeiten kann. |
| 3304 | Optionales Eingabefeld hinzugefügt | Optionales Eingabefeld hinzugefügt. Überprüfen Sie die Implementierung, um sicherzustellen. |
| 3305 | Implementierte Benutzeroberfläche hinzugefügt | Das Feld kann weitere Informationen akzeptieren/bereitstellen, die in der Implementierung berücksichtigt werden können. |
| 3306 | Wert zu Enum hinzugefügt | Ein Wert wurde zu einer -Enumeration hinzugefügt. Wenn Clients eine switch -Anweisung zum Wert der Enum enthalten und keinen Standardfall enthalten, kann diese Änderung zu unerwartetem Verhalten führen. |
| 3308 | Optionales Argument hinzugefügt | Wenn die Abfrage bei der Anpassung ein neues Argument verwendet, muss es möglicherweise der Anfrage hinzugefügt werden. |

{style=&quot;table-layout:auto&quot;}
