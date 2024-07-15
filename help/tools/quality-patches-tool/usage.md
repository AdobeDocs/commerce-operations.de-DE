---
title: Nutzung
description: Erfahren Sie, wie Sie den  [!DNL Quality Patches Tool] verwenden.
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# Nutzung

Die [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) liefert individuelle Patches, die von Adobe und der Magento Open Source Community entwickelt wurden. Damit können Sie allgemeine Informationen zu allen einzelnen Patches, die für die installierte Version von Adobe Commerce verfügbar sind, anwenden, wiederherstellen und anzeigen. Sie können Patches auf Adobe Commerce-Projekte anwenden, unabhängig davon, wer den Patch entwickelt hat. Sie können beispielsweise einen von der Community entwickelten Patch auf Adobe Commerce-Projekte anwenden.

Sehen Sie sich dieses [technische Video](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) an und erfahren Sie, wie Sie das Tool &quot;Qualitätsmuster&quot;für Adobe Commerce verwenden.

>[!INFO]
>
>Anweisungen zum Anwenden von Patches auf Adobe Commerce-Projekte finden Sie unter [Anwenden einzelner Patches](#apply-individual-patches) . Siehe [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) , um eine vollständige Liste der veröffentlichten Patches zu überprüfen.

>[!WARNING]
>
>Es wird nicht empfohlen, den [!DNL Quality Patches Tool]-Wert zu verwenden, um eine große Anzahl von Patches anzuwenden, da dies die Komplexität Ihres Codes erhöht und die Aktualisierung auf eine neue Version erschwert.

## Installieren

>[!INFO]
>
>Wenn es noch nicht installiert ist, müssen Sie [[!DNL Git]](https://github.com/git-guides/install-git) oder [Patch](https://man7.org/linux/man-pages/man1/patch.1.html) installieren, bevor Sie die [!DNL Quality Patches Tool] installieren. Fügen Sie das Paket `magento/quality-patches` Composer zu Ihrer Datei `composer.json` hinzu:

```bash
composer require magento/quality-patches
```

## Einzelne Patches anzeigen

So zeigen Sie die Liste der einzelnen Patches an, die für Ihre Adobe Commerce-Version verfügbar sind:

```bash
./vendor/bin/magento-patches status
```

Sie sehen die Ausgabe ähnlich der folgenden:

| ID | Titel | Typ | Status | Details |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC wird während der Bereitstellung deaktiviert | Optional | Nicht angewendet | Betroffene Komponenten:<br> - magento/module-page-cache |
| MCLOUD-5650 | Halten Sie die Bereitstellungskonfiguration fest, nachdem Sie die Datei gelesen haben | Optional | Nicht angewendet | Betroffene Komponenten:<br> - magento/framework |
| MCLOUD-5684 | Paginierung funktioniert nicht - product_list_limit=all | Optional | Nicht angewendet | Betroffene Komponenten: - magento/module-elasticsearch |
| MCLOUD-5837 | Problem mit dem Lastenausgleich beheben | Veraltet | Angewandt | Empfohlene Ersetzung: MC-1 <br> Betroffene Komponenten: - Magento/Framework |
| BUNDLE-2554 | Fehler mit Zahlungsinformationen festlegen | Optional | Nicht angewendet | Betroffene Komponenten: <br>- amzn/amazon-pay-module |
| MC-1 | Behebungsfehler 1 | Optional | Angewandt | Betroffene Komponenten: <br> - magento/module-cms |
| MC-2 | Behebungsfehler 2 | Optional | Nicht angewendet | Betroffene Komponenten: <br> - magento/module-cms |
| MC-3 | Behebungsfehler 3 | Optional | Nicht angewendet | Erforderliche Patches:<br> - MC-2 <br>Betroffene Komponenten: <br>- magento/module-cms |
| MC-3-V2 | Aktualisierte Fehlerbehebung für Problem 3 ersetzt den MC-3 Patch | Optional | Nicht zutreffend | Betroffene Komponenten: <br>- magento/module-cms |

Adobe Commerce 2.3.5.

Die Statustabelle enthält:

- **Typ**:
   - `Optional` - Alle Patches aus dem Paket [!DNL Quality Patches Tool] und dem Paket [Commerce on Cloud Infrastructure Guide > Apply patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) sind für Adobe Commerce-Installationen optional.
   - `Deprecated` - Adobe hat den einzelnen Patch nicht mehr unterstützt. Wenn Sie den Patch angewendet haben, empfehlen wir Ihnen, ihn zurückzusetzen. Der Vorgang &quot;Reverse&quot;entfernt auch den Patch aus der Statustabelle.

- **Status**:
   - `Applied` - Der Patch wurde angewendet.
   - `Not applied` - Der Patch wurde nicht angewendet.
   - `N/A` - Der Status des Patch kann aufgrund von Konflikten nicht definiert werden.

- **Details**:
   - `Affected components` - Die Liste der betroffenen Module.
   - `Required patches` - Die Liste der Patches, die angewendet werden müssen, damit ein angegebener Patch ordnungsgemäß funktioniert (Abhängigkeiten).
   - `Recommended replacement` - Der Patch, der als Ersatz für einen veralteten Patch empfohlen wird.

>[!INFO]
>
>Nach dem Upgrade auf eine neue Version von Adobe Commerce müssen Sie Patches erneut anwenden, wenn die Patches nicht in der neuen Version enthalten sind. Siehe [Erneutes Anwenden von Patches nach einem Upgrade](#re-apply-patches-after-an-upgrade).

## Anwenden einzelner Patches {#apply-individual-patches}

>[!WARNING]
>
>Es empfiehlt sich, alle Patches in einer Staging- oder Entwicklungsumgebung zu testen, bevor sie in der Produktion bereitgestellt werden. Es wird auch empfohlen, Ihre Daten vor dem Anwenden eines Patches zu sichern. Siehe [Backup and Rollback the file system, media, and database](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Um einen einzelnen Patch anzuwenden, führen Sie den folgenden Befehl aus, wobei `MAGETWO-XXXX` die Patch-ID ist, die in der Statustabelle angegeben ist:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

Sie können auch mehrere Patches gleichzeitig anwenden, indem Sie jede zusätzliche Patch-ID durch ein Leerzeichen trennen:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Sie müssen den Cache nach dem Anwenden von Patches bereinigen, um Änderungen in der Adobe Commerce-Anwendung zu sehen:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Erwägen Sie, eine Liste der angewendeten Patches an einem anderen Ort zu speichern. Möglicherweise müssen Sie einige von ihnen nach dem Upgrade auf eine neue Version von Adobe Commerce erneut anwenden. Siehe [Erneutes Anwenden von Patches nach einem Upgrade](#re-apply-patches-after-an-upgrade).

## Zurücksetzen einzelner Patches

>[!WARNING]
>
>Es empfiehlt sich, alle Patches in einer Staging- oder Entwicklungsumgebung zu testen, bevor sie in der Produktion bereitgestellt werden. Es wird auch empfohlen, Ihre Daten vor dem Anwenden eines Patches zu sichern. Siehe [Backup and Rollback the file system, media, and database](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Um einen einzelnen Patch wiederherzustellen, führen Sie den folgenden Befehl aus, wobei `MAGETWO-XXXX` die Patch-ID ist, die in der Statustabelle angegeben ist:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

Außerdem können Sie mehrere Patches gleichzeitig wiederherstellen, indem Sie jede zusätzliche Patch-ID durch ein Leerzeichen trennen:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

So stellen Sie alle angewendeten Patches wieder her:

```bash
./vendor/bin/magento-patches revert --all
```

Sie müssen den Cache nach dem Wiederherstellen von Patches bereinigen, um Änderungen in der Adobe Commerce-Anwendung zu sehen:

```bash
./bin/magento cache:clean
```

## Aktualisierungen abrufen

Adobe Commerce veröffentlicht regelmäßig neue individuelle Patches. Sie müssen die [!DNL Quality Patches Tool] aktualisieren, um neue einzelne Patches zu erhalten:

```bash
composer update magento/quality-patches
```

Zeigen Sie die hinzugefügten Patches an:

>[!TIP]
>
>Am unteren Rand der Tabelle werden neue Hinzufügen-Patches angezeigt.

```bash
./vendor/bin/magento-patches status
```

## Erneutes Anwenden von Patches nach einem Upgrade {#re-apply-patches-after-an-upgrade}

Beim Upgrade auf eine neue Version von Adobe Commerce müssen Sie Patches erneut anwenden, wenn die Patches nicht in der neuen Version enthalten sind.

So wenden Sie Patches erneut an:

1. Aktualisieren Sie die [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Öffnen Sie die Liste der zuvor angewendeten Patches, die in [Anwenden einzelner Patches](#apply-individual-patches) empfohlen wurde.

1. Wenden Sie die Patches an:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   Am besten wenden Sie Patches einzeln an.

1. Cache leeren:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Wenn Sie den Befehl `status` ausführen, werden die in der neuen Version enthaltenen Patches nicht mehr in der Tabelle der verfügbaren Patches angezeigt.

## Protokollierung

Die [!DNL Quality Patches Tool] protokolliert alle Vorgänge in der Datei `<Magento_root>/var/log/patch.log`.
