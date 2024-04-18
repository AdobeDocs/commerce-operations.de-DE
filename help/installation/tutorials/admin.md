---
title: Erstellen, Bearbeiten oder Entsperren eines Administratorkontos
description: Führen Sie diese Schritte aus, um das Administratorkonto Ihrer Adobe Commerce Admin App zu verwalten.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Erstellen, Bearbeiten oder Entsperren eines Administratorkontos

Bevor Sie diesen Befehl verwenden können, müssen Sie Folgendes tun:

- [Erstellen der Bereitstellungskonfiguration](deployment.md)
- [Mindestens die Module Magento_Authorization und Magento_User aktivieren](manage-modules.md)
- Datenbankschema erstellen

>[!NOTE]
>
>Die einfachste Möglichkeit, die Datenbank zu erstellen, besteht darin, den Befehl `magento setup:upgrade`.

## Erstellen oder Bearbeiten von Administratoren

Verwenden Sie diesen Befehl, um einen Administrator zu erstellen oder einen vorhandenen Administrator zu bearbeiten.

>[!NOTE]
>
>Wenn Sie einen Administrator bearbeiten, wird nur der `first name`, `last name`, und `password` kann bearbeitet werden.

Befehlsverwendung:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Wobei die folgende Tabelle Parameter und Werte definiert:

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--admin-firstname` | Vorname des Administratorbenutzers. | Ja |
| `--admin-lastname` | Nachname des Administratorbenutzers. | Ja |
| `--admin-email` | E-Mail-Adresse des Administrators. | Ja |
| `--admin-user` | Administrator-Benutzername. | Ja |
| `--admin-password` | Administratorkennwort. Das Kennwort muss mindestens 7 Zeichen lang sein und mindestens ein alphabetisches und ein numerisches Zeichen enthalten. <br><br>Wir empfehlen ein längeres, komplexeres Passwort. Wenn die Kennwortzeichenfolge Sonderzeichen enthält, die eine wörtliche Interpretation erfordern (wie umgekehrte Schrägstriche oder Leerzeichen), fügen Sie das Kennwort in einfache Anführungszeichen ein. | Ja |
| `--magento-init-params` | Zu jedem Befehl hinzufügen, um die Initialisierungsparameter der Anwendung anzupassen<br/><br/>Beispiel: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nein |

Anwendungsbeispiel:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```terminal
Created Magento administrator user named j.doe
```

Wenn Sie keinen der erforderlichen Parameter angeben, werden Sie von der Anwendung in der CLI zu diesen gefragt:

```bash
bin/magento admin:user:create
```

```terminal
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```terminal
Created Magento administrator user named John
```

Die folgenden Beispielaktualisierungen `first name`, `last name`, und `password` von `j.doe` Admin-Benutzer:

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```terminal
Created Magento administrator user named j.doe
```

## Entsperren eines Administratorkontos

Verwenden Sie diesen Befehl, um das Konto eines gesperrten Administrators zu entsperren, normalerweise aufgrund mehrerer falscher Anmeldeversuche.

```bash
bin/magento admin:user:unlock {username}
```

Sie müssen den Benutzernamen des Administrators angeben. Beispiel:

```bash
bin/magento admin:user:unlock admin
```

```terminal
The user account "admin" has been unlocked
```

Wenn das Konto nicht entsperrt ist oder ein Problem aufgetreten ist, wird die folgende Meldung angezeigt:

```terminal
The user account "admin" was not locked or could not be unlocked
```

Vergewissern Sie sich, dass der Benutzer Administrator ist, der Benutzer aktiv ist und das Konto gesperrt ist. Um die Liste gesperrter Benutzer in der Admin-Konsole anzuzeigen, melden Sie sich als Administrator an und klicken Sie auf **System** > **Berechtigungen** > **Gesperrte Benutzer**.

Wenn das Konto nicht vorhanden ist, wird die folgende Meldung angezeigt:

```terminal
Couldn't find the user account "bob"
```
