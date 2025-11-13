---
title: Administratorkonto erstellen, bearbeiten oder entsperren
description: Führen Sie diese Schritte aus, um das Administratorkonto Ihres Adobe Commerce Admin-Programms zu verwalten.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: aaed7dba7d11085eb8e2793cefffb8c8b082e750
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Administratorkonto erstellen, bearbeiten oder entsperren

Bevor Sie diesen Befehl verwenden können, müssen Sie Folgendes tun:

- [Erstellen der Bereitstellungskonfiguration](deployment.md)
- [Aktivieren Sie mindestens die Module Magento_Authorization und Magento_User](manage-modules.md)
- Erstellen des Datenbankschemas

>[!NOTE]
>
>Die einfachste Möglichkeit, die Datenbank zu erstellen, besteht in der Verwendung der `magento setup:upgrade`.

## Erstellen oder Bearbeiten eines Administrators

Verwenden Sie diesen Befehl, um einen Administrator zu erstellen oder einen vorhandenen Administrator zu bearbeiten.

>[!NOTE]
>
>Wenn Sie einen Administrator bzw. eine Administratorin bearbeiten, können nur `first name`, `last name` und `password` bearbeitet werden.

Befehlsverwendung:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Dabei definiert die folgende Tabelle Parameter und Werte:

| -Name | Wert | Erforderlich? |
|--- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| `--admin-firstname` | Vorname des Admin-Benutzers. | Ja |
| `--admin-lastname` | Nachname des Administrator-Benutzers. | Ja |
| `--admin-email` | E-Mail-Adresse des Administrator-Benutzers. | Ja |
| `--admin-user` | Benutzername des Administrators. | Ja |
| `--admin-password` | Administratorkennwort Das Kennwort muss mindestens 12 Zeichen lang sein und mindestens ein alphabetisches und mindestens ein numerisches Zeichen enthalten. <br><br>Adobe empfiehlt, ein längeres, komplexeres Kennwort anzugeben. Wenn die Kennwortzeichenfolge Sonderzeichen enthält, die wörtlich interpretiert werden müssen (z. B. umgekehrte Schrägstriche oder Leerzeichen), schließen Sie das Kennwort in einfache Anführungszeichen ein. | Ja |
| `--magento-init-params` | Fügen Sie zu einem beliebigen Befehl hinzu, um die Initialisierungsparameter der Anwendung anzupassen<br/><br/>Beispiel: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nein |

Anwendungsbeispiel:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

Wenn Sie keinen der erforderlichen Parameter angeben, fragt das Programm in der CLI danach:

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

Im folgenden Beispiel werden `first name`, `last name` und `password` `j.doe` Admin-Benutzers aktualisiert:

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## Entsperren eines Administratorkontos

Verwenden Sie diesen Befehl, um das Konto eines Administrators zu entsperren, das gesperrt wurde, in der Regel aufgrund mehrerer falscher Anmeldeversuche.

```bash
bin/magento admin:user:unlock {username}
```

Sie müssen den Benutzernamen des Administrators angeben. Beispiel:

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

Wenn das Konto entweder nicht entsperrt wurde oder ein Problem aufgetreten ist, wird die folgende Meldung angezeigt:

```
The user account "admin" was not locked or could not be unlocked
```

Vergewissern Sie sich, dass der Benutzer Administrator ist, dass der Benutzer aktiv ist und dass das Konto gesperrt ist. Um die Liste der gesperrten Benutzer im Admin anzuzeigen, melden Sie sich als Administrator an und klicken Sie auf **System** > **Berechtigungen** > **Gesperrte Benutzer**.

Wenn das Konto nicht vorhanden ist, wird die folgende Meldung angezeigt:

```
Couldn't find the user account "bob"
```
