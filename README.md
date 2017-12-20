# Maxima2School

Diese Erweiterung stellt einige brauchbare Funktionen für den Mathematikunterricht zur Verfügung.

Kopiere die Datei InitMaxima.mac in das gleiche Verzeichnis wie deine Maxima Datei.
Als erste Zeile schreibst du batchload("InitMaxima.mac")$. 
Ab dann stehen dir folgende Funktionen zur Verfügung.

Beschreibung | Beispiel
------------ | -------------
Zeichne(f(x), x_min, ,x_max, Dateiname) | Zeichnet die gegebene Funktion und speichert sie als SVG Datei ab.
Zeichne(f(x), x_min, ,x_max, Dateiname, xAchse, yAchse) | Zeichnet die gegebene Funktion und speichert sie als SVG Datei ab, wobei die Achsen beschriftet werden können.

Beispiel | 
```
Zeichne(
    cos(2*x),0,4,"Test"
);
Zeichne_Label(
    cos(2*x),0,4,"Test","x-Achse","y-Achse"
);
```


GlSys2(gl1,gl2);
GlSys2Var(gl1,gl2,x,y);
GlSys2(gl1,gl2);
GlSys2Var(gl1,gl2,x,y);
Löst eine Gleichungssystem aus zwei Gleichungen auf.
Löst eine Gleichungssystem aus zwei Gleichungen auf wobei die Variablen angegeben werden können

CreateFunktion(p1,p2, f);
p1:[5,100]$
p2:[8,130]$
f: y=a*b^x$
f: CreateFunktion(p1,p2, f);
Erstellt eine Funktion bei zwei gegebenen Punkten

