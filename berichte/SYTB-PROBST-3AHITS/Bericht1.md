# Shell Basics

- Peter Petricevic
- 3AHITS
- SYTB
- 11.10.26
- SYTB


### Beschreibe wie mit vim Dateien erstellt, bearbeitet und gespeichert werden können.

Eingabe:
```sh
vim beispiel.sh
-- Erstellt eine Datei namens beispiel.
``` 

### Führe die wichtigsten Befehle auf und beschreibe sie kurz.
Folgende Befehle:
in der Datei,
drücken Sie die Taste "i", um in der Datei schreiben zu können.

```sh
- :q = quit (Verlassen der Datei)
- :q! = quit! (Verlassen einer Datei ohne sie zu speichern)
- :w = write (Speichern der Datei)
- :wq or :x = writequit (Speichern und Verlassen der Datei)
```


### Erstelle ein HelloWorld script, welches bei Ausführung "Hello World" auf der Konsole ausgibt.
```sh
- vim helloWorld
- (Taste "i" drücken)
- echo Hello World
- :x
```

### Bevor wir es mit ./helloWorld.sh ausführen können müssen wir vorher was machen.

Im Terminal:

```sh
chmod 777 helloWorld.sh
./helloWorld.sh
```

Ausgabe im Terminal:
```sh
Hello World
```

### Wie können Argumente übergeben werden und wie erfolgt der Zugriff?
Zeige, die Möglichkeiten in einem Skript.

in der Datei:

```sh
echo $0
echo $1
echo $#
```

Im Terminal:
```sh
./helloWorld.sh Peter Hallo Welt
```
Ausgabe:
```sh
./helloWorld.sh
Peter
3
```
- echo $0 = gibt den Namen der Datei aus: in diesem Fall: ./helloWorld.sh
- echo $1 = Gib das erste Zeichen aus: in diesem Fall: Peter
- echo $# = Gibt den Wert an, wie viele Zeichen ausgegeben wurden
