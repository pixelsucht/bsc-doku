### LESS-PHP-Compiler und Cachingsystem nutzen


Der LESS-PHP-Compiler vom Basecondition ist im Folder `bsc-unit` enthalten. Über die im Dokument-Root abgelegte `.htaccess` werden alle Dateien mit im folgenden Aufgeführten Datei-Endungen über die im Ordner
`bsc-unit` enthaltene `index.php` ausgegeben.


* `.cc.css`
* `.cc.min.css`
* `.bsc.css`
* `.bsc.min.css`


Existiert ein LESS-Pendant wird dieses geladen, zu CSS-Code geparst, als Caching-Datei gespeichert und final als CSS angezeigt.


```html
<link rel="stylesheet" href="site/stylesheets/screen.min.cc.css" media="screen, print">
```


Alternativ, sollte serverseitig die `.htaccess`-Weiterleitung über die `index.php` des Compilers nicht möglich sein, kann eine Datei auch direkt über die `index.php` aufgerufen werden.


```html
<link rel="stylesheet" href="bsc-unit/?f=site/stylesheets/screen.min.css" media="screen, print">
```


#### CSS-Compressing


Der Zusatz `.min` bewirkt, dass der Compiler den CSS-Code kompressiert. Es können auch Nicht-LESS-Stylesheet-Dateien also einfache CSS-Dateien kompressiert werden, der Compiler erkennt ob die Datei eine CSS- oder LESS-Datei ist. CSS-Dateien werden um reduzierte Ladezeiten gewährleisten zu können auch gecacht, sobald sie über den Compiler aufgerufen werden.


#### Caching-Mechanik


Sobald eine LESS-Datei geparst wurde wird ein Caching-File des erzeugten Outputs angelegt. Diese Caching-Datei wird vom Compiler genutzt bis das zugrundeliegende LESS-Pendant verändert wird, in diesem Falle wird die Caching-Datei mit dem neu generierten Output überschrieben. Der Compiler nutzt für ein verfeinertes Cachings die Header-Rückgabe-Information `304 Not Modified`.


***


### LESS-Javascript-Compiler nutzen


Um LESS und die Basecondition-Ressourcen auch auf System ohne PHP nutzen zu können ist im Ordner `site/javascript/vendor` `less.x.min.js` abgelegt. 

Die LESS-Stylesheets werden mit dem `rel`-Attribut `stylesheet/less` im `<head/>` des Dokuments versehen eingebunden.


```html
<link rel="stylesheet/less" type="text/css" href="site/stylesheets/screen.less">
```


Es können beliebig viele LESS-Dateien geladen werden, wichtig ist das darauf folgend das Javascript eingebunden wird. 

Das LESS-Javascript-Compiler-File muss wie bereits erwähnt anschließend im `<head/>` des Dokuments eingebunden werden.


```html
<script src="site/javascript/vendor/less.x.min.js" type="text/javascript"></script>
```


#### Developer Mode


Wer beim Entwickeln mit LESS-JS nicht immer den Browser-Cache leeren möchte kann den Developer-Mode aktivieren.


```html
<script>
   less.env = "development";
</script>
```


#### Noscript nutzen wenn PHP verfügbar ist


Möchte man beide Varianten der Kompilierung einsetzen um zu gewährleisten, dass auch bei inaktivem Javascript die Stylsheets bereitstehen kann man die LESS-Dateien mit Hilfe des LESS-PHP-Compiler in einem `<noscript/>`-Tag einbinden.


```html
<noscript>
  <link rel="stylesheet" href="site/stylesheets/screen.min.cc.css" media="screen, print">
</noscript>
```


***