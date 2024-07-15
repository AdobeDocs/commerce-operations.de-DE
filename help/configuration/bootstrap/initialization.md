---
title: Anwendungsinitialisierung und Bootstrap
description: Erfahren Sie mehr über die Initialisierung und Bootstrap-Logik für die Commerce-Anwendung.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Übersicht über Initialisierung und Bootstrap

Um die Commerce-Anwendung auszuführen, werden die folgenden Aktionen in [pub/index.php][index] implementiert:

- Schließen Sie [app/bootstrap.php][bootinitial] ein, das wichtige Initialisierungsroutinen wie die Fehlerbehandlung, die Initialisierung des Autoloaders, die Festlegung von Profilerstellungsoptionen und die Festlegung der standardmäßigen Zeitzone durchführt.
- Erstellen einer Instanz von [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Erstellen Sie eine Commerce-Anwendungsinstanz: [\Magento\Framework\AppInterface][app-face]
- Commerce ausführen

## Bootstrap-Ausführungslogik

[Das Bootstrap-Objekt][bootinitial] verwendet den folgenden Algorithmus zum Ausführen der Commerce-Anwendung:

1. Initialisiert den Fehler-Handler.
1. Erstellt den [Objektmanager][object] und die grundlegenden freigegebenen Dienste, die überall verwendet werden und von der Umgebung betroffen sind. Die Umgebungsparameter werden ordnungsgemäß in diese Objekte eingefügt.
1. Stellt sicher, dass der Wartungsmodus _nicht_ aktiviert ist; andernfalls wird beendet.
1. Stellt sicher, dass die Commerce-Anwendung installiert ist, andernfalls wird beendet.
1. Startet die Commerce-Anwendung.

   Jede nicht abgefangene Ausnahme während des Anwendungsstarts wird in der `catchException()` -Methode, die Sie zur Verarbeitung der Ausnahme verwenden können, automatisch an Commerce zurückgegeben. Letzterer muss entweder `true` oder `false` zurückgeben:

   - Wenn `true`: Commerce hat die Ausnahme erfolgreich verarbeitet. Es ist nicht notwendig, etwas Anderes zu tun.
   - Wenn `false`: (oder ein anderes leeres Ergebnis), hat Commerce die Ausnahme nicht verarbeitet. Das Bootstrap-Objekt führt die standardmäßige UnterRoutine für die Ausnahmebehandlung aus.

1. Sendet die Antwort, die vom Anwendungsobjekt bereitgestellt wird.

   >[!INFO]
   >
   >Die Behauptung, dass die Commerce-Anwendung installiert ist und sich nicht im Wartungsmodus befindet, ist das Standardverhalten der Klasse `\Magento\Framework\App\Bootstrap` . Sie können sie beim Erstellen des Bootstrap-Objekts mithilfe eines Einstiegspunktskripts ändern.

   Beispieleinstiegspunktskript, das das Bootstrap-Objekt ändert:

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## Standardmäßige Ausnahmebehandlung

Das bootstrap -Objekt gibt an, wie die Commerce-Anwendung nicht abgefangene Ausnahmen wie folgt handhabt:

- Im [Entwicklermodus](../bootstrap/application-modes.md#developer-mode) zeigt die Ausnahme unverändert an.
- In jedem anderen Modus versucht, Ausnahmefehler zu protokollieren und eine allgemeine Fehlermeldung anzuzeigen.
- Beendet Commerce mit Fehlercode `1`

## Einstiegspunktanwendungen

Es gibt die folgenden Einstiegspunktanwendungen (d. h. von Commerce definierte Anwendungen, die vom Webserver als Ordnerindex verwendet werden):

### HTTP-Einstiegspunkt

[\Magento\Framework\App\Http][http] funktioniert wie folgt:

1. Bestimmt den [Anwendungsbereich](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Startet die Front-Controller- und Routing-Systeme, um eine Controller-Aktion zu finden und auszuführen.
1. Verwendet ein HTTP-Antwortobjekt, um ein Ergebnis zurückzugeben, das von der Controller-Aktion abgerufen wurde.
1. Fehlerbehandlung (in der folgenden Prioritätsreihenfolge):

   1. Wenn Sie den [Entwicklermodus](../bootstrap/application-modes.md#developer-mode) verwenden:
      - Wenn die Commerce-Anwendung nicht installiert ist, führen Sie eine Umleitung zum Einrichtungsassistenten durch.
      - Wenn die Commerce-Anwendung installiert ist, zeigen Sie einen Fehler und den HTTP-Statuscode 500 (Interner Serverfehler) an.
   1. Wenn sich die Commerce-Anwendung im Wartungsmodus befindet, zeigen Sie eine benutzerfreundliche Landingpage &quot;Dienst nicht verfügbar&quot;mit dem HTTP-Status-Code 503 (Dienst nicht verfügbar) an.
   1. Wenn die Commerce-Anwendung _nicht_ installiert ist, leiten Sie den Einrichtungsassistenten weiter.
   1. Wenn die Sitzung ungültig ist, führen Sie eine Umleitung zur Startseite durch.
   1. Wenn ein anderer Anwendungsinitialisierungsfehler auftritt, zeigen Sie eine benutzerfreundliche Seite &quot;Seite nicht gefunden&quot;mit dem HTTP-Status-Code 404 (Nicht gefunden) an.
   1. Zeigen Sie bei jedem anderen Fehler eine benutzerfreundliche Seite &quot;Dienst nicht verfügbar&quot;mit HTTP-Antwort 503 an, generieren Sie einen Fehlerbericht und zeigen Sie dessen ID auf der Seite an.

### Einstiegspunkt für statische Ressourcen

[\Magento\Framework\App\StaticResource][static-resource] ist eine Anwendung zum Abrufen statischer Ressourcen (z. B. CSS, JavaScript und Bilder). Dadurch werden alle Aktionen mit einer statischen Ressource verschoben, bis die Ressource angefordert wird.

>[!INFO]
>
>Der Einstiegspunkt für statische Ansichtsdateien wird nicht im [Produktionsmodus](application-modes.md#production-mode) verwendet, um potenzielle Exploits auf dem Server zu vermeiden. Im Produktionsmodus erwartet das Commerce-Programm, dass alle erforderlichen Ressourcen im Verzeichnis `<your Commerce install dir>/pub/static` vorhanden sind.

Im Standard- oder Entwicklermodus wird eine Anfrage für eine nicht vorhandene statische Ressource gemäß den in der entsprechenden `.htaccess` festgelegten Neuschreibungsregeln an den statischen Einstiegspunkt umgeleitet.
Wenn die Anforderung an den Einstiegspunkt weitergeleitet wird, analysiert die Commerce-Anwendung die angeforderte URL anhand der abgerufenen Parameter und sucht die angeforderte Ressource.

- Im Modus [developer](application-modes.md#developer-mode) wird der Inhalt der Datei zurückgegeben, sodass bei jeder Anforderung der Ressource der zurückgegebene Inhalt auf dem neuesten Stand ist.
- Im Modus [Standard](application-modes.md#default-mode) wird die abgerufene Ressource veröffentlicht, sodass sie über die zuvor angeforderte URL aufgerufen werden kann.

  Alle zukünftigen Anforderungen für die statische Ressource werden vom Server genauso verarbeitet wie statische Dateien, d. h. ohne den Einstiegspunkt zu berücksichtigen. Wenn es erforderlich ist, veröffentlichte Dateien mit ursprünglichen zu synchronisieren, sollte das Verzeichnis `pub/static` entfernt werden. Daher werden Dateien automatisch mit der nächsten Anfrage erneut veröffentlicht.

### Einstiegspunkt für Medienressourcen

[Magento\MediaStorage\App\Media][media] ruft Medienressourcen (d. h. alle Dateien, die in den Medienspeicher hochgeladen wurden) aus der Datenbank ab. Sie wird immer dann verwendet, wenn die Datenbank als Medienspeicher konfiguriert ist.

`\Magento\Core\App\Media` versucht, die Mediendatei im konfigurierten Datenbankspeicher zu finden, sie in das Verzeichnis `pub/static` zu schreiben und gibt dann ihren Inhalt zurück. Bei Fehler wird ein HTTP-Statuscode 404 (Nicht gefunden) im Header ohne Inhalt zurückgegeben.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
