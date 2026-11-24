# Cmdsubst

- Peter Petricevic
- 3AHITS
- SYTB
- 04.11.26
- https://github.com/HTL-Braunau-probst/SYTB-3-LAB-AHITS24/blob/main/0302_cmdsubst_ue.md

## Übung (Tage bis zum Ball)

### Schreibe ein Shell-Skript das die Anzahl der Tage bis zum HTL Ball ermittelt. Das Datum des Balls soll am Anfang des Skripts in einer Variable stehen. Die Ausgabe soll in der folgenden Form sein:

So soll es aussehen:
```sh
Es sind noch 94 Tage bis zum HTL Ball (2027-01-15)
```

- in der Datei tagezumBall.sh

```sh
#!/bin/bash

ball_datum:"2027-01-15"

heute=$(date +%s)
ball=$(date --date="$ball_datum" +%s)

tage=$(( (ball - tage) / 86400))

echo "Es sind noch $tage Tage bis zum HTL Ball ($ball_datum)"
```

- im Terminal
```sh
bash tagezumBall.sh
```

---

## Übung (Zufälliger Satz)

### Erstelle ein Skript das einen Satz aus 5 zufälligen Wörtern bildet, z.B.:

```sh
richtig ganzen Kilometer auf Mittel
```

Wähle die Wörter aus dieser Wortliste: Wörter (link)

- Lade die Wortliste mit ```wget``` herunter.
- Das Skript soll auch die Anzahl der in der Wortliste enthaltenen Wörter ermitteln. D.h. die Konstante 1000 soll im Skript nicht vorkommen.

- im Terminal
```sh
wget https://raw.githubusercontent.com/HTL-Braunau-probst/testdata/refs/heads/main/wordlist.txt
```

- in der Datei rndmSatz.sh

```sh
#!/bin/bash

anzahl=$(wc -l < wordlist.txt)

word1=$(sed -n "$((RANDOM % anzahl + 1))p" wordlist.txt)
word2=$(sed -n "$((RANDOM % anzahl + 1))p" wordlist.txt)
word3=$(sed -n "$((RANDOM % anzahl + 1))p" wordlist.txt)
word4=$(sed -n "$((RANDOM % anzahl + 1))p" wordlist.txt)
word5=$(sed -n "$((RANDOM % anzahl + 1))p" wordlist.txt)

echo "$word1 $word2 $word3 $word4 $word5"

```

- im Terminal

```sh
bash rndmSatz.sh 
```

---

## Übung (Datierte Kopie V1)

### Schreibe ein Skript, das einen Dateinamen als erstes Argument übernimmt und eine datierte Kopie der Datei anlegt. Heißt die Datei z.B. ```file1.txt``` und ist heute der 2026-10-13, so soll die Kopie ```2026-10-13_file1.txt``` heißen.

- in der Datei datecopy.sh

```sh
#!/bin/bash

date=$(date +%Y-%m-%d)

file=$1

new="${date}_${file}"

cp "$file" "$new"
```

- im Terminal

```sh
bash datecopy.sh
```