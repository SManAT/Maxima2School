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
Zeichne([f1(x), f2(x)], x_min, ,x_max,<br>&nbsp;&nbsp;&nbsp;filename>"Dateiname",<br>&nbsp;&nbsp;&nbsp;xlable>"x-Achse",<br>&nbsp;&nbsp;&nbsp;ylable>"y-Achse"<br>) | Zeichnet die gegebenen Funktionen f1 und f2 und speichert die Grafik sie als SVG Datei (Dateiname.svg) ab, wobei die Achsen beschriftet werden. Die Parameter *filename*, *xlable*, *ylable* müssen korrekt geschrieben sein, ansonsten werden sie nicht akzeptiert.<br>Es können beliebig viele Funktionen in einer Liste zusammengefasst werden.|

SVG Dateien sind skalierbar ohne Qualitätsverlust. Libreoffice kann damit umgehen.

**Beispiel**
```
Zeichne(cos(2*x),0,4);
Zeichne(
  [cos(2*x), x^3+2x, x], 0,4
);
Zeichne_Label( cos(2*x),0,4,
  filename>"Supergrafik",
  xlable>"die x-Achse",
  ylable>"die y-Achse"
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
