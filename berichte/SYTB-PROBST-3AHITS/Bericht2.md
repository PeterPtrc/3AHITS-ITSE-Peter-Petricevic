# Scripts

- Peter Petricevic
- 3AHITS
- SYTB
- 02.11.26
- SYTB

# Übung (Directory Struktur) 

### Schreibe ein Shell-Script das Unterverzeichnisse und Dateien anlegt, es wird ein Argument an das Script übergeben. 

Im Terminal: 
```sh
./make_dir.sh abcd
``` 
Dies führt zu folgender Directorystruktur:

```sh
./ 
└── abcd/ 
    ├── abcd_01/ 
    │   ├── abcd.01.1.txt 
    │   ├── abcd.01.2.txt 
    │   └── abcd.01.3.txt 
    └── abcd_02/ 
        ├── abcd.02.1.txt 
        ├── abcd.02.2.txt 
        └── abcd.02.3.txt 
```

### Schreibe weiters ein Shell-Script clean_dir.sh das diese Verzeichnisstruktur wieder löscht.

--- 

- in der Datei make_dir.sh:


```sh
#!/bin/bash

name="$1"
mkdir -p "$name"
for i in 01 02
do
    mkdir -p "$name/${name}_${i}"
    for j in 1 2 3
    do
        touch "$name/${name}_${i}/${name}.${i}.${j}.txt"
    done
done
```

- im Terminal:

```sh
chmod 755 make_dir.sh 
./make_dir.sh abcd 
tree abcd
```

---

## Löschen des Ordners

- Datei anlegen
```sh
touch delete_dir.sh
```

- In der Datei

```sh
#!/bin/bash 

rm -r "$1"
```

- Im Terminal

```sh
chmod 755 delete_dir.sh
```

Ausgabe ebenfalls im Terminal: 

```sh
./delete_dir.sh abcd
```

# Übung (Skript Generator)

## Schreibe ein Skript das 
-  eine Skriptdatei erzeugt (Name wird als Argument übergeben), 
-  die She-Bang Zeile einfügt, 
-  einen echo Befehl einfügt und 
- das eXecution Flag für das Skript setzt.

- Ausführung:
```sh 
./makescript.sh test
```

- erstellt die Datei test.sh

```sh
#!/bin/sh 
echo "test Skript" 
# write yor script here
```

- Dieses Skript kann sofort ausgeführt werden:
```sh
./test.sh
```

---

- Erstellen der Datei:

```sh
touch make_gen.sh
```

- In der Datei:

```sh
#!/bin/bash
touch "$1.sh" 
chmod +x "$1.sh" 
echo "#!/bin/sh" >> "$1.sh" 
echo "echo \"$1 Skript\"" >> "$1.sh" 
echo "# Dein Skript" >> "$1.sh"
```

- Im Terminal
```sh
chmod 755 make_gen.sh
./make_gen.sh test 
./test.sh
```

- Ausgabe:
```sh
test Skript
```

# Übung (Headline Cat)

## Verwende $@ zur Lösung dieser Aufgabenstellung.

## Schreibe ein Skript das eine Art cat zur Verfügung stellt. Als Argumente werden eine beliebige Anzahl von Textdateien übergeben. Das Ergebnis wird in die Datei result.txt geschrieben (ist die Datei vorhanden soll deren Inhalt überschrieben werden). Jedem Datei-Inhalt soll eine Überschrift vorangestellt werden.

- (Beispiel):
- Eingabe:
```sh
./headline_cat.sh file1.txt file2.txt file3.txt
```

- Ausgabe:
```sh
== file1.txt ========================================== 
Das ist der Inhalt der ersten datei 

== file2.txt ========================================== 
Das ist der Inhalt der zweiten datei 

== file3.txt ========================================== 
Das ist der Inhalt der dritten datei
```

--- 

- Erstellen der Datei:
```sh
touch headline_cat.sh
```

- in der Datei
```sh
#!/bin/bash
> strich.txt

for file in "$@"
do
echo "== $file ==========================================" >> strich.txt
cat "$file" >> strich.txt
echo "" >> strich.txt
done
```

- im Terminal
```sh
chmod 755 headline_cat.sh 
echo "beispiel1" > file1.txt 
echo "beispiel2" > file2.txt 
echo "beispiel3" > file3.txt 
./headline_cat.sh file1.txt file2.txt file3.txt 
cat beispiel.txt
```