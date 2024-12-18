---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# CLI-Optionen für Nachrichtenwarteschlangen-Verbraucher

| -Name | Beschreibung | Wert | Erforderlich |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | Legt fest, ob Verbraucher auf eine Nachricht aus der Warteschlange warten. | 1 - Ja, 0 - Nein | Nein |

* `0`: Privatkunden verarbeiten verfügbare Nachrichten in der Warteschlange, schließen die TCP-Verbindung und beenden sie. Verbraucher warten nicht auf den Eintritt zusätzlicher Nachrichten in die Warteschlange, selbst wenn die Anzahl der verarbeiteten Nachrichten kleiner ist als der beim Starten von Verbrauchern angegebene `--max_messages`.

* `1`: Verbraucher verarbeiten weiterhin Nachrichten aus der Nachrichtenwarteschlange, bis die maximale Anzahl von Nachrichten erreicht ist (der Wert, der für `--max_messages` im `queue:consumers:start`-Befehl angegeben wurde), bevor sie die TCP-Verbindung schließen und den Verbraucherprozess beenden. Wenn die Warteschlange geleert wird, bevor `--max_messages` erreicht wird, wartet der Verbraucher auf den Eingang weiterer Nachrichten. Wenn Sie Worker verwenden, um Verbraucher auszuführen, anstatt einen Cron-Auftrag zu verwenden, setzen Sie diese Variable auf `1`.

>[!WARNING]
>
>Die `--consumers-wait-for-messages` Option ist eine globale Option und kann nicht für jeden Verbraucher separat konfiguriert werden.
