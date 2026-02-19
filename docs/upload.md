# Upload von PDF-, Audio- und Video-Dateien

Der Bludit-Uploader erlaubt das Laden folgender Datei-Typen:

* gif
* png
* jpg
* jpeg
* svg

Um PDF-, Audio- oder Video-Dateien auf den Server zu laden und in eine Seite einzubinden oder zum Download anzubieten, bietet sich eine der zwei folgenden Möglichkeiten an.

## Ab Bludit v3.0.0

**1. Verwendung eines FTP-Clients**

Die Datei wird beispielsweise mit einem [FTP-Client](/file-transfer-protocol-ftp) in das Verzeichnis /bl-content/uploads/ auf den Server geladen.

**2. Bearbeitung der Datei variables.php und media.php**

Die Datei variables.php (im Verzeichnis /bl-kernel/boot/) wird um zusätzliche Datei-Erweiterungen und -Typen erweitert. Welche Datei-Typen geladen werden dürfen, ist in in zwei Arrays definiert (ab Zeile 109):

```
// Allowed image extensions
$GLOBALS['ALLOWED_IMG_EXTENSION'] = array('gif', 'png', 'jpg', 'jpeg', 'svg');

// Allowed image mime types
$GLOBALS['ALLOWED_IMG_MIMETYPES'] = array('image/gif', 'image/png', 'image/jpeg', 'image/svg+xml');
```

Um zusätzlich das Laden von beispielsweise PDF-Dateien zu erlauben, kann definiert werden:

```
// Allowed image extensions
$GLOBALS['ALLOWED_IMG_EXTENSION'] = array('gif', 'png', 'jpg', 'jpeg', 'svg', 'pdf');

// Allowed image mime types
$GLOBALS['ALLOWED_IMG_MIMETYPES'] = array('image/gif', 'image/png', 'image/jpeg', 'image/svg+xml', 'application/pdf');
```

Zudem muss die Datei media.php des Themes des Admin-Bereichs angepasst werden. Standard ist das Theme Booty, bei diesem befindet sich die Datei media.php im Verzeichnis /bl-kernel/admin/themes/booty/html (Zeile 182):

`const validImageTypes = ['image/gif', 'image/jpeg', 'image/png', 'image/svg+xml'];`

Um PDF-Dateien zu verwenden, kann hier erweitert werden:

const validImageTypes = ['image/gif', 'image/jpeg', 'image/png', 'image/svg+xml', 'application/pdf'];

## Bis Bludit v2.3.4

**1. Verwendung eines FTP-Clients**

Die Datei wird beispielsweise mit einem [FTP-Client](/file-transfer-protocol-ftp) in das Verzeichnis /bl-content/uploads/ auf den Server geladen.

**2. Bearbeitung der Datei uploader.php**

Die Datei uploader.php (im Verzeichnis /bl-kernel/ajax/) wird um zusätzliche Datei-Typen erweitert. Welche Datei-Typen unter "Bilder" auf den Server geladen werden dürfen, ist in einem Array definiert (Zeile 18):

`$validExtension = array('tiff', 'gif', 'png', 'jpg', 'jpeg', 'bmp', 'svg');`

Um zusätzlich das Laden von PDF-Dateien zu erlauben, kann also definiert werden:

`$validExtension = array('tiff', 'gif', 'png', 'jpg', 'jpeg', 'bmp', 'svg','pdf');`
