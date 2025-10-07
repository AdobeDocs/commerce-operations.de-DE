---
title: Benutzerdefinierter Cron-Auftrag und Cron-Gruppenreferenz
description: Erfahren Sie, wie Sie Crons mithilfe von Crons-Gruppen und Crontabs in Adobe Commerce anpassen können. Erkunden Sie die Einrichtung benutzerdefinierter Module und die Konfiguration geplanter Aufgaben.
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Anpassen der Cron-Referenz

Dieses Thema hilft Ihnen beim Einrichten von crontabs und optional crongroups für benutzerdefinierte Module. Wenn Ihr benutzerdefiniertes Modul regelmäßig Aufgaben planen muss, müssen Sie für dieses Modul eine crontab einrichten. Eine _crontab_ ist eine Cron-Auftragskonfiguration.

Optional können Sie eine benutzerdefinierte Gruppe einrichten, die es Ihnen unter anderem ermöglicht, in dieser Gruppe definierte Cron-Aufträge unabhängig von anderen Cron-Aufträgen auszuführen.

Eine schrittweise Anleitung finden Sie unter [Konfigurieren von benutzerdefinierten Cron-Aufträgen und Cron-Gruppen (Tutorial)](custom-cron-tutorial.md).

Einen Überblick über Cron-Aufträge finden Sie [Konfigurieren von Cron-Aufträgen](../cli/configure-cron-jobs.md).

## Cron-Gruppen konfigurieren

In diesem Abschnitt wird beschrieben, wie Sie optional eine Cron-Gruppe für ein benutzerdefiniertes Modul erstellen. Wenn Sie dies nicht tun müssen, fahren Sie mit dem nächsten Abschnitt fort.

Eine _Cron-Gruppe_ ist eine logische Gruppe, mit der Sie Cron einfach für mehr als einen Prozess gleichzeitig ausführen können. Die meisten Commerce-Module verwenden die `default` Cron-Gruppe; einige Module verwenden die `index`.

Wenn Sie Cron für ein benutzerdefiniertes Modul implementieren, können Sie die `default` oder eine andere Gruppe verwenden.

**So konfigurieren Sie eine Cron-Gruppe für Ihr Modul**:

Erstellen Sie eine `crontab.xml`-Datei in Ihrem Modulverzeichnis:

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
| `method` | Methode in `classpath` aufzurufenden Instanz. |
| `time` | Zeitplan im Cron-Format. Lassen Sie diesen Parameter aus, wenn der Zeitplan in der Commerce-Datenbank oder einem anderen Speicher definiert ist. |

Die resultierende `crontab.xml` mit zwei Gruppen könnte wie folgt aussehen:

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

Als Beispiel dient [Magento_Customer_crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Angeben der Cron-Gruppenoptionen

Sie können eine neue Gruppe deklarieren und ihre Konfigurationsoptionen (die alle im Bereich der Store-Ansicht ausgeführt werden) über die `cron_groups.xml`-Datei angeben, die sich in befindet:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Nachfolgend finden Sie ein Beispiel für die `cron_groups.xml`:

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
| `schedule_generate_every` | Häufigkeit (in Minuten), mit der Zeitpläne in die `cron_schedule` geschrieben werden. |
| `schedule_ahead_for` | Zeit (in Minuten) im Voraus, zu der Zeitpläne in die `cron_schedule` geschrieben werden. |
| `schedule_lifetime` | Zeitfenster (in Minuten), in dem ein Cron-Auftrag gestartet werden muss oder der Cron-Auftrag als verpasst gilt („zu spät“ zum Ausführen). |
| `history_cleanup_every` | Zeit (in Minuten), zu der der Cron-Verlauf in der Datenbank gespeichert wird. |
| `history_success_lifetime` | Zeit (in Minuten), die der Datensatz der erfolgreich abgeschlossenen Cron-Aufträge in der Datenbank gespeichert wird. |
| `history_failure_lifetime` | Zeit (in Minuten), die der Datensatz fehlgeschlagener Cron-Aufträge in der Datenbank gespeichert wird. |
| `use_separate_process` | Die Aufträge dieser Cron-Gruppe in einem separaten PHP-Prozess ausführen |

## Deaktivieren von Cron-Aufträgen

Cron-Aufträge haben keine `disable` Funktion wie wir für [Beobachter](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). Ein Cron-Auftrag kann jedoch mithilfe der folgenden Technik deaktiviert werden: `schedule` einer Zeit, die ein Datum enthält, das niemals eintreten wird.

Deaktivieren Sie beispielsweise den `visitor_clean` Cron-Auftrag, der in `Magento_Customer` Modul definiert ist:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Um den `visitor_clean` Cron-Auftrag zu deaktivieren, erstellen Sie ein benutzerdefiniertes Modul und schreiben Sie die `visitor_clean` Cron-`schedule` neu:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

Jetzt wurde der `visitor_clean` Cron-Auftrag auf 00 % :00 30. Februar eingestellt - an dem Datum, das nie eintreten wird.
