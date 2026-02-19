# Wechsel des URL

Eine einfache Möglichkeit, die Domain zu wechseln, bietet das Plugin Domain Migrator. Das Plugin gehört zur Ausstattung von Bludit Pro. Es kann aber auch gekauft werden unter

https://gumroad.com/l/domain-migrator

Das Plugin erlaubt

* die Migration von einer Domain zu einer anderen Domain,
* die Migration von einer Domain zu einer Unterdomain,
* die Migration von http zu https.

## Vorgehen mit dem Plugin Domain Migrator

Bei der Migration mit dem Plugin Domain Migrator wird wie folgt vorgegangen:

1. Aktivieren des Plugins. Dabei wird die bestehende Domain in das Feld "Old Domain" übernommen.
2.  In das Feld "New Domain" die neue Domain eingeben.
3. Den Button "Start" drücken.
4. Bludit unter der neuen Domain installieren.
5. Das Verzeichnis `/bl-content/`der neuen Installation löschen.
6. Das Verzeichnis `/bl-content-migrator/` der alten Installation in die neue Installation kopieren und das Verzeichnis in `/bl-content/` umbennenen (das Plugin gibt den genauen Pfad an, wo das Verzeichnis `/bl-content-migrator/` auf dem Server zu finden ist).
