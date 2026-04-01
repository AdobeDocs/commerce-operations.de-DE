---
title: Optimieren von CSS- und JS-Ressourcendateien
description: Erfahren Sie, wie Sie CSS- und JavaScript-Dateien (JS) für Adobe Commerce-Projekte über die Admin-Benutzeroberfläche oder die Befehlszeile zusammenführen und minimieren können.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: a08560eb307638a36fdc52224c41bdf2c5d47763
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Ressourcendateien optimieren

Für eine reaktionsschnellere Commerce-Site optimieren Sie CSS- und JavaScript (JS)-Ressourcendateien und eliminieren Sie Render-Blocking-Ressourcen.

- **Optimieren von CSS- und JS-Dateien** - Verringern Sie den Zeitaufwand für das Laden von CSS- und JavaScript-Dateien (JS), indem Sie Adobe Commerce so konfigurieren, dass Dateien minimiert und gebündelt werden.
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

Um die CSS-Zusammenführung oder -Minimierung zu aktivieren, navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL CSS Settings]**.

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

### Verwenden von [!UICONTROL Admin]

Navigieren Sie in der [!UICONTROL Admin] Seitenleiste zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

### Verwenden der Befehlszeile

So aktivieren Sie die JS-Minimierung in Adobe Commerce auf der Cloud-Infrastruktur:

1. Führen Sie diesen Befehl lokal aus:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Übertragen Sie Änderungen in die `app/etc/config.php` und stellen Sie sie erneut bereit.

## Bundle-JS-Dateien

Sie können die Bündelung im Commerce-[!UICONTROL Admin] aktivieren: **[!UICONTROL Stores]** > ***[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

>[!NOTE]
>
>Zusammenführung und Bündelung können nicht gleichzeitig aktiviert werden.

Sie können auch über die Befehlszeile die integrierte Bündelung (Basic Bundling) von Adobe Commerce aktivieren:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Zusammenführen von JS-Dateien (nicht empfohlen) {#merge-js-files}

>[!WARNING]
>
>Es wird nicht empfohlen, **[!UICONTROL Merge JavaScript Files]** zu aktivieren. Diese Einstellung wurde nur für synchron geladene JavaScript im **[!UICONTROL HEAD]** Abschnitt der Seite entwickelt und kann dazu führen, dass Bundles und [!DNL RequireJS] nicht korrekt funktionieren. Sie wird nur aus Gründen der Abwärtskompatibilität beibehalten und bietet keinen Leistungsvorteil, wenn HTTP/2 aktiviert ist.
>
>Wenn Sie **[!UICONTROL Merge JavaScript Files]** aktiviert haben und Probleme auftreten, versuchen Sie, es zu deaktivieren, bevor Sie Patches anwenden. Siehe [ACSD-67908](../../../tools/quality-patches-tool/patches-available-in-qpt/v1-1-73/acsd-67908.md), wenn Sie die Zusammenführung nicht deaktivieren können.

## Weitere Informationen

- [Client-seitige Optimierungseinstellungen](../../../performance/configuration.md#client-side-optimization-settings)
- [Tipps zur ](../../../performance/configuration.md#bundling-tips) in *Best Practices für die Konfiguration* - Bundle-Tools von Drittanbietern, HTTP/2 und Anleitungen zur veralteten JS- und CSS-Zusammenführung
- [Benutzerhandbuch: Ressourcendateien optimieren](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Frontend-Entwicklerhandbuch: CSS-Zusammenführung, Minimierung und Site-Performance](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Erweiterte JavaScript-Pakete](../../../performance/advanced-js-bundling.md)
