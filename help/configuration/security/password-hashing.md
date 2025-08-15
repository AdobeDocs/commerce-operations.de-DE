---
title: Kennworthashing
description: Erfahren Sie mehr über Passwort-Hashing-Strategien und -Implementierung.
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Kennworthashing

Derzeit verwendet Commerce eine eigene Strategie für das Hashing von Passwörtern, die auf verschiedenen nativen PHP-Hashing-Algorithmen basiert. Commerce unterstützt mehrere Algorithmen wie `MD5`, `SHA256` oder `Argon 2ID13`. Wenn die Erweiterung Sodium installiert ist (standardmäßig in PHP 7.3 installiert), dann wird `Argon 2ID13` als Standard-Hash-Algorithmus gewählt. Andernfalls ist `SHA256` der Standard. Commerce kann die native PHP-`password_hash` mit Argon 2i-Algorithmusunterstützung verwenden.

Um zu vermeiden, dass ältere Kennwörter, die mit veralteten Algorithmen wie `MD5` gehasht wurden, beeinträchtigt werden, bietet die aktuelle Implementierung eine Methode, um den Hash zu aktualisieren, ohne das ursprüngliche Kennwort zu ändern. Im Allgemeinen hat der Passwort-Hash folgendes Format:

```text
password_hash:salt:version<n>:version<n>
```

Dabei stellt `version<n>`…`version<n>` alle Hash-Algorithmusversionen dar, die für das Kennwort verwendet werden. Außerdem wird das Salz immer zusammen mit dem Passwort-Hash gespeichert, sodass wir die gesamte Kette von Algorithmen wiederherstellen können. Ein Beispiel sieht wie folgt aus:

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

Der erste Teil stellt den Passwort-Hash dar. Das zweite, `8qnyO4H1OYIfGCUb` ist das Salz. Die letzten beiden sind die verschiedenen Hash-Algorithmen: 1 ist `SHA256` und 2 ist `Argon 2ID13`. Das bedeutet, dass das Passwort des Kunden ursprünglich mit `SHA256` gehasht wurde. Danach wurde der Algorithmus mit `Argon 2ID13` aktualisiert und der Hash mit Argon neu gehasht.

## Hash-Strategie aktualisieren

Beachten Sie, wie der Hash-Upgrade-Mechanismus aussieht. Angenommen, ursprünglich wurde ein Passwort mit `MD5` gehasht und dann wurde der Algorithmus mehrmals mit Argon 2ID13 aktualisiert. Das folgende Diagramm zeigt den Hash-Upgrade-Ablauf.

![Hash-Upgrade-Workflow](../../assets/configuration/hash-upgrade-algorithm.png)

Jeder Hash-Algorithmus verwendet den vorherigen Passwort-Hash, um einen neuen Hash zu generieren. Commerce speichert das ursprüngliche, unformatierte Kennwort nicht.

![Hash-Upgrade-Strategie](../../assets/configuration/hash-upgrade-strategy.png)

Wie oben erläutert, kann es vorkommen, dass auf den Passwort-Hash mehrere Hash-Versionen auf das ursprüngliche Passwort angewendet werden.
So funktioniert der Mechanismus zur Passwortüberprüfung während einer Kundenauthentifizierung.

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

Da Commerce alle verwendeten Passwort-Hash-Versionen zusammen mit dem Passwort-Hash speichert, können wir die gesamte Hash-Kette während der Passwort-Verifizierung wiederherstellen. Der Hash-Verifizierungsmechanismus ähnelt der Hash-Upgrade-Strategie: Basierend auf Versionen, die zusammen mit dem Passwort-Hash gespeichert werden, generiert der Algorithmus Hashes aus dem bereitgestellten Passwort und gibt das Vergleichsergebnis zwischen dem Hash-Passwort und dem in der Datenbank gespeicherten Hash zurück.

## Implementierung

Die `\Magento\Framework\Encryption\Encryptor`-Klasse ist für die Erzeugung und Verifizierung von Passwort-Hashs verantwortlich. Der Befehl [`bin/magento customer:hash:upgrade`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#customerhashupgrade) aktualisiert einen Kunden-Passwort-Hash auf den neuesten Hash-Algorithmus.
