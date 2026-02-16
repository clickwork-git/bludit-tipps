# Sicherheitszertifikat (SSL)

## Anfragen auf https umleiten

Damit Anfragen von http auf https umgeleitet werden, d. h. dass nach Einrichten eines Zertifikats eine Website nicht sowohl unter http und https aufgerufen werden kann, muss die Datei .htaccess angepasst werden. Wobei es auch Hostings gibt, bei denen eine Option gewählt werden kann (beispielsweise Hostpoint).

### Alle Anfragen auf https umleiten

Wenn alle Anfragen eines Accounts mit mehreren Websites auf https umgeleitet werden sollen, kann folgende Anweisung in die Datei .htaccess eingetragen werden:

```
RewriteEngine On
RewriteCond %{HTTPS} =off
RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [QSA,L,R=301]
```

Bei Hostpoint:

```
RewriteEngine On
RewriteCond %{SERVER_PORT} !=443
RewriteRule .* https://%{SERVER_NAME}%{REQUEST_URI} [R=301,L]
```

### Alle Anfragen einer Domain auf https umleiten

Wenn alle Anfragen einer bestimmten Domain auf https umgeleitet werden sollen, kann folgende Anweisung in die Datei .htaccess eingetragen werden:

```
RewriteEngine On
RewriteCond %{HTTP_HOST} ^meinedomain\.ch$ [OR]
RewriteCond %{HTTP_HOST} ^www\.meinedomain\.ch$
RewriteCond %{HTTPS} =off
RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [QSA,L,R=301]
```

### Nur eine bestimmte Seite auf https umleiten

```
RewriteEngine On
RewriteCond %{HTTPS} =off
RewriteRule ^(beispiel.*)$ https://www.ihredomain.com/seitenname.html [R=301,L]
```

### Mixed Content

Wird nach einer Umstellung auf https kein Schloss in der Adressleiste angezeigt oder zusätzlich ein Warnsymbol, kann die Ursache dafür Mixed Content sein. Das heisst, dass die Seite Elemente (Fonts, Bilder usw.) verwendet, die nicht über eine sichere Verbindung mit https aufgerufen werden.

Um eine Website auf Mixed Content zu untersuchen, eignet sich Chrome. Mit den Entwicklertools kann die Anzahl Mixed-Content-Fehler und der Mixed Content angezeigt werden.
