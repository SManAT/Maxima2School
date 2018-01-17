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
Zeichne(f(x), x_min, ,x_max, Dateiname) | Zeichnet die gegebene Funktion und speichert sie als SVG Datei ab.
Zeichne(f(x), x_min, ,x_max, Dateiname, xAchse, yAchse) | Zeichnet die gegebene Funktion und speichert sie als SVG Datei ab, wobei die Achsen beschriftet werden können.

SVG Dateien sind skalierbar ohne Qualitätsverlust. Libreoffice kann damit umgehen.

**Beispiel**
```
Zeichne(
    cos(2*x),0,4,"Test"
);
Zeichne(
    [cos(2*x), x^3+2x, x], 0,4,"Test"
);
Zeichne_Label(
    cos(2*x),0,4,"Test","x-Achse","y-Achse"
);
```
### Gleichungssysteme lösen

Funktion | Beschreibung
------------ | -------------
GlSys2(gl1,gl2) | Löst eine Gleichungssystem mit zwei Gleichungen nach x und y auf
GlSys2Var(gl1,gl2,x,y) | Löst eine Gleichungssystem mit zwei Gleichungen auf, wobei die Variablen angegeben werden können

**Beispiel**
```
gl1: 2*x+3*y=12;
gl2: 2*x-4*y=14;
GlSys2(gl1,gl2);
GlSys2Var(gl1,gl2,x,y);
> [x=45/7,y=-2/7]
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
