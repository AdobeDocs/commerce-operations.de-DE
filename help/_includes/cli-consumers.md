---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# CLI-Optionen für Nachrichtenwarteschlangen-Verbraucher

| Name | Beschreibung | Wert | Erforderlich |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Bestimmt, ob Verbraucher auf eine Nachricht aus der Warteschlange warten. | 1 - Ja, 0 - Nein | Nein |

* `0`: Die Verbraucher verarbeiten verfügbare Nachrichten in der Warteschlange, schließen die TCP-Verbindung und beenden sie. Die Verbraucher warten nicht darauf, dass zusätzliche Nachrichten in die Warteschlange gelangen, selbst wenn die Anzahl der verarbeiteten Nachrichten kleiner ist als der beim Start der Verbraucher festgelegte Wert `--max_messages` .

* `1`: Verbraucher verarbeiten weiterhin Nachrichten aus der Nachrichtenwarteschlange, bis sie die maximale Anzahl von Nachrichten erreichen (der für `--max_messages` beim Befehl `queue:consumers:start` angegebene Wert), bevor sie die TCP-Verbindung schließen und den Verbraucherprozess beenden. Wenn die Warteschlange vor Erreichen von `--max_messages` geleert wird, wartet der Verbraucher, bis weitere Nachrichten eintreffen. Wenn Sie Sekundäre verwenden, um Verbraucher anstatt eines Cron-Auftrags auszuführen, setzen Sie diese Variable auf `1`.

>[!WARNING]
>
>Die Option `--consumers-wait-for-messages` ist eine globale Option und kann nicht für jeden Verbraucher einzeln konfiguriert werden.
