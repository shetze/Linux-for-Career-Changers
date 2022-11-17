#Linux Toolbox Essentials

Um Linux in seiner Vielfalt zu erschließen, ist es sinnvoll und notwendig, ein paar Werkzeuge kennenzulernen und deren Verwendung einzuüben.
Ich möchte hier eine subjektive Auswahl der aus meiner Sicht wichtigsten Werkzeuge vorstellen. Jedes dieser Werkzeuge verdient spezielle Aufmerksamkeit und Beachtung. In der kurzen Vorstellungsrunde kann ich die Macht und die Möglichkeiten dieser Werkzeuge nicht einmal annähernd aufzeigen. Es geht mir eher darum, die Verwendung in einem relevanten Kontext zu zeigen und den praktischen Wert unserer Werkzeugkiste zu demonstrieren.

Für eine eigene und tiefere Erkenntnis und Erfahrung musst du für jedes dieser Werkzeuge mindestens eine halbe Stunde Zeit einrechnen, in der du dich intensiv mit den Optionen und der Funktion vertraut machst. Einige der Tools brauchen und verdienen mehrere Stunden. Das ist aber auf jeden Fall gut investierte Zeit! Wenn du dann beginnst, jeden Tag mit diesen Werkzeugen zu arbeiten, wirst du schnell deinen eigenen Weg in die Welt von Linux und Open Source Software finden.

Ich gehe davon aus, dass du einen Linux Arbeitsplatzrechner oder wenigstens eine Virtuelle Maschine vor dir hast, mit dem du die von mir gezeigten Schritte nachvollziehen kannst. In den Beispielen verwende ich Red Hat Enterprise Linux, du solltest das aber auch mit jeder anderen Linux Distribution machen können.

Ich empfehle, zuerst diesen Text als Ganzes zu lesen und erst im Anschluss mit den eigenen Übungen zu beginnen.
In diesem Dokument sind alle Schritte und Beispiele aufgeführt, so dass du sie selbst in deiner eigenen Geschwindigkeit nachvollziehen kannst.



##Gnome Terminal
Los geht's mit dem Gnome Terminal. 

Auf dem RHEL Notebook findest du das Programm unter `Applications->Sytem Tools->Terminal`

Als Terminal wurde im letzten Jahrtausend eine mit dem Computer verbundene Arbeitsstation aus Textbildschirm und Tastatur bezeichnet. Der Begriff Terminal steht seither auch innerhalb einer sonst grafischen Benutzeroberfläche für das textbasierte Interface zum Betriebssystem.

Nachdem du das Gnome Terminal im Menü aufgerufen hast, erscheint ein Fenster mit schwarzem Hintergrund und einer Eingabeaufforderung in weißer Schrift. Du kannst das Aussehen und einige Eigenschaften des Terminalfensters deinem Geschmack oder deinen Anforderungen anpassen.

Die Standardgröße des Terminal Fensters ist 80x24, das heisst du hast 24 Zeilen zu je 80 Zeichen Länge. Das Fenster lässt sich mit der Maus ziehen und in jede Größe verändern. Über den Menüpunkt `Terminal` lassen sich auch andere fest eingestellte Terminalgrößen auswählen. Im Menüpunkt View kann die Schriftgröße verändert werden.
Die meisten Menüpunkte lassen sich auch über Tastaturkürzel erreichen. Zum Beispiel mit der Tastenkombination `Shift-Ctrl-T` kannst du in dem gleichen Fenster ein zweites Tab mit einem weiteren Terminal aufmachen. Mit der Tastenkombination `Alt-1` und `Alt-2` kannst du zwischen dem ersten und zweiten Tab umschalten. Mit `Ctrl-PageUp` und `Ctrl-PageDown` kannst du in einer Reihe von Tabs rauf und runter blättern.

##bash
In dem Terminalfenster siehst du eine Eingabeaufforderung. Das ist eine Zeichenkette und eine Markierung für die Texteingabe. Die Zeichenkette zeigt normalerweise meinen Benutzernamen und den Namen des Rechners auf dem ich arbeite. Außerdem wird der Name des Verzeichnisses angezeigt, in dem ich mich aktuell befinde. Mit der Tilde wird mein Heimatverzeichnis bezeichnet.

Die Eingabeaufforderung gehört zu den wichtigsten aller Programme in meiner Liste, der Shell. Die Shell ist ein Programm, dessen Zweck darin besteht, andere Programme zu starten und diesen Programmen eine definierte Laufzeitumgebung zur Verfügung zu stellen. 

In der Regel wird eine solche Shell interaktiv verwendet, es sitzt also eine Person an dem Terminal und gibt die Befehle über eine Tastatur ein. Die Shell kann aber auch automatisch ablaufen und die Befehle aus einer Textdatei lesen. Diese Textdatei heißt Shellscript oder Batch. In so einem Shellscript können echte Programme geschrieben werden, mit Variablen, Funktionen, Schleifen und allem, was so zu einem Computerprogramm dazugehört. Mit dem Lesen von Programmen werden wir uns in einer späteren Session befassen.

Alle Daten, das sind Programme, Texte, Bilder oder irgendwelche anderen in Bits und Bytes codierten Informationen, die sich in einem Linux System befinden sind in einem einzigen Dateisystem repräsentiert. Dieses Dateisystem ist ein Baum aus Verzeichnissen. Die Struktur dieses Baums folgt dem Linux Datei System Standard.

Jeder User hat sein eigenes Home Verzeichnis in dem `/home` Ast des Verzeichnisbaums. Mit dem Shellkommando `pwd` wird mir das aktuelle Arbeitsverzeichnis angezeigt. Mit `cd` kann ich in ein anderes Verzeichnis wechseln. Dabei kann ich den Namen des Zielverzeichnisses absolut mit einem führenden Slash oder ohne Slash relativ zu meinem aktuellen Verzeichnis angeben.

Mit `cd` ohne Angabe eines Zielverzeichnisses gelange ich immer sofort in mein Heimatverzeichnis. Mit `cd -` wechsele ich zurück in das zuletzt verwendete Verzeichnis.

Die Shell ist ein enorm mächtiges Programm und es lohnt sich, dessen Verwendung und Möglichkeiten gründlich zu erlernen. 

##man
Um alle Details zur Verwendung eines Programms zu erfahren, gibt es die Manual Pages.

Mit `man bash` wird mir die Dokumentation zur Shell angezeigt. In dem Dokument sehen wir, dass die bash seit 1989 verwendet wird und dass sie der Nachfolger der Bourne Shell ist. Das war damals schon eine sehr beliebte und weit verbreitete Shell für UNIX Systeme. Die bash ist eine verbesserte und um so mehr beliebte Version. Es gibt noch andere Shells für Unix, zum Beispiel die Korn Shell oder die C Shell. In der bash sind einige der besten Features dieser anderen Shells enthalten, so dass wir heute praktisch nur noch die bash verwenden.

Du wirst einige Zeit brauchen, um dich mit den vielen Möglichkeiten der bash vertraut zu machen. Nimm dir diese Zeit, sie ist gut investiert. Ich habe mich irgendwann 1990 oder 1991 mehrere Wochen ganz intensiv mit der bash beschäftigt und sie für mich zu Minix portiert. Ich würde sagen, diese Stunden gehören sicher zu den besten Investitionen in meine persönliche Entwicklung.

Die Manualpage von bash ist ziemlich lang, du kannst mit den Tasten `Space` und `b` vorwärts und rückwärts blättern. Die Tasten `PageUp` und `PageDown` haben die gleiche Funktion. Du kannst mit `/` einen beliebigen Suchbegriff eingeben und mit `n` und `N` zwischen den Fundstellen hin und her navigieren. Mit `q` für quit verlässt du die Manualpage und gelangst zurück zur Eingabeaufforderung.

Mit `Ctrl-L` wird der aktuelle Inhalt des Terminalfensters gelöscht.

##ls
Sämtliche Daten im Linux System sind in dem einen großen Dateisystem organisiert. Um hier eine Übersicht zu bekommen, gibt es das Werkzeug ls. Mit `ls` wird der Inhalt eines Verzeichnisses angezeigt.

Ohne weitere Argumente wird einfach der Inhalt des aktuellen Arbeistverzeichnisses gelistet. Oben haben wir gesehen das das interne bash Kommando `pwd` den Namen und den Pfad dieses Verzeichnisses anzeigt.

Das Wurzelverzeichnis in dem der gesamte Dateisystembaum beginnt wird mit einem `/` bezeichnet. `ls /` zeigt den Inhalt dieses Wurzelverzeichnisses an.

Um zusätzliche Informationen zu den Eigenschaften der aufgelisteten Objekte in einem Verzeichnis zu bekommen, kann ls mit zusätzlichen Optionen aufgerufen werden. Eine Liste aller Optionen bekomme ich mit `ls --help`.

Wenn wie hier die Ausgabe eines Programms auf die Standardausgabe des Terminals über einen Bildschirminhalt hinaus geht, bietet das Gnome Terminal die Möglichkeit mit `Shift-PageUp` und `Shift-PageDown` im Inhalt zurück und wieder vor zu blättern. Bei anderen Terminalprogrammen kann diese Funktion ganz fehlen oder mit anderen Tastenkombinationen verbunden sein.

Es lohnt sich, alle möglichen Optionen von ls zu verstehen und auszuprobieren. Beispielsweise erhalten wir mit `ls -l` ein langes Listing in dem der Dateityp, die Zugriffsrechte, die Anzahl der Unterverzeichnisse, Eigentümer und Gruppe sowie die Größe und das Datum der letzten Änderung an.

Objekte, deren Name mit einem Punkt beginnt, werden bei einem einfachen Listing nicht angezeigt. Um alle Dateien in dem Listing zu sehen, muss die Option `ls -a` angegeben werden.

Als normaler User habe ich nicht das Recht, alle Daten zu sehen. Noch weniger kann ich Daten verändern. Nur in meinem Heimatverzeichnis gehören mir alle Daten und ich habe alle Rechte.

##mkdir

Zum Beispiel kann ich in meinem Heimatverzeichnis neue Verzeichnisse anlegen.

`mkdir -p Uebungen/Tools`

Ich kann sofort mit `cd` in dieses Verzeichnis als neues Arbeitsverzeichnis wechseln und dann darin arbeiten.

Um mir die doppelte Eingabe des Verzeichnisnamen zu ersparen, kann ich bei der Eingabe auf der Kommandozeile von bash einfach `Esc-.` eingeben. Dann erscheint automatisch das letzte Argument der letzten Kommandozeile. Anstelle von `cd Uebungen/Tools` gebe ich einfach `cd Esc-.` ein. Nach einer Weile wirst du dieses `Esc-.` ganz automatisch verwenden.

Wie gesagt, es lohnt sich ein bischen Zeit in das Lernen von bash zu investieren. Diese Zeit wird im Laufe des Lebens Sekunde für Sekunde zurückgezahlt.

Mit bash kann ich auch eine ganze Liste von Verzeichnissen in einem einzigen Aufruf anlegen.

`mkdir -p ~/rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}`

##vim 
Wenn ich eine existierende Textdatei bearbeiten oder eine neue erzeugen möchte, brauche ich einen Texteditor. Im Jahr 1976 wurde von Bill Joy für diesen Zweck das UNIX Programm vi geschrieben. Eine verbesserte Version dieses Editors ist in jedem Linux System unter dem Namen `vim` enthalten.

Auch für vim gibt es eine Manualpage `man vim`. Ausserdem kann ich im Editor mit dem Befehl `:help` sehr ausführliche Informationen zur Verwendung des Editors bekommen. Auch für vim lohnt es sich, ein paar Stunden in das Studium der verschiedenen Funktionen zu investieren. Im Unterschied anderen Editoren sind die zentralen Funktionen seit vielen Jahrzehnten bewährt und stabil. Finde selbst heraus, weshalb dieser Editor als Standard für alle UNIX und Linux Systeme etabliert ist.

Als ersten Einstieg: Der Editor arbeitet in verschiedenen Modi. Das Programm startet im Befehlsmodus in dem die Tastatureingaben bestimmte Aktionen auslösen. Mit dem Befehl `i` wechselt der Editor in den Insert Modus, in dem dann alle Tastatureingaben an der aktuellen Position des Cursors eingefügt werden. Mit der `Esc` Taste wechselt der Editor zurück in den Befehlsmodus.
Mit `x` lösche ich das Zeichen unter dem Cursor, mit `D` lösche ich die Zeile vom Cursor bis zum Zeilenende, mit `dd` lösche ich die gesamte Zeile. Mit `p` kann ich die so gelöschte Zeile unterhalb des Cursors wieder Einfügen, mit `P` wird die Zeile oberhalb eingefügt.
Mit `:w` wird die Datei geschrieben und mit `:q` verlasse ich den Editor.

##view 
Wenn ich verhindern will, dass ich eine existierende Datei aus Versehen verändere, kann ich den Editor auch unter dem Namen view aufrufen. Dann startet er automatisch im read only Modus.

##less 
Eine andere Möglichkeit Dateien einfach nur anzuzeigen ohne sie zu editieren bietet ein sogenannter Pager. `less` ist so ein Werkzeug. Ohne es zu merken haben das schon bei den Aufrufen von man kennengelernt. Less ist nämlich der Standard-Pager und wird von man zum Anzeigen der Manualpages automatisch verwendet. 

##chmod
Für die eigenen Dateien und Verzeichnisse kann ich bestimmen, welche Rechte meine Gruppe und die übrigen Nutzer an diesen Objekten haben. Dafür gibt es das Tool `chmod`.
In der Manualpage `man chmod` wird auch die Bedeutung der verschiedenen Rechte erklärt.

##yumdownloader
Es gibt viele Möglichkeiten, Dateien aus dem Internet in mein Heimatverzeichnis zu laden. Wenn ich die Quelltexte und alle Steuerdateien zum Erzeugen eines der im RHEL enthaltenen Programme in mein Heimatverzeichnis laden möchte, kann ich das Werkzeug yumdownloader verwenden.
 
`yumdownloader --source bash`
lädt das Source RPM Paket von Red Hat aus dem Internet. Das geht für alle aus RPM Paketen installierten Programme, vorausgesetzt das System ist mit einer gültigen Red Hat Subskription ausgestattet.

Wenn das Programm yumdownloader noch nicht auf deinem System installiert ist, muss da Paket yum-utils nachinstalliert werden.

##rpm
Um ein mit yumdownloader geholtes Source RPM Paket auszupacken, verwende ich das Red Hat Package Manager Tool `rpm`
Das Source RPM installiert alle Dateien automatisch in meinem Heimatverzeichnis in dem Unterverzeichnis `rpmbuild`. Zufällig habe ich das ja in mit `mkdir -p ~/rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}` vorhin schon angelegt.
Wenn dieses Verzeichnis nicht existiert wird es beim Auspacken des Source RPM automatisch erzeugt.

In dem Verzeichnis `~/rpmbuild/SOURCES` werden alle Quelltexte abgelegt, die Red Hat zum Bauen des ausführbaren Programms verwendet hat. Im Verzeichnis `~/rpmbuild/SPECS` liegt die Steuerdatei für das RPM Build System in der die Spezifikation zum automatischen Bauen hinterlegt ist.

Die meisten SOURCES Dateien sind relativ kleine Patches. Patches sind Änderungen, die während des Bauens an den Sourcen vorgenommen werden. Das eigentliche Source-Paket ist die Datei mit der Endung `tar.gz`
Dabei handelt es sich um ein mit gzip komprimiertes TAR Archiv.

##tar
`tar` ist ein Werkzeug und ein Dateiformat, das für UNIX schon im Jahr 1979 entwickelt wurde. Der Name weist auf die ursprüngliche Funktion zum Schreiben und Lesen von Datensicherungen auf Magnetbändern hin. Es lassen sich aber ebenso gut Archivdateien auf einer Festplatte damit bearbeiten.

```
cd ~/rpmbuild/BUILD
tar xvfz ../SOURCES/bash-4.2.tar.gz
```

##cp 
##mv 
##rm 
##rmdir 
##git
##grep 
##sort 
##head 
##tail 
##make 


