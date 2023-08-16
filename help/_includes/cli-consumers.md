---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# CLI-Optionen für Nachrichtenwarteschlangen-Verbraucher

| Name | Beschreibung | Wert | Erforderlich |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Bestimmt, ob Verbraucher auf eine Nachricht aus der Warteschlange warten. | 1 - Ja, 0 - Nein | Nein |

* `0`: Die Verbraucher verarbeiten verfügbare Nachrichten in der Warteschlange, schließen die TCP-Verbindung und beenden sie. Die Verbraucher warten nicht darauf, dass zusätzliche Nachrichten in die Warteschlange gelangen, selbst wenn die Anzahl der verarbeiteten Nachrichten kleiner ist als die Anzahl der `--max_messages` -Wert, der beim Starten von Verbrauchern angegeben wird.

* `1`: Verbraucher verarbeiten weiterhin Nachrichten aus der Nachrichtenwarteschlange, bis sie die maximale Nachrichtenanzahl erreichen (der für `--max_messages` auf `queue:consumers:start` -Befehl), bevor Sie die TCP-Verbindung schließen und den Consumer-Prozess beenden. Wenn die Warteschlange vor dem Erreichen geleert wird `--max_messages` der Verbraucher wartet auf das Eintreffen weiterer Nachrichten. Wenn Sie Sekundäre verwenden, um Verbraucher anstatt eines Cron-Auftrags auszuführen, setzen Sie diese Variable auf `1`.

>[!WARNING]
>
>Die `--consumers-wait-for-messages` -Option ist eine globale Option und kann nicht für jeden Verbraucher einzeln konfiguriert werden.
