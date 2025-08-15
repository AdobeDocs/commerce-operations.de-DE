---
title: Module aktivieren oder deaktivieren
description: Führen Sie diese Schritte aus, um Adobe Commerce-Module zu verwalten.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Module aktivieren oder deaktivieren

Dieser Befehl ist nicht erforderlich.

## Modulstatus

Verwenden Sie den folgenden Befehl, um aktivierte und deaktivierte Module aufzulisten:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Hierbei gilt

* `--enabled` werden alle aktivierten Module aufgelistet.
* `--disabled` werden alle deaktivierten Module aufgelistet.
* `<module-list>` ist eine durch Leerzeichen getrennte Liste von Modulen zur Statusüberprüfung. Wenn ein Modulname Sonderzeichen enthält, schließen Sie den Namen entweder in einfachen oder doppelten Anführungszeichen ein.

>[!NOTE]
>
>Module können nicht direkt in Cloud-Projekten aktiviert oder deaktiviert werden. Sie müssen diese Befehle lokal ausführen und dann Änderungen für eine Umgebung an die `app/etc/config.php`-Datei pushen. Siehe [Pro-Projekt-Workflow: Bereitstellungs-Workflow](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=de#deployment-workflow).

## Modul aktivieren, deaktivieren

Verwenden Sie den folgenden Befehl, um verfügbare Module zu aktivieren oder zu deaktivieren:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Hierbei gilt

* `<module-list>` ist eine durch Leerzeichen getrennte Liste von Modulen, die aktiviert oder deaktiviert werden sollen. Wenn ein Modulname Sonderzeichen enthält, schließen Sie den Namen entweder in einfachen oder doppelten Anführungszeichen ein.
* `--all` alle Module gleichzeitig zu aktivieren oder zu deaktivieren.
* `-f` oder `--force`, um die Aktivierung oder Deaktivierung eines Moduls trotz der Abhängigkeiten zu erzwingen. Bevor Sie diese Option verwenden, lesen Sie [Informationen zum Aktivieren und Deaktivieren von Modulen](#about-enabling-and-disabling-modules).
* `-c` oder `--clear-static-content` bereinigt [generierte statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md).

  Wenn die statischen Ansichtsdateien nicht gelöscht werden, können Probleme auftreten, wenn mehrere Dateien mit demselben Namen vorhanden sind und nicht alle gelöscht werden.

  Anders ausgedrückt: Wenn Sie aufgrund der [statischen Datei-Fallback](../../configuration/cli/static-view-file-deployment.md)-Regeln statische Dateien nicht löschen und es mehr als eine Datei mit dem Namen `logo.svg` gibt, die unterschiedlich sind, kann ein Fallback dazu führen, dass die falsche Datei angezeigt wird.

Um beispielsweise das Modul `Magento_Weee` zu deaktivieren, geben Sie Folgendes ein:

```bash
bin/magento module:disable Magento_Weee
```

Wichtige Informationen zum Aktivieren und Deaktivieren von Modulen finden Sie unter [Informationen zum Aktivieren und Deaktivieren von Modulen](#about-enabling-and-disabling-modules).

## Datenbank aktualisieren

Wenn Sie ein oder mehrere Module aktiviert haben, führen Sie den folgenden Befehl aus, um die Datenbank zu aktualisieren:

```bash
bin/magento setup:upgrade
```

Reinigen Sie dann den Cache:

```bash
bin/magento cache:clean
```

## Informationen zum Aktivieren und Deaktivieren von Modulen

Mit Adobe Commerce können Sie die derzeit verfügbaren Module aktivieren oder deaktivieren, d. h. alle von Adobe bereitgestellten Module oder die derzeit verfügbaren Drittanbietermodule.

Bestimmte Module weisen Abhängigkeiten von anderen Modulen auf. In diesem Fall können Sie ein Modul möglicherweise nicht aktivieren oder deaktivieren, da es Abhängigkeiten von anderen Modulen hat.

Darüber hinaus kann es *(widersprüchliche* Module geben, die nicht beide gleichzeitig aktiviert werden können.

Beispiele:

* Modul A hängt von Modul B ab. Sie können Modul B nur deaktivieren, wenn Sie zuerst Modul A deaktivieren.

* Modul A hängt von Modul B ab, beide sind deaktiviert. Sie müssen Modul B aktivieren, bevor Sie Modul A aktivieren können.

* Modul A steht in Konflikt mit Modul B. Sie können Modul A und Modul B deaktivieren oder eines der beiden Module deaktivieren, aber Sie *können* Modul A und Modul B gleichzeitig aktivieren.

* Abhängigkeiten werden im Feld `require` in der Adobe Commerce-`composer.json` für jedes Modul deklariert. Konflikte werden im Feld `conflict` in den `composer.json` der Module deklariert. Anhand dieser Informationen erstellen wir ein Abhängigkeitsdiagramm: `A->B` bedeutet, dass Modul A von Modul B abhängt.

* Eine *Abhängigkeitskette* ist der Pfad von einem Modul zu einem anderen. Wenn zum Beispiel Modul A von Modul B und Modul B von Modul C abhängt, dann ist die Abhängigkeitskette `A->B->C`.

Wenn Sie versuchen, ein Modul zu aktivieren oder zu deaktivieren, das von anderen Modulen abhängig ist, wird das Abhängigkeitsdiagramm in der Fehlermeldung angezeigt.

>[!NOTE]
>
>Es ist möglich, dass die `composer.json` von Modul A einen Konflikt mit Modul B erklärt, aber nicht umgekehrt.

*Nur Befehlszeile:* Um zu erzwingen, dass ein Modul unabhängig von seinen Abhängigkeiten aktiviert oder deaktiviert wird, verwenden Sie das optionale Argument `--force` .

>[!NOTE]
>
>Die Verwendung von `--force` kann Ihren Store deaktivieren und Probleme beim Zugriff auf den Admin verursachen.
