---
title: Anwendungsinitialisierung und Bootstrap
description: Informationen zur Initialisierung und Bootstrap-Logik für das Commerce-Programm.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Übersicht über Initialisierung und Bootstrap

Um das Commerce-Programm auszuführen, werden die folgenden Aktionen in [pub/index.php implementiert][index]:

- Schließen Sie [app/bootstrap.php][bootinitial] ein, das wichtige Initialisierungsroutinen durchführt, z. B. die Fehlerbehandlung, die Initialisierung des Autoloaders, das Festlegen von Profiloptionen und das Festlegen der standardmäßigen Zeitzone.
- Instanz von [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. --> erstellen
- Erstellen Sie eine Commerce-Anwendungsinstanz: [\Magento\Framework\AppInterface][app-face]
- Commerce ausführen

## Bootstrap-Ausführungslogik

[Das Bootstrap-Objekt][bootinitial] verwendet den folgenden Algorithmus, um die Commerce-Anwendung auszuführen:

1. Initialisiert den Fehler-Handler.
1. Erstellt den [Objekt-Manager][object] und grundlegende freigegebene Dienste, die überall verwendet werden und von der Umgebung betroffen sind. Die Umgebungsparameter werden ordnungsgemäß in diese Objekte eingefügt.
1. Stellt sicher, dass der Wartungsmodus _nicht_ aktiviert ist; andernfalls wird er beendet.
1. Erklärt, dass die Commerce-Anwendung installiert ist, andernfalls wird beendet.
1. Startet die Commerce-Anwendung.

   Jede nicht erfasste Ausnahme während des Anwendungsstarts wird automatisch an Commerce in der `catchException()` zurückgegeben, die Sie zum Verarbeiten der Ausnahme verwenden können. Diese müssen entweder `true` oder `false` zurückgeben:

   - Wenn `true`: Ausnahmefehler wurde von Commerce erfolgreich behandelt. Sie brauchen nichts anderes zu tun.
   - Wenn `false`: (oder ein anderes leeres Ergebnis) Commerce hat die Ausnahme nicht verarbeitet. Das Bootstrap-Objekt führt die standardmäßige Unterroutine zur Ausnahmebehandlung aus.

1. Sendet die vom Anwendungsobjekt bereitgestellte Antwort.

   >[!INFO]
   >
   >Die Bestätigung, dass die Commerce-Anwendung installiert ist und sich nicht im Wartungsmodus befindet, ist das Standardverhalten der `\Magento\Framework\App\Bootstrap`. Sie können sie beim Erstellen des Bootstrap-Objekts mithilfe eines Einstiegspunktskripts ändern.

   Beispiel-Einstiegspunktskript, das das Bootstrap-Objekt ändert:

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

Das Bootstrap-Objekt gibt an, wie die Commerce-Anwendung nicht erfasste Ausnahmen wie folgt verarbeitet:

- Im [Entwicklermodus](../bootstrap/application-modes.md#developer-mode) zeigt die Ausnahme unverändert an.
- In jedem anderen Modus versucht , Ausnahmen zu protokollieren und eine allgemeine Fehlermeldung anzuzeigen.
- Beendet Commerce mit Fehlercode `1`

## Einstiegspunktanwendungen

Wir haben die folgenden Einstiegspunktanwendungen (d. h. von Commerce definierte Anwendungen, die vom Webserver als Verzeichnisindex verwendet werden):

### HTTP-Einstiegspunkt

[\Magento\Framework\App\Http][http] funktioniert wie folgt:

1. Bestimmt den [Anwendungsbereich](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Startet den Frontcontroller und das Routing-System, um eine Controller-Aktion zu finden und auszuführen.
1. Verwendet ein HTTP-Antwortobjekt, um das von der Controller-Aktion erhaltene Ergebnis zurückzugeben.
1. Fehlerbehandlung (in der folgenden Prioritätsreihenfolge):

   1. Wenn Sie den [Entwicklermodus“ &#x200B;](../bootstrap/application-modes.md#developer-mode):
      - Wenn die Commerce-Anwendung nicht installiert ist, leiten Sie zum Setup-Assistenten weiter.
      - Wenn die Commerce-Anwendung installiert ist, zeigen Sie den HTTP-Status-Code 500 (Interner Server-Fehler) an.
   1. Wenn sich die Commerce-Anwendung im Wartungsmodus befindet, zeigen Sie eine benutzerfreundliche Landingpage „Service nicht verfügbar“ mit HTTP-Status-Code 503 (Service nicht verfügbar) an.
   1. Wenn die Commerce-Anwendung _nicht_ installiert ist, leiten Sie zum Setup-Assistenten weiter.
   1. Wenn die Sitzung ungültig ist, leiten Sie zur Startseite weiter.
   1. Wenn ein anderer Anwendungsinitialisierungsfehler auftritt, zeigen Sie eine benutzerfreundliche Seite „Page Not Found“ (Seite nicht gefunden) mit HTTP-Status-Code 404 (Nicht gefunden) an.
   1. Bei jedem anderen Fehler zeigen Sie eine benutzerfreundliche Seite „Service nicht verfügbar“ mit HTTP-Antwort 503 an, generieren einen Fehlerbericht und zeigen die zugehörige ID auf der Seite an.

### Einstiegspunkt für statische Ressourcen

[\Magento\Framework\App\StaticResource][static-resource] ist ein Programm zum Abrufen statischer Ressourcen (z. B. CSS, JavaScript und Bilder). Sie verschiebt alle Aktionen mit einer statischen Ressource, bis die Ressource angefordert wird.

>[!INFO]
>
>Der Einstiegspunkt für statische Ansichtsdateien wird im [Produktionsmodus) nicht verwendet](application-modes.md#production-mode) um potenzielle Ausnutzungen auf dem Server zu vermeiden. Im Produktionsmodus erwartet die Commerce-Anwendung, dass alle erforderlichen Ressourcen im `<your Commerce install dir>/pub/static` vorhanden sind.

Im Standard- oder Entwicklermodus wird eine Anfrage für eine nicht vorhandene statische Ressource gemäß den vom entsprechenden `.htaccess` angegebenen Neuschreibungsregeln an den statischen Einstiegspunkt umgeleitet.
Wenn die Anfrage an den Einstiegspunkt weitergeleitet wird, analysiert die Commerce-Anwendung die angeforderte URL auf der Grundlage der abgerufenen Parameter und findet die angeforderte Ressource.

- Im [Entwicklermodus](application-modes.md#developer-mode) wird der Inhalt der Datei zurückgegeben, sodass der zurückgegebene Inhalt jedes Mal auf dem neuesten Stand ist, wenn die Ressource angefordert wird.
- Im [Standard](application-modes.md#default-mode)Modus wird die abgerufene Ressource veröffentlicht, sodass sie über die zuvor angeforderte URL zugänglich ist.

  Alle zukünftigen Anforderungen für die statische Ressource werden vom Server auf die gleiche Weise wie statische Dateien verarbeitet, d. h. ohne den Einstiegspunkt zu involvieren. Wenn veröffentlichte Dateien mit den ursprünglichen synchronisiert werden müssen, sollte das `pub/static` entfernt werden. Daher werden die Dateien bei der nächsten Anfrage automatisch erneut veröffentlicht.

### Einstiegspunkt für Medienressourcen

[Magento\MediaStorage\App\Media][media] ruft Medienressourcen (d. h. alle in den Medienspeicher hochgeladenen Dateien) aus der Datenbank ab. Er wird immer dann verwendet, wenn die Datenbank als Medienspeicher konfiguriert ist.

`\Magento\Core\App\Media` versucht, die Mediendatei im konfigurierten Datenbankspeicher zu finden, sie in das `pub/static` Verzeichnis zu schreiben und dann ihren Inhalt zurückzugeben. Bei einem Fehler wird ein HTTP-404-Status-Code (Nicht gefunden) in der Kopfzeile ohne Inhalt zurückgegeben.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
