Mit MacOSX hat man mit wxmaxima das Problem, dass gnuplot (=grafische Ausgabe) nicht funktioniert. Der Trick besteht darin, gnuplot korrekt zu installieren.
Diese Anleitung sollte zum Erfolg f�hren, und wurde auf High Sierra getestet.
Ein Nachteil ist, das man Xcode installieren muss (~6GB) obwohl man es nicht ben�tigt.

#Schritte

- AppStore installiere Xcode
- Terminal
  *sudo xcode-select -s /Applications/Xcode.app/Contens/Developer*
- Terminal
  *xcode-select --install*

    4. Terminal, Homebrew Package Manager installieren
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

    5. Terminal
brew install gnuplot �-with-qt
brew install maxima
brew install wxmaxima

    6. Jetzt noch Maxima selbst anpassen
Finder ? Profilverzeichnis
 ? .maxima f�hrt zu diesem versteckten Verzeichnis

    7. Terminal
maxima-init.mac
gnuplot_command:"/usr/local/bin/gnuplot"$
draw_command:"/usr/local/bin/gnuplot"$
set_plot_options([gnuplot_term, qt])$

Ab dann klappt klappen die plot() und draw() Befehle.

Was nicht klappt ist: wxplot2d() !!!!!
