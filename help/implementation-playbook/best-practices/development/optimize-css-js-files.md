---
title: Optimieren von CSS- und JS-Ressourcendateien
description: Erfahren Sie, wie Sie CSS- und JavaScript-Dateien (JS) für Adobe Commerce-Projekte über die Admin-Benutzeroberfläche oder die Befehlszeile zusammenführen und minimieren können.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 5f4edc2e694c9bdbdffbe48b0e5d69907cbc0027
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Ressourcendateien optimieren

Für eine reaktionsschnellere Commerce-Site optimieren Sie CSS- und JavaScript (JS)-Ressourcendateien und eliminieren Sie Render-Blocking-Ressourcen.

- **Optimieren von CSS- und JS-Dateien** - Verringern Sie den Zeitaufwand für das Laden von CSS- und JavaScript (JS)-Dateien, indem Sie Adobe Commerce so konfigurieren, dass separate Dateien zusammengeführt, minimiert und zu einer einzigen Datei gebündelt werden.
- **Eliminieren von Render-Blocking-Ressourcen** - Erwägen Sie, wichtige JS- und CSS-Funktionen inline bereitzustellen und alle nicht kritischen JS-/CSS-Stile zurückzustellen. Eine Anleitung finden Sie unter [Beseitigen von Render-Blocker-Ressourcen](https://web.dev/render-blocking-resources/).

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen 2.3 und höher](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Zusammenführen oder Minimieren von CSS-Dateien

Der Zeitaufwand für das Laden von CSS- und JavaScript-Dateien (JS) kann reduziert werden, indem separate Dateien zusammengeführt, minimiert und zu einer einzigen Datei gebündelt werden.

>[!IMPORTANT]
>
>Adobe Commerce in der Cloud-Infrastruktur wird immer im Produktionsmodus ausgeführt und kann nicht anderweitig festgelegt werden. Daher müssen Sie die Befehlszeilenmethode verwenden, um das Zusammenführen, Minimieren und Bündeln zu aktivieren.

Führen Sie keine Dateien zusammen oder bündeln Sie sie, wenn Ihre Bereitstellung HTTP/2 verwendet. HTTP/2 lädt statische Dateien asynchron herunter. Browser müssen eine gesamte zusammengeführte Datei herunterladen, bevor sie den Dateiinhalt verarbeiten können.

### Verwenden von Admin

Um die CSS-Zusammenführung oder -Minimierung zu aktivieren, navigieren Sie zu [!UICONTROL **Admin** > **Stores** > **Setting** > **Configuration** > **Advanced** > **Developer** > **CSS Settings**].

### Verwenden der Befehlszeile

So aktivieren Sie die CSS-Zusammenführung in Adobe Commerce in der Cloud-Infrastruktur:

1. Führen Sie diesen Befehl lokal aus:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Übertragen Sie Änderungen in die `app/etc/config.php` und stellen Sie sie erneut bereit.

So aktivieren Sie die CSS-Minimierung in Adobe Commerce in der Cloud-Infrastruktur:

1. Führen Sie diesen Befehl lokal aus:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Übertragen Sie Änderungen in die `app/etc/config.php` und stellen Sie sie erneut bereit.

## Minimieren von JS-Dateien

### Verwenden von Admin

Navigieren Sie in *Admin*-Seitenleiste zu **Stores** > **Settings** > **Configuration** > **Advanced** > **Developer** > **JavaScript Settings**.

### Verwenden der Befehlszeile

So aktivieren Sie die JS-Minimierung in Adobe Commerce auf der Cloud-Infrastruktur:

1. Führen Sie diesen Befehl lokal aus:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Übertragen Sie Änderungen in die `app/etc/config.php` und stellen Sie sie erneut bereit.

## Zusammenführen und Bündeln von JS-Dateien

Sie können das Zusammenführen oder Bündeln in Commerce Admin aktivieren (Zusammenführen und Bündeln können nicht gleichzeitig aktiviert werden): [!UICONTROL **Stores** > **Settings** > **Configuration** > **Advanced** > **Developer** > **JavaScript Settings**].

Sie können auch über die Befehlszeile die integrierte Bündelung (Basic Bundling) von Adobe Commerce aktivieren:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Weitere Informationen

- [Client-seitige Optimierungseinstellungen](../../../performance/configuration.md#client-side-optimization-settings)
- [Benutzerhandbuch: Ressourcendateien optimieren](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Frontend-Entwicklerhandbuch: CSS-Zusammenführung, Minimierung und Site-Performance](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Erweiterte JavaScript-Pakete](../../../performance/advanced-js-bundling.md)
