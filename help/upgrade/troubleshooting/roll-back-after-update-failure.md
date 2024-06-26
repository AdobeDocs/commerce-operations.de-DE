---
title: Zurücksetzen nach einem Fehler bei der Modulaktualisierung
description: Fehlerbehebung bei Ihrem Adobe Commerce-Upgrade nach Auftreten eines Modulaktualisierungsfehlers.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# Zurücksetzen nach einem Fehler bei der Modulaktualisierung

Wenn die Aktualisierung Ihres Moduls fehlschlägt, werden ähnliche Meldungen im Konsolenprotokoll angezeigt:

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

Im obigen Beispiel gibt es keine Komponentenversion, auf die zurückgegriffen werden kann. Wenden Sie sich an den Komponentenanbieter oder versuchen Sie, das Problem selbst zu beheben.

In der Zwischenzeit können Sie eine frühere Version wiederherstellen, indem Sie auf **Rollback**, wodurch Ihre Daten auch dann abgerufen werden, wenn Sie zuvor keine Sicherung durchgeführt haben.
