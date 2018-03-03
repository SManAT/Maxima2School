Mit MacOSX hat man mit wxmaxima das Problem, dass gnuplot (=grafische Ausgabe) nicht funktioniert. Der Trick besteht darin, gnuplot korrekt zu installieren.
Diese Anleitung sollte zum Erfolg f�hren, und wurde auf High Sierra getestet.
Ein Nachteil ist, das man Xcode installieren muss (~6GB) obwohl man es nicht ben�tigt.

# Schritte

- AppStore installiere Xcode
- Terminal
  *sudo xcode-select -s /Applications/Xcode.app/Contens/Developer*
- Terminal
  *xcode-select --install*

- Terminal, Homebrew Package Manager installieren<br>
  */usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"*

- Terminal<br>
```brew install gnuplot �-with-qt
brew install maxima
brew install wxmaxima
```
- Jetzt noch Maxima selbst anpassen
```
Finder - Profilverzeichnis - SHIFT+CONTROL+G - .maxima führt zu diesem versteckten Verzeichnis
```
- Terminal<br>
**maxima-init.mac**
```
gnuplot_command:"/usr/local/bin/gnuplot"$
draw_command:"/usr/local/bin/gnuplot"$
set_plot_options([gnuplot_term, qt])$
```
Ab dann klappt klappen die plot() und draw() Befehle.

Was nicht klappt ist: wxplot2d() !!!!!
