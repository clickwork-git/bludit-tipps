# Navigation

Je nach Theme wird die Navigation verschieden angzeigt. Durch Anpassung des Templates des Themes kann dies angepasst werden.

## Theme Blog X

Beim Theme Blog X werden in der horizontalen Navigationsleiste am oberen Bildrand die statischen Seiten angezeigt. Unterseiten werden neben den Oberseiten angezeigt.

Der Code dafür ist:

```
<?php foreach ($staticContent as $staticPage): ?>
<li class="nav-item">
   <a class="nav-link" href="<?php echo $staticPage->permalink() ?>"><?php echo $staticPage->title() ?></a>
</li>
<?php endforeach ?>
```

Für ein Dropdown-Menü kann stattdessen folgender Code verwendet werden:

```
<?php
foreach ($staticContent as $staticPage) {
	$children = $staticPage->children();
	if (!$staticPage->isChild())
	{
			if ($staticPage->hasChildren())
			{
			    echo '<li class="nav-item dropdown">';
		         echo '<a class="nav-link dropdown-toggle" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" href="'. $staticPage->permalink().'">'.$staticPage->title().'</a>';

				echo PHP_EOL.'<div class="dropdown-menu" aria-labelledby="navbarDropdown">'.PHP_EOL;
				foreach ($children as $child)
				{
					echo '<a class="dropdown-item" href="'.$child->permalink().'">'.$child->title().'</a>'.PHP_EOL;
				}
				echo '</div>'.PHP_EOL;
			} else {
			    echo '<li class="nav-item">';
	        	echo '<a class="nav-link" href="'. $staticPage->permalink().'">'.$staticPage->title().'</a>';
	}
		echo '</li>'.PHP_EOL;
	}
}
?>
```
