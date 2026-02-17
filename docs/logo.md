# Logo

Unter "Einstellungen" > "Allgemein" > "Logo" kann ein Logo zur Website hinzugefügt werden.

**Ob diese Funktion verwendet werden kann ist allerdings vom verwendeten Theme abhängig.**

Der Name des Logos entspricht dem Seitentitel.

## Theme mit Code ergänzen

Um das Theme mit dem Logo zu ergänzen, das unter "Einstellungen" hinzugefügt werden kann, kann folgendes Snippet zum Theme hinzugefügt werden:

`<img src="/bl-content/uploads/<?php echo $site->title(); ?>.png" alt="logo">`
