# Maxima2School

Diese Erweiterung stellt einige brauchbare Funktionen für den Mathematikunterricht zur Verfügung.

## Verwendung
Kopiere die Datei `InitMaxima.mac` in das gleiche Verzeichnis wie deine Maxima Datei.
Als erste Zeile schreibst du `batchload("InitMaxima.mac")`.
Ab dann stehen dir folgende Funktionen zur Verfügung.

## Funktionsliste

### Zeichnen von Funktionen

Funktion | Beschreibung
------------ | -------------
Zeichne(f(x), x_min, ,x_max) | Zeichnet die gegebene Funktion im Intervall x_min bis x_max |
Zeichne([f1(x), f2(x)], x_min, ,x_max,<br>&nbsp;&nbsp;y>[ymin,ymax],<br>&nbsp;&nbsp;filename>"Dateiname",<br>&nbsp;&nbsp;xlabel>"x-Achse",<br>&nbsp;&nbsp;ylabel>"y-Achse",<br>&nbsp;&nbsp;titel>"Mein Titel",<br>&nbsp;&nbsp;colors>["#aa33bb", green],<br>&nbsp;&nbsp;width>[2, 4, 5],<br>&nbsp;&nbsp;labels>[<br>&nbsp;&nbsp;&nbsp;&nbsp;["Bars",1,1],<br>&nbsp;&nbsp;&nbsp;&nbsp;["Points and Polygon",2,1],<br>&nbsp;&nbsp;]<br>&nbsp;&nbsp;legend>["Kurve1", "Kurve2"],<br>&nbsp;&nbsp;subst>[a,b,c,d]<br>) | Zeichnet die gegebenen Funktionen f1 und f2 und speichert die Grafik sie als SVG Datei (Dateiname.svg) ab, wobei die Achsen beschriftet werden. Die Parameter (*filename*, *xlabel*, *ylabel*, etc) müssen korrekt geschrieben sein, ansonsten werden sie nicht akzeptiert.<br><br>Es können beliebig viele Funktionen in einer Liste zusammengefasst werden.<br>Farben kann man im gewohnten RGB Modell oder mit Standardnamen (blue,red,green, etc) angeben<br><br>*labels* setzt eine Beschriftung an die Koordinaten ["Text", x, y]<br>*width* setzt die Stärke der Linien, Default: 3<br>*legend* fügt eine Legende ein<br>*subst* ersetzt Variable a>b, c>d usw.|
Zeichne([Punkte, Punkte2], x_min, x_max); | funktioniert mit den obigen Parametern, nur werden Punkte gezeichnet.|
Zeichne(<br>[Rectangles], x_min, x_max<br>bars>1<br>); | zeichnet eine Liste von rectangles[]|
Zeichne(<br>[Rectangles], x_min, x_max<br>bars>1<br>); | zeichnet eine Liste von rectangles[]|

SVG Dateien sind skalierbar ohne Qualitätsverlust. Libreoffice kann damit umgehen.

**Beispiel**
```
Zeichne(cos(2*x),0,4);
Zeichne(
  [cos(2*x), x^3+2x, x], 0,4
);
Zeichne_Label( cos(2*x),0,4,
  filename>"Supergrafik",
  xlabel>"die x-Achse",
  ylabel>"die y-Achse"
);

Punkte: [ [0, 0], [0.5, 2.5], [1, 5], [1.5, 7.5], [2, 10], [2.5, 12.5] ];
Punkte2:[ [0, -3], [0.5, -2.5], [1, 5], [1.5, 7.5], [2, 8], [2.5, 9] ];

Zeichne(
    [Punkte, Punkte2], 0, 3,
    xlabel> "Zeit [s]",
    ylabel> "Weg [m]",
    y>[0,20],
    colors>["blue","green"],
    legend>["Kurve1", "Kurve2"]
);

pointlist:append(
    makelist(rectangle([k-1,0],[k, 1]),k,5,10)
) $
pointlist;
Zeichne(
    pointlist , 0, 10,
    bars>1
)$

functions:append(
    makelist(parametric(x, 2*x, x,5,10)
) $
pointlist;
Zeichne(
    functions , 0, 10,
    parametric>1
)$
```
### CSV Dateien

Funktion | Beschreibung
------------ | -------------
ReadCSV(filename,[options]) | Liest eine CSV Datei ein und gibt eine Matrix zurück<br>separator ist ohne Angabe ein *;*<br>skip gibt an, wie viele Zeilen übersprungen werden

**Beispiel**
```
Punkte: ReadCSV("filename.csv",
    separator>",",
    skip>1
);
Zeichne(
    Punkte,0,10,
    legend>["CSV Datei"]
)$
```

### Funktion aus zwei Punkten erstellen

Funktion | Beschreibung
------------ | -------------
CreateFunktion(p1,p2, f) | Erstellt eine Funktion, die durch zwei Punkte festgelegt werden kann

**Beispiel**
```
p1:[5,100]$
p2:[8,130]$
f: y=a*b^x$
f: CreateFunktion(p1,p2, f);
> y=64.58*1.091^x
```
