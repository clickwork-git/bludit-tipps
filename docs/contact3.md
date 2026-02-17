# Kontaktformular Contact3

Mit dem Plugin Contact3 lässt sich ein einfaches Kontaktformular einrichten.

Standardmässig enthält das Formular die folgenden Felder:

* Name
* E-Mail-Adresse
* Mitteillung

## Zusätzliches Feld

Im folgenden Beispiel soll ein zusätzliches Feld "Adresse" eingerichtet werden.

**Datei plugin.php**

Zuerst wird die Datei `plugin.php` im Verzeichnis ` /bl-plugins/contact3/plugin.php` erweitert.


***1) Variable des Feldes***

Das neue Feld "Adresse" muss in der Datei `plugin.php` als Variable deklariert werden (Zeile 22):

```
  private $address = '';
```

Der Code sieht dann wie folgt aus:

```
  private $senderEmail = '';
  private $senderName = '';
  private $address = '';
  private $message = '';
  private $success = false;
  private $error = false;
  private $reCaptchaResult = false;
```

***2) Enfernung überflüssiger Zeichen***

Um überflüssige Zeichen bei der Eingabe eines Wertes zu entfernen, wird die Datei mit folgender Anweisung ergänzt (Zeile 624):

```
    if(isset($_POST['address'])){
      $this->address = trim(strip_tags($_POST['address']));
    }
````

Der Code sieht dann wie folgt aus:

```
  private function readPost(){
    // removes bad content - just a little protection - could be better

    if(isset($_POST['name'])) {
      $this->senderName =  trim(strip_tags($_POST['name']));
    }
    if(isset($_POST['email'])) {
      $this->senderEmail =  trim(preg_replace("/[^0-9a-zA-ZäöüÄÖÜÈèÉéÂâáÁàÀíÍìÌâÂ@ \-\+\_\.]/", " ", $_POST['email']));
    }
    if(isset($_POST['address'])){
      $this->address = trim(strip_tags($_POST['address']));
    }
    if(isset($_POST['message'])){
      $this->message = trim(strip_tags($_POST['message']));
    }
  }
```

***3) Ausgabe in der E-Mail***

Für die Ausgabe des Felds "Adresse" in einer E-Mail, die mit HML formatiert ist, wird die Datei mit folgender Anweisung ergänzt:

```
      $emailText .= '<b>'.$L->get('Address').': </b>'.$this->address.'<br>';
```

Der Code sieht dann wie folgt aus:

```
      $emailText  = '<b>'.$L->get('Your Name').': </b>'.$this->senderName.'<br>Test';
      $emailText .= '<b>'.$L->get('Your Email').': </b>'.$this->senderEmail.'<br>';
      $emailText .= '<b>'.$L->get('Address').': </b>'.$this->address.'<br>';
      $emailText .= '<b>'.$L->get('Your Message').': </b><br>'.nl2br($this->message).'<br>';
```

Für die Ausgabe des Felds "Adresse" als reiner Text wird die Datei mit folgender Anweisung ergänzt:

```
      $emailText .= $L->get('Address').': '.$this->address."\r\n\r";
```

Der Code sieht dann wie folgt aus:

```
      $emailText  = $L->get('Your Name').': '.$this->senderName."\r\n\r";
      $emailText .= $L->get('Your Email').': '.$this->senderEmail."\r\n\r";
      $emailText .= $L->get('Address').': '.$this->address."\r\n\r";
      $emailText .= $L->get('Your Message').': '."\r\n".$this->message."\r\n\r";
```

**Datei contact3.php**

Für das Eingabefeld der Adresse wird die Datei `contact3.php` im Verzeichnis `/bl-plugins/contact3` mit Folgendem ergänzt:

```
	<div class="form-group">
	   <input id="address" type="text" name="address" value="<?php echo sanitize::html($this->address); ?>" placeholder="<?php echo $L->get('Address'); ?>" class="form-control">
	</div>
```

Der Code sieht dann wie folgt aus:

```
	<div class="form-group">
	   <input id="name" type="text" name="name" value="<?php echo sanitize::html($this->senderName); ?>" placeholder="<?php echo $L->get('Your Name'); ?>" class="form-control" required="">
	</div>

	<div class="form-group">
	   <input id="email" type="email" name="email" value="<?php echo sanitize::email($this->senderEmail); ?>" placeholder="<?php echo $L->get('Your Email'); ?>" class="form-control" required="">
	</div>

	<div class="form-group">
	   <input id="address" type="text" name="address" value="<?php echo sanitize::html($this->address); ?>" placeholder="<?php echo $L->get('Address'); ?>" class="form-control">
	</div>

	<div class="form-group">
	   <textarea id="message" rows="6" name="message" placeholder="<?php echo $L->get('Your Message'); ?>" class="form-control" required=""><?php echo sanitize::html($this->message); ?>
```



**Anpassung der Sprachdatei**

Der Platzhalter für den Wert, kann wie oben beschrieben als `placeholder="<!--?php echo $L--->get('Address'); ?>"` definiert werden. Es könnte aber auch placeholder="Adresse" verwendet werden.

Wenn die erste Version gewählt wird, muss die Sprachdatei angepasst werden. Dazu muss die gewählte deutschsprachige Datei de_CH.json oder de_DE.json im Verzeichnis `/bl-plugins/contact3/languages` mit folgendem Eintrag ergänzt werden:

```
"address": "Adresse",
```

Achtung: Wenn der Eintrag am Schluss hinzugefügt wird, muss das Komma weggelassen werden, dafür die vorhangehende Zeile mit einem Komma ergänzt.
