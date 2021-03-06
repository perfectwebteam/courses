class: middle
# Template Overrides
## door Jisse Reitsma
### <a href="http://twitter.com/jissereitsma">@jissereitsma</a>

---
# Template Overrides
- Template overrides ofwel output overrides
- Voordelen
	* HTML aanpassen naar eigen wens
	* Wijzigingen behouden bij updates

---
# HTML code
* Componenten
* Modules
* Templates

---
# Bestanden bij modules
Folder `modules/mod_example`:
```
mod_example.xml
mod_example.php
helper.php
tmpl/default.php
```
De `tmpl` folder bevat de PHP+HTML templates

---
# Bestanden bij componenten
Folder `components/com_example`:
```
models/example.php
views/example/view.html.php
views/example/tmpl/default.php
controller.php
controllers/example.php
tables/example.php
helpers/helper.php
```
De `tmpl` folder bevat de PHP+HTML templates

---
# Stappenplan
1. Copie van bestand maken
2. HTML een beetje aanpassen
3. Basis PHP structuur aanpassen
4. Geavanceerde tips & trucs

---
# Stap 1: Copie maken
* Van component of module naar template
* Welk bestand?

---
# Stap 1 - module
Van
```
modules/mod_articles_latest/tmpl/default.php
```

Naar
```
templates/TEMPLATE/html/mod_articles_latest/default.php
```

---
# Stap 1 - artikel view
URL
```
index.php?option=com_content&view=article
```

Van
```
components/com_content/views/article/tmpl/default.php
```

Naar
```
templates/TEMPLATE/html/com_content/article/default.php
```

---
# Stap 1 - blog overzicht
URL
```
index.php?option=com_content&view=category&layout=blog
```

Van
```
components/com_content/views/category/tmpl/blog.php
components/com_content/views/category/tmpl/blog_*.php
```

Naar
```
templates/TEMPLATE/html/com_content/category/blog.php
templates/TEMPLATE/html/com_content/category/blog_*.php
```

---
# Stap 2 - HTML code
* CSS klasses toevoegen of aanpassen
* HTML hierarchie aanpassen
* Onnodige blokken HTML weghalen

---
# Stap 3 - PHP structuur
```php
<?php if ($something) : ?>
<?php else: ?>
<?php endif; ?>
```
```php
<?php foreach($loop) : ?>
<?php endforeach; ?>
```

* Houd de PHP structuur intact
* Test altijd voor PHP Warnings of Fatal Errors

---
# Parameters

Parameters zijn instelbaar in component opties of Menu-Item opties,
maar als je ze niet gebruikt kan je ze ook in de code weghalen

```php
<?php if ($params->get('show_title')) : ?>
<h2><?php echo $this->escape($this->item->title); ?></h2>
<?php endif; ?>
```

---
# Stap 4 - Geavanceerde trucs
* Klassen van Joomla Framework aanhalen
	* `JMenu`, `JURI`, `JDocument`, `JUser`
	* `JFactory::getApplication()->input`
    * Model van component aanroepen voor extra data

---
# Uitvoer van content plugins

Binnen `view.html.php` worden Content Plugins aangeroepen om 
de artikel content te bewerken. Output van deze Content Plugins
kan in aparte variabelen terecht komen:

```php
echo $this->item->event->afterDisplayTitle;
echo $this->item->event->beforeDisplayContent;
echo $this->item->event->afterDisplayContent;
```

Houd deze variabelen intact in jouw template override.

---
# Alternative layouts
Extra layout bestanden zelf aanmaken
```
templates/TEMPLATE/html/com_content/article/product.php
```

* Optie **Alternative Layout** nodig binnen Menu-Item opties!
* Niet alle Menu-Items hebben deze optie
* Maak `product.xml` aan om ook keuze voor layout binnen Menu-Item mogelijk te maken

---
# Vragen?

<br><br>

## Resources
* [How to override Joomla output](http://docs.joomla.org/How_to_override_the_output_from_the_Joomla!_core)
* [Layout overrides](http://docs.joomla.org/Layout_Overrides_in_Joomla)
