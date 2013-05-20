## Basecondition Framework


### Was ist Basecondition

Basecondition ist ein LESS-Framework, das als Basis zur Entwicklung komplexer Webseitenlayouts dient. Das Framework ist so angelegt, dass es schnell und intuitiv eingesetzt werden kann, dabei verfolgt es das Ziel dem Frontendentwickler eine stabile Basis durch individuell anpassbare Komponenten an die Hand zu geben. 


###### Was Basecondition an Mehrwert mit sich bringt ist:

* ein zuverlässigen LESS-Kompilierungsmechanismus,
* die Möglichkeit beliebige CSS-Dateien und aus LESS generierten Code zu compressieren,
* Cachingsystem für kompilierten und/oder compressierten Code,
* ein sinnvolle Mixins und ein als LESS-Code verfügbares UI-Kit zum optionalen Einsatz,
* grundlegende Ausrichtung zur Unterstützung responsiver Designs,
* integration sinnvoller Konponenten unterschiedlicher Frameworks,
* schnelle, einfache und intuitive Nutzbarkeit,
* übergreifende Browserkompatibilität,
* Einsatzfähigkeit auf localen Entwicklungsumgebungen.


## Kerntechnologie und Systemlogik


### Less als Grundlegende Systemtechnik

Die Anwendungslogik der einzelnen Basecondition Komponenten baut auf dem CSS-Preprocessor [LESS](https://github.com/cloudhead/less.js) auf. LESS erweitert CSS mit dynamischem Verhalten und ermöglicht es komplexere Logik in aufrufbaren Algorithmen abzubilden.


###### Basecondition nutzt zwei Wege zur Kompilierung der LESS-Syntax:

* durch den [PHP-LESS-Compiler](https://github.com/leafo/lessphp),
* durch den original [LESS-Javascript-Compiler](https://github.com/cloudhead/less.js).


#### LESS-PHP-Compiler und Cachingsystem

Der Kompilierungsmechanismus ist so angelegt, dass Caching-Dateien der aufgerufenen Files angelegt werden, wodurch das eigentliche Parsen der Less-Syntax in reinen CSS-Code nur dann nötig ist, wenn eine Less-Datei bearbeitet wurde. Wird also vom Browser eine im HTML notierte CSS Datei mit der Dateiendung `.bsc.css`, `.cc.css` oder `.min.bsc.css`, `.min.cc.css` aufgerufen, wird, sofern keine Caching-Datei existiert, deren Less-Pendant (sofern vorhanden) ausgelesen, geparst und ausgegeben.


###### Durch diese Mechanik wird OnTheFly aus LESS CSS. 


#### LESS-Javascript-Compiler

Um Basecondition auch local oder auf Systemen ohne installiertes PHP einsetzen zu können ist im Ordner `site/javascript/vendor/` der LESS-Javascript-Compiler abgelegt.


## Systemvoraussetzungen

Basecondition ist für den Einsatz auf Webservern konzipiert und benötigt für eine optimale Funktionalität PHP ab Version 4.3.2. Basecondition arbeitet auch fehlerfrei mit localen Servertechnologien wie MAMP oder XAMPP. Durch den integrierten LESS-Javascript-Compiler ist Basecondition auch auf Localen- oder System-Umgebungen ohne PHP lauffähig.


##### Hinweis

Für einen fehlerfreien Betreib auf Servern müssen Lese- und Schreibrechte entsprechend korrekt vergeben werden. Je nach Servereinstellungen müssen alle PHP Dateien und Ordner im Verzeichnis `bsc_unit` volle Lese- und Schreibrechte erhalten.


## Copyright und Lizenz

Copyright 2013 Joachim Doerr, hello@basecondition.com

Bascondition unterliegt der MIT Lizenz, den genauen Wortlaut ist der [LICENSE.md](https://github.com/joachimdoerr/basecondition/blob/master/LICENSE.md) zu entnehmen.