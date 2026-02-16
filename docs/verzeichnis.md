Bludit kann im Hauptverzeichnis (root) oder in einem Unterverzeichnis wie beispielsweise `/bludit` installiert werden.

Je nach Hoster kann das Hauptverzeichnis oder das Vezeichnis einer Installation verschieden benannt sein und konfiguriert werden.

<h2 id="unterverzeichnis">Installation in einem Unterverzeichnis</h2>

Wird Bludit in einem Unterverzeichnis  eingerichtet, muss bei einigen Hostern die Datei `.htaccess` im Installationsverzeichnis angepasst werden.

Wird Bludit beispielsweise im Unterverzeichnis `bludit` installiert, muss in diesem Falle die Datei `.htaccess` wie folgt angepasst werden (Zeile 9):

```
# Base directory
RewriteBase /bludit/
```

statt

```
# Base directory
RewriteBase /
```
