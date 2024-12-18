---
title: Nutzung
description: Erfahren Sie, wie Sie die  [!DNL Quality Patches Tool].
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# Nutzung

Das [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) liefert individuelle Patches, die von Adobe und der Magento Open Source-Community entwickelt wurden. Damit können Sie allgemeine Informationen zu allen einzelnen Patches, die für die installierte Version von Adobe Commerce verfügbar sind, anwenden, zurücksetzen und anzeigen. Sie können Patches auf Adobe Commerce-Projekte anwenden, unabhängig davon, wer den Patch entwickelt hat. Sie können beispielsweise einen von der Community entwickelten Patch auf Adobe Commerce-Projekte anwenden.

In diesem [technischen Video](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) erfahren Sie, wie Sie das Quality Patches Tool für Adobe Commerce verwenden.

>[!INFO]
>
>Anweisungen [ Anwenden von Patches auf Ihre Adobe Commerce](#apply-individual-patches)Projekte finden Sie unter „Anwenden einzelner Patches“. Siehe [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) um eine vollständige Liste der veröffentlichten Patches anzuzeigen.

>[!WARNING]
>
>Es wird nicht empfohlen, die [!DNL Quality Patches Tool] zum Anwenden einer großen Anzahl von Patches zu verwenden, da dies die Komplexität Ihres Codes erhöht und die Aktualisierung auf eine neue Version erschwert.

## Installieren von

>[!INFO]
>
>Wenn es noch nicht installiert ist, müssen Sie [[!DNL Git]](https://github.com/git-guides/install-git) oder [Patch](https://man7.org/linux/man-pages/man1/patch.1.html) installieren, bevor Sie die [!DNL Quality Patches Tool] installieren. Fügen Sie das `magento/quality-patches` Composer-Paket zu Ihrer `composer.json` hinzu:

```bash
composer require magento/quality-patches
```

## Anzeigen einzelner Patches

So zeigen Sie die Liste der einzelnen Patches an, die für Ihre Version von Adobe Commerce verfügbar sind:

```bash
./vendor/bin/magento-patches status
```

Es wird eine Ausgabe ähnlich der folgenden angezeigt:

| ID | Titel | Typ | Status | Details |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC wird während der Bereitstellung deaktiviert | optional | Nicht angewendet | Betroffene Komponenten:<br> - magento/module-page-cache |
| MCLOUD-5650 | Bereitstellungskonfiguration nach dem Lesen aus der Datei speichern | optional | Nicht angewendet | Betroffene Komponenten:<br> - Magento/Framework |
| MCLOUD-5684 | Paginierung funktioniert nicht - product_list_limit=all | optional | Nicht angewendet | Betroffene Komponenten: - magento/module-elasticsearch |
| MCLOUD-5837 | Problem mit dem Lastenausgleich beheben | Veraltet | Angewendet | Empfohlener Austausch: MC-1 <br> Betroffene Komponenten: - Magento/Framework |
| BUNDLE-2554 | Fehler bei Zahlungsinformationen festlegen | optional | Nicht angewendet | Betroffene Komponenten: <br>- amzn/amazon-pay-module |
| MC-1 | Behebt Problem 1 | optional | Angewendet | Betroffene Komponenten: <br> - magento/module-cms |
| MC-2 | Behebt Problem 2 | optional | Nicht angewendet | Betroffene Komponenten: <br> - magento/module-cms |
| MC-3 | Behebt Problem 3 | optional | Nicht angewendet | Erforderliche Patches:<br> - MC-2 <br>Betroffene Komponenten: <br>- magento/module-cms |
| MC-3-V2 | Fehlerkorrektur für Problem 3 aktualisiert, ersetzt MC-3-Patch | optional | Nicht zutreffend | Betroffene Komponenten: <br>- magento/module-cms |

Adobe Commerce 2.3.5.

Die Statustabelle enthält:

- **Typ**:
   - `Optional` - Alle Patches aus dem [!DNL Quality Patches Tool] und dem Paket [Handbuch für Commerce in Cloud-Infrastruktur > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) sind für Adobe Commerce-Installationen optional.
   - `Deprecated` - Adobe hat den einzelnen Patch nicht mehr unterstützt. Wenn Sie das Pflaster aufgeklebt haben, empfehlen wir, es rückgängig zu machen. Der Wiederherstellungsvorgang entfernt auch den Patch aus der Statustabelle.

- **Status**:
   - `Applied` - Das Patch wurde angewendet.
   - `Not applied` - Das Patch wurde nicht angewendet.
   - `N/A` - Der Status des Patches kann aufgrund von Konflikten nicht definiert werden.

- **Details**:
   - `Affected components` - Die Liste der betroffenen Module.
   - `Required patches` - Die Liste der Patches, die angewendet werden müssen, damit ein angegebenes Patch ordnungsgemäß funktioniert (Abhängigkeiten).
   - `Recommended replacement` - Das Patch, das als Ersatz für einen veralteten Patch empfohlen wird.

>[!INFO]
>
>Nach dem Upgrade auf eine neue Version von Adobe Commerce müssen Sie Patches erneut anwenden, wenn die Patches nicht in der neuen Version enthalten sind. Siehe [Erneutes Anwenden von Patches nach einem Upgrade](#re-apply-patches-after-an-upgrade).

## Anwenden einzelner Patches {#apply-individual-patches}

>[!WARNING]
>
>Es empfiehlt sich, alle Patches in einer Staging- oder Entwicklungsumgebung zu testen, bevor sie in der Produktion bereitgestellt werden. Es wird außerdem empfohlen, eine Sicherungskopie der Daten zu erstellen, bevor Sie ein Patch anwenden. Siehe [Sichern und Rollback des Dateisystems, der Medien und der Datenbank](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Um einen einzelnen Patch anzuwenden, führen Sie den folgenden Befehl aus, wobei `MAGETWO-XXXX` die in der Statustabelle angegebene Patch-ID ist:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

Sie können auch mehrere Patches gleichzeitig anwenden, indem Sie jede zusätzliche Patch-ID durch ein Leerzeichen trennen:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Sie müssen den Cache nach dem Anwenden von Patches bereinigen, um Änderungen in der Adobe Commerce-Anwendung sehen zu können:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Sie sollten eine Liste der angewendeten Patches an einem separaten Speicherort aufbewahren. Möglicherweise müssen Sie einige davon nach dem Upgrade auf eine neue Version von Adobe Commerce erneut anwenden. Siehe [Erneutes Anwenden von Patches nach einem Upgrade](#re-apply-patches-after-an-upgrade).

## Einzelne Patches zurücksetzen

>[!WARNING]
>
>Es empfiehlt sich, alle Patches in einer Staging- oder Entwicklungsumgebung zu testen, bevor sie in der Produktion bereitgestellt werden. Es wird außerdem empfohlen, eine Sicherungskopie der Daten zu erstellen, bevor Sie ein Patch anwenden. Siehe [Sichern und Rollback des Dateisystems, der Medien und der Datenbank](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Um einen einzelnen Patch wiederherzustellen, führen Sie den folgenden Befehl aus, wobei `MAGETWO-XXXX` die in der Statustabelle angegebene Patch-ID ist:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

Außerdem können Sie mehrere Patches gleichzeitig rückgängig machen, indem Sie jede zusätzliche Patch-ID durch ein Leerzeichen trennen:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

So setzen Sie alle angewendeten Patches zurück:

```bash
./vendor/bin/magento-patches revert --all
```

Sie müssen den Cache nach dem Zurücksetzen von Patches bereinigen, um Änderungen in der Adobe Commerce-Anwendung sehen zu können:

```bash
./bin/magento cache:clean
```

## Updates abrufen

Adobe Commerce veröffentlicht regelmäßig neue individuelle Patches. Sie müssen die [!DNL Quality Patches Tool] aktualisieren, um neue einzelne Patches zu erhalten:

```bash
composer update magento/quality-patches
```

Anzeigen der hinzugefügten Patches:

>[!TIP]
>
>Neue Patches hinzufügen werden unten in der Tabelle angezeigt.

```bash
./vendor/bin/magento-patches status
```

## Patches nach einem Upgrade erneut anwenden {#re-apply-patches-after-an-upgrade}

Wenn Sie ein Upgrade auf eine neue Version von Adobe Commerce durchführen, müssen Sie die Patches erneut anwenden, wenn die Patches nicht in der neuen Version enthalten sind.

So wenden Sie Patches erneut an:

1. Aktualisieren Sie die [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Öffnen Sie die Liste der zuvor angewendeten Patches, die unter [Anwenden einzelner Patches“ empfohlen ](#apply-individual-patches).

1. Patches anwenden:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   Es empfiehlt sich, Patches einzeln anzuwenden.

1. Cache leeren:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Wenn Sie den `status` Befehl ausführen, werden die in der neuen Version enthaltenen Patches nicht mehr in der Tabelle der verfügbaren Patches angezeigt.

## Protokollierung

Die [!DNL Quality Patches Tool] protokolliert alle Vorgänge in der `<Magento_root>/var/log/patch.log`.
