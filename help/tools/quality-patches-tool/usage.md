---
title: Nutzung
description: Erfahren Sie, wie Sie die [!DNL Quality Patches Tool].
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Nutzung

Die [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) bietet individuelle Patches, die von Adobe und der Magento Open Source Community entwickelt wurden. Damit können Sie allgemeine Informationen zu allen einzelnen Patches, die für die installierte Version von Adobe Commerce oder Magento Open Source verfügbar sind, anwenden, wiederherstellen und anzeigen. Sie können Patches auf Adobe Commerce- und Magento Open Source-Projekte anwenden, unabhängig davon, wer den Patch entwickelt hat. Sie können beispielsweise einen von der Community entwickelten Patch auf Adobe Commerce-Projekte anwenden.


Sehen Sie sich dies an [technisches Video](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) und erfahren Sie, wie Sie das Tool &quot;Qualitätsmuster&quot;für Adobe Commerce und Magento Open Source verwenden.

>[!INFO]
>
>Siehe [Anwenden einzelner Patches](#apply-individual-patches) für Anweisungen zum Anwenden von Patches auf Ihre Adobe Commerce- oder Magento Open Source-Projekte. Siehe [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) , um eine vollständige Liste der veröffentlichten Patches zu überprüfen.

>[!WARNING]
>
>Es wird nicht empfohlen, die [!DNL Quality Patches Tool] , um eine große Anzahl von Patches anzuwenden, da dies die Komplexität Ihres Codes erhöht und die Aktualisierung auf eine neue Version erschwert.

## Installieren

>[!INFO]
>
>Wenn es noch nicht installiert ist, müssen Sie [[!DNL Git]](https://github.com/git-guides/install-git) oder [Patch](https://man7.org/linux/man-pages/man1/patch.1.html) vor der Installation [!DNL Quality Patches Tool]. Fügen Sie die `magento/quality-patches` Composer-Paket zu Ihrem `composer.json` Datei:

```bash
composer require magento/quality-patches
```

## Einzelne Patches anzeigen

So zeigen Sie die Liste der einzelnen Patches an, die für Ihre Adobe Commerce- oder Magento Open Source-Version verfügbar sind:

```bash
./vendor/bin/magento-patches status
```

Sie sehen die Ausgabe ähnlich der folgenden:

| ID | Titel | Typ | Status | Details |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC wird während der Bereitstellung deaktiviert | Optional | Nicht angewendet | Betroffene Komponenten:<br> - magento/module-page-cache |
| MCLOUD-5650 | Halten Sie die Bereitstellungskonfiguration fest, nachdem Sie die Datei gelesen haben | Optional | Nicht angewendet | Betroffene Komponenten:<br> - Magento/Framework |
| MCLOUD-5684 | Paginierung funktioniert nicht - product_list_limit=all | Optional | Nicht angewendet | Betroffene Komponenten: - magento/module-elasticsearch |
| MCLOUD-5837 | Problem mit dem Lastenausgleich beheben | Veraltet | Angewandt | Empfohlener Ersatz: MC-1 <br> Betroffene Komponenten: - Magento/Framework |
| BUNDLE-2554 | Fehler mit Zahlungsinformationen festlegen | Optional | Nicht angewendet | Betroffene Komponenten: <br>- amzn/amazon-pay-module |
| MC-1 | Behebungsfehler 1 | Optional | Angewandt | Betroffene Komponenten: <br> - magento/module-cms |
| MC-2 | Behebungsfehler 2 | Optional | Nicht angewendet | Betroffene Komponenten: <br> - magento/module-cms |
| MC-3 | Behebungsfehler 3 | Optional | Nicht angewendet | Erforderliche Patches:<br> - MC-2 <br>Betroffene Komponenten: <br>- magento/module-cms |
| MC-3-V2 | Aktualisierte Fehlerbehebung für Problem 3 ersetzt den MC-3 Patch | Optional | Nicht zutreffend | Betroffene Komponenten:  <br>- magento/module-cms |

Adobe Commerce 2.3.5.

Die Statustabelle enthält:

- **Typ**:
   - `Optional` — Alle Patches der [!DNL Quality Patches Tool] und [Commerce on Cloud Infrastructure Guide > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) Das -Paket ist für Installationen von Adobe Commerce und Magento Open Source optional.
   - `Deprecated` — Adobe hat das einzelne Pflaster veraltet. Wenn Sie den Patch angewendet haben, empfehlen wir Ihnen, ihn zurückzusetzen. Der Vorgang &quot;Reverse&quot;entfernt auch den Patch aus der Statustabelle.

- **Status**:
   - `Applied` — Das Pflaster wurde aufgebracht.
   - `Not applied` — Das Pflaster wurde nicht aufgebracht.
   - `N/A` — Der Status des Patches kann aufgrund von Konflikten nicht definiert werden.

- **Details**:
   - `Affected components` — Die Liste der betroffenen Module.
   - `Required patches` — Die Liste der Patches, die für einen angegebenen Patch angewendet werden müssen, damit er ordnungsgemäß funktioniert (Abhängigkeiten).
   - `Recommended replacement` — Das Patch, das als Ersatz für ein veraltetes Patch empfohlen wird.

>[!INFO]
>
>Nach dem Upgrade auf eine neue Version von Adobe Commerce oder Magento Open Source müssen Sie Patches erneut anwenden, wenn die Patches nicht in der neuen Version enthalten sind. Siehe [Erneutes Anwenden von Patches nach einem Upgrade](#re-apply-patches-after-an-upgrade).

## Anwenden einzelner Patches {#apply-individual-patches}

>[!WARNING]
>
>Es empfiehlt sich, alle Patches in einer Staging- oder Entwicklungsumgebung zu testen, bevor sie in der Produktion bereitgestellt werden. Es wird auch empfohlen, Ihre Daten vor dem Anwenden eines Patches zu sichern. Siehe [Backup und Rollback des Dateisystems, der Medien und der Datenbank](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Um einen einzelnen Patch anzuwenden, führen Sie den folgenden Befehl aus, wobei `MAGETWO-XXXX` ist die Patch-ID, die in der Statustabelle angegeben ist:

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
>Erwägen Sie, eine Liste der angewendeten Patches an einem anderen Ort zu speichern. Möglicherweise müssen Sie einige von ihnen erneut anwenden, nachdem Sie auf eine neue Version von Adobe Commerce oder Magento Open Source aktualisiert haben. Siehe [Erneutes Anwenden von Patches nach einem Upgrade](#re-apply-patches-after-an-upgrade).

## Zurücksetzen einzelner Patches

>[!WARNING]
>
>Es empfiehlt sich, alle Patches in einer Staging- oder Entwicklungsumgebung zu testen, bevor sie in der Produktion bereitgestellt werden. Es wird auch empfohlen, Ihre Daten vor dem Anwenden eines Patches zu sichern. Siehe [Backup und Rollback des Dateisystems, der Medien und der Datenbank](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Um einen einzelnen Patch wiederherzustellen, führen Sie den folgenden Befehl aus, wobei `MAGETWO-XXXX` ist die Patch-ID, die in der Statustabelle angegeben ist:

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

Adobe Commerce veröffentlicht regelmäßig neue individuelle Patches. Sie müssen die [!DNL Quality Patches Tool] um neue individuelle Patches zu erhalten:

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

Beim Upgrade auf eine neue Version von Adobe Commerce oder Magento Open Source müssen Sie Patches erneut anwenden, wenn die Patches nicht in der neuen Version enthalten sind.

So wenden Sie Patches erneut an:

1. Aktualisieren Sie die [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Öffnen Sie die Liste der zuvor angewendeten Patches, die in [Anwenden einzelner Patches](#apply-individual-patches).

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
   >Wenn Sie die `status` -Befehl, werden die in der neuen Version enthaltenen Patches nicht mehr in der Tabelle der verfügbaren Patches angezeigt.

## Protokollierung

Die [!DNL Quality Patches Tool] protokolliert alle Vorgänge in `<Magento_root>/var/log/patch.log` -Datei.
