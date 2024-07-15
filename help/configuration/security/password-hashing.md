---
title: Kennwort-Hashing
description: Erfahren Sie mehr über Hashing-Strategien für Passwörter und Implementierung.
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Kennwort-Hashing

Derzeit verwendet Commerce eine eigene Strategie für das Hashing von Passwörtern, basierend auf verschiedenen nativen PHP-Hashing-Algorithmen. Commerce unterstützt mehrere Algorithmen wie `MD5`, `SHA256` oder `Argon 2ID13`. Wenn die Sodium-Erweiterung installiert ist (standardmäßig in PHP 7.3 installiert), wird `Argon 2ID13` als Standard-Hashing-Algorithmus ausgewählt. Andernfalls ist `SHA256` der Standardwert. Commerce kann die native PHP `password_hash`-Funktion mit Argon 2i-Algorithmusunterstützung verwenden.

Um zu vermeiden, dass ältere Passwörter kompromittiert werden, die mit veralteten Algorithmen wie `MD5` gehasht wurden, bietet die aktuelle Implementierung eine Methode zum Aktualisieren des Hashs, ohne das ursprüngliche Kennwort zu ändern. Im Allgemeinen hat der Kennwort-Hash das folgende Format:

```text
password_hash:salt:version<n>:version<n>
```

Dabei stellt `version<n>`...`version<n>` alle im Kennwort verwendeten Hash-Algorithmusversionen dar. Außerdem wird das Salz immer zusammen mit dem Passwort-Hash gespeichert, sodass wir die gesamte Kette von Algorithmen wiederherstellen können. Ein Beispiel sieht wie folgt aus:

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

Der erste Teil stellt den Passwort-Hash dar. Die zweite, `8qnyO4H1OYIfGCUb`, ist das Salz. Die letzten beiden sind die verschiedenen Hash-Algorithmen: 1 ist `SHA256` und 2 ist `Argon 2ID13`. Das bedeutet, dass das Kennwort des Kunden ursprünglich mit `SHA256` gehasht wurde und danach der Algorithmus mit `Argon 2ID13` aktualisiert wurde und der Hash mit Argon neu erstellt wurde.

## Hash-Strategie aktualisieren

Überlegen Sie, wie der Hash-Upgrade-Mechanismus aussieht. Angenommen, ursprünglich wurde ein Passwort mit `MD5` gehasht und dann wurde der Algorithmus mehrmals mit Argon 2ID13 aktualisiert. Das folgende Diagramm zeigt den Hash-Aktualisierungsfluss.

![Hash-Upgrade-Workflow](../../assets/configuration/hash-upgrade-algorithm.png)

Jeder Hash-Algorithmus verwendet den vorherigen Passwort-Hash, um einen neuen Hash zu generieren. Commerce speichert das ursprüngliche Rohkennwort nicht.

![Hash-Upgrade-Strategie](../../assets/configuration/hash-upgrade-strategy.png)

Wie oben erläutert, kann der Kennwort-Hash mehrere Hash-Versionen auf das ursprüngliche Kennwort anwenden.
So funktioniert der Mechanismus zur Kennwortüberprüfung während einer Kundenauthentifizierung.

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

Da Commerce alle verwendeten Passwort-Hash-Versionen zusammen mit dem Passwort-Hash speichert, können wir die gesamte Hash-Kette während der Passwortüberprüfung wiederherstellen. Der Hash-Überprüfungsmechanismus ähnelt der Hash-Upgrade-Strategie: Basierend auf den gemeinsam mit dem Passwort-Hash gespeicherten Versionen generiert der Algorithmus Hashes aus dem bereitgestellten Kennwort und gibt das Vergleichsergebnis zwischen dem Hash-Kennwort und dem in der Datenbank gespeicherten Hash zurück.

## Implementierung

Die Klasse `\Magento\Framework\Encryption\Encryptor` ist für die Erstellung und Überprüfung des Kennworthashs verantwortlich. Der Befehl [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) aktualisiert einen Kunden-Passwort-Hash auf den neuesten Hash-Algorithmus.
