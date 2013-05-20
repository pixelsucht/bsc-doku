### Ein Wort zu Grid-Systemen


Sie sind zur Grundlage professionell gestalteter Webseiten geworden und aus dem Alltag von Frontend-Designern nicht wegzudenken. Sie sind für moderne und professionelle Frontend-Entwickler so "nervig" wie wichtig.


##### "Nervig": 


* Weil es von ihnen viel zu viele gibt.
* Weil die meisten von ihnen mehr Nachteile wie Vorteile liefern.
* Weil sie HTML-Struktur und CSS-Notation diktieren.
* Weil sie für responsiv angelegte Layouts ein Alptraum sind.


##### Wichtig: 


* Weil Grid-Raster Gestaltungsgrundlegend sind.


CSS-Frameworks und vor allem Grid-Systeme nötigen also die Entwickler dazu spezielle Namensdeklarationen und HTML-Strukturen zu verwenden, wodurch sich sich eine Notationspraxis ergibt, die überholt und nicht mehr zeitgemäß ist. Dabei liefern Grid-Systeme auch unnötigen CSS-Code welcher in den meisten Fällen ungenutzt nur die Ladezeiten der CSS-Dateien vergrößert.


#### Wie Basecondition Grid-Systeme nutzt


Basecondition will an dieser Stelle dem Entwickler eine alternative Einsatzmöglichkeit bieten. Dem Entwickler stehen diverse Mixins zur Verfügung die es erlauben Grid-Ressourcen genau dort einsetzen zu können, wo sie benötigt werden. Der CSS-Code bleibt frei von nicht nutzbaren Segmenten. Es gibt keine Vorgabe was Benennung und Strukturierung betrifft.


#### Zielgerichtet Grids nutzen


Um mit Basecondition Grid-Systeme anzulegen kann man verschiedene Wege gehen, die je nach Verwendungszweck und Vorlieben des Entwicklers eingesetzt werden können. Ebenso wie alle anderen Basecondition Mixins sind auch die Grid-System-Mixins so angelegt, dass sie Elementen oder Klassen zugewiesen werden müssen. Im folgenden einige Beispiele für den Einsatz der Mixins.


***


### Verfügbare standard Grid-System Mixins


##### Grid Wrapper Mixin


```css
#grid > .wrapper ( 16, 40px, 20px );
```


###### Das Grid Wrapper Mixin erwartet 3 Werte nach folgendem Schema: 


`@number-of-columns, @column-width, @gutter-width`


##### Grid Row Mixin


```css
#grid > .row ( 20px );
```


###### Das Grid Row Mixin erwartet 1 Werte nach folgendem Schema: 


`@gutter-width`


##### Grid Column Mixin


```css
#grid > .column ( 1, 40px, 20px );
```


###### Das Grid Column Mixin erwartet 3 Werte nach folgendem Schema: 


`@index, @column-width, @gutter-width`


##### Grid Offset Mixin


```css
#grid > .offset ( 1, 40px, 20px );
```


###### Das Grid Offset Mixin erwartet 3 Werte nach folgendem Schema: 


`@index, @column-width, @gutter-width`


***


### Verfügbare extra Grid-System Mixins


##### Grid Write Columns Mixin


```css
#grid > .write-columns ( col-, 16, 40px, 20px );
```


###### Das Grid Write Columns Mixin erwartet 4 Werte nach folgendem Schema: 


`@column-class, @number-of-columns, @column-width, @gutter-width`


##### Grid Write Offsets Mixin


```css
#grid > .write-offsets ( offset-, 16, 40px, 20px );
```


###### Das Grid Write Offsets Mixin erwartet 4 Werte nach folgendem Schema: 


`@offset-class, @number-of-columns, @column-width, @gutter-width`


***


### Nutzungsbeispiele für Grid-System Mixins


##### Einsatz ohne gridtypische Klassen-Benennung

```css
div#page {
  #grid > .wrapper ();
  
  article {
    #grid > .row ();
    
    section.main {
      #grid > .column ( 8 );
    }
    aside {
      #grid > .column ( 4 );
    }
  }
}
```

###### Hinweis: 

* Werden dem jeweiligen Mixin keine Werte übergeben nutzt Basecondition die "Base" Werte.

##### Grid mit den Columns 1,3,8,12 ohne Offsets


```css
section.grid-12-columns {
  #grid > .wrapper ();
  
  .row {
    #grid > .row ();
    
    div.col-1 {
      #grid > .column ( 1 );
    }
    div.col-3 {
      #grid > .column ( 3 );
    }
    div.col-8 {
      #grid > .column ( 8 );
    }
    div.col-12 {
      #grid > .column ( 12 );
    }
  }
}
```


##### Grid mit den Columns 1-16 ohne Offsets


```css
section.grid-16-columns {
  #grid > .wrapper ( 16, 40px, 20px );
  
  .row {
    #grid > .row ( 20px );
    #grid > .write-columns ( col-, 16, 40px, 20px );
  }
}
```


##### Fluid Columns Grid mit 940px Breite ohne Offsets


```css
section.grid-12-float-columns {
  #base > .center ();
  
  width: 940px;
  
  .row {
    #grid > .row ( 0 );
    #grid > .write-columns ( col-, 12, 6.382978723%, 2.127659574% );
    
    [class*="col-"] {
      &:first-child {
        margin-left: 0;
      }
    }
  }
}
```


***


### Hinweis

* Der ID-Aufruf `#grid` wird als Namespace für die Grid-System Mixins genutzt.
* Der Grid-Wrapper gibt die Grid-Gesamtbreite vor.
* Das Grid-Row setzt die Grid-Gutterbreite als negativen `margin-left` Wert.
* Die Columns erhalten immer die gesamte Grid-Gutterbreite als `margin-left` Wert.