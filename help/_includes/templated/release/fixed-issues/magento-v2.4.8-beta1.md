---
source-git-commit: e05e4e4ef547bfb95fdcc53c2095ef0725b0a6e1
workflow-type: tm+mt
source-wordcount: '14731'
ht-degree: 0%

---
# Versionshinweise zu Magento Open Source (v2.4.8-beta1)

## Highlights

Die folgenden 49 Highlights gelten für die Version 2.4.8 von Magento Open Source.

### Framework

* _AC-10721_: Aktualisieren der League/Flysystem Composer-Abhängigkeiten auf die neueste Version
   * _Fix Hinweis_: Aktualisieren Sie die Abhängigkeiten von 2.x League/Flysystem Composer auf die neueste Version 3.x
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11495_: 2.4.8-Beta1 Plattformkomponenten-Upgrade
* _AC-11673_: Untersuchen Sie die neuesten Versionen von php-amqplib/php-amqplib
   * _Fehlerbehebung_: Die neueste Version php-amqplib/php-amqplib wurde aktualisiert:^3.x
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11723_: Refaktorierung des Integrationstest-Frameworks für die Kompatibilität mit phpunit 10 - IntegrationTest.php nicht gefunden
   * _Fehlerbehebung_: PHPUnit 9 wurde auf PHPUnit 10 aktualisiert, mit Integrations- und WebAPI Test Framework-Änderungen von Adobe Commerce. PHPUnit 10 Änderungen sind abwärtskompatibel.
   * _GitHub-Code-Beitrag_: &lt;https://github.com/magento/magento2/ (intern, nicht zusammengeführt)>
* _AC-11813_: WebApi Test Framework for phpunit 10 compatibility - Issue related to RabbitMQ connector with SOAP and B2B modules
   * _Fehlerbehebung_: PHPUnit 9 wurde auf PHPUnit 10 aktualisiert, mit Integrations- und WebAPI Test Framework-Änderungen von Adobe Commerce. PHPUnit 10 Änderungen sind abwärtskompatibel.
   * _GitHub-Code-Beitrag_: &lt;https://github.com/magento/magento2/ (intern, nicht zusammengeführt)>
* _AC-11816_: Hinzufügen der Kompatibilität mit MySQL 8.4 LTS
* _AC-11911_: jQuery/fileuploader-CSS-Bereinigung nach der Migration zur Uppy-Bibliothek
   * _Fehlerbehebung_: jQuery/fileUploader-Bibliothek wurde entfernt, da sie in die Uppy-Bibliothek migriert wurde
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_: Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für Magento CE
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12014_: Elasticsearch 8-Modul als veraltet markieren
* _AC-12015_: ExtJS-Ordnerbereinigung nach der Migration zur jsTree-Bibliothek
   * _Fehlerbehebung_: ExtJs-Ordner wurde entfernt, da die zugehörige Funktion zu jsTree migriert wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_: Aktualisieren der Monolog-/Monolog-Systemabhängigkeit auf die neueste Hauptversion
   * _Fehlerbehebung_: Das System wurde aktualisiert, um die neueste Hauptversion der Bibliothek „monolog/monolog:^3.x“ zu verwenden, wodurch Kompatibilität und verbesserte Leistung gewährleistet sind. Zuvor verwendete das System eine veraltete Version der Bibliothek „monolog/monolog“, was zu potenziellen Problemen und Einschränkungen hätte führen können.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_: Aktualisieren Sie die Abhängigkeit von wikimedia/less.php auf die neueste Hauptversion
   * _Fehlerbehebung_: Das System wurde aktualisiert, um die neueste Hauptversion 5.x der Bibliothek &quot;wikimedia/less.php&quot; zu verwenden, wodurch Kompatibilität und aktuelle Funktionen gewährleistet sind. Zuvor verwendete das System eine veraltete Version der Bibliothek, was zu Sicherheitsproblemen hätte führen können.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_: Aktualisieren von jquery/validate-Bibliotheksabhängigkeiten auf die neueste Nebenversion
   * _Fehlerbehebung_: Aktualisieren von jquery/validate library-Abhängigkeiten auf die neueste Nebenversion 1.20.0
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_: Aktualisieren der Systemabhängigkeit von moment.js auf die neueste Nebenversion
   * _Hinweis:_ Sie die Systemabhängigkeit von moment.js auf die neueste Nebenversion 2.30.1 auf.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_: Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für EE
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_: Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für B2B
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_: Hinzufügen der Kompatibilität mit MySQL 8.4 LTS für Bundle-Erweiterungen
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_: Kompatibilität mit MariaDB 11.4 LTS für CE hinzufügen
   * _Fehlerbehebung_: MariaDB 11.4-Unterstützung für Adobe Commerce und -Erweiterungen hinzugefügt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_: Abonnentenoptimierung - PhpUnit10
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_: Unterstützt weitere Verbindungsversuche für Redis-Sitzung und kompatibel mit colinmollenhour/php-redis-session-abstract v2.0.0
   * _Fehlerbehebung_: Die neueste Version von colinmollenhour/php-redis-session-abstract v2.0.0 wurde aktualisiert und ist mit Adobe Commerce kompatibel
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12268_: Aktualisieren von League/Flysystem Composer-Abhängigkeiten auf die neueste Version
   * _Fix Hinweis_: Aktualisieren Sie die Abhängigkeiten von 2.x League/Flysystem Composer auf die neueste Version 3.x
* _AC-12576_: Untersuchung der Fehler bei Automatisierungstests mit MySQL 8.4 LTS
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_: Kompatibilität mit MariaDB 11.4 LTS for EE hinzufügen
   * _Fehlerbehebung_: MariaDB 11.4-Unterstützung für Adobe Commerce und -Erweiterungen hinzugefügt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12693_: Erfahren Sie mehr über das Data Migration Tool (DMT) mit MySQL 8.4 LTS
* _AC-12715_: Aktualisieren der Laminas Composer-Abhängigkeiten auf die neueste Version
   * _Fehlerbehebung_: Das System unterstützt jetzt die neuesten Versionen von Laminas Composer-Abhängigkeiten:
laminas/laminas-serviceManager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
Gewährleistung der Kompatibilität und aktuellen Funktionalität. Zuvor konnte eine Aktualisierung auf die neuesten Versionen dieser Abhängigkeiten zu Problemen mit der Abwärtskompatibilität und Testfehlern führen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12752_: Hinzufügen der Kompatibilität mit MariaDB 11.4 LTS für das Datenmigrations-Tool
   * _Fehlerbehebung_: MariaDB 11.4-Unterstützung für Adobe Commerce und -Erweiterungen hinzugefügt
* _AC-12823_: Untersuchen Sie den Fehler beim Modultest aufgrund einer Aktualisierung des phpunit-Patches während des Komponenten-Upgrades.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12897_: SVC- und EAT-Tool-Kompatibilität mit MySQL 8.4
* _AC-12898_: UCT-Tool-Kompatibilität mit MySQL 8.4
   * _Fehlerbehebung_: Das Upgrade-Kompatibilitäts-Tool (UCT) ist jetzt mit MySQL 8.4 kompatibel, sodass ein reibungsloser Betrieb und Kompatibilitätsprüfungen für Instanzen, die auf dieser Version ausgeführt werden, gewährleistet sind. Zuvor wurde das UCT-Tool nicht auf Kompatibilität mit MySQL 8.4 getestet und verifiziert.
* _AC-9749_: Upgrade PHPUnit 10
   * _Fix Hinweis_: Die phpunit/phpunit Composer-Abhängigkeiten wurden auf kompatible Version aktualisiert - „phpunit/phpunit“:„10.x“

### Installieren und Verwalten

* _AC-6819_: Setzen Sie die Indexer standardmäßig auf „Nach Zeitplan aktualisieren“

### Reihenfolge

* _ACP2E-2709_: [Funktionsanfrage] Kunde schlägt vor, dass die Schaltfläche „Kommentar senden“ auf der Seite „Bestelldetails“ verwirrend ist und in etwas Anderes geändert werden sollte
   * _Hinweis korrigieren_: Um die Verwirrung zu minimieren, wurde die Beschriftung der Schaltfläche „Kommentar übermitteln“ auf der Seite mit den Bestelldetails in „Aktualisieren“ geändert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/488c1034>

### Sonstige

* _AC-11420_: Setzen Sie Indexer auf den Status „Bereit“, wenn eine neue Version von Adobe Commerce installiert wird
   * _Fix Hinweis_: Nach dem Installations-Magento muss der Indexerstatus standardmäßig *Bereit* sein.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_: Legen Sie in einer bestehenden Magento-Installation bei der Installation des Indexermoduls eines Drittanbieters die Indexer standardmäßig in der geplanten Aktualisierung fest.
   * _Hinweis:_ neuen Indexer befinden sich standardmäßig im Modus [Nach Zeitplan aktualisieren]. Zuvor war der Standardmodus &quot;[ beim Speichern]. Dasselbe gilt auch für benutzerdefinierte Indexer.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_: Die Optionen für Elasticsearch 7 und 8 sollten in der Admin-Konfiguration als veraltet gekennzeichnet sein.
   * _Fehlerbehebung_: Die Option &quot;Elasticsearch 8“ in der Admin Config-Option wird mit veraltetem Text angezeigt, um Benutzende darüber zu informieren, dass Elasticsearch 8 nicht mehr empfohlen wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_: Textnotiz hinzufügen, wenn die Option &quot;Elasticsearch&quot; in der Admin-Konfiguration ausgewählt ist
   * _Fehlerbehebung_: Es wurde ein Textkommentar hinzugefügt, um Adobe Commerce-Admin-Benutzern mitzuteilen, dass Elasticsearch nicht mehr vom Adobe unterstützt wird und nicht mehr unterstützt wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12870_: SVC- und EAT-Tool-Kompatibilität mit MariaDB 11.4
   * _Fix Hinweis_: SVC- und EAT-Tool-Kompatibilität mit MariaDB 11.4
* _AC-12876_: UCT-Tool-Kompatibilität mit MariaDB 11.4
* _LYNX-374_: Bestätigungs-E-Mail über GraphQL dokumentieren
* _LYNX-376_: Dokumenterstellungskonfigurationen für reCAPTCHA in GraphQL
* _LYNX-409_: DB-Abfrageoptimierung für die Mutation „Warenkorbartikel aktualisieren“

### Sicherheit

* _AC-11041_: Sicherheitsverbesserungen für 2.4.8-beta1 ab Version Juni 2024
* _AC-11864_: Sicherheitsverbesserungen für 2.4.8-beta1 ab Version August 2024
* _AC-12346_: Sicherheitsverbesserungen für 2.4.8-beta1 ab Version Oktober 2024
* _AC-12691_: [2.4.8-beta1] Endpunkt der REST-API für Kundenaktualisierungen funktioniert nicht
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4102373>, <https://github.com/magento/magento2/commit/a4102373>

### UI-Framework

* _AC-12726_: [2.4.8-beta1] TinyMCE 5 Migration zu TinyMCE 7
   * _Fehlerbehebung_: TinyMCE 5 wurde auf TinyMCE 7.3.0 migriert, um eine unterstützte Version für Adobe Commerce zu sein. Zuvor verwendete das System 5.10.2, das veraltet war und Sicherheitslücken meldete
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_: [2.4.8-beta1] TinyMCE 5 Migration zu TinyMCE 7 Page Builder
   * _Fehlerbehebung_: TinyMCE 5 wurde auf TinyMCE 7.3.0 migriert, um eine unterstützte Version für Adobe Commerce zu sein. Zuvor verwendete das System 5.10.2, das veraltet war und Sicherheitslücken meldete
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_: [2.4.8-beta1] TinyMCE 5 Migration zu TinyMCE 7 - Magento2-infra - Banned Words
   * _Fehlerbehebung_: TinyMCE 5 wurde auf TinyMCE 7.3.0 migriert, um eine unterstützte Version für Adobe Commerce zu sein. Zuvor verwendete das System 5.10.2, das veraltet war und Sicherheitslücken meldete
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_: Require.js-Upgrade auf die neueste Version 2.3.7 (Sicherheitslücke CVE-2024-38999)
   * _Hinweis:_ Require.js wurde auf die neueste Version 2.3.7 aktualisiert. In der vorherigen Version meldete Sicherheitslücke
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>

## Behobene Probleme

Es wurden 253 Probleme im Kern-Code von Magento Open Source 2.4.8 behoben. Nachfolgend werden einige der in dieser Version enthaltenen behobenen Probleme beschrieben.

### APIs

* _AC-10042_: /V1/Transactions REST API gibt einen Fehler zurück, wenn parent_txn_id = txn_id ist
   * _Fehlerbehebung_: Das System verarbeitet jetzt korrekt die übergeordneten und untergeordneten Concept-Transaktionen, bei denen die übergeordnete Transaktions-ID mit der Transaktions-ID identisch ist, sodass beim Abfragen des /V1/transaction-REST-API-Endpunkts keine Endlosschleife entsteht. Zuvor führte dieses Szenario aufgrund der Überschreitung der maximalen Ausführungszeit zu einem schwerwiegenden Fehler.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [GraphQL] Typproblem in 2.4.7
   * _Hinweis beheben_: Das System verarbeitet jetzt beim Ausführen einer GraphQL-Abfrage Ganzzahlwerte in der GetCustomSelectedOptionAttributes-Funktion korrekt, sodass typbezogene Fehler vermieden werden. Zuvor führte das Starten einer GraphQL-Abfrage, die GetCustomSelectedOptionAttributes mit einem ganzzahligen Argument verwendet hat, zu einem Typfehler.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38662>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38663>
* _ACP2E-2927_: [REST API]: „Standardwert in Store-Ansicht verwenden“ bleibt nach dem Hinzufügen von Konfigurationen für ein konfigurierbares Produkt nicht aktiviert
   * _Hinweis beheben_: Das Problem wurde behoben, indem sichergestellt wurde, dass die Datenbankeinträge für die anpassbaren Optionen eines nicht standardmäßigen Speichers korrekt sind. Das Kontrollkästchen für den benutzerdefinierten Store im Abschnitt „Admin > Katalog > Produktbearbeitung > Anpassbare Optionen“ war zuvor aufgrund ungenauer Datenbankeinträge deaktiviert, auch wenn der Optionstitel für den benutzerdefinierten Store genauso geblieben ist wie der Standardstore.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_: REST-API kann bei Verwendung von Oauth1 keine Anfragen mit Schrägstrich (/) in der SKU stellen
   * _Fehlerbehebung_: Vor der Fehlerbehebung waren Sie nicht in der Lage, einen erfolgreichen API-Aufruf für ein Produkt durchzuführen, das &quot;/&quot; in der SKU hatte. Jetzt können Sie eine erfolgreiche API-GET-Anfrage für Produktdetails ausführen, obwohl ihre SKU einen Schrägstrich enthält.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_: Aktualisierung der Kundenadresse schlägt fehl, wenn die Aktualisierung über die REST-API erfolgt, wenn „validateDefaultAddress“ aktiviert ist
   * _Hinweis:_ API-Endpunkt funktioniert jetzt wie beabsichtigt, nachdem das Problem mit dem fehlenden ID-Schlüssel in der API-Payload behoben wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [Cloud] Erstellen der Kundengruppe „Doppelter Website-Gruppenpreis“ in der Stufen-Preis-API.
   * _Fehlerbehebung_: Die Tier Price Rest-API erlaubt es jetzt nicht, die Kundengruppe „Preis der doppelten Website-Gruppe“ zu erstellen.
Zuvor war es möglich, die Kundengruppe „Duplizierte Website-Preisgruppe“ in der Stufen-Preis-API zu erstellen, die die Validierung in Admin während der Produktspeicherung nicht bestehen konnte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: Befehl mit Status kann nicht über die REST-API hinzugefügt werden
   * _Hinweis:_ Problem wurde behoben, indem die Änderung des Bestellstatus zugelassen wurde, wenn sie nur aus dem aktuellen Status stammt. Zuvor wurde der Bestellstatus nicht berücksichtigt und Änderungen in einem Bestellstatus verhindert, selbst wenn er aus demselben Status stammte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>

### Konto

* _AC-10782_: Das Formular „Kundenadresse“ ermöglicht zufälligen Code in den Namensfeldern
   * _Fehlerbehebung_: Das System validiert jetzt die Eingabe in den Feldern Vorname und Nachname im Formular der Kundenadresse, wodurch die Verwendung von zufälligem Code verhindert wird. Zuvor ermöglichte das System die Verwendung von zufälligem Code in diesen Feldern ohne einen Fehler auszulösen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38331>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38345>
* _AC-10990_: Adresse für mein Konto beim Speichern abstürzt
   * _Fehlerbehebung_: Das System speichert Kundenadressen jetzt korrekt, selbst wenn das Feld Region nicht angezeigt wird, wodurch ein Absturz während des Speichervorgangs verhindert wird. Zuvor führte der Versuch, eine Adresse ohne angezeigtes Bereichsfeld hinzuzufügen oder zu bearbeiten, zu einem Ausnahmefehler.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38406>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38407>
* _AC-11919_: Admin: Schaltflächen für Seitenaktionen unverankert links statt rechts
   * _Fehlerbehebung_: Die Schaltflächen für Seitenaktionen werden nun korrekt auf der rechten Seite der Sticky-Kopfzeile im Admin-Bedienfeld ausgerichtet, was das professionelle Look-and-Feel verbessert. Zuvor waren diese Schaltflächen fälschlicherweise auf der linken Seite der Sticky-Kopfzeile unverankert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38701>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: dev:di:info-Fehler in Magento 2.4.7
   * _Hinweis beheben_: Das System zeigt jetzt beim Ausführen des Befehls dev.:di: die Konstruktorparameter korrekt an, um Fehler zu vermeiden. Zuvor führte die Ausführung dieses Befehls zu einem Fehler aufgrund eines Typkonflikts im -Argument.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38740>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_: Der Kunde ist angemeldet, zeigt jedoch einen 404-Fehler im Frontend an.
   * _Fehlerbehebung_: Die Kunden-Dashboard-Seite für die Storefront wird jetzt wie erwartet geladen, wenn sich ein Kunde anmeldet. Zuvor konnten sich Kunden zwar anmelden, auf dieser Seite wurde jedoch ein 404-Fehler angezeigt. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35838>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: Kundenattributinformationen können nicht im Abschnitt „Kundenbearbeitung“ von Admin gespeichert werden;
   * _Fehlerbehebung_: Die Store-ID des Kunden wird jetzt ordnungsgemäß pro Website-Umfang für das Admin-Kundenbearbeitungs-Formular implementiert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/488c1034>

### Admin-Benutzeroberfläche

* _AC-11588_: Die Datenvalidierung ist erfolgreich und die Schaltfläche „Importieren“ ist beim Importieren von Produkten mit dem Verhalten „Ersetzen“ vorhanden
   * _Fehlerbehebung_: Das System validiert jetzt die Daten korrekt und blendet die Schaltfläche „Importieren“ während des Produktimports mit dem Verhalten „Ersetzen“ aus, um einen unbeabsichtigten Datenaustausch zu verhindern. Zuvor hat das System die Daten falsch validiert und die Schaltfläche „Importieren“ angezeigt, was zu potenziellen Dateninkonsistenzen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Bug] Magento 2.4.7 erlaubt keine Produktfotos mit der Dateierweiterung „Großbuchstaben“.
   * _Fehlerbehebung_: Das System akzeptiert jetzt das Hochladen von Produktbildern mit Großbuchstaben-Dateierweiterungen, um einen reibungslosen Produkterstellungsprozess sicherzustellen. Zuvor wurden Bild-Uploads mit Großbuchstaben-Dateierweiterungen abgelehnt, was Benutzer zwang, die Dateierweiterung in Kleinbuchstaben zu ändern.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38831>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-6975_: [Problem] Standardindexermodus auf „schedule“ festlegen
   * _Fix Hinweis_: Alle neuen Indexer befinden sich standardmäßig im **[!UICONTROL Update by Schedule]**.  Zuvor war der Standardmodus **[!UICONTROL Update on Save]**. Bestehende Indexer sind davon nicht betroffen. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36419>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: [Problem] Indexer-Änderungsprotokolltabellen bei mview abmelden
   * _Fehlerbehebung_: Das System entfernt jetzt automatisch nicht verwendete Änderungsprotokolltabellen, wenn ein Index von „Aktualisierung planmäßig“ in „Aktualisierung beim Speichern“ geändert wird. Der Index wird dadurch als ungültig markiert, um sicherzustellen, dass keine Einträge übersehen werden. Zuvor würde ein Wechsel eines Index zu „Aktualisierung beim Speichern“ nicht verwendete Änderungsprotokolltabellen im System belassen und alle geänderten Indizes als „gültig“ markieren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/29789>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/25859>
* _AC-9843_: i18n:collect-phrases bricht die Übersetzungsintegrität
   * _Fehlerbehebung_: Der Befehl `bin/magento i18n:collect-phrases -o` erfasst und fügt nun neue Ausdrücke aus JavaScript- und PHTML-Dateien hinzu, um sicherzustellen, dass Übersetzungen korrekt in der Übersetzungsdatei widergespiegelt werden. Zuvor konnte das System nicht mehrzeilige Übersetzungsausdrücke aus JavaScript-Dateien und Ausdrücke aus .phtml-Dateien in die Übersetzungsdatei einbeziehen, was zu unvollständigen oder falschen Übersetzungen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_: Apostroph in Store-Ansicht wird durch &quot;&quot; ersetzt
   * _Hinweis korrigieren_: Die Filter für die Store-Ansicht des Rasters zeigen jetzt Apostrophe korrekt an
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38395>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: Favicon-Upload kann .ico-Dateien nicht validieren
   * _Fix Hinweis_: Der Fehler bei der Dateivalidierung wurde in „Dateivalidierung fehlgeschlagen“ aktualisiert. Überprüfen Sie die Bildverarbeitungseinstellungen in der Store-Konfiguration.“ Zuvor hieß es einfach „Dateivalidierung fehlgeschlagen“.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: In der Galerie in PageBuilder wird eine alte Miniaturansicht anstelle eines neu hochgeladenen Bildes angezeigt
   * _Fehlerbehebung_: Generieren Sie Bildvorschauen für Bilder, die gelöscht und mit demselben Namen über die Mediensammlung im Page Builder-Inhalt erneut hochgeladen wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_: Durch das Speichern von Produkten durch Admin-Benutzende mit anderem Rollenbereich werden vorhandene zugehörige Produktinformationen im Produkt überschrieben/gelöscht
   * _Fehlerbehebung_: Vor der Fehlerbehebung wurden die zugehörigen Produkte zurückgesetzt und leer, wenn der sekundäre Admin-Benutzer auf die Schaltfläche Speichern klickte, ohne das zugehörige Produkt zu ändern. Nach dieser Fehlerbehebung klickt der sekundäre Admin-Benutzer auf die Schaltfläche Speichern , das Produkt wird nicht zurückgesetzt und erfolgreich gespeichert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: Es können nicht mehr als 200 Bestellungen exportiert werden
   * _Fehlerbehebung_: Die Serverbeschränkungen für die Anfragengröße von zuvor gesendeten IDs wurden vernachlässigt, indem die HTTP-Anfrage von GET in POST geändert wurde, um das Problem zu beheben. Aufgrund der Serverbeschränkungen für die Größe der GET-Anfrage ist zuvor ein Problem aufgetreten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: Meldung bei Validierung der Checkout-Seite falsch.
   * _Fehlerbehebung_: Wenn ein erforderliches Feld leer gelassen wird, z. B. „Adresse“, zeigt die Server-seitige Validierung die Nachricht nicht an. Die Client-seitige Validierung stellt sicher, dass die Fehlerbenachrichtigung für das erforderliche Feld angezeigt wird, in der steht: „Dies ist ein erforderliches Feld.“ Zuvor wurde zusätzlich zur Client-seitigen Validierungsmeldung die Meldung „Adresse ist erforderlich“ angezeigt, wenn ein erforderliches Feld leer gelassen wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: Problem mit der Vorlage zum Zurücksetzen des Kennworts bei einem Admin-Benutzer
   * _Hinweis:_ Problem wurde durch Verwendung des richtigen Schlüssels behoben, der jetzt den Admin-Benutzernamen in die E-Mail-Vorlage enthält und den Betreff ordnungsgemäß ausfüllt. Zuvor bestand das Problem aus einem veralteten Schlüssel, der verwendet wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_: Doppelte Schrägstriche in der Kundensegment-URL
   * _Hinweis korrigieren_: Doppelte Schrägstriche werden in der URL nicht angezeigt, wenn im Raster auf „Filter zurücksetzen“ geklickt wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_: Für bestimmte zugelassene Länder ist kein Kabeljau verfügbar
   * _Fehlerbehebung_: Jetzt ist Nachnahme für bestimmte Länder verfügbar, wenn sie benötigt wird, und   AC-3216 funktioniert erwartungsgemäß.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_: Status der benutzerdefinierten erstellten Bestellung kann nicht aktualisiert werden
   * _Notiz korrigieren_: &#39;
Wir können jetzt den Status der benutzerdefinierten Bestellung aktualisieren, während der Status zuvor nur geändert werden konnte, wenn der aktuelle Status entweder „Verarbeitung läuft“ oder „Betrug“ war.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38659>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>

### Admin-Benutzeroberfläche, Leistung

* _ACP2E-3169_: Nach der Aktualisierung auf 2.4.5-p8 treten 500 Fehler auf, wenn eine Bestellung vom Administrator erstellt wird
   * _Fehlerbehebung_: Zuvor konnte beim Aktivieren der HTML-Minimierung keine Bestellung vom Administrator aufgegeben werden. Mit aktivierter HTML-Minimierung kann die Bestellung jetzt erfolgreich vom Administrator aufgegeben werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Admin-Benutzeroberfläche, Versand

* _ACP2E-2519_: Die Anzahl der Couponcodes wird in der   Die Spalte „Verwendete Zeit“ auf der Registerkarte „Gutscheincodes verwalten“, wenn eine Bestellung mit Mehrfachversand aufgegeben wird.
   * _Fehlerbehebung_: Wenn früher eine Bestellung mit mehreren Versandvorgängen aufgegeben wurde, wurde die Anzahl der Gutscheincodes nicht in der Spalte „Verwendete Zeit“ auf der Registerkarte „Gutscheincodes verwalten“ aktualisiert. Jetzt wird die richtige Anzahl sowohl in der „Verwendeten Zeit“ angezeigt, die die gewünschten Werte bei Multi-Versand widerspiegelt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/4745100c>

### Analytics/Reporting

* _ACP2E-2570_: Fortschrittsbericht funktioniert nicht
   * _Fehlerbehebung_: Das System unterstützt jetzt die Generierung von Datendateien für erweiterte Berichte für extragroße Datensätze, indem Berichte in Stapeln von 10.000 geladen und geschrieben werden. Zuvor konnte das Modul für erweiterte Berichterstellung keine Datendateien für besonders große Datensätze generieren, was zu Fehlern von „MySQL Server ist verschwunden“ während der Ausführung des Cron-Auftrags analytics_collect_data führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Problem mit der Sichtbarkeit des Datumsbereichs für vom Administrator bestellte Produkte.
   * _Fehlerbehebung_: Der Benutzer kann ein beliebiges Datum aus dem Bericht Bestellte Produkte auswählen. Zuvor wird nach einer Tabellenaktualisierung durch die Auswahl von „Von“ das „Bis“-Datum zurückgesetzt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Falsche cURL-Kopfzeilen, die dazu führen, dass newrelic:create:deploy-marker nicht funktioniert
   * _Fehlerbehebung_: Das System formatiert jetzt cURL-Kopfzeilen korrekt, sodass der Befehl :create:-deploy-marker erfolgreich eine Bereitstellungsmarkierung in New Relic erstellen kann. Zuvor verhinderten falsche cURL-Kopfzeilen die Erstellung einer Bereitstellungsmarkierung in New Relic.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37641>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>

### Analytics/Reporting, B2B

* _ACP2E-2300_: B2B - Sitemap enthält Produkte/Kategorien, die nicht dem freigegebenen Katalog zugewiesen sind
   * _Fehlerbehebung_: Beschränken Sie die von der Sitemap generierten Kategorien und Produkte auf die Kategorien und Produkte, die nur dem öffentlichen freigegebenen Katalog und/oder der Einrichtung der Katalogkategorie zugewiesen sind.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/Reporting, Cloud

* _ACP2E-3067_: Magento verwirft die meisten New Relic Cron-Transaktionen #34108
   * _Fehlerbehebung:_ meldet korrekt Cron-auftragsbezogene Transaktionen an NewRelic. Zuvor wurden einige Cron-Job-bezogene Transaktionen als „OtherTransaction/Action/Unknown“ in NR angezeigt
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-3044_: Unnötige Ränder im Abschnitt Meine Bestellungen
   * _Fehlerbehebung_: Zuvor wurde ein zusätzlicher Container (Auftragsreferenzen) erstellt, der zusätzliche CSS-Klassen anwandte, was dazu führte, dass unnötige Rahmenlinien unterhalb der Bestellnummer im Abschnitt Meine Bestellungen angezeigt wurden, der jetzt nicht sichtbar ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>

### B2B, Framework

* _AC-9607_: Das Filtern des Firmenrasters und der anschließende Versuch, einen CSV-Export für das Raster durchzuführen, schlagen fehl und lösen eine Ausnahme aus
   * _Fehlerbehebung_: Das System ermöglicht jetzt einen erfolgreichen CSV-Export der Rasterdaten des Unternehmens im Admin-Bedienfeld, auch wenn Filter wie „Ausstehender Saldo“ und „Unternehmenstyp“ angewendet werden. Zuvor führte das Anwenden bestimmter Filter und der Versuch, die Rasterdaten zu exportieren, zu einem Fehler und einer Ausnahme.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _BUNDLE-3367_: Bezahlung über LPM
   * _Fehlerbehebung_: Das System rendert jetzt lokale Zahlungsmethoden (LPM) beim ersten Laden korrekt, auch wenn die Versand- und Rechnungsadressen eines angemeldeten Kunden nicht übereinstimmen, was einen reibungslosen Checkout-Prozess gewährleistet. Zuvor konnte LPM aufgrund einer Diskrepanz zwischen den Versand- und Rechnungsadressen eines Kunden nicht gerendert werden, was zu potenziellen Störungen während des Checkouts führen konnte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3368_: Konfigurierbar mit Virtual as Child Product
   * _Fehlerbehebung_: Das System ermöglicht jetzt Express-Zahlungsmethoden für konfigurierbare Produkte mit einem virtuellen untergeordneten Produkt, wodurch ein reibungsloser Checkout-Prozess gewährleistet ist. Zuvor waren keine Express-Zahlungsmethoden verfügbar, wenn ein konfigurierbares Produkt mit einem virtuellen untergeordneten Produkt zum Warenkorb hinzugefügt wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3369_: Fehler bei CVV-Überprüfung fehlgeschlagen
   * _GitHub-Code-Beitrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3370_: Vaulting Über den Kontobereich Anfragen 247
   * _Fix Hinweis_: Das System ermöglicht es Kunden jetzt, neue Karten- oder PayPal-Kontoinformationen auf mehreren Websites zu speichern, ohne auf Autorisierungsfehler zu stoßen. Zuvor konnten Kunden keine neuen Zahlungsmethoden auf verschiedenen Websites speichern und erhielten eine Autorisierungsfehlermeldung.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3371_: Versand an eine Adresse eines anderen Landes
   * _Fix Hinweis_: Das System ermöglicht jetzt die fehlerfreie Verarbeitung von Transaktionen beim Versand an eine Adresse aus einem anderen Land und gewährleistet so einen reibungslosen Checkout-Prozess. Zuvor führte der Versuch, eine Adresse aus einem anderen Land zu versenden, zu Konsolenfehlern, obwohl keine sichtbaren Fehler im Frontend vorhanden waren.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3372_: Kreditkarte - Abreißfunktion
   * _Fix Hinweis_: Das System verarbeitet jetzt den Zerfall von Braintree-PayPal-Komponenten korrekt, wenn ein Kunde von der Zahlungsseite zur Versandseite zurückkehrt, um Fehler zu vermeiden und sicherzustellen, dass die PayPal-Express-Schaltflächen korrekt dargestellt werden. Zuvor führte das Zurücknavigieren von der Zahlungsseite zur Versandseite manchmal zu einem Fehler, wenn versucht wurde, die Braintree-PayPal-Komponenten zu zerlegen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3373_: Versandrückruf für PayPal Express
   * _Fehlerbehebung_: Das System zeigt jetzt die verfügbaren Versandmethoden korrekt im modalen PayPal-Express an, sodass Kunden ihre bevorzugte Versandmethode auswählen können, bevor sie zur Überprüfungsseite wechseln oder ihre Transaktion abschließen. Zuvor waren im Modal „PayPal Express“ keine Versandmethoden verfügbar, sodass Kunden eine Versandmethode auf einer separaten Überprüfungsseite auswählen mussten, bevor sie ihre Transaktion abschließen konnten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/ext-braintree/pull/204>

### Warenkorb und Checkout

* _AC-10660_: Ausnahme wird beim Hinzufügen eines Produkts zum Warenkorb auf der Seite „Produkt vergleichen“ nicht ordnungsgemäß verarbeitet
   * _Fehlerbehebung_: Das System verarbeitet jetzt Ausnahmen korrekt, wenn ein Produkt von der Seite „Produkt vergleichen“ zum Warenkorb hinzugefügt wird und eine Meldung des Nachrichten-Managers im Controller angezeigt wird. Zuvor führte eine Ausnahme dazu, dass eine JSON-codierte Seite zurückgegeben wurde, anstatt ordnungsgemäß erfasst und verarbeitet zu werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38200>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag sendet keine Transaktionspreise und -summen.
   * _Fehlerbehebung_: Das System sendet jetzt die Transaktionspreise und -summen korrekt an Google Tag, wenn GTag aktiviert ist, was eine genaue Verfolgung von E-Commerce-Daten gewährleistet. Zuvor wurde die Währung fälschlicherweise als Teil der „All“-Bestellungen gesendet, anstatt mit der einzelnen Bestellung verknüpft zu werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37348>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Problem] [Checkout] Abhängige Anweisungen in fehlgeschlagener E-Mail-Vorlage für Zahlung aktualisiert
   * _Fehlerbehebung_: Die Versandadresse und Versandmethode in der E-Mail-Vorlage für fehlgeschlagene Zahlungen für virtuelle Produkte wird jetzt korrekt weggelassen, sodass die E-Mail nur relevante Informationen enthält. Zuvor enthielt die fehlgeschlagene Zahlungs-E-Mail für virtuelle Produkte fälschlicherweise die Versandadresse und die Versandmethode.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32781>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32511>
* _AC-11876_: [Problem] Regression der Verkaufsregeln in 2.4.7
   * _Fehlerbehebung_: Das System validiert jetzt die Verkaufsregeln korrekt, was die Anwendung eines Gutscheincodes auf einen Warenkorb verhindert, wenn die Produktbedingung mit keinem Produktnamen übereinstimmt. Zuvor konnte eine Verkaufsregel angewendet und ein Rabatt auf den Versandbetrag gewährt werden, selbst wenn die Produktbedingung mit keinem Produktnamen übereinstimmte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38671>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_: [Problem] Der Lader blockiert die Versandmethoden, nachdem die Postleitzahl geändert wurde. Validierungsregeln für Versandraten
   * _Fehlerbehebung_: Das System verarbeitet jetzt benutzerdefinierte Versandmethoden ohne Validierungsregeln für Versandraten korrekt, sodass der Lader die Versandmethoden nicht blockiert, nachdem die Postleitzahl während des Checkouts in der Versandadresse geändert wurde. Zuvor führte eine Änderung der Postleitzahl in der Versandadresse während des Checkouts dazu, dass der Lader die Versandmethoden blockiert und nicht verschwindet, wenn benutzerdefinierte Versandmethoden ohne Validierungsregeln für Versandraten verwendet wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38742>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: Die Gutscheincode-Funktion funktioniert auf der Kaufbestätigungsseite auf Magento 2.4.7 nicht ordnungsgemäß
   * _Fehlerbehebung_: Das System aktiviert jetzt das Eingabefeld für Rabattcode/Coupon auf der Checkout-Seite für virtuelle und herunterladbare Produkte, sodass Benutzer Rabattcodes wie erwartet anwenden können. Zuvor war die Eingabe des Rabattcodes/Coupons deaktiviert und der Text des Schaltflächentitels wurde als „Coupon abbrechen“ angezeigt, was Benutzer daran hinderte, Rabattcodes anzuwenden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38826>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-8103_: Umsatzsteuer in der Adressausgabe
   * _Fehlerbehebung_: Das System ermöglicht jetzt die Übersetzung des Textes „VAT“, „T“, „F“ in den Adressen-Renderern, sodass Benutzer diese Begriffe in die spezifische Sprache des Geschäfts übersetzen können. Zuvor waren diese Begriffe nicht übersetzbar, was die Benutzer dazu zwang, eine Problemumgehung anzuwenden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36942>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: Doppelte Bestellungen mit derselben Angebots-ID zur gleichen Zeit mit wenig Zeitunterschied
   * _Hinweis korrigieren_: Es wurde ein Problem behoben, bei dem Adobe Commerce-Kunden auf doppelte Bestellungen stießen, die mit derselben QuoteID aufgegeben wurden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: Beständiger Warenkorb während des Checkout-Schritts gelöscht
   * _Fehlerbehebung_: Nach der Fehlerbehebung wird die persistente Sitzung nicht beendet, wenn Sie die Zahlungsmethode während des Checkouts auswählen, während Sie nicht angemeldet sind.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: Reorder fügt nicht zugewiesenes Produkt zum Warenkorb hinzu
   * _Fehlerbehebung_: Zuvor können für die verschiedenen Stores Produkte aus dem anderen Store neu bestellt werden. Nachdem diese Fehlerbehebung nur auf denselben Store angewendet wurde, kann dasselbe Produktumfang neu bestellt werden, wenn die Kundenkontofreigabe aktiviert ist
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: In Admin wird der „Warenkorb“ auf der linken Seite nicht aktualisiert, wenn die Artikel ausgewählt werden und „Zum Warenkorb wechseln“ auf der rechten Seite angezeigt wird
   * _Fehlerbehebung_: Der „Warenkorb“ auf der linken Seite wird aktualisiert, wenn Sie die Artikel auswählen und „Zum Warenkorb wechseln“ auf der rechten Seite in der Admin-Seite. Zuvor funktionierte diese Funktion nicht, da die umgewandelten Warenkorbelemente nicht aus der Sitzung leer wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: [Cloud] Verkaufsregel nicht auf erste Bestellung von Multi Shipping angewendet
   * _Fehlerbehebung_: Nach der Fehlerbehebung wird der Rabatt für jede Bestellung desselben Multi-Shipping-Angebots korrekt angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [Cloud]-Produktionsanfragen zum Hinzufügen desselben Produkts zum Warenkorb führen zu zwei separaten Elementen in der Warenkorb-REST-API
   * _Fehlerbehebung_: Das System verarbeitet jetzt korrekt mehrere parallele Anfragen, um dasselbe Produkt zum Warenkorb in einem einzigen Zeileneintrag hinzuzufügen, wodurch die Erstellung separater Zeileneinträge für dieselbe SKU verhindert wird. Zuvor führte das parallele Anfordern desselben Produkts über die REST-API zum Warenkorb, zu mehreren Zeileneinträgen für dieselbe SKU.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_: Das Cookie kann nicht gesendet werden. Größe von „image-messages“ beim Versuch, eine Neuanordnung vorzunehmen
   * _Hinweis beheben_: Der Neuanordnungsprozess erzeugt jetzt keine eigenen Fehler. Dies beruht auf der Auflistung der in den Warenkorb integrierten Artikelprüfungen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: Die Standard-Versandadresse ist beim Checkout nicht ausgewählt
   * _Fehlerbehebung_: Im Kontext der aktivierten Adresssuche wird jetzt die standardmäßige Versandadresse ausgewählt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [CLOUD] graphql addProductsToCart API-Problem mit benutzerdefinierter Option
   * _Fehlerbehebung_: GraphQL fügt dasselbe Produkt mit verschiedenen benutzerdefinierten Optionen korrekt in den Warenkorb
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: Mehrere Adressen werden dem Konto beim Checkout als neuer Kunde hinzugefügt
   * _Hinweis beheben_: Das System speichert jetzt eine neue Kundenadresse nur einmal, wenn die Bestellung nicht erstellt werden konnte, wodurch die Erstellung mehrerer identischer Adressen im Falle von Fehlern bei der Bestellplatzierung verhindert wird. Zuvor speicherte das System jedes Mal eine neue Adresse, wenn ein Bestellplatzierungsversuch unternommen wurde, unabhängig davon, ob der Auftrag erfolgreich erstellt wurde oder nicht.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Die Neuanordnung einer Kundenbestellung über ein Gastbestellungsformular führt zu einem leeren Warenkorb
   * _Fehlerbehebung_: Zuvor wurde der Kunde bei der Neubestellung über die Seite Bestellungen und Rücksendungen zur Anmeldeseite weitergeleitet. Nachdem diese Fehlerbehebung angewendet wurde, wird der registrierte Kunde bei der Neubestellung korrekt zur Seite Warenkorb anzeigen weitergeleitet. Der Fluss funktioniert genauso wie bei Gastkunden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: Administratorbenutzer mit eingeschränkten Rollenressourcen kann den Warenkorb nicht anzeigen
   * _Fehlerbehebung_: Zuvor konnte der Admin, der über Einschränkungen verfügt, den abgebrochenen Warenkorb nicht über das Admin-Bedienfeld für eine zugehörige Website sehen. Nachdem diese Fehlerbehebung angewendet wurde, kann der eingeschränkte Administrator den Transaktionsabbruch im Admin-Bedienfeld einsehen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d1f7dc95>

### Warenkorb &amp; Checkout, Checkout/ Eine Seite Checkout

* _AC-9386_: [Zufallsfehler] Das E-Mail-Feld wird nicht gerendert oder benötigt viel Zeit, um auf der Kaufbestätigungs-, Versand- oder Zahlungsseite anzuzeigen.
   * _Fehlerbehebung_: Commerce rendert jetzt das **[!UICONTROL Email]** auf den Seiten Checkout-Versand und Zahlung wie erwartet. Zuvor war dieses Feld entweder nicht vorhanden oder wurde langsam gerendert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/e1babcfd>

### Warenkorb und Checkout, Bestellung

* _ACP2E-3097_: Datumsauswahl für ein Produkt mit mehreren anpassbaren Optionen, wobei Datumsfelder bei der Bestellung von einem Administrator nicht funktionieren
   * _Fehlerbehebung_: Die Datumsauswahl wird jetzt für alle Datumsfelder korrekt angezeigt, wenn ein Produkt mit mehreren anpassbaren Datumsoptionen im Erstellungsprozess von Admin-Aufträgen konfiguriert wird. Zuvor wurde die Datumsauswahl nur für das erste Datumsfeld angezeigt, sodass die verbleibenden Felder keine Datumsauswahl aufweisen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>

### Warenkorb und Checkout, Versand

* _AC-12119_: Sofortkauf „Günstigster Versand“ für konfigurierbare Produkte defekt
   * _Fehlerbehebung_: Mit der Funktion Instant Purchase wurde fälschlicherweise die teurere Versandoption im Geschäft für konfigurierbare Produkte anstelle der günstigsten Flatrate-Methode ausgewählt. Durch diese Fehlerbehebung wird sichergestellt, dass die richtige Versandmethode auf der Grundlage des tatsächlichen Preises ausgewählt wird.“
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38811>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Katalog

* _AC-10910_: Die Bereinigung der Datenbanktabelle cron_schedule bereinigt keine nicht vorhandenen Aufträge
   * _Fix Hinweis_: Das System bereinigt jetzt automatisch die Datenbanktabelle cron_schedule und entfernt Einträge für Aufträge, die nicht mehr im System vorhanden sind. Dadurch wird eine optimale Leistung gewährleistet, indem eine minimale Anzahl von Zeilen in der Tabelle beibehalten wird. Zuvor wurden Einträge für Aufträge von inaktiven oder entfernten Modulen nicht bereinigt, was zu einer unnötigen Datenakkumulation in der cron_schedule-Tabelle führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38217>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: Stufenpreis wird nicht aus konfigurierbarem Produkt gelöscht
   * _Fehlerbehebung_: Das System entfernt jetzt den Stufenpreis eines Produkts korrekt, wenn es von einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wird, um eine genaue Preisanzeige im Frontend zu gewährleisten. Zuvor wurde der Stufenpreis eines konfigurierbaren Produkts nicht gelöscht, wenn ein Produkt von einem einfachen Produkt in ein konfigurierbares Produkt konvertiert wurde, was zu einer Diskrepanz beim angezeigten Preis führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38390>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: Kategoriebeschreibung WYSIWYG ist in einer nicht standardmäßigen Storeview leer
   * _Fehlerbehebung_: Die Kategoriebeschreibung wird jetzt im WYSIWYG-Editor korrekt gespeichert und angezeigt, wenn eine Kategorie auf der Store-Ansichtsebene bearbeitet wird. Zuvor war der WYSIWYG-Editor nach dem Speichern einer Kategoriebeschreibung auf Store-Ansichtsebene leer.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38622>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38623>
* _AC-12076_: [Problem] Wortlaut des Filterelements in der mehrschichtigen Navigation korrigieren
   * _Fehlerbehebung_: Das System verwendet jetzt korrekt die Wörter „Element“ und „Elemente“ im Filterelement für die mehrschichtige Navigation, wodurch die Klarheit und Genauigkeit der Filterbeschreibungen verbessert wird. Zuvor wurden diese Wörter falsch verwendet, was zu Verwirrung bei Benutzenden führen kann, die in den Filteroptionen navigieren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38789>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: Datum- und Uhrzeitformat für benutzerdefinierte Option funktioniert nicht
   * _Fehlerbehebung_: Das System wendet das konfigurierte Datumsformat jetzt korrekt auf benutzerdefinierte Produktoptionen vom Typ Datum an, um sicherzustellen, dass das Datumsformat im Frontend korrekt angezeigt wird. Zuvor spiegelten Änderungen an der Datumsformatkonfiguration das Frontend für benutzerdefinierte Optionen des Typs Datum nicht wider.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32990>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38925>
* _AC-6738_: Fehlender eindeutiger Schlüssel in der Tabelle eav_attribute_option_value
   * _Fehlerbehebung_: Das System enthält jetzt einen eindeutigen Schlüssel für die Spalten „option_id“ und „store_id“ in der Tabelle „eav_attribute_option_value“, was verhindert, dass eine Option mehrere Werte für dieselbe Shop-Ansicht hat. Zuvor konnte ein fehlerhafter Code dazu führen, dass eine Option mehrere Werte für dieselbe Shop-Ansicht hatte, was Probleme bei der Bearbeitung von Produkten oder Attributen verursachte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/24718>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [Problem] Verwenden Sie die Sichtbarkeitsklasse für den Produkt-Indexer der Kategorie anstelle hartcodierter Werte
   * _Fehlerbehebung_: Das System verwendet jetzt die Sichtbarkeitsklasse für den Produkt-Indexer der Kategorie anstelle hartcodierter Werte, was die Modularität verbessert. Zuvor wurden im Produkt-Indexer der Kategorie hartcodierte Werte verwendet, was die Flexibilität und Anpassungsfähigkeit einschränkte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37200>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: Der Währungs-Code ändert sich nicht im Widget „Neues Produkt“
   * _Fehlerbehebung_: Der Währungs-Code im Widget „Neues Produkt“ wird jetzt korrekt aktualisiert, wenn die Währung im Frontend geändert wird. Dies gewährleistet die Konsistenz der Währungsanzeige auf der Website. Zuvor hatte das Ändern der Währung im Frontend keine Auswirkungen auf den Währungs-Code, der im Widget Neues Produkt angezeigt wird.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37898>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: Regulärer Preis wird nicht auf PLP für konfigurierbares Produkt angezeigt
   * _Fehlerbehebung_: Der reguläre Preis wird jetzt auf Produktlistenseiten für konfigurierbare Produkte angezeigt, die untergeordnete Produkte mit Sonderpreis enthalten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: Stock-Informationen werden im visuellen Merchandising-Raster nicht korrekt angezeigt
   * _Hinweis korrigieren_: Der Lagerbestand wird jetzt entsprechend dem ausgewählten Store angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: Widget-Inhalte werden auf der CMS-Seite nicht aktualisiert
   * _Fehlerbehebung_: Das System aktualisiert jetzt den Widget-Inhalt auf einer CMS-Seite, wenn ein Produkt als neu festgelegt und gespeichert wird, und stellt sicher, dass die Seite die aktualisierte Produktsammlung anzeigt. Zuvor wurde die Seite aufgrund der falschen Cache-Identitäten, die für das Widget im Cache verwendet wurden, nicht aktualisiert, um das neue Produkt anzuzeigen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_: Probleme beim Einsparen von erweiterten Preisen für Bundle-Produkte
   * _Fix-Hinweis_: Leistungsverbesserung durch Bundle-Produkteinsparung.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [On-Premise]-Neuindizierungsprozess ist beim Erstellen von Katalogpreisregeln ineffizient
   * _Fix Hinweis_: Durch das Speichern einer Katalogpreisregel werden Indexer nicht ungültig, sondern nur die betroffenen Produkte neu indiziert
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_: Aktualisieren von Datums- und Uhrzeitattributen des Produkttyps über den CSV-Import
   * _Fix Hinweis_: Jetzt verfügen Datums-/Uhrzeitattribute über einen Zeitanteil in den exportierten Daten. Es ist auch möglich, die Zeit für solche Attribute mithilfe des Imports zu aktualisieren. Auch wenn „Einschließungsfelder“ aktiviert ist, werden Attributwerte in der Spalte „additional_attributes“ in doppelte Anführungszeichen gesetzt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38306>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_: Keine entsprechende Fehlermeldung, wenn die Website-ID in der Anfrage falsch ist
   * _Fehlerbehebung_: Jetzt wurde die entsprechende Fehlermeldung hinzugefügt, die angezeigt wird, wenn die Website-ID in der Anfrage falsch ist. Zuvor gab es keine Validierung, wenn die Website-ID in der Anfrage falsch war.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_: Das Produktbild geht verloren, nachdem ein vorhandenes geplantes Update gelöscht wurde, das sich nicht auf das Bild auswirkt
   * _Fehlerbehebung_: Produktbilder werden beim Löschen der Staging-Aktualisierung nicht entfernt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Cloud] Falscher Bundle-Produktpreis bei Verwendung mit Stufenpreisen
   * _Hinweis:_ zuvor bei der Berechnung bestimmter prozentualer Rabatte, auf 2 Dezimalpunkte aufgerundet, werden unterschiedliche Endpreise für die Warenkorb- und Produktlistenseite/Produktdetailseite generiert. Nachdem diese Fehlerbehebung angewendet wurde, ist der Endpreis für das Bundle-Produkt derselbe wie auf der Produktdetailseite, der Produktlistenseite und der Mini-Warenkorbseite.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38091>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: Regel für Katalog-Promotions funktioniert nicht mit dem Attribut quantity_and_stock_status
   * _Fehlerbehebung_: Das Attribut quantity_and_stock_status wird jetzt von der Regel für die Katalogbeförderung berücksichtigt, die zuvor beim Generieren eines neuen Produkts von der Admin-Seite aus nicht berücksichtigt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35627>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_: Spaltenwerte der Produktentität aktualisiert_at werden beim Aktualisieren des Preises über die REST-API nicht aktualisiert
   * _Fehlerbehebung_: Die Spalte „Zuletzt aktualisiert am“ des Administrators wird zum richtigen Zeitpunkt aktualisiert, während die vorhandenen Produkte über die REST-API aktualisiert werden. Zuvor wurde die Spalte „Zuletzt aktualisiert um“ nicht ordnungsgemäß aktualisiert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_: Nicht eindeutige Werte können über den Produktimport festgelegt werden
   * _Fehlerbehebung_: Das System erzwingt jetzt beim Produktimport korrekt die Beschränkung des eindeutigen Werts für eindeutige Produktattribute, sodass für dieses Attribut keine doppelten Werte vorhanden sind. Zuvor war es möglich, nicht eindeutige Werte für Produktattribute festzulegen, die über den Produktimport für eindeutige Werte konfiguriert wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38445>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: Produkte im Frontend verwenden Store-spezifische Daten, wenn der Einzelspeicher-Modus aktiviert ist
   * _Fehlerbehebung_: Wenn wir zuvor den Einzelspeichermodus für die standardmäßige Store-Ansicht aktiviert haben, wurden die Änderungen nicht in den Umfang auf Website-Ebene migriert. Wenn wir nach dieser Fehlerbehebung den Einzelspeichermodus aktivieren, werden die standardmäßigen speicheransichtsspezifischen Daten mit Website-spezifischen Daten synchronisiert und die möglichen Konflikte für Produkte und Kategorien werden aufgelöst.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_: „Standard-Sortieren nach“ kann in einer Kategorie nicht mit der REST-API festgelegt werden
   * _Hinweis korrigieren_: Aktualisieren Sie default_sort_by korrekt für eine Kategorie über eine REST-/SOAP-API-Anfrage.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Cloud] Der Händler hat Probleme mit der Anzahl der Wunschlisten
   * _Fehlerbehebung_: Wenn Sie ein Produkt in einem Geschäft zur Wunschliste hinzufügen, erhöht sich die Wunschlistenanzahl in anderen Geschäften, die im selben Browser geöffnet sind, nicht mehr. Wenn beide Stores im selben Browser geladen wurden, stieg die Anzahl der Wunschlisten auch im anderen Store.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: Kategorieseite am Frontend zeigt bei Verwendung des Bundle-Produkts leere Slots an
   * _Fehlerbehebung_: Bundle-Produkte, die im aktuellen Store-Kontext nicht verfügbar sind, werden nicht mehr indiziert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_: [Cloud] Problem des Zitats in der Architektur mit mehreren Websites
   * _Fehlerbehebung_: Zuvor konnten Multi-Website-Architekturen mit unterschiedlichen Währungen und Kundengruppen Rabatte nicht korrekt auf den Store anwenden. Nachdem diese Fehlerbehebung implementiert wurde, wird die Multi-Website-Architektur mit unterschiedlichen Preisnachlässen für Kundengruppen erfolgreich auf verschiedene Stores angewendet.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38506>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 Nicht erfasster TypFehler: dataRecord.slice beim Bearbeiten von Bundle-Produkten
   * _Hinweis beheben_: Beim Löschen einer Option aus dem Produktpaket tritt in der Browser-Konsole kein JavaScript-Fehler auf.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38505>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [Cloud] Bundle Falsche Produktpreise in Bestellbestätigung
   * _Fehlerbehebung_: Wenn eine andere Währung als die Basiswährung verwendet wurde, wird der richtige Betrag für die Bundle-Optionen in der Reihenfolge auf der Storefront angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: Fehler beim Hinzufügen von YouTube-Videos
   * _Fehlerbehebung_: Produktbilder und Videos werden im globalen Umfang konfiguriert. Da ein Produktvideo nicht in einem Umfang und nicht in einem anderen enthalten sein kann, wurde die Einstellung für den YouTube-API-Schlüssel auf den globalen Umfang festgelegt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [Cloud] URL-Aktualisierung nur für store_id=0
   * _Fehlerbehebung_: Der „URL-Pfad“ wird jetzt mit der richtigen Store-ID gespeichert. Zuvor war die Store-ID falsch, was dazu führte, dass beim Verschieben von Kategorien falsche URL-Pfade in der Datenbank verbleiben.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all ausgeführt und ein Fehler erstellt.
   * _Hinweis beheben_: Falsche Produktverknüpfungsdaten in REST-API-Aufrufen verursachen keine kritischen Fehler mehr.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [Cloud] Problem bei Mobilgeräten kann nur das PDP-Bild nicht zusammendrücken
   * _Fehlerbehebung_: Das System unterstützt jetzt die Pinch-to-Zoom-Funktion bei Produktdetailseitenbildern in der mobilen Ansicht auf Chrome, was das mobile Benutzererlebnis verbessert. Zuvor wurde das Bild in der mobilen Ansicht auf Chrome beim Doppeltippen nicht wie erwartet vergrößert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: Fehlende Beschriftung in LayeredNavigation mit Optionsname 0
   * _Hinweis beheben_: Das Problem wurde behoben, indem eine leere Werteprüfung für den Attributwert 0 übersprungen wurde. Zuvor wurde es als leer betrachtet und verursachte das Problem.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: Kunden sehen Preise von anderen Kundengruppen
   * _Hinweis_: Es wurde ein Problem behoben, bei dem Informationen zu Kundengruppen aufgrund des alten Wertes der X-Magento-Vary-Anfrage in einem falschen Segment gespeichert wurden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: Fehler beim Löschen von Paketoptionen
   * _Hinweis beheben_: Das System löscht jetzt die Bundle-Optionen korrekt, ohne einen Fehler auszulösen oder die Seite nicht mehr reagieren zu lassen. Zuvor führte der Versuch, Bundle-Optionen zu löschen, zu einem Fehler „Seite reagiert nicht“ und verhindert, dass das Produkt gespeichert wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_: [Cloud] Bilddatei ist nicht im New Relic-Fehlerprotokoll vorhanden
   * _Fehlerbehebung_: Das System synchronisiert jetzt benutzerdefinierte Platzhalterbilder mit dem lokalen Speicher, um sicherzustellen, dass sie bei der Verwendung von Remote-Speicher wie AWS S3 korrekt gerendert werden. Zuvor konnten benutzerdefinierte Platzhalterbilder bei der Verwendung des Remote-Speichers nicht gerendert werden, was zu einer fehlerhaften Bildanzeige und zu Fehlerprotokollen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_: [Cloud] Die GQL-Antwort der Produktmediensammlung ist nicht nach Bildposition sortiert
   * _Fehlerbehebung_: Das System sortiert jetzt Elemente in der Mediensammlung korrekt nach der Position in der GraphQL-Antwort, um eine genaue Anzeigereihenfolge zu gewährleisten. Zuvor wurden Elemente in der Mediensammlung nicht nach Position sortiert, was zu einer falschen Anzeigereihenfolge führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37671>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Cloud] Unterkategorieelemente werden nicht in der Widget-Bearbeitung im Admin-Backend angezeigt
   * _Hinweis beheben_: Die Kategoriestruktur auf der neuen Widget-Seite sollte keine Probleme mehr beim Laden von Kategorie(n) der Stufe 5+ aufweisen. Zuvor fehlten beim Laden des Baums über die Kategorie der Ebene 5 hinaus einige Kategorien.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>

### Katalog, Framework

* _ACP2E-2949_: [Cloud]Follow-up: Nicht übereinstimmender Datenvergleich bei der Überprüfung, ob Daten Änderungen aufweisen
   * _Hinweis korrigieren_: Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für ein beliebiges numerisches Datenfeld wie int/float/double). Das Flag „_hasDataChanges“ wird als „true“ Trigger und die Speicherfunktion wird aufgerufen. Außerdem werden die von der Zeichenfolge gekapselten Gleitkommazahlen nicht geprüft. Nach dieser Korrektur ruft die Speicherfunktion nur noch auf, wenn die Daten geändert werden. Der Datenwert für int/float/double-check mit dem Wert, der an die Funktion übergeben wird, und führt eine strikte Typübereinstimmung durch
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>

### Catalog, GraphQL

* _ACP2E-3090_: Umgang mit Kategoriefiltern in GraphQL: includeDirectChildrenOnly und category_uid
   * _Hinweis korrigieren_: Beim Filtern nach category_uid werden nur die direkt untergeordneten Kategorien abgerufen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [Cloud] GraphQL-Produktsortierung funktioniert nicht
   * _Fehlerbehebung_: Die Sortierung von GraphQL-Produkten nach mehreren Feldern, wenn die Felder in Variablen übergeben werden, funktioniert jetzt erwartungsgemäß.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>

### Katalog, Preise, Staging und Vorschau

* _ACP2E-2672_: [Cloud] Der API-Endpunkt für Sonderpreise gibt einen Fehler zurück, wenn eine große Anzahl von Produkten gleichzeitig aktualisiert wird
   * _Fehlerbehebung_: Jetzt erstellt die Special Price Bulk Update API für jeden Datumsbereich eine einzelne Kampagne anstelle mehrerer geplanter Aktualisierungen für jedes Produkt und jeden Datumsbereich. Außerdem unterstützt es gleichzeitige API-Anfragen für eine schnellere Verarbeitung einer großen Anzahl von SKUs.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/f89a447e>

### Katalog, Produkt

* _AC-7050_: Die Kategorieauswahlstruktur im bearbeiteten Produkt ist nicht in der gleichen Reihenfolge wie im Katalog->Kategorien
   * _Fehlerbehebung_: Der Kategorieauswahlbaum im Produktbearbeitungsabschnitt wird nun in der gleichen Reihenfolge wie unter Katalog->Kategorien angezeigt, was die Produktverwaltung in großen Katalogen erleichtert. Zuvor wurde die Kategoriestruktur im Produktbearbeitungsabschnitt in der Reihenfolge der Kategorienerstellung angezeigt, unabhängig von der Anzeigereihenfolge, die unter Katalog->Kategorien festgelegt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36101>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36104>

### Katalog, Suche

* _ACP2E-2757_: Produkte werden nicht in Kategorie und Suche angezeigt, aber direkte Links funktionieren
   * _Hinweis korrigieren_: Zuvor funktioniert das benutzerdefinierte Attribut „Ja/Nein“ mit dem _* „price attribute_code“ nicht bei der Indizierung. Nach dieser Korrektur funktioniert das benutzerdefinierte Attribut Ja/Nein erwartungsgemäß.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Cloud] Elastischer Suchfehler auf bestimmten Kategorieseiten
   * _Fix Hinweis_: Wenn wir das Konfigurationsticket bereits erwähnt haben und den Preis 0 für mehrere Produkte angeben, wird auf der Frontend-Kategorieseite eine Ausnahme ausgelöst. Nachdem diese Fehlerbehebung angewendet wurde, wenn mehrere Produktpreise 0 sind und wir die Kategorieseite im Frontend laden, wird keine Ausnahme ausgelöst und die Kategorieseite wird erfolgreich geladen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>

### Cloud

* _ACP2E-_: [Cloud] PHPSESSID ändert jede POST-Anfrage
   * _Fehlerbehebung_: PHPSESSID wird bei POST-Anfragen im Frontend-Bereich für einen angemeldeten Kunden nicht mehr neu generiert, wenn der L2-Redis-Cache aktiviert ist und der Kunde vom Backend aktualisiert wurde
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>

### Inhalt

* _AC-10539_: [Problem] Problem mit der Preisanzeige im Widget „Kürzlich angezeigt“
   * _Fehlerbehebung_: Das System zeigt jetzt im Widget „Kürzlich angezeigtes Produkt“ den Preis nicht vorrätiger einfacher Produkte korrekt an, wodurch die Konsistenz aller Widgets und Produktlistenseiten sichergestellt wird. Zuvor wurde der Preis für nicht vorrätige einfache Produkte aufgrund einer Bedingung in den Preisladevorlagen nicht im Widget „Kürzlich angezeigtes Produkt“ angezeigt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38167>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problem] Korrigieren Sie Tippfehler und Grammatik in der Datei acl.xsd
   * _Fehlerbehebung_: Das System korrigiert jetzt einen Tippfehler und Grammatikfehler in der Datei acl.xsd, wodurch die Klarheit und Genauigkeit der Dokumentation verbessert wird. Zuvor enthielt die Datei acl.xsd einen Tippfehler und eine falsche Grammatik, was möglicherweise zu Verwirrung führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38061>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: Bild des PageBuilder-Banners nicht in der Galerie sichtbar
   * _Fix Hinweis_: Das System zeigt jetzt korrekt Bannerbilder an, die in neu erstellte Ordner in der PageBuilder-Galerie hochgeladen wurden, sodass frühere Konsolenfehler vermieden werden. Vor dieser Fehlerbehebung waren Bannerbilder in der Galerie nicht sichtbar, wenn sie in einen neuen Ordner hochgeladen wurden, was einen Konsolenfehler verursachte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: „Area code not set“ nach der Aktualisierung auf 2.4.5-p8
   * _Fehlerbehebung_: Das System schließt jetzt den statischen Prozess der Inhaltsbereitstellung erfolgreich ab, wenn das Magento_CSP-Modul aktiviert ist und „dev/js/translate_strategy“ auf „embedded“ eingestellt ist, ohne den Fehler „Area Code Not Set“ auszulösen. Zuvor schlug der statische Prozess der Inhaltsbereitstellung unter diesen Bedingungen mit dem Fehler „Area Code Not Set“ fehl.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38845>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38922>
* _AC-9638_: [Problem] Problem beim Hochladen von Dateien im WYSIWYG-Editor auf der Produktseite
   * _Fehlerbehebung_: Das System zeigt jetzt die Ordnerstruktur korrekt an und ermöglicht das Hochladen von Bildern im WYSIWYG-Editor auf der Produktseite, selbst nachdem die Registerkarte „Bild und Videos“ zuerst erweitert wurde. Zuvor führte das Erweitern der Registerkarte „Bild und Videos“ zunächst dazu, dass die Ordnerstruktur nicht angezeigt wurde und eine Fehlermeldung angezeigt wurde, wenn versucht wurde, ein Bild im WYSIWYG-Editor hochzuladen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38026>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [On-Premise] Problem mit dynamischen Blöcken
   * _Hinweis:_ werden Widgets jetzt ordnungsgemäß in dynamischen Blöcken gerendert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_: [Cloud] Frontend wird aufgrund eines Problems in der Newsletter-Vorlage nicht geladen
   * _Fehlerbehebung_: Das Hinzufügen von Blöcken über den Seiteninhaltsabschnitt von CMS führt nicht mehr zu einer Ausnahme
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [Cloud] Investigate-Ausnahme im Protokoll gefunden: InvalidArgumentException: Klasse ist in vendor/magento/module-rule/Model/ConditionFactory.php nicht vorhanden
   * _Fehlerbehebung_: Wenn Sie eine Bedingung für die Inhaltseinstellungen von PageBuilder-Produkten entfernen, wird keine Ausnahme mehr in den Protokolldateien aufgezeichnet. Zuvor führte das Entfernen einer Bedingung für die Inhaltseinstellungen von PageBuilder-Produkten dazu, dass eine kritische Ausnahme in den Protokollen aufgezeichnet wurde, obwohl dies keine Probleme im Frontend verursachte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: Wechseln zum Einzelspeichermodus - Globale Inhalte werden nicht mehr angezeigt
   * _Fehlerbehebung_: Das System synchronisiert jetzt Design-Konfigurationen für Store-Ansichten mit Website-Design-Konfigurationen, wenn es den Single-Store-Modus aktiviert, um sicherzustellen, dass Inhaltsaktualisierungen im Frontend sichtbar sind. Zuvor wurde durch den Wechsel zum Einzelspeichermodus verhindert, dass Inhaltsaktualisierungen in der Storefront widergespiegelt werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: Page Builder ersetzt das Bild, wenn versucht wird, Link- und andere Nutzungsfehler hinzuzufügen.
   * _Fehlerbehebung_: Wenn Sie jetzt auf ein Bild klicken, werden Links im WYSIWYG-Editor im Textelement von Page Builder ordnungsgemäß in das Bild geladen, und das Dialogfeld für die Link-Konfiguration wird angezeigt. Auch das Hinzufügen eines Links zu einem Bild im Editor funktioniert jetzt ordnungsgemäß. Zuvor wurde das Bild durch einen Link ersetzt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: Die alte Mediensammlung kann keine Bilder rendern, wenn ein 0-Byte-Bild im Verzeichnis platziert wird
   * _Fehlerbehebung_: Das System verarbeitet jetzt 0-Byte-Bilder in der Mediensammlung, ohne die Funktionalität zu beeinträchtigen, sodass andere Bilder im Verzeichnis wie erwartet angezeigt und ausgewählt werden können. Zuvor verhinderte das Vorhandensein eines 0-Byte-Bildes in der Mediensammlung, dass alle Bilder im Verzeichnis angezeigt oder ausgewählt wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: Fehler von Page Builder beim Bearbeiten des CMS-Blocks
   * _Fehlerbehebung_: Das System speichert jetzt mit Page Builder korrekt im Administratorbereich vorgenommene Änderungen, ohne den Fehler „Page Builder wurde 5 Sekunden lang gerendert, ohne Sperren freizugeben.“ In der Browser-Konsole. Zuvor trat dieser Fehler beim Versuch auf, Änderungen zu speichern, wodurch die erfolgreiche Aktualisierung des Inhalts verhindert wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [CLOUD] Keine Schaltflächen für Checkout oder Warenkorb bearbeiten im Warenkorbabschnitt
   * _Fehlerbehebung_: Das Bundle-Produkt wird jetzt fehlerfrei über Widgets zum Warenkorb hinzugefügt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3127_: imagecreatetruecolor(): Der #2 ($height) muss größer als 0 sein. Bestimmtes Bild kann nicht hochgeladen werden
   * _Hinweis_: Das Problem, das beim Hochladen von Bildern mit einer Höhe von 0 über die Mediensammlung zu Fehlern in der Admin-Instanz führte, wurde behoben und die Asset-Synchronisierung mithilfe des Befehls sync wurde erfolgreich durchgeführt. Zuvor kann das Bild nicht über die Mediensammlung hochladen, und der Synchronisierungsbefehl schlägt auch fehl, wenn sich ein bestimmtes Bild in der Galerie befindet.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from steht im Konflikt mit der Google Maps-API
   * _Fehlerbehebung_: Google Maps werden jetzt im PageBuilder-Editor ordnungsgemäß gerendert. Zuvor verhinderte ein JavaScript-Fehler, dass Google Maps korrekt gerendert wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>

### Kunde/Kunden

* _AC-12162_: Frontend - Die Validierung des Geburtsdatums schlägt auf der Kundenerstellungsseite fehl
   * _Fix Hinweis_: Stellen Sie sicher, dass die gesamte Validierung nach dem Upgrade von moment.js Systemabhängigkeit auf die neueste Nebenversion funktionieren sollte
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>

### Framework

* _AC-10654_: Frage/Problem mit V1/customers/password-Endpunkt
   * _Fehlerbehebung_: Bei der Verarbeitung von Passwortänderungsanfragen über die API hält sich das System jetzt an die in der Verwaltungs-Benutzeroberfläche festgelegten Einschränkungen, um einen potenziellen Missbrauch der Passwortrücksetzfunktion zu verhindern. Zuvor konnte die API Passwortänderungsanfragen außerhalb der in der Verwaltungs-Benutzeroberfläche definierten Regeln verarbeiten, was möglicherweise einen konstanten Stream von Zurücksetzungs-E-Mails ermöglichte, wenn gültige E-Mails bekannt waren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38238>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_:
   * _Fix Hinweis_: Aktualisieren der League/flysystem Composer-Abhängigkeiten auf die neueste Version
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _GitHub-Code-Beitrag_: Aktualisieren Sie die Abhängigkeiten von 2.x League/flysystem Composer auf die neueste Version 3.x
* _AC-10838_: Indizierungsprozess für Katalogsuchindex-Fehler
   * _Fix Hinweis_: Das System führt nun den Neuindizierungsbefehl erfolgreich aus, ohne dass Fehler auftreten, unabhängig von der mit PHP kompilierten libxml-Version. Zuvor führte die Ausführung des Befehls re-index zu einem Fehler „Catalog Search index process error during indexation process“, wenn PHP mit bestimmten Versionen von libxml kompiliert wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38254>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: Filter „created_at“, „status“ und „grand_total“ wurden zur Abfrage von Kundenaufträgen hinzugefügt und Fehler bei mehreren Filtern behoben
   * _Fehlerbehebung_: Das System unterstützt jetzt die Verwendung der Filter „created_at“, „status“ und „grand_total“ in Kundenauftragsabfragen und hat ein Problem behoben, bei dem mehrere Filter nicht korrekt angewendet wurden. Zuvor hat das System diese Filter nicht unterstützt und würde nicht alle Filter anwenden, wenn mehr als einer in einer Abfrage verwendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38392>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36949>
* _AC-10971_: https://github.com/magento/magento2/issues/38415
   * _Fix Hinweis_: PHP 8.2/8.3, nur eine Abhängigkeit schlägt derzeit fehl: league/flysystem
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub-Code-Beitrag_: Das System unterstützt nun PHP 8.2/8.3, indem es das league/flysystem-Paket auf Version 3.0.20 aktualisiert, um sicherzustellen, dass keine PHP-Verknüpfungsfehler auftreten. Zuvor führte das Ausführen von PHP-Dateien durch den PHP-Linter mit PHP 8.3 zu Linting-Fehlern im League/flysystem-Paket.
* _AC-10991_: zufällig mit Abfragen aus verwandten/Upsell-/Crosssell-Blöcken und Preisindizierung überflutet werden
   * _Fehlerbehebung_: Das System optimiert jetzt Abfragen aus verwandten, Upsell- und Crosssell-Blöcken, verbessert die Leistung und verhindert, dass die Site aufgrund übermäßiger Abfragen abstürzt. Zuvor konnte das System mit Abfragen aus diesen Blöcken überlastet werden, was zu erheblichen Verzögerungen führte und möglicherweise die Site lahmlegte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36667>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Exception: Warning: Try to access array offset in… -> Calendar.php since upgrade to ICU 74.1 (PHP Intl)
   * _Fehlerbehebung_: Commerce protokolliert die folgende Ausnahme nicht mehr in „exception.log“, wenn ein Käufer oder Händler die Storefront oder den Administrator besucht: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38214>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [Problem] Beheben von Problemen mit Kundendaten, wenn das Formular ein Element mit dem Namen &quot;`method`&quot; enthält
   * _Fehlerbehebung_: Das System identifiziert jetzt das Attribut „method“ in Formularübermittlungen korrekt, auch wenn ein Element mit dem Namen „method“ im Formular vorhanden ist. Dadurch wird eine präzise Verarbeitung der Kundendaten gewährleistet. Wenn ein Formularelement zuvor „Methode“ genannt wurde, würde dies die Identifizierung des Attributs „Methode“ bei Formularübermittlungen beeinträchtigen, was zu potenziellen Problemen bei der Verarbeitung von Kundendaten führen würde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38484>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [Problem] Fix PHPDocs for \Magento\Framework\Data\Collection::getItemById
   * _Fehlerbehebung_: Die PHPDocs für die Methode \Magento\Framework\Data\Collection::getItemById wurden aktualisiert, sodass sie null als möglichen Rückgabetyp enthalten, wodurch Probleme mit statischen Analyse-Tools behoben werden. Zuvor wurde in den PHPDocs der Methode nicht null als möglicher Rückgabetyp angegeben, was zu Warnungen oder Fehlern bei der statischen Analyse führte, wenn die Methode in bedingten Anweisungen verwendet wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38485>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38439>
* _AC-11651_: Magento versucht, die schreibgeschützte Eigenschaft in der __wakeup-Methode von LoggerProxy zu ändern
   * _Fehlerbehebung_: Das System ermöglicht jetzt die Änderung von zuvor schreibgeschützten Eigenschaften in der __wakeup-Methode von LoggerProxy, wodurch ein reibungsloser Betrieb gewährleistet wird, ohne dass Benutzer gezwungen werden, eine Problemumgehung zu verwenden. Zuvor hatte der Versuch, den Wert einer schreibgeschützten Eigenschaft in der WakeUp-Methode __ LoggerProxy neu zuzuweisen, Probleme verursacht.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38526>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_:
   * _Fix Hinweis_: Untersuchen Sie die neuesten Versionen von php-amqplib/php-amqplib
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub-Code-Beitrag_: Die neueste Version php-amqplib/php-amqplib wurde aktualisiert:^3.x
* _AC-11681_: [Problem] AC-2039 AC-1667 Upgrade TinyMCE Referenzen
   * _Fix Hinweis_: Die tinymce-neueste Version in composer.json wurde aktualisiert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38533>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker funktioniert nicht in mehreren Threads
   * _Hinweis beheben_: Das System unterstützt jetzt Process Fork für die MView-Indizierung, wodurch Fehler bei der Indexerausführung bei der Arbeit mit mehreren Threads verhindert werden. Zuvor führte das Ausführen von ChangelogBatchWalker auf mehreren Threads zum Löschen von Tabellen, die von anderen Threads verwendet wurden, was einen Fehler während der Indexerausführung verursachte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38246>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [Problem] Umbenennen einer falsch benannten Variablen
   * _Fehlerbehebung_: Das System benennt nun die Variable, die den Betrag an Geld enthält, der noch zurückerstattet werden kann, korrekt, um Verwirrung beim Debugging zu vermeiden. Zuvor wurde diese Variable fälschlicherweise als totalRefund bezeichnet, was zu Missverständnissen für Entwickler führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38609>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36205>
* _AC-11808_:
   * _Fehlerbehebung_: Untersuchen und Aktualisieren der Adobe Commerce Core-Abhängigkeitsliste
   * _GitHub-Code-Beitrag_: Adobe Commerce Core-Abhängigkeitsliste muss aktualisiert werden 
* _AC-11819_: Der integrierte FPC-Cache ist in Version 2.4.7 für einige Konfigurationen fehlerhaft
   * _Fehlerbehebung_: Das System speichert jetzt korrekt Seiten zwischen, wenn der Parameter MAGE_RUN_CODE festgelegt ist, was eine optimale Leistung gewährleistet. Zuvor wurden Seiten unter diesen Bedingungen nicht zwischengespeichert, was zu potenziellen Leistungsproblemen führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38626>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_: [Problem] Behebung von Inkonsistenzen bei der Ausnahmebehandlung zwischen Entwickler- und Produktionsmodus
   * _Fehlerbehebung_: Das System verarbeitet jetzt durchgängig Ausnahmen zwischen dem Entwickler- und dem Produktionsmodus und verhindert so eine unerwartete Weiterleitung zur Anmeldeseite, wenn eine Ausnahme ausgelöst wird. Zuvor konnte eine Inkonsistenz bei der Ausnahmebehandlung zu einer Umleitung zur Anmeldeseite im Produktionsmodus führen, anstatt die Ausnahmemeldung anzuzeigen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38639>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37712>
* _AC-11852_: „PayPal-Konto“-Übersetzung in token_list.phtml ersetzen
   * _Fehlerbehebung_: Der Abschnitt für Tokenizable-Konto-Zahlungsmethoden wird jetzt auf der Seite „Gespeicherte Zahlungsmethoden“ als „Konto“ anstelle von „PayPal-Konto“ gekennzeichnet, wodurch er besser für seine Funktion repräsentativ ist. Zuvor wurde dieser Abschnitt speziell als „PayPal-Konto“ gekennzeichnet, was irreführend war, wenn andere Token-fähige Konto-Zahlungsmethoden hinzugefügt wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35622>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37959>
* _AC-11905_: [Problem] Statische Inhaltsbereitstellung - Typfehler
   * _Fehlerbehebung_: Das System verarbeitet jetzt leere LESS-Dateien während der Bereitstellung statischer Inhalte korrekt und zeigt die Fehlermeldung „LESS-Datei ist leer“ an. Zuvor wurde ein Fehler vom Typ „Falsch“ ausgelöst, wenn während der Bereitstellung eine leere LESS-Datei auftrat.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38682>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38683>
* _AC-11911_:
   * _Fehlerbehebung_: jQuery/fileuploader css cleanup nach der Migration zur Uppy-Bibliothek
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub-Code-_: jQuery/fileUploader-Bibliothek wurde entfernt, da sie in die Uppy-Bibliothek migriert wurde
* _AC-12002_: [Problem] [Ansicht] Zusätzlicher Platz im Link- und Skript-Tag entfernt
   * _Fehlerbehebung_: Das System stellt jetzt sicher, dass die Link- und Skript-Tags keine zusätzlichen Leerzeichen enthalten, was für saubereren und effizienteren Code sorgt. Zuvor konnten zwischen Attributen in den Link- und Skript-Tags doppelte Leerzeichen gefunden werden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/32920>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32919>
* _AC-12015_:
   * _Fehlerbehebung_: ExtJs-Ordnerbereinigung nach der Migration zur jsTree-Bibliothek
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub-Code-_: ExtJs-Ordner wurde entfernt, da die zugehörige Funktion zu jsTree migriert wurde.
* _AC-12022_:
   * _Fehlerbehebung_: Aktualisieren der monolog/monolog-Systemabhängigkeit auf die neueste Hauptversion
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub-Code-_: Das System wurde aktualisiert, um die neueste Hauptversion der Bibliothek „monolog/monolog:^3.x“ zu verwenden, wodurch Kompatibilität und verbesserte Leistung gewährleistet sind. Zuvor verwendete das System eine veraltete Version der Bibliothek „monolog/monolog“, was zu potenziellen Problemen und Einschränkungen hätte führen können.
* _AC-12023_:
   * _Fehlerbehebung_: Aktualisieren Sie die Abhängigkeit von wikimedia/less.php auf die neueste Hauptversion
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub-Code-_: Das System wurde aktualisiert, um die neueste Hauptversion 5.x der Bibliothek &quot;wikimedia/less.php&quot; zu verwenden, wodurch Kompatibilität und aktuelle Funktionen gewährleistet sind. Zuvor verwendete das System eine veraltete Version der Bibliothek, was zu Sicherheitsproblemen hätte führen können.
* _AC-12024_:
   * _Fehlerbehebung_: Aktualisieren von jquery/validate library-Abhängigkeiten auf die neueste Nebenversion
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub-Code-Beitrag_: Aktualisieren von jquery/validate-Bibliotheksabhängigkeiten auf die neueste Nebenversion 1.20.0
* _AC-12025_:
   * _Hinweis:_ Sie die Systemabhängigkeit von moment.js auf die neueste Nebenversion
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub-Code-Beitrag_: Aktualisieren Sie die Systemabhängigkeit von moment.js auf die neueste Nebenversion 2.30.1
* _AC-12267_:
   * _Fix Hinweis_: Unterstützt Verbindungswiederholungen für Redis-Sitzung und kompatibel mit colinmollenhour/php-redis-session-abstract v2.0.0
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub-Code-Beitrag_: Aktualisierte neueste Version von colinmollenhour/php-redis-session-abstract v2.0.0, kompatibel mit Adobe Commerce
* _AC-12268_:
   * _Fix Hinweis_: Aktualisieren Sie die Abhängigkeiten von League/Flysystem Composer auf die neueste Version.
   * _GitHub-Code-Beitrag_: Aktualisieren Sie die Abhängigkeiten von 2.x League/flysystem Composer auf die neueste Version 3.x
* _AC-12594_: [Problem] Verwenden Sie die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration.
   * _Fehlerbehebung_: Das System verwendet jetzt die kompilierte Konfiguration für generierte Daten anstelle der allgemeinen Konfiguration, wodurch die Netzwerkübertragung und der Overhead von Daten, die von einer bestimmten Version des Codes abhängen, reduziert werden. Diese Änderung verhindert das Überschreiben des Caches in freigegebenen Instanzen beim Austausch von Containern, was zu verbesserter Stabilität und reduzierten Ausfallzeiten führt. Zuvor verwendeten bestimmte Kernklassen gemeinsame Konfigurationstypen, was aufgrund von Unterschieden in den Codeversionen über mehrere Server hinweg zu Cache-Überschreibungen oder Anwendungsausfällen führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38785>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problem] Verweise auf Dateien aus ExtJS entfernen, die in e1ccdb entfernt wurden…
   * _Fix Hinweis_: Das System entfernt jetzt Verweise auf Dateien aus ExtJS, die zuvor entfernt wurden, wodurch Fehler in der Browser-Konsole und der Systemprotokolldatei vermieden werden. Zuvor verursachten diese Verweise Fehler, da die referenzierten Dateien nicht vorhanden waren.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38960>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38951>
* _AC-12715_:
   * _Fix Hinweis_: Aktualisieren der Laminas Composer-Abhängigkeiten auf die neueste Version
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _GitHub-Code-_: Das System unterstützt jetzt die neuesten Versionen von Laminas Composer-Abhängigkeiten:
laminas/laminas-serviceManager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
Gewährleistung der Kompatibilität und aktuellen Funktionalität. Zuvor konnte eine Aktualisierung auf die neuesten Versionen dieser Abhängigkeiten zu Problemen mit der Abwärtskompatibilität und Testfehlern führen.
* _AC-12778_: [Problem] Kleinere Bereinigung: Fehlerhafte Verwendung von sprintf behoben, es braucht nur 2 Platzhalter hier und w…
   * _Fehlerbehebung_: Das System verwendet nun die sprintf-Funktion korrekt mit der entsprechenden Anzahl von Platzhaltern, was die Code-Sauberkeit und -Konsistenz verbessert. Zuvor wurde die Sprint-Funktion fälschlicherweise mit einem zusätzlichen Argument verwendet, was zwar keine größeren Probleme verursachte, aber nicht die richtige Verwendung war.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39062>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38628>
* _AC-12866_:
   * _Fehlerbehebung_: Veraltete Funktionen entfernen - PhpUnit10-Integrationstests
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub-Code-Beitrag_: Auflösung der veralteten PHPUnit-Dateien
* _AC-12868_:
   * _Fehlerbehebung_: Veraltete Funktionen entfernen - PhpUnit10 WebAPI-Tests
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub-Code-Beitrag_: Auflösung der veralteten PHPUnit-Dateien
* _AC-12869_: [Problem] Behebt den Verweis falscher Klassen in Magento-Modulen.
   * _Fehlerbehebung_: Das System verweist jetzt korrekt auf Klassen in -Modulen, wodurch ein reibungsloserer Betrieb gewährleistet und Abstürze aufgrund nicht vorhandener Klassen verhindert werden. Dazu gehören eine Fehlerbehebung im Indexer- und Creditmemo-Modul sowie die Implementierung der HttpGetActionInterface-Klasse in der PrintAction-Klasse. Zuvor führten falsche Klassenverweise zu Fehlern und potenziellen Systemabstürzen, und bestimmte Funktionen, wie der Dateiname für CreditMemo-PDF-Dateien und die Neuindizierung von Aktien, funktionierten nicht wie erwartet.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/39126>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37784>
* _AC-6754_: Tippfehler in einer js-Datei.
   * _Fehlerbehebung_: Das System verwendet jetzt korrekt den Begriff „Abonnenten“ in der JavaScript-Datei, um sicherzustellen, dass die zugehörigen Funktionen ordnungsgemäß funktionieren. Zuvor führte ein typografischer Fehler in der JavaScript-Datei zur falschen Verwendung des Begriffs „Abonnenten“.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36163>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36171>
* _AC-8353_: [Problem] Entfernen Sie verbotenes `@author` Tag
   * _Fix-Hinweis_: Das System hält sich jetzt an die Kodierungsstandards, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um saubereren und standardisierten Code sicherzustellen. Zuvor war das `@author`-Tag in einigen Modulen vorhanden, was gegen die etablierten Codierungsstandards verstieß.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37253>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Problem] Entfernen eines verbotenen `@author`-Tags aus `Magento_Customer` (Teil 2)
   * _Fix-Hinweis_: Das System hält sich jetzt an den Kodierungsstandard, indem es das verbotene `@author`-Tag aus bestimmten Modulen entfernt, um saubereren und standardisierten Code sicherzustellen. Zuvor war das `@author`-Tag in einigen Modulen vorhanden, was gegen die etablierten Codierungsstandards verstieß.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37250>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: Leerzeichen in editorconfig Syntax bricht Regel für [{composer,auth}.json]
   * _Hinweis beheben_: Nach der Behebung eines Syntaxfehlers in editorconfig wendet das System jetzt korrekt einen Einzug mit vier Leerzeichen auf die Dateien composer und auth.json an. Aufgrund eines Leerzeichens in der EditorConfig-Syntax wurden diese Dateien zuvor falsch mit einem Einzug aus zwei Leerzeichen formatiert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37394>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37395>
* _AC-8984_: [Problem] Fügt der Ausgabe bestimmter Setup-Befehlszeilenbefehle einige weitere Farben hinzu
   * _Fehlerbehebung_: Das System fügt jetzt der Ausgabe bestimmter Setup-Befehlszeilenschnittstellen-Befehle mehr Farben hinzu, was die Lesbarkeit und das Benutzererlebnis verbessert. Bisher war die Ausgabe dieser Befehle aufgrund fehlender Farbdifferenzierung schwieriger zu lesen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/29335>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: Beim Upgrade von Magento wird „general/region/state_required“ zurückgesetzt, wenn ein neues Land mit dem erforderlichen Bundesland bzw. der erforderlichen Region hinzugefügt wird.
   * _Fehlerbehebung_: Das System fügt das geänderte Land jetzt nur noch dann zur Konfiguration „general/region/state_required“ hinzu, wenn ein neues Land mit den erforderlichen Status hinzugefügt wird. Dadurch wird jede Unterbrechung des benutzerdefinierten Codes verhindert, der davon ausgeht, dass die Region deaktiviert ist. Zuvor würde das Hinzufügen eines neuen Landes mit erforderlichen Status die Konfiguration „general/region/state_required“ auf Standardländer mit einem erforderlichen Status zurücksetzen und möglicherweise den Shop zerstören.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37796>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: Unterschied in weniger Kompilierung zwischen php &amp; nodejs Bibliothek (grunt) mit komplizierten `calc` Ausdrücken
   * _Fix Hinweis_: Korrigieren Sie den Unterschied in weniger Kompilierung zwischen php und nodejs Bibliothek (grunt) nach dem Update wikimedia/less.php:^5.x
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37841>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: Fehler „Basistabelle oder Ansicht nicht gefunden“ tritt auf, wenn eine partielle Indizierung ausgeführt wird
   * _Fix Hinweis_: Die partielle Neuindizierung funktioniert jetzt korrekt mit einem großen Änderungsprotokoll im Falle einer sekundären DB-Verbindung
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: Probleme nach der Aktualisierung von MariaDB auf 10.5.1 oder höher
   * _Fix Hinweis_: Es wurde ein Problem behoben, bei dem Datums-/Uhrzeitwerte in einer DB nach dem MySQL-Upgrade :00: 0000-00-00 00 00 konvertiert wurden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Nicht übereinstimmende Typen beim Datenvergleich bei der Überprüfung, ob Daten Änderungen aufweisen
   * _Hinweis korrigieren_: Zuvor wurde das Speicherobjekt jedes Mal ohne Datenänderungen aufgerufen (für ein beliebiges numerisches Datenfeld wie int/float/double). Das Flag „_hasDataChanges“ wird als „true“ Trigger und die Speicherfunktion wird aufgerufen. Nach dieser Korrektur ruft die Speicherfunktion nur noch auf, wenn die Daten geändert werden. Der Datenwert für int/float/double-check mit dem Wert, der an die Funktion übergeben wird, führt eine strikte Typübereinstimmung durch.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [Cloud]-Import kann nicht mit Verzeichnis-Var verwendet werden
   * _Fehlerbehebung_: Das Produkt kann unabhängig vom Dateinamen erfolgreich importiert werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: Auf dem iPad mini werden das Menü und die Kopfzeile als Mobilgerät geladen. Stattdessen sollten sie als Desktop geladen werden.
   * _Fehlerbehebung_: Das System behandelt Geräte mit einer Breite von 768 Pixel jetzt als Desktop, um sicherzustellen, dass das Menü und die Kopfzeile korrekt geladen werden. Zuvor wurden Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt, wodurch das Menü und die Kopfzeile in einer Mobilansicht geladen wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>

### Framework, GraphQL

* _AC-7976_: [Problem] Einführung der Unterstützung benutzerdefinierter Skalartypen für GraphQL-Schemata
   * _Fehlerbehebung_: Das System unterstützt jetzt benutzerdefinierte Skalartypen für GraphQL-Schemata, sodass Entwickelnde benutzerdefinierte Skalartypen und Implementierungen definieren können. Diese Funktion kann besonders nützlich sein, um Werte auszudrücken, die möglicherweise einer Validierung bedürfen, z. B. HTML, E-Mails, URLs, Daten usw., und für komplexere Fälle wie EAV-Attribute. Zuvor unterstützte das System nicht die Verarbeitung von benutzerdefinierten Skalartypen in GraphQL.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/36877>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL

* _AC-11729_: Magento_GraphQL führt die Header-Verarbeitung auch dann aus, wenn der Header-Wert die Validierung nicht besteht
   * _Fehlerbehebung_: Das System stellt jetzt sicher, dass die Kopfzeilenverarbeitung nur einmal und nur dann ausgeführt wird, wenn der Kopfzeilenwert die Validierung besteht, was die Sicherheit erhöht und potenzielle Sicherheitslücken verhindert. Zuvor wurde die Header-Verarbeitung auch dann ausgeführt, wenn der Header-Wert die Validierung nicht bestanden hat, was zu potenziellen Sicherheitslücken und unerwartetem Verhalten aufgrund der doppelten Verarbeitung von Header-Werten führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: Die physischen Geschenkkartenoptionen haben nicht die richtige Sortierreihenfolge
   * _Fehlerbehebung_: Das System sortiert jetzt bei der Abfrage über GraphQL die Optionen physischer Geschenkkartenprodukte korrekt, was eine konsistente Darstellung mit dem Luma-Design gewährleistet. Zuvor war die Sortierreihenfolge gemäß dem Luma-Design falsch, was zu einer falschen Anzeige und Sortierung von Optionen wie Absendername, Empfängername und Betrag führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: Der Cache des [GraphQL]-Resolvers wird beim Erstellen/Bearbeiten/Verschieben/Löschen eines Staging-Updates ungültig
   * _Fehlerbehebung_: Das System stellt jetzt sicher, dass der Resolver-Cache nicht beim Erstellen, Bearbeiten, Verschieben oder Löschen eines Staging-Updates ungültig wird, sondern nur, wenn das Staging-Update auf die Entität angewendet wird. Zuvor wurde der Resolver-Cache vorzeitig invalidiert, noch bevor die Staging-Aktualisierung angewendet wurde, was zu unnötigen Cache-Invalidierungen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: Fastly-Cache nicht für die Aktualisierung des Inhalts-Staging gelöscht
   * _Fehlerbehebung_: Jetzt wird GraphQL mit PageBuilder-Inhaltsantwort-Cache ungültig, wenn die PageBuilder-Inhaltsentitäten aktualisiert werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Deaktivieren der mehrschichtigen Navigation - entfernt die Aggregation nicht aus GraphQL
   * _Hinweis:_ Problem wurde behoben, nachdem die Prüfung beim Anfordern einer Produktsuche mit Kategorieaggregationen über eine GraphQL-Abfrage über die Admin-Konfigurationseinstellung „Katalog > Mehrschichtige Navigation > Kategoriefilter anzeigen“ angewendet wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: GraphQL Products-Aufruf, der den Preisfilter {from:„0“} enthält, gibt kein Ergebnis zurück
   * _Fehlerbehebung_: Zuvor gab GraphQL-Produkte, die mit dem Filter nach Nullpreisen suchten, aufgrund einer ausgelösten Ausnahme überhaupt keine Ergebnisse zurück. Jetzt gibt die Suche die erwarteten Ergebnisse zurück.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-3128_: [Cloud] Beschädigter GraphQL-Aufruf für getPurchaseOrder mit Knotenanführungszeichen
   * _Hinweis beheben_: Der GraphQL-Aufruf für Bestellungen kann die Aufgabe ausführen, ohne dass interne Server-Fehler auftreten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [Cloud] Konfigurierbare Produkte werden nicht auf der Produktions-Site angezeigt, wenn das Produkt nicht in „Alle Store-Ansichten“ aktiviert ist
   * _Fehlerbehebung_: Das System zeigt jetzt konfigurierbare Produkte auf der Website korrekt an, auch wenn das Produkt nicht in „Alle Store-Ansichten“ aktiviert ist, sondern in bestimmten Store-Ansichtsbereichen aktiviert ist.
Wenn ein Produkt zuvor in „Alle Store-Ansichten“ deaktiviert und nur in bestimmten Store-Ansichtsbereichen aktiviert wurde, werden die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt, was dazu führt, dass das Produkt nicht richtig angezeigt wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: GraphQL [Cloud]-Produkte mit Fehler, wenn dasselbe einfache Produkt mehreren konfigurierbaren Produkten zugewiesen wurde
   * _Fehlerbehebung_: Zuvor gibt grapQL mit separaten konfigurierbaren Produkten mit demselben einfachen Produkt einen Fehler zurück. Nachdem diese Fehlerbehebung angewendet wurde, gibt GraphQL ohne Fehler Ergebnisse für verschiedene konfigurierbare Produkte mit demselben einfachen Produkt zurück.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3253_: GraphQL-WarenkorbelementeV2-Paginierung funktioniert nicht ordnungsgemäß
   * _Hinweis beheben_: Das Problem wurde behoben, indem der richtige Wert für das aktuelle Seitenargument in der Sammlungsabfrage übergeben wurde. Zuvor wurde der falsche Wert übergeben, um die aktuelle Seite festzulegen, was das Problem verursachte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>

### GraphQL, Inventar/MSI

* _ACP2E-2607_: Die MergeCart-Mutation löst eine Ausnahme aus, wenn Quell- und Zielkarten dieselben Bundle-Elemente enthalten
   * _Notiz korrigieren_: &#39;-
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Inventar/MSI, Leistung

* _ACP2E-1716_: Standort nach Upgrade nicht verfügbar
   * _Fehlerbehebung_: Die Leistung beim Abrufen von Bundle-Produkten über GraphQL wurde verbessert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, Leistung

* _AC-9569_: [GraphQL Resolver] Kundenresolverdaten werden nicht für den Import ungültig gemacht
   * _Fehlerbehebung_: Der Cache des GraphQL-Kundenauflösers wird jetzt wie erwartet ungültig, wenn ein Kunde durch Importe bearbeitet oder gelöscht wird. Zuvor wurde der Cache nicht ungültig gemacht, und Kundendaten konnten während des Imports bearbeitet oder gelöscht werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Suche

* _ACP2E-_: Sortieren von GraphQL-Produktlisten nach mehreren Parametern funktioniert nicht
   * _Fehlerbehebung_: Die Produktsortierung nach mehreren Feldern in GraphQL funktioniert jetzt wie in der Dokumentation beschrieben
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>

### Import/Export

* _AC-12172_: Problem beim Produktimport bei Bereitstellung mit benutzerdefiniertem Optionstyp: Datei (Erstelltes Produkt enthält keinen Preis für benutzerdefinierte Option und zeigt nur die erste angegebene Dateityperweiterung an)
   * _Fehlerbehebung_: Das System importiert Produktdaten jetzt korrekt mit benutzerdefinierten Optionen vom Typ „Datei“, um sicherzustellen, dass alle bereitgestellten Dateierweiterungen angezeigt werden und der Preis für die benutzerdefinierte Option enthalten ist. Wenn beim Produktimport zuvor eine benutzerdefinierte Option des Typs „Datei“ mit mehr als einer Dateierweiterung bereitgestellt wurde, wurde nur die erste Erweiterung angezeigt und der Preis für die benutzerdefinierte Option fehlte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38805>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: Falsche Ausführungszeit für Importvorgang im Importverlaufsraster
   * _Fehlerbehebung_: Die Ausführungszeit des Importberichts wird korrekt unabhängig vom Admin-Gebietsschema angezeigt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: Doppelte Kunden werden mit derselben E-Mail-Adresse beim Import erstellt
   * _Fehlerbehebung_: Importieren Sie den Kunden, während die Kontofreigabe auf „Global“ eingestellt ist, wird der importierte Kunde, der im System vorhanden ist, aktualisiert.
Zuvor importierter Kunde wurde dupliziert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_: Import von Produkten hinzufügen/aktualisieren, die anpassbare Optionen duplizieren
   * _Hinweis zur Fehlerbehebung_: Das Problem wurde behoben, indem den Produktoptionen beim CSV-Import der richtige Store zugewiesen wurde.
Zuvor dem Admin-Store anstelle des entsprechenden Stores zugewiesen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: Datum „created_at“ des Kunden wurde beim Export nicht in die Speicherzeitzone konvertiert
   * _Fehlerbehebung_: Ein Datumswert der Spalte „created_at“ wird basierend auf der Zeitzone des Speichers im CSV-Abschnitt für den Kundenexport in das richtige Datumsformat konvertiert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Cloud] Fehler beim Überprüfen der Daten in Importdaten mithilfe von CSV
   * _Hinweis korrigieren_: Beim Überprüfen der Daten während des CSV-Imports tritt kein Fehler auf. Zuvor war die angezeigte Fehlermeldung: „Wir können keinen Kunden finden, der diese E-Mail- und Website-Code in Zeile(n): 1 abgleicht“, wenn die Daten im Importabschnitt mithilfe von CSV von der Administratorin bzw. dem Administrator überprüft werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/8459b17d>

### Installieren und Verwalten

* _ACP2E-2102_: Keine Export-VCL für die Schaltfläche „Lack 7“ im Admin-Bedienfeld
   * _Fix Hinweis_: Die Schaltfläche „VCL für Lack 7 exportieren“ wurde dem Admin-Bedienfeld hinzugefügt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventar/MSI

* _AC-11593_: Google-Google-API-Schlüssel funktioniert nicht beim Hinzufügen von Zuordnungen mit Attributen
   * _Fehlerbehebung_: Das System unterstützt jetzt die neueste Google Maps-API-Version 3.56, sodass Benutzende erfolgreich einen Zuordnungs-Inhaltsblock aus dem PageBuilder-Menü zum Staging hinzufügen können, ohne auf Fehler zu stoßen. Zuvor konnten Benutzende aufgrund von Kompatibilitätsproblemen mit der Google Maps API-Version keinen Zuordnungs-Inhaltsblock hinzufügen, was zu einer Fehlermeldung führte, dass etwas schiefgelaufen ist.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2794_: [Cloud] Kritisches Problem mit Produktlisten mit leeren Platzierungen
   * _Fehlerbehebung_: Das System zeigt jetzt Produktlisten korrekt ohne Leerzeichen an, wenn Produkte auf „Nicht vorrätig“ eingestellt sind, was eine konsistente und genaue Anzeige der verfügbaren Produkte gewährleistet. Zuvor führte das Festlegen eines Produkts auf „Nicht vorrätig“ dazu, dass ein leerer Bereich in der Produktliste angezeigt wurde, was das Layout störte und Kunden möglicherweise verwirrte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>

### Reihenfolge

* _AC-10828_: Übersichtsbildschirm für Backend-Aufträge: Rückstandsmenge nicht auf Bestellartikelebene sichtbar
   * _Fehlerbehebung_: Das System zeigt jetzt die Anzahl der zurückgestellten Artikel in der Spalte „Menge“ auf dem Bildschirm „Auftragsübersicht“ des Backends an. Dadurch wird sichergestellt, dass Benutzende den Status aller Artikel in einer Bestellung genau verfolgen können. Zuvor wurde in der Spalte „Menge“ nur die Anzahl der bestellten, fakturierten und versandten Artikel angezeigt, nicht jedoch die Anzahl der nachbestellten Artikel.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38252>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problem] Falsche Store-ID im Renderer für Auftragsadressen verwendet
   * _Fehlerbehebung_: Das System verwendet jetzt bei der Darstellung der Bestelladresse korrekt die mit einer Bestellung verknüpfte Store-ID, um sicherzustellen, dass Adressen entsprechend ihrer jeweiligen Store-ID korrekt formatiert sind. Zuvor verwendete das System fälschlicherweise die aktuelle Store-ID, was zu einer falschen Adressformatierung führen konnte, wenn mehrere E-Mails zu Bestellungen aus verschiedenen Stores gesendet werden mussten.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38412>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37932>
* _AC-11798_: [Problem] Versandpreis wird in gedruckter PDF angezeigt
   * _Fehlerbehebung_: Das System zeigt jetzt die Versandpreise in gedruckten PDF entsprechend den Steuerkonfigurationseinstellungen korrekt an, um die Konsistenz zwischen der Auftragsrechnungsseite und der gedruckten Rechnung sicherzustellen. Zuvor war der auf der gedruckten PDF angezeigte Versandpreis ohne MwSt., unabhängig von den Steuerkonfigurationseinstellungen.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38608>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _ACP2E-2622_: Änderungen an der Telefonnummer in den vorhandenen Bestelldetails können nicht gespeichert werden
   * _Fix Hinweis_: Jetzt kann der Benutzer das internationale Präfix 00 in das Telefonfeld der Bestelladresse einfügen
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38201>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: E-Mails werden nicht gesendet
   * _Fehlerbehebung_: Das System verfügt jetzt über die Konfigurationsoption async_sending_attempts , mit der Anzahl von Versuchen, eine E-Mail zu senden, bevor sie gestoppt werden, was die Handhabung von fehlgeschlagenen E-Mail-Sendungen verbessert, wenn „Asynchrones Senden“ aktiviert ist. Zuvor versuchte das System, eine E-Mail nicht zu senden, und versuchte kontinuierlich, sie erneut zu senden, was zu einer endlosen Schleife von Fehlermeldungen im Systemprotokoll führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [Cloud] Bestellstatus wurde in „Abgeschlossen“ geändert, wenn eine teilweise Rückerstattung einer teilweise versendeten Bestellung erfolgt ist
   * _Fehlerbehebung_: Beim Ausstellen einer Gutschrift wird der Bestellstatus nicht mehr in „Abgeschlossen“ geändert, wenn es Artikel gibt, die noch nicht versandt wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [CLOUD] kann das Senden von E-Mails über die Admin-Benutzeroberfläche nicht deaktivieren, wie in den Entwicklungsdokumenten angezeigt wird
   * _Fehlerbehebung_: Das System verhindert jetzt korrekt, dass Verkaufs-E-Mails gesendet werden, wenn die E-Mail-Kommunikation deaktiviert ist. Diese E-Mails werden nicht mehr gesendet, wenn die E-Mail-Kommunikation wieder aktiviert wird. Zuvor wurden Verkaufs-E-Mails, die initiiert wurden, während die E-Mail-Kommunikation deaktiviert war, weiterhin gesendet, sobald die E-Mail-Kommunikation wieder aktiviert wurde.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Bestellung abgeschlossen ohne vollständige Rückerstattung
   * _Fehlerbehebung_: Der Bestellstatus wird jetzt korrekt als „Verarbeitung“ und der Rechnungsstatus als „Ausstehend“ beibehalten, wenn eine Bestellung mit einer nicht erfassten Zahlung erstellt wurde. Dadurch wird sichergestellt, dass Bestellungen erst nach vollständiger Rückerstattung als „Geschlossen“ gekennzeichnet werden. Zuvor wurde der Bestellstatus bei der Erstellung einer Lieferung für einen Auftrag mit ausstehender Rechnung fälschlicherweise in „Geschlossen“ geändert.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>

### Reihenfolge, Rückgabe

* _ACP2E-2982_: Die Bestellerstattung führt zu einer doppelten Gutschrift
   * _Fehlerbehebung_: Wenn die Rückerstattung über die REST-API erfolgt, wenn zwei identische Anfragen gleichzeitig ausgeführt wurden, werden keine doppelten Gutschriften mehr erstellt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/a4fbf702>

### Bestellung, Steuer

* _ACP2E-3003_: [CLOUD] Falsche base_row_total in RESTFUL order API bei der Aktivierung grenzüberschreitender Transaktionen und der Anwendung von Couponrabatten
   * _Fehlerbehebung_: Jetzt wird die korrekte base_row_total von der RESTFUL Order API zurückgegeben, wenn die grenzüberschreitende Transaktion aktiviert ist und ein Couponrabatt angewendet wird.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/9af794a4>

### Andere Entwickler-Tools

* _AC-10658_: [Problem] Behebung eines HTML-Syntaxfehlers in visual.phtml
   * _Fehlerbehebung_: Das System schließt jetzt das Start-Tag in der Datei „visual.phtml“ korrekt, um eine ordnungsgemäße HTML-Syntax sicherzustellen. Zuvor wurde das Start-Tag nicht ordnungsgemäß geschlossen, was zu einem HTML-Syntaxfehler führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38247>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Problem] im Befehl „bin/magento maintenance:status“ auf „aktiviert“ geändert
   * _Fehlerbehebung_: Das System bietet jetzt genauere Statusmeldungen für den Wartungsmodusbefehl, wobei der Status von „aktiv“ in „aktiviert“ und von „nicht aktiv“ in „deaktiviert“ geändert wird. Zuvor wurde die Statusmeldung für den Wartungsmodusbefehl als „aktiv“ oder „nicht aktiv“ angezeigt, was zu Verwirrung führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38486>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: Die Navigation in der Kategoriestruktur führt zu Fehlern in Redis: „Redis-Sitzung hat gleichzeitige Verbindungen überschritten“
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38851>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0611e750>

### Zahlungen

* _ACP2E-2841_: Payflow erstellt jedes Mal eine neue Transaktion, wenn wir auf den Abruf-Button im Bildschirm Transaktion anzeigen klicken
   * _Fehlerbehebung_: Das System ruft jetzt Transaktionsdaten korrekt ab, ohne eine neue Zahlungsbuchung zu erstellen, sobald die Schaltfläche „Abrufen“ auf dem Bildschirm „Transaktion anzeigen“ angeklickt wird. Zuvor wurde durch Klicken auf die Schaltfläche „Abrufen“ fälschlicherweise eine neue Zahlungstransaktion für eine bereits bezahlte Bestellung erstellt.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: PayLater-Nachricht wird für kanadisches PayPal-Händlerkonto nicht in PDP angezeigt
   * _Fehlerbehebung_: Die PayLater-Nachricht für kanadische PayPal-Händlerkonten wird jetzt korrekt auf der Produktdetailseite (PDP) angezeigt, wenn das Land des Käufers anhand der Rechnungsadresse oder der Lieferung des Kontos ermittelt werden kann. Zuvor wurde die PayLater-Nachricht aufgrund eines fehlenden Parameters nicht angezeigt, was zu einem Fehler in der Browser-Konsole führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/6a185204>

### Leistung

* _AC-12000_: [Problem] Code-Bereinigung und Hinzufügen eines neuen kritischen Head-Blocks und Verschieben von kritischem CSS vor Assets
   * _Fehlerbehebung_: Das System enthält jetzt einen neuen kritischen Head Block und verschiebt wichtiges CSS vor Assets, was eine bessere Anpassung und Leistungsoptimierung im Frontend ermöglicht. Zuvor wurde das kritische CSS nicht vor den Assets positioniert, was die Anpassungs- und Optimierungsmöglichkeiten einschränkte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38748>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: Die Design-Kompilierung funktioniert nicht mehr, wenn der MySQL-Host Port-Informationen enthält
   * _Fehlerbehebung_: Das System verarbeitet jetzt die MySQL-Host-Konfiguration, die Port-Informationen enthält, korrekt, um eine erfolgreiche Design-Kompilierung sicherzustellen. Zuvor schlug die Design-Kompilierung fehl, wenn die MySQL-Host-Konfiguration in der Datenbankverbindung Port-Informationen enthielt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38799>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38842>
* _ACP2E-2494_: Leistungsproblem beim Laden von Produktattributen in Warenkorbregeln
   * _Fix Hinweis_: Verbesserte Abfrageleistung für Verkaufsregeln - von rund 150 ms auf einstellige ms.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: Preis-partielle Indexierungsleistung
   * _Fix Hinweis_: Die Leistung bei der partiellen Indizierung im Preis wurde verbessert, indem einige der Löschabfragen optimiert wurden, die im Indizierungsprozess verwendet werden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: Bestellung wird bei Multi-Store-Setup bei Verwendung der asynchronen Auftragsverarbeitung abgelehnt + Allgemeine Geschäftsbedingungen
   * _Fehlerbehebung_: Die Bestellungen von nicht standardmäßigen Websites mit aktivierten Nutzungsbedingungen werden jetzt verarbeitet.
Bevor sie automatisch abgelehnt wurden.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: Die Ausführung des Aufruf der Order-Rest-API dauert sehr lange
   * _Fehlerbehebung_: Das System führt nun den Aufruf der Order Rest-API innerhalb eines angemessenen Zeitraums aus, was die Leistung beim Abrufen einer großen Anzahl von Bestellungen verbessert. Zuvor dauerte die Ausführung des Order Rest-API-Aufrufs lange, was zu Verzögerungen beim Abrufen einer großen Anzahl von Bestellungen führte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/001e5188>

### Produkt

* _AC-10535_: Sonderzeichen im konfigurierbaren zugehörigen Produktnamen werden in HTML-Entitäten konvertiert.
   * _Fehlerbehebung_: Beim Bearbeiten eines konfigurierbaren Produkts behält das System jetzt Sonderzeichen in den Namen der zugehörigen Produkte korrekt bei, was verhindert, dass diese in HTML-Entitäten konvertiert werden. Zuvor wurden Sonderzeichen in zugehörigen Produktnamen beim Bearbeiten des konfigurierbaren Produkts in HTML-Entitäten konvertiert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38146>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: Die ProductRepository-Funktion GetById erstellt nicht den richtigen Cache-Schlüssel
   * _Fehlerbehebung_: Das System erstellt jetzt korrekt einen Cache-Schlüssel in der GetById-Funktion des ProductRepositorys, unabhängig davon, ob die Speicher-ID als Zeichenfolge oder als Ganzzahl übergeben wird. Dadurch wird sichergestellt, dass das Produkt bei nachfolgenden Aufrufen aus dem Speicher abgerufen wird, was die Leistung verbessert. Zuvor konnte das System das Produkt jedes Mal aus der Datenbank abrufen, wenn die Funktion aufgerufen wurde, auch mit denselben Parametern, da ein falscher Cache-Schlüssel erstellt wurde.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38384>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [Problem] [MFTF] AdminClickAddOptionForBundleItemsActionGroup hinzugefügt
   * _Fehlerbehebung_: Das System enthält jetzt die AdminClickAddOptionForBundleItemsActionGroup, wodurch die Funktionalität des Admin-Bedienfelds erweitert wird. Zuvor war diese Aktionsgruppe nicht verfügbar.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/30857>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/30838>
* _AC-5969_: AlertProcessor - #2 ($storeId) muss vom Typ int sein, Zeichenfolge angegeben
   * _Fehlerbehebung_: Das System erstellt jetzt einen korrekten Trigger der E-Mail-Warnungen für Produkte, indem sichergestellt wird, dass die Kennung des Stores vom richtigen Datentyp ist. Zuvor wurden keine E-Mails zu Produktwarnungen gesendet, da der Typ in der Store-Kennung nicht übereinstimmt.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/35602>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: [Cloud] addFilterToMap-Funktion funktioniert für bestimmte Spalten nicht
   * _Hinweis korrigieren_: Jetzt kann das benutzerdefinierte Modul im Bestellraster verwendet werden. Bei der Verwendung eines benutzerdefinierten Moduls sind zuvor Fehler aufgetreten.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/3a7c4d17>

### Promotion

* _ACP2E-2602_: Kundenattribut beim Erstellen eines Kontos aus einer Einladung nicht sichtbar
   * _Fehlerbehebung_: Kundenattribute sind beim Erstellen eines Kontos über eine Einladung verfügbar.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: Couponcode mit Uses per Coupon-Limit wird nicht für Zahlung freigegeben, der mit der Stornierung der Bestellung fehlgeschlagen ist
   * _Fehlerbehebung_: Das System aktualisiert jetzt sofort die Couponnutzung, wenn eine Bestellung erstellt oder storniert wird, und fügt einer Warteschlange Regelverwendungen hinzu, um potenzielle Deadlocks zu verhindern. Dadurch wird sichergestellt, dass ein Gutscheincode mit einem Limit „Nutzungen pro Gutschein“ freigegeben wird und wiederverwendet werden kann, wenn eine Bestellung aufgrund einer fehlgeschlagenen Zahlung storniert wird. Zuvor gab das System den Couponcode nicht zur Wiederverwendung frei, was zu einer Fehlermeldung führte, die besagt, dass der Couponcode nicht gültig war.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [Cloud] Neuindizierung Katalogregel Produktindexer throws SQLSTATE[HY000]: Allgemeiner Fehler: Der MySQL-Server 2006 ist verschwunden.
   * _Fix Hinweis_: Das System verarbeitet jetzt den benutzerdefinierten Wert „batchCount“ in der Datei „di.xml“ für &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot; korrekt, wodurch SQL-Fehler wie „Allgemeiner Fehler: 2006 MySQL Server ist verschwunden“ während der Neuindizierung des Catalog Rule Product Indexer aufgrund der falschen Batch-Größe bei großen Katalogen verhindert werden
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>

### SEO

* _AC-11907_: Das Hinzufügen von URL-Neuschreibungen mit einem Akzent verursacht unendliche Ladevorgänge
   * _Fix Hinweis_: Das System erstellt und verwendet jetzt erfolgreich URL-Neuschreibungen mit Akzenten, wodurch das unendliche Laden während des Speichervorgangs verhindert wird. Zuvor führte das Hinzufügen einer URL-Umschreibung mit einem Akzent zu einem unendlichen Ladeproblem.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38692>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_: URL-Rewrite für die falsche Kategorie in Multi Store für Kategorie der dritten Ebene
   * _Fehlerbehebung_: Generieren korrekter URL-Neuschreibungen für untergeordnete Elemente mit einem übergeordneten Element mit benutzerdefiniertem URL-Schlüssel
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_: Doppelbyte-Zeichen (Sonderzeichen) im Feld Produktname blockieren die Produkterstellung im Backend
   * _Fehlerbehebung_: Es wurde eine neue Einstellung hinzugefügt, mit der Sie Transliteration auf Produkt-URLs anwenden können oder nicht. Einstellung ist hier verfügbar: Stores > Konfiguration > Katalog > Katalog > Suchmaschinenoptimierung: „Transliteration für Produkt-URL anwenden“
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>

### Sicherheit

* _AC-11762_:
   * _Notiz korrigieren_: 2FA OTP-Fensterfeld nach BiC-Änderung mit korrekter Beschreibung und Standardwert aktualisieren
   * _GitHub-Code-_: Aktualisierter Befehl für die Art und Weise, wie der Zeitraum „otp_window“ von jetzt an in „bin/magento config:set twofactorauth/google/otp_window“ eingegeben wird
in bin/magento config:set twoFactorAuth/google/leeway VALUE
* _AC-11855_: [Problem] Fehlendes Font CSP Paylater Popup
   * _Fix Hinweis_: Das System erlaubt jetzt das Laden der Schriftart &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; ohne gegen die Content Security Policy Direktive zu verstoßen, um die korrekte Anzeige des Paylater Popup sicherzustellen. Zuvor wurde das Laden der Schriftart aufgrund eines Verstoßes gegen die Content Security Policy-Direktive abgelehnt, was zu Anzeigeproblemen mit dem Paylater-Popup führte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38624>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/37401>
* _AC-11937_:
   * _Notiz korrigieren_: 2FA OTP-Fensterfeld nach BiC-Änderung mit korrekter Beschreibung und Standardwert aktualisieren
   * _GitHub-Code-_: Aktualisierter Befehl für die Art und Weise, wie der Zeitraum „otp_window“ von jetzt an in „bin/magento config:set twofactorauth/google/otp_window“ eingegeben wird
in bin/magento config:set twoFactorAuth/google/leeway VALUE
* _AC-12309_:
   * _Fehlerbehebung_: Aktualisieren der Benutzerdokumentation für die Zwei-Faktor-Authentifizierung (2FA) zum Ändern des Befehls otp_window
   * _GitHub-Code-Beitrag_: Aktualisieren Sie die Benutzerdokumentation für die Zwei-Faktor-Authentifizierung (2FA), um den OTP_WINDOW-Einstellungsbefehl gemäß https://jira.corp.adobe.com/browse/AC-11762 zu ändern.

### Lieferung

* _AC-10757_: [Problem] Tippfehler in tracking.phtml behoben - JS-Funktionen in „Currier“ umbenannt in „carrier“
   * _Fehlerbehebung_: Das System verwendet jetzt in den in der Bestellverfolgungsvorlage verwendeten JavaScript-Handler-Funktionen korrekt den Begriff „Carrier“ anstelle des falsch geschriebenen „Currier“, um eine ordnungsgemäße Funktionsbenennung und Code-Klarheit zu gewährleisten. Zuvor wurde der falsch geschriebene Begriff „Currier“ verwendet, was zu Verwirrung und Inkonsistenz in der Codebasis führen konnte.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/34523>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/33414>
* _AC-11811_:
   * _Fehlerbehebung_: UPS REST „Eine Sendung kann keine KGS/IN- oder LBS/CM- oder OZS/CM-Einheit als Maßeinheit haben“
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _GitHub-Code-Beitrag_: UPS-Raten sind an der Kasse und im Warenkorb sichtbar.
* _AC-11916_:
   * _Fehlerbehebung_: [QPT] UPS REST „Eine Sendung kann keine KGS/IN oder LBS/CM oder OZS/CM als Maßeinheit haben“
   * _GitHub-Code-Beitrag_: UPS-Raten sind an der Kasse und im Warenkorb sichtbar.
* _AC-11938_: UPS REST „Eine Sendung darf keine KGS/IN- oder LBS/CM- oder OZS/CM-Einheit als Maßeinheit haben“
   * _Fix Hinweis_: Stellen Sie sicher, dass die UPS-Tarife an der Kasse und im Warenkorb sichtbar sind.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38618>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_:
   * _Fehlerbehebung_: [QPT] UPS REST „Eine Sendung kann keine KGS/IN oder LBS/CM oder OZS/CM als Maßeinheit haben“
   * _GitHub-Code-Beitrag_: UPS-Raten sind an der Kasse und im Warenkorb sichtbar.
* _AC-11984_:
   * _Fehlerbehebung_: [QPT] UPS REST „Eine Sendung kann keine KGS/IN oder LBS/CM oder OZS/CM als Maßeinheit haben“
   * _GitHub-Code-Beitrag_: UPS-Raten sind an der Kasse und im Warenkorb sichtbar.
* _ACP2E-2738_: Tracking-Fenster zeigt das falsche erwartete Lieferdatum an
   * _Fehlerbehebung_: Zeigt das richtige Lieferdatum für Fedex Carrier an.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Tabellen-Sätze werden weiterhin angezeigt, obwohl kostenloser Versand angewendet wird
   * _Fehlerbehebung_: Die Versandmethode „Table Rate“ wird jetzt angezeigt, auch wenn nach der Anwendung des Coupons der kostenlose Versand verfügbar wird
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF-Test AdminCreatingShippingLabelTest schlägt fehl aufgrund von Anmeldeinformationen, die nicht in der Jenkins-Umgebung hinzugefügt wurden
   * _Fehlerbehebung_: mftf test fix
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Zielgruppenbestimmung

* _AC-9432_: [Problem] Verwendung von CIDR-Bereichen in der Wartungs-Zulassungsliste zulassen
   * _Fehlerbehebung_: Das System unterstützt jetzt die Verwendung von CIDR-Bereichen in der Zulassungsliste für IP-Adressen im Wartungsmodus, sodass ein Bereich von IP-Adressen den Wartungsmodus umgehen kann. Zuvor erlaubte der Wartungsmodus, dass die IP-Liste nur einzelne IP-Adressen den Wartungsmodus umgeht.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37943>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/30699>

### Test-Framework

* _AC-11491_:
   * _Fehlerbehebung_: [Überspringen] Muss rückgängig gemacht werden Integrationstest
   * _GitHub-Problem_: &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _GitHub-Code-Beitrag_: Überspringen Sie alle Integrationstests, die in dieser PR übersprungen werden - https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_: Integrationstest schlägt fehl bei testDbSchemaUpToDate aufgrund von JSON-Spaltentyp
   * _Fehlerbehebung_: Das System erkennt jetzt bei Integrationstests JSON-Spaltentypen im Datenbankschema korrekt, um Testfehler aufgrund einer Diskrepanz zwischen dem Datenbankschema und dem deklarativen Schema zu verhindern. Zuvor hat das System JSON-Spaltentypen in MariaDB fälschlicherweise als LONGTEXT identifiziert, wodurch Integrationstests fehlschlugen.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/ef81f5a2>

### UI-Framework

* _AC-12128_: Behebung der Sicherheitslücke in Prototype.js CVE-2020-27511
   * _Fehlerbehebung_: Das System wurde aktualisiert, um die Sicherheitslücke CVE-2020-27511 in Prototype.js 1.7.3 zu beheben und so die allgemeine Sicherheit des Systems zu verbessern. Vor diesem Update war das System anfällig für einen Regular Expression Denial of Service (ReDOS) durch Strippen von HTML-Tags.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less verwendet pub/prefix für Quellenkarten
   * _Fehlerbehebung_: Das System generiert jetzt bei der Verwendung von grunt less/css-Quellzuordnungen ohne das /pub-Präfix für Pfade, sodass keine Problemumgehung in der Webserver-Konfiguration erforderlich ist. Zuvor war für die Verwendung des Präfixes /pub in Quellzuordnungspfaden eine bestimmte Konfiguration im Webserver erforderlich, damit es ordnungsgemäß funktioniert.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/38837>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/38840>
* _AC-1306_: Statischer Inhalt wird für deaktivierte Module bereitgestellt.
   * _Fehlerbehebung_: Das System schließt jetzt CSS für deaktivierte Module aus den endgültigen CSS-Ausgabedateien aus, um sicherzustellen, dass unnötige Stile nicht geladen werden. Zuvor wurde CSS für deaktivierte Module in die endgültigen CSS-Ausgabedateien eingefügt, was dazu führte, dass zusätzliche, unnötige Stile geladen wurden.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/24666>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/32922>
* _AC-9007_: [Problem] Laden Sie den Backend-Blockkontext nicht in Frontend
   * _Fix Hinweis_: Das System stellt jetzt sicher, dass der Backend-Block-Kontext nicht im Frontend geladen wird, was die Erstellung unnötiger Backend-Sitzungen und potenzieller Sitzungssperren verhindert. Zuvor hat das System fälschlicherweise den Backend-Blockkontext im Frontend geladen, was zur Erstellung von Backend-Sitzungen und potenziellen Sitzungssperren geführt hat.
   * _GitHub-Problem_: <https://github.com/magento/magento2/issues/37617>
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_: Ausnahme beim Überprüfen eines Geschenkgutscheinsaldos, wenn reCAPTCHA aktiviert ist
   * _Hinweis korrigieren_: Benutzer können auf dem Bildschirm „Warenkorb anzeigen“ und „Warenkorb bearbeiten“ den Guthaben der Geschenkkarte abrufen. Zuvor wurden diese Details nicht angezeigt, während reCAPTCHA aktiviert war.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [Klärung] Funktionsanfrage ADA-Konformität
   * _Fehlerbehebung_: Das System stellt jetzt die ADA-Konformität sicher, indem es nicht unterstützte CSS-Eigenschaften entfernt und sie durch unterstützte Eigenschaften in der Datei „print.css“ ersetzt. Zuvor führte die Verwendung nicht unterstützter CSS-Eigenschaften zu Problemen mit der Browser-Kompatibilität.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Cloud] Konfusionsbibliothekscode in effect-drop.js von AC 2.4.4-p8
   * _Fehlerbehebung_: Das System implementiert jetzt die Bibliothek „effect-drop.js“ korrekt, um die ordnungsgemäße Funktion der jQuery-UI-Effekte sicherzustellen. Zuvor wurde die Bibliothek „effect-drop.js“ versehentlich mit der Bibliothek „effect-clip.js“ überschrieben, was zu Problemen mit jQuery-UI-Effekten führen konnte.
   * _GitHub-Code-Beitrag_: <https://github.com/magento/magento2/commit/35b1b1da>
