---
title: CSS- und JS-Ressourcendateien optimieren
description: Erfahren Sie, wie Sie CSS- und JavaScript (JS)-Dateien für Adobe Commerce-Projekte über den Admin oder über die Befehlszeile zusammenführen und minimieren können.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Optimieren von Ressourcendateien

Optimieren Sie für eine reaktionsfähigere Commerce-Site CSS- und JavaScript-Ressourcendateien (JS) und eliminieren Sie Renderer-Blockierungsressourcen.

- **CSS- und JS-Dateien optimieren**: Reduzieren Sie die zum Laden von CSS- und JavaScript (JS)-Dateien erforderliche Zeit, indem Sie Adobe Commerce so konfigurieren, dass separate Dateien zusammengeführt, minimiert und in einer Datei zusammengefasst werden.
- **Renderer-Blocker-Ressourcen eliminieren** - Erwägen Sie die Inline-Bereitstellung kritischer JS- und CSS-Funktionen und die Verschiebung aller nicht kritischen JS-/CSS-Stile. Eine Anleitung finden Sie unter [Renderer-Blocker-Ressourcen beseitigen](https://web.dev/render-blocking-resources/).

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen, 2.3 und höher](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Zusammenführen oder Minimieren von CSS-Dateien

Die Ladezeit von CSS- und JavaScript-Dateien (JS) kann durch Zusammenführen, Minimieren und Bündeln separater Dateien in einer Datei reduziert werden.

>[!IMPORTANT]
>
>Adobe Commerce in der Cloud-Infrastruktur wird immer im Produktionsmodus ausgeführt. Andernfalls ist es nicht möglich, sie festzulegen. Daher müssen Sie die Befehlszeilenmethode verwenden, um das Zusammenführen, Minimieren und Bundling zu ermöglichen.

Führen Sie keine Dateien zusammen oder bündeln Sie sie, wenn Ihre Bereitstellung HTTP/2 verwendet. HTTP/2 lädt statische Dateien asynchron herunter. Browser müssen eine gesamte zusammengeführte Datei herunterladen, bevor die Dateiinhalte verarbeitet werden.

### Verwenden von Admin

Um die CSS-Zusammenführung oder -Minimierung zu aktivieren, gehen Sie zu &quot;[!UICONTROL **Admin**&quot;> &quot;**Stores**&quot;> &quot;**Einstellung**&quot;> &quot;**Konfiguration**&quot;> &quot;**Erweitert**&quot;> &quot;**Entwickler**&quot;> &quot;**CSS-Einstellungen**]&quot;.

### Befehlszeile verwenden

Aktivieren der CSS-Zusammenführung in Adobe Commerce in der Cloud-Infrastruktur:

1. Führen Sie diesen Befehl lokal aus:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Übertragen Sie Änderungen an der Datei &quot;`app/etc/config.php`&quot;und stellen Sie sie erneut bereit.

Aktivieren der CSS-Minimierung in Adobe Commerce in der Cloud-Infrastruktur:

1. Führen Sie diesen Befehl lokal aus:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Übertragen Sie Änderungen an der Datei &quot;`app/etc/config.php`&quot;und stellen Sie sie erneut bereit.

## Minimieren von JS-Dateien

### Verwenden von Admin

Wechseln Sie in der Seitenleiste *Admin* zu **Stores** > **Einstellungen** > **Konfiguration** > **Erweitert** > **Entwickler** > **JavaScript-Einstellungen**.

### Befehlszeile verwenden

Aktivieren der JS-Minimierung in Adobe Commerce in der Cloud-Infrastruktur:

1. Führen Sie diesen Befehl lokal aus:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Übertragen Sie Änderungen an der Datei &quot;`app/etc/config.php`&quot;und stellen Sie sie erneut bereit.

## Zusammenführen und Bundle von JS-Dateien

Sie können das Zusammenführen oder Bundling im Commerce Admin aktivieren (das Zusammenführen und Bundling kann nicht gleichzeitig aktiviert werden): [!UICONTROL **Stores** > **Einstellungen** > **Konfiguration** > **Erweitert** > **Entwickler** > **JavaScript-Einstellungen**].

Sie können auch das integrierte Adobe Commerce-Bundling (Basis-Bundling) über die Befehlszeile aktivieren:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Weitere Informationen

- [Clientseitige Optimierungseinstellungen](../../../performance/configuration.md#client-side-optimization-settings)
- [Benutzerhandbuch: Optimieren von Ressourcendateien](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Frontend-Entwicklerhandbuch: CSS-Zusammenführung, Minimierung und Site-Leistung](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Erweitertes JavaScript-Bundling](../../../performance/advanced-js-bundling.md)
