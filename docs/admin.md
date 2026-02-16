Bei der Installation gibt Bludit einen Standardbenutzer "admin" vor.

Wer beispielsweise aus Sicherheitsgründen den Standarbenutzer ändern will, hat dazu folgende zwei Möglichkeiten:

1) Unter "Verwalten" > "Benutzer" kann ein neuer Benutzer mit Administratorenrechten angelegt werden. Dieser kann denselben Vor- und Nachnamen wie der Benutzer "admin" haben. Darauf kann der Standardbenutzer "admin" deaktiviert werden.

2) Der Standardbenutzer "admin" kann nachträglich manuell in der Datei /bl-content/databases/users.php geändert werden. Dazu einfach statt "admin" den gewünschten Benutzernamen für das Login definieren:

```
<?php defined('BLUDIT') or die('Bludit CMS.'); ?>
{
    "admin": {
        "firstName": "Edi",
        ...
    }
}
```
