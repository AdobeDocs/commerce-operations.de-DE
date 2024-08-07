---
title: Benutzerdefinierter Cron-Auftrag und Cron-Gruppenreferenz
description: Erfahren Sie, wie Sie Crons mithilfe von Cron-Gruppen anpassen können.
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Anpassen der ECrons-Referenz

Dieses Thema hilft Ihnen beim Einrichten von Registerkarten und optional Cron-Gruppen für benutzerdefinierte Module. Wenn Ihr benutzerdefiniertes Modul Aufgaben periodisch planen muss, müssen Sie eine Kronenregisterkarte für dieses Modul einrichten. Eine _crontab_ ist eine Cron-Auftragskonfiguration.

Optional können Sie eine benutzerspezifische Gruppe einrichten, mit der Sie unter anderem in dieser Gruppe definierte Cron-Aufträge unabhängig von anderen Cron-Aufträgen ausführen können.

Eine schrittweise Anleitung finden Sie unter [Konfigurieren von benutzerdefinierten Cron-Aufträgen und Cron-Gruppen (Tutorial)](custom-cron-tutorial.md).

Einen Überblick über Cron-Aufträge finden Sie unter [Konfigurieren von Cron-Aufträgen](../cli/configure-cron-jobs.md).

## Cron-Gruppen konfigurieren

In diesem Abschnitt wird beschrieben, wie Sie optional eine Cron-Gruppe für ein benutzerdefiniertes Modul erstellen. Wenn Sie dies nicht benötigen, fahren Sie mit dem nächsten Abschnitt fort.

Eine _Cron-Gruppe_ ist eine logische Gruppe, mit der Sie Cron einfach für mehrere Prozesse gleichzeitig ausführen können. Die meisten Commerce-Module verwenden die Cron-Gruppe `default`; einige Module verwenden die Gruppe `index`.

Wenn Sie Cron für ein benutzerdefiniertes Modul implementieren, können Sie die Gruppe `default` oder eine andere Gruppe verwenden.

**So konfigurieren Sie eine Cron-Gruppe für Ihr Modul**:

Erstellen Sie eine `crontab.xml` -Datei in Ihrem Modulverzeichnis:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

Für eine Gruppe sollte die Datei den folgenden Inhalt haben:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

Dabei gilt:

| Wert | Beschreibung |
|---|---|
| `group_name` | Name der Cron-Gruppe. Der Gruppenname muss nicht eindeutig sein. Sie können Cron für jeweils eine Gruppe ausführen. |
| `job_name` | Eindeutige ID für diesen Cron-Auftrag. |
| `classpath` | Zu instanziierende Klasse (Klassenpfad). |
| `method` | Methode in `classpath`, die aufgerufen werden soll. |
| `time` | Im Cron-Format planen. Lassen Sie diesen Parameter weg, wenn der Zeitplan in der Commerce-Datenbank oder in einem anderen Speicher definiert ist. |

Das resultierende `crontab.xml` mit zwei Gruppen kann wie folgt aussehen:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Ein Beispiel finden Sie unter [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Festlegen von Cron-Gruppenoptionen

Sie können eine neue Gruppe deklarieren und ihre Konfigurationsoptionen (die alle im Bereich der Store-Ansicht ausgeführt werden) über die Datei &quot;`cron_groups.xml`&quot;angeben, die sich unter:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Nachfolgend finden Sie ein Beispiel für die Datei `cron_groups.xml` :

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

Dabei gilt:

| Option | Beschreibung |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | Häufigkeit (in Minuten), mit der Zeitpläne in die Tabelle `cron_schedule` geschrieben werden. |
| `schedule_ahead_for` | Zeit (in Minuten) vor dem Schreiben der Zeitpläne in die Tabelle `cron_schedule`. |
| `schedule_lifetime` | Zeitfenster (in Minuten), in dem ein Cron-Auftrag gestartet werden muss oder der Cron-Auftrag als verpasst gilt (&quot;zu spät&quot; für die Ausführung). |
| `history_cleanup_every` | Uhrzeit (in Minuten), zu der der Cron-Verlauf in der Datenbank beibehalten wird. |
| `history_success_lifetime` | Zeit (in Minuten), zu der der Datensatz mit erfolgreich abgeschlossenen Cron-Aufträgen in der Datenbank gespeichert wird. |
| `history_failure_lifetime` | Zeit (in Minuten), in der der Datensatz mit fehlgeschlagenen Cron-Aufträgen in der Datenbank gespeichert wird. |
| `use_separate_process` | Führen Sie die Aufträge dieser Cron-Gruppe in einem separaten PHP-Prozess aus |

## Cron-Auftrag deaktivieren

Cron-Aufträge verfügen nicht über eine `disable` -Funktion, wie wir sie für [Beobachter](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers) haben. Ein Cron-Auftrag kann jedoch mithilfe der folgenden Technik deaktiviert werden: `schedule` eine Zeit, die ein Datum enthält, das nie eintritt.

Deaktivieren Sie beispielsweise den Cron-Auftrag `visitor_clean` , der im Modul `Magento_Customer` definiert ist:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Um den Cron-Auftrag `visitor_clean` zu deaktivieren, erstellen Sie ein benutzerdefiniertes Modul und schreiben Sie den `visitor_clean` cron-Auftrag `schedule` neu:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Nun wurde der Cron-Auftrag `visitor_clean` so eingestellt, dass er am 30. Februar um 00:00 Uhr ausgeführt wird - zu dem Datum, das nie eintreten wird.
