---
title: Zurücksetzen nach fehlgeschlagener Modulaktualisierung
description: Fehlerbehebung beim Adobe Commerce-Upgrade nach Auftreten eines Modulaktualisierungsfehlers.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Zurücksetzen nach fehlgeschlagener Modulaktualisierung

Wenn die Aktualisierung des Moduls fehlschlägt, werden Meldungen ähnlich der folgenden im Konsolenprotokoll angezeigt:

```
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

Im vorherigen Beispiel gibt es keine Komponentenversion, auf die zurückgesetzt werden kann. Wenden Sie sich an den Komponentenanbieter oder versuchen Sie, das Problem selbst zu beheben.

In der Zwischenzeit können Sie zu einer früheren Version zurückkehren, indem Sie auf **Rollback** klicken, wodurch Ihre Daten auch dann wiederhergestellt werden, wenn Sie zuvor keine Sicherung durchgeführt haben.
