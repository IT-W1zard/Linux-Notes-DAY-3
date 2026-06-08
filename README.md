# Linux-Notes DAY 2  
cd /etc  
[ONMO@localhost etc]$ ls /etc/profile /etc/bashrc  
/etc/bashrc  /etc/profile  
[ONMO@localhost etc]$ ls -al /etc/profile /etc/bashrc  
-rw-r--r--. 1 root root 2658  7. Apr 2024  /etc/bashrc  
-rw-r--r--. 1 root root 1899  7. Apr 2024  /etc/profile  
cat /etc/bashrc Ruft die Globale Bash Konfigurationsdatei  
Zeigt die Zugriffsberechtigungen den besiter die größe den Zeitstepel und den Standort der Globale Konfigurations Dateien  
gelten für alle User  

alias NAME='BEFEHL' Gibt einen Temporären Shortcut als Name für einen Befehl an  
Sudo („superuser do“) erlaubt es dir, einen Befehl mit den Rechten eines anderen Benutzers – meist des Administrators (root) –  auszuführen  

unalias NAME  

source .bashrc akuallisiert die Bashrc  

nano .bashrc bearbeitet die bashrc  
"Erlaubt dauerhafte alias zu machen aktualisieren nicht vergssen nach dem verlassen der Bashrc"  

WERT1=WERT2  
echo $WERT1  
Ausgabe WERT2  

printenv/env umgebungsvariable zeigt die komplette Umgebung=Session oder auch die Aktuelle Sitzung nach start des PCs  
printenv HOME  
printenv SHELL  
printenv USER  
printenv PATH pfad zum benutzerverzeichniss/user spezifische umgebungsvariablen  

| head zeigt die ersten 10 zeile an (modifizierbar -20 -30 usw  
| tail zeigt die letzten 10 zeile an (modifizierbar -20 -30 usw  
| BEFEHL | BEFEHL Pipes "|" führen immer einen Befehl nach dem anderen aus  

stdout 1  
BEFEHL > NAME erstellt eine Datei und erneute eingabe überschreibt die Datei mit eingegebenem Text  
BEFEHL >> NAME erstellt eine Datei und erneute eingabe fügt Text hinzu  

BEFEHL 2> NAME erstellt eine Datei und erneute eingabe überschreibt die Datei mit der Fehlerangabe z.B. Syntax Error  
BEFEHL 2>> NAME erstellt eine Datei und erneute eingabe fügt die Fehlerangabe z.B. Syntax Error hinzu  

BEISPIEl  
find 2> /(<--- root) t  /dev/null (<--- um die Fehler rauszuwerfen ergebniss)  
  
findet alles mit t im root verzeichnis und schmeißt die error/fehler also z.B. datein auf die wir keinen zugriff haben raus  

<_datin  
<< text  

FIFO Pipe: First In - First Out  

stdin 0  am anfang eines befehls gibt es weiter an dne stdout an nach der pipe am ende des befehls
stdout 1  
stderr 2  

xargs nl, expand, unexpand, uniq  

find name perm dataError  

find /             / gibt hier den startpunkt an  

-perm um nach rechten(permissions) zu suchen

# Linux-Notes-DAY-3
filter programme die nach der pipe eingesetzt werden können  
cat, passwd, bash, head, tail, wc, less, more, ssh, cut, tac  

xargs nl, expand, unexpand, uniq  

xargs macht aus nicht filterprogrammen filterprogramme  
is, cp, mv, rm, ping, netstat, mkdir, cd, rmdir, find, pwd, date, man ,apropos, whatis,  
whoami, info, type, file, whereis, who, w, user, stat, df, free, top, uptime, uname, id, touch  

tr translate keine dateiennamen, einzelne zeichen löschen, ersetzen  

echo Bärenhöhle | tr 'a-zäöü' 'A-Z'  
B??RENH??HLE  
 -d delete löscht zeichen X vom text Bären-höhle Bärenhöhle  
 -s squeeze entfernt jedes zeichen bis auf eines in einer reiche von zeichen Bären------höhle Bären-höhle  
   
 Sonderzeichen sind möglich, benannte Bereiche nach POSIX [:alpha:] alle Buchstaben, inklusve umlaute  

echo Bären---höhle | tr -s '-'        Ergebniss= Bären-höhle  
echo Bären---höhle | tr -s '-' '\'    Ergebniss= Bären\höhle  
echo Bären---höhle | tr -s '-' '\t'   Ergebniss= Bären höhle  
echo Bären---höhle | tr -s '-' '\n'   Ergebniss= BärenZEILENUMBRUCHhöhle  

Cut vertikal durch einen Text -c character zeichen  
cut -c 1-3,5/etc/passwd  

 -d delimiter z.B. der Doppelpunkt - gibt den Stop and  
 -f einzelne Felder - gibt wie viele stops an  
 -s separator, Verhindert die Ausgabe von Feldern ohne Trennzeichen - macht einen stop bei leerzeichen  

cut -d: -f1,5 /etc/passwd  

sort
-n sortiert alphanumerisch
-r sortierreihenfolge umkehren
-u nur einmalige Werte, keine dubletten

* steht für alle zeichen außer für . am Namensanfang; auch kein Zeichen

? genau 1 beliebiges Zeichen außer . am Namensanfang

[....] genau ein Zeichen der angegebenen Zeichen menge außer . am Namensanfang

[^...] genau 1 Zeichen aus der Nicht angegebenen Zeichenmenge ansonsten wie [...] aufer . am Namensanfang  

{dat..,V...xyz} erlaubt mehrere Dat/Verz Namen mit obigen Sonderzeichen ACHTUNG: Keine Leerzeichen  



| Trennt Kommandos unabhänigig voneinander  

; kommandos werden nacheinander ausgeführt sind unabhängig voneinander Ausführung:nacheinander  

- Kommandos sind unabhängig voneinander ausführung: quasi gleichzeitig  



&& verkürztes if: arbeitet cmd1 korrekt dann wird cmd2 ausgeführt  

|| verkürztes if arbeitet cmd1 fehlerhaft wird cmd 2 ausgefphrt  

echo $? zum prüfen ob richtig ausgeführt RS: >0 RS: =0  



\ entzieht dem nachfolgenden Zeichen die Sonderbedeutung  

' ' entzieht allen zeichen die Sonderbedeutung  

´´ ´´ ist ähnlich wie ' ', aber die Sonderbedeutung bleibt bestehen  



^ alles hier nach NICHT BEACHTEN  



() alles in der () wird wie EIN kommando gesehen u in einer Subshell ausgeführt KOmmandosubstitution  
Subshell  
$[] Kommandosubstitution  
[] [^ ] Datei-Verz.-Expansion, Filterzeichen  
{} wie () aber in der momentanen Shell  
{} Variablensubstitution  



[ONMO@localhost ~]$ cd /etc; echo "Aktuelle Shell: $(pwd)" 
Aktuelle Shell: /etc  
[ONMO@localhost etc]$ cd ~                           <--- Wechsel zu /etc  
[ONMO@localhost ~]$ (cd /etc; echo "Aktuelle Shell: $(pwd)")   
Aktuelle Shell: /etc                                 <--- Springt unsichtbar in die Subshell um den Befehl dort auszuführen  
[ONMO@localhost ~]$                                  <--- Wegen () noch in der akutellen Shell   




-rw programm  
drw directory/verzeichniss  
l symbolische links  



[ONMO@localhost ~]$ mkdir Ort && touch ./Ort/dat1  
[ONMO@localhost ~]$ ls ./Ort  
dat1  
[ONMO@localhost ~]$  



[ONMO@localhost ~]$ true && echo Wahr || echo Fehler  
Wahr  
[ONMO@localhost ~]$ false && echo Wahr || echo Fehler  
Fehler  
[ONMO@localhost ~]$  



[ONMO@localhost ~]$ echo ${USER}123  
ONMO123  

# DAY4

Zugriffsrechte unter Unix

- Datei
- d Verzeichnis
- l softlink
- c Character Device
- b Block Device
- p Named Pipe
- s Unix Domain Socket

drwxr-xr-x. 2 semus semus 4096 25 Jan 12:31
-rw-r--r--. 1 semus semus 4410 30 jan 13:53 semus

 Anzahl | Username | Gruppenname | Größe | Datum | Dat.Verz |
-------------------------------------------------------------
r Datei:Lesen Verz: Inhalt auflisten
w Datei: änderbar Verz: Einträge Löschen/anlegen/ändern
x Datei: Execute Recht Verz: cd Recht
--------------------------------------------------------------
4 2 1 = 7 
r w x 

4   1 = 5
r   x 

usw

Man kann 1 also x nur von ungerade zahlen abziehen

Rechte entfernen chmod u-w DATEI
Rechte hinzufügen chmod u+w DATEI

u USER
g GROUP
a OTHERS

  USER GROUP OTHERS
l rwx   rwx   rwx

getfacl zeug zeigt mir alle Rechte einer Datei
andere option ls -l

umask ändert die rechte um einen wert standard 777 (innerhalb des verzeichnisses) umask 0|022 Verzeichnis Rechte 755 - Datei Rechte wenn ungerade Execute rechte abziehen also -1 wenn nicht bleibt gleich 644 Ergebniss

## SONDER RECHTE
U s steht für SUID Set User ID Bit

G s steht für SGID Set Group ID Bit

O t steht für Sticky Bit Verz mit allen rechten aber ursprüngliche Rechte bleiben "kleben"

Sonderrechte können nur für Programme gesetzt werden!!!



Hardlink In ./Ort/HARDLINK /Ort/HARDZIEL
Softlink In -s ./Ort .Ziel/



Hardlink counter Dateien 1 / Verzeichenisse 2 (alles wegen Ebenen)



# DAY5


echo $? -prüft ob der vorherige befehl funktiniert hat 0=Ja alles andere ist die anzahl der fehler

echo $ "variable" gibt variable aus wie z.B. 4 5 oder hallo



Kennwerte: unter/proc
PID Process ID; eine eindeutige Prozessnummer
PPID Parent process ID; alle Prozesse kennen die Nummer des Elrernprozesses
UID, GID User ID, Group ID; Benutzer von denen der Prozess erzeugt wurde
PRI, NI priority, nice; Scheduler: Verteilung der Zeitscheiben nach Priorität; Prozesse: Eingabe-,
        Ausgabeoperation >PRI als Prozesse, die nur Rechenzeit verbrauchen; PRI kann nicht geändert
        werden 


## Der Kernel -
Initalisiert die Hardware und startet den 1.Prozess:
init (früher)
systemd (heute Linux) forking(gabel. = Prozessverdopplung)

process listing
ps, ps a, ps ax ohne -  ps -e, ps -ef mit ,-´ Tipp: man ps, pstree -p zeigt Prozess Baumliste
ps       zeigt alle über eine auswahl der activen prozesse
ps a     das gleiche wie ps aber in einem anderen style
ps ax    um jeden prozess zu sehen der BSD Syntax benutzt

ps -e    um alle prozesse auf dem System zu sehen
ps -ef



Runable, Sleeping, Zombie, Waiting, Finished =Prozessstatus
Idle minimale Ressourcen verbrauch basically Standby


kill -SIGNAL pid (pid= Process ID)
killall prozessname
kill -l Listet ale Signale mit Name u. Zahl default SIGTERM(15)



nice -n cmd macht Befehle freundlicher, höhere Nice-Wert geringe Priorität, negative Werte nur als root
möglich; Setzt default +10 wenn keine Zahl hinter dem Kommando eingeben wurde
Nice-Werte: -20 bs +19, default gesetzt: 0

renice zahl pid    greift auf laufende Prozess zu und verändert den Wert über Prozess-ID

sudo renice -5 PROZESS ID [nur bei laufenden prozessen]



pstree -p Praktisch Tree + alle verzweigungen



innerhalb des top befehls
strg + z SigStopp [packt den prozess in den Hintergrundmodus]
strg + c Siginterrupt

jobs [um die Job ID zu finden]

fg %JOBID fg=foreground

sleep 100 & [versetzt einen prozess für 100sekunden in den schlafmodus] [& versetzt prozesse in den Hintergrund]

tty = strg alt F2 [öffnet eine konsole die mit sowohl dem root als auch dem User bedient werden kann falls z.B. die Konsole
auf dem Hauptrechner nicht mehr funktioniert]

# DAY6

top -bin 5 > DATEINAME [für den top befehl start ohne visuelle oberfläche wegen -b i sagt du nimmst nur die aktiven prozesse und n sagt du nimmst 5 Snapshots auf in der datei DATEINAME]

tar -befehl z.B. c dann optionen dann Archivdatei und dann was du aktivieren willst
tar steht in jeder unix implementierung zur verfügung
BEISPIEL: tar --delete -f archiv.tar ./Kontinente/Italien
Betriebsmods:
-c (create)  
-x (extract)  
-t (table of contents) inhaltsverzeichniss anzeigen  
-r um neue Dateien hinzuzufügen oder anzuhängen  
Optionen:
-v (verbose, "geschwätzig") Mittelsamkeit Ausgabe wie mit -l  
-f (file) Angabe des Dateinamens des Archives  
-r um neue Dateien hinzuzufügen oder anzuhängen  
--delete -f Archivdatei Verzeichniss-Dateien  

./ am ende legt eine Datei an

Für GNU-Tar können Kompressionsprogramme angegeben werden
gzip, bzip2, xz  <--- programme 
 -z,   -j,   -J  <--- Optionen
 .gz, .bz2,  .xz <--- Endungen

Tar-Archiv mit gzip Komprimierung
tar -czf archiv.tar.gz Verzeichnis
tar -c Verzeichnis | gzip > archiv.tar.gz
Beide machen das gleiche

Entpacken von Tar.Archiv
tar -xzf archiv.tar.gz

Effiziensparameter -1 bs -9; default -6 bei gzip u. xz, default -9 bei bzip2
gzip kompressionsgeschwindigkeit vs kompressionsstärke
bzip2 speicherplatz vs kompressionsstärke
xz virtueller speicher wird zum komprimieren benötigt, entsprechend kann das kompressionsergebnis
unterschiedlich aussehen, Genaue Tabellen xz (1)
gzip datei datei wird durch datei.gz ersetzt
gzip -c datei > datei.gz Originaldatei bleibt erhalten
gzip -9 -c datei > datei.gz mit -9 stärke Komprimierung, langsamste Komprimierungsgeschwindigkeit

Option -r rekursiv: alle Dateien in Unterverzeichnisen werden ebenfalls (de-)komprimiert, gzip u. xz
bzip2 kennt keine Rekursivität

gzip -dc = zcat gzip -d = gunzip analog für xz, unxz und xzcat



Dateinamen: Datei wird ins Archiv getan, ausgepackt usw.
Verzeichnis: mit Dateien und Unterverzeichnissen, tar is immer explizit rekursiv



dnf (Projektmanager) stellt repositorys bzw programme in den repositorys zur verfügung



# DAY7

 ## Skripte

 Befehle:
 echo " " gibt aus was in den Klammern steht
 $#       gibt die anzahl aller eingegebenen Parameter aus
 $@       gibt alle eingegebenen Parameter aus
 $*       gibt alle eingegebenen Parameter als ein einzigen String aus

#! /usr/bin/env bash

Die . gehören nicht dazu

.# Alternative /bin/bash, allerdings im Wurzelverzeichnis
.# /Usr/bin/env bash ist portabel, Ausführen von Skripten an andere Ortenm z.B. cronjobs (Zeitgesteuerte Kommandosausführen)

.# Testen der Anzahl der Übergabeparamteter
.#Vergleichsoperatoren -lt less than, > < sind nicht mögich da I/O Operationen
.# -eq equal(gleich) entspircht ==
.# -ne not equal(ungleich) entspricht !=
.# -gt greater than(größer als) entspricht >
.# -ge greater equal(größer oder gleich) entspricht >=
.# -lt less than(kleiner als) enspricht <
.# -le less equal(kleiner oder gleich) entspricht <=

## Beispiel:

if [ $# -lt 2 ]; then 
        echo "Fehler du musst mindestens zwei Parameter angeben!"
        exit 1
fi

.# Hier ist alles ok

echo "Genug Parameter eingeben"
exit 0 # Optional: Erfolgreiche Ausführung, Rückgabestatuswert 0, das macht aber schon das echo

## Beispiel:

for i in {1..5}
do
       echo $i
done

## Beispiel:

! /usr/bin/env bash

while read LINE
do
  	echo "--$LINE--" >> datLesen$(date +%m%d-%H%M).txt
done < $1

"--$LINE--" <--- geht jede LINE/textzeile durch und kopiert sie mit -- am anfang aund -- am ende 
>>          <--- anhängend
<           <--- done < $1 das erste angegebene argument z.B. Pfad

## Beispiel:
                
#! /usr/bin/env bash

i=0
while (( i < 10 ))
do
  	i=$(( i + 1 ))
        if [ $i -eq 5 ]; then
                continue # die 5 wird nicht ausgegeben
        fi
	echo "zahl: $i"
done 




(( i=1; i<6; i++ )) Das ist arithmetischer Modus. Bash behandelt den Inhalt wie Mathematik bzw. C-ähnliche Ausdrücke.

Typisch für:
Rechnen
Vergleiche mit Zahlen
Inkrementieren (i++)
Schleifenbedingungen



[ "$name" = "Max" ] Die eckigen Klammern sind eigentlich ein Kommando namens test.

Das wird benutzt für:
Stringvergleiche
Dateitests
einfache numerische Vergleiche

Leerzeichen sind Pflicht:




Geschweifte Klammern gruppieren Befehle.
{
    echo "Hallo"
    echo "Welt"
}

mehrere Befehle zusammenfassen
Umleitungen auf mehrere Befehle anwenden

Beispiel:
| Syntax  | Bedeutung               | Typischer Einsatz              |
| ------- | ----------------------- | ------------------------------ |
| `(( ))` | Mathematik / Arithmetik | `i++`, `x+1`, Zahlenvergleiche |
| `[ ]`   | Bedingungen/Test        | `if`, Datei prüfen, Strings    |
| `{ }`   | Befehlsblock            | mehrere Befehle gruppieren     |





# DAY 8

## Regex

\(...\) definiert eine ,regex`-oder Zeichenketten-Bereich (maxmimal 9 Bereiche auch verschacchtelt)

Selektieren von Text
.	Steht für eine beliebiges Zeichen
^,$ ^Zeilenanfang, $Zeilenende
\<, \> < Wortanfang, > Wortende
[....] ein Zeichen aus der angegebenen Zeichenmenge
[^...] ein Zeichen aus der nicht angegebenen Zeichenmenge

Multiplikatoren das davor stehtende Zeichen oder der davor stehenden reguläre Ausdruck
* darf beliebig oft vorkommen auch 0-mal
+ darf beliebig oft vorkommen mindestens 1-mal
? darf 0- oder 1-mal vorkommen
{n,m} muss mindestens n-mal, maximal m-mal vorkommen
{n} muss genau n-mal vorkommen
{n,} muss mindestens n-mal vorkommen

ifconfig zeigt ein protokoll über die pakete die man empfangen und gesendet hat + fehler.
nmcli    zeigt DNS information + loopback info.
passwd	 enthält Benutzerkonten des Systems.
services enthält die Zuordnung von: Dienstnamen, Portnummern, Protokollen.
ip link zeigt die Netzwerk-Schnittstellen (Interfaces) deines Systems.

## grep:

\ muss angegeben werden als entwertungszeichen wenn man z.B. \{n\} benutzt

grep = generischer Textsucher
er sucht Zeilenweise in Texten
das „pattern“ bestimmst du selbst

👉 Ohne Muster weiß grep nichts von IP-Adressen, IPv4 oder irgendwas Netzwerk-spezifischem.

🧠 Unterschied zu normalem grep
❌ normales grep (Basic Regex)
Viele Sonderzeichen müssen escaped werden:

Beispiel:
grep '\(abc\)\{2\}'

✅ grep -E (Extended Regex)
viel einfacher zu schreiben:

Beispiel:
grep -E '(abc){2}'



## awk
erkennt automatisch mehrere Leerzeichen
ist für Spalten gedacht
stabiler als cut



Weil die UID nie:
am Anfang der Zeile
oder am Ende steht.
Sie ist immer mitten drin.
zwischen zwei : :



✅ POSIX-Charclass:
[[:space:]]
→ „ein beliebiges Leerzeichen“

# DAY9
Wiederholungen
und mehr Regex aus den Übungen 1-9

# DAY10

Vim einführung und dessen Befehle
Befehle:

## Löschen & Rückgängig machen
-dd um eine Zeile zu löschen
-x um ein Zeichen zu löschen
-ce um den rest eines wortes nach dem Cursor zu löschen
-dw um ein Wort zu löschen
-d$ um bis zum Ende der Zeile zu löschen
-u um eine eingabe rückgängig zu machen
-strg r um das undo (u) rückgängig zu machen

## Eingabe öffnen
-i um die Text eingabe am Cursor zu Starten
-I um die Text eingabe am Zeilen Anfang zu starten
-a um die Text eingabe ein Zeichen weiter zu starten
-A um die Text eingabe am Ende der Zeile zu starten

## Speichern & Verlassen
-w zum speichern
-q zum verlassen
-wq zum speichern und verlassen

## Bewegen
-d bewegen w bis zum nächsten wort e zum Ende des Aktuellen Wortes $ zum Ende der Zeile MIT dem letzten Zeichen 
-2w um den Cursor zwei wörter vorwärts zu bewegen
-3e um dne Cursor zum Ende des dritten Wortes zu bewegen
-0 um zum Anfang der Zeile zu gelangen
-G um sich zum Ender der Datei zu begeben
-gg um sich zum Anfang der Datei zu begeben

## Kopieren/Markieren & Ersetzen
-p um etwas das mit dd z.B. gelöscht oder mit v markiert wurde wo anders hin zu kopieren
-r um ein Zeichen zu ersetzen
-R um mehrere Zeichen zu ersetzen
-:s/AltesWort/NeuesWort/g um ein Altes Wort durch ein neues Wort in einer Zeile zu ersetzen 
	!!Ersetzt alle vorkommen vom Alten Wort in der Zeile!!
-v um einen Text zu Markieren
-:w TEST um die aktuelle Datei zu testen

## Suchen
-/Wort um nach "Wort" zu suchen
	Tippe n um nach der nächsten vorkommen des "Wort" zu gehen Tippe N um zum vorherigen vorkommen des "Wort" zu gehen
-% um die gegenüberliegende Klammer zu finden { (  [ ] ) }

## Zeilen Einfügen
-o um eine Zeile unterhalb einzufügen
-O um eine Zeile oberhalb einzufügen

## Ignore/Hilfe
-set ic ignoriert groß und kleinschreibung bei der suche
-set hls is highlights die gesuchte Zeichenkette
-F1/Hilfetaste oder :Help um eine Fenster zu öffnen für den jeweiligen Befehl

# Ausführen eines Externen Kommandos
-:! Kommando um ein Externes Kommando auszuführen

# DAY11
Vimtutor
Vim-Editor

# DAY12

systemctl status DIENST zeigt den Status eines Dienstes ob er an aus ist und restliche Infos

jeder User hat seine eigen crontab und kann diese temporär in der Shell öffnen

in der crontab immer absolute Pfade angeben!

## crontab

 * Min(0-59) * Stunden(0-23) * Tag(1-31) * Monat(1-12) * Wochentag(0-7)

 45 9 * * * echo "In 5 Minuten ist Pause" > /dev/pts/0

cron erkennt das die * für werte stehen wie Minuten Stunden Tage usw


## comm

~/.bash_history weil einfach history in crontab nicht funktioniert

comm vergleicht zwei sortierte Dateien/Streams Zeile für Zeile.

comm [OPTIONEN] datei1 datei2

Beispiel:
comm -13 <(sort Daily-History) <(sort ~/.bash_history)

Bedeutung von -13

Die Zahlen stehen für die 3 Spalten.

-1 → verstecke Spalte 1
-2 → verstecke Spalte 2
-3 → verstecke Spalte 3

Also bedeutet -13
verstecke:
alles nur aus Datei1
alles was in beiden vorkommt

➡️ übrig bleibt nur Spalte 2

AKA:

Zeilen die nur in ~/.bash_history vorkommen
also neue Befehle.

## Was sind <(...) temporäre Streams?

Das nennt sich:

Process Substitution
<(COMMAND)

Bash tut so, als wäre die Ausgabe eines Befehls eine Datei.

## Warum braucht man /bin/bash -c oft bei cron?

Cron führt Befehle nicht immer mit Bash aus.

Oft benutzt cron:

/bin/sh

Aber Features wie:

<(...)
Arrays
bestimmte Bash-Syntax

funktionieren nur in Bash.

-i
startet Bash interaktiv

## History DAY12

| Thema                                    | Erklärung                                    | Beispiel                              |
| ---------------------------------------- | -------------------------------------------- | ------------------------------------- |
| `history`                                | Zeigt RAM-History der aktuellen Shell        | `history`                             |
| `~/.bash_history`                        | Gespeicherte History-Datei auf Disk          | `cat ~/.bash_history`                 |
| Unterschied `history` vs `.bash_history` | `history` enthält oft neuere Befehle         | neue Commands erst später gespeichert |
| `history -a`                             | Schreibt neue RAM-History in `.bash_history` | `history -a`                          |
| Cron Syntax                              | Zeitpunkt für automatische Jobs              | `50 15 * * *`                         |
| `/bin/bash -c`                           | Führt String als Bash-Code aus               | `/bin/bash -c 'echo hi'`              |
| `-i`                                     | Startet Bash interaktiv                      | `/bin/bash -i`                        |
| `sort`                                   | Sortiert Zeilen alphabetisch                 | `sort file.txt`                       |
| `comm`                                   | Vergleicht 2 sortierte Inputs                | `comm A B`                            |
| `comm -13`                               | Zeigt nur Zeilen aus Datei2                  | neue Commands finden                  |
| Process Substitution                     | Befehlsausgabe wie Datei nutzen              | `<(sort file)`                        |
| `-` bei `comm`                           | stdin als Datei verwenden                    | `comm A -`                            |
| `sed`                                    | Text verändern/filtern                       | `sed "s/^ *[0-9]\+ *//"`              |
| Entfernen von History-Nummern            | Löscht führende Zahlen aus `history`         | `history \| sed ...`                  |
| `&&`                                     | Zweiten Befehl nur bei Erfolg ausführen      | `A && B`                              |
| `;`                                      | Befehle nacheinander ausführen               | `A ; B`                               |
| `( ... )`                                | Gruppiert Befehle/Subshell                   | `(echo hi; date)`                     |
| `>>`                                     | An Datei anhängen                            | `echo hi >> file`                     |
| `>`                                      | Datei überschreiben                          | `echo hi > file`                      |
| `date`                                   | Datum/Uhrzeit ausgeben                       | `date "+%Y-%m-%d"`                    |
| `\%` in cron                             | `%` muss escaped werden                      | `+\%Y-\%m-\%d`                        |
| stdin                                    | Eingabe aus Pipe                             | `command -`                           |
| Pipe `\|`                                | Ausgabe an nächsten Befehl senden            | `cat a \| sort`                       |
| Warum cron-Probleme hatte                | cron hat keine interaktive Shell-History     | `history` oft leer                    |
| Finale Lösung                            | Nur neue Commands speichern + Zeitstempel    | dein funktionierender Cronjob         |

/etc/skel

# DAY13

- -z $line: -z überprüft ob etwas leer ist und springt weiter also hier überprüft er die nächste line
-[[ ]]: prüft ob etwas wahr oder falsch ist
-p: in der Commandline sagt gib keine Fehler Meldung aus
-sudo usermod -aG wheel USER: Setzt die Gruppe des benutzers
-id USER: Zeigt in welcher gruppe der User sich befindet
-USERadd-m: Legt user mit home-verzeichnis an
-passwd -S USER: Statusinformatinen für User passwort
    1.Username: LK locked, NP no password, PS passwort vorhanden
    2.PW-Status: Passwort-Status eines Users
    3.Letzte Änderung:
    4.Min days: Tage wann wieder eine Passwort änderung möglich ist
    5.Max days: Tage wie lange eine Passwort änderung gültig ist
    6.Warning: Days Anzahl der Tage vor Ablauf des passworts gewarnt wird default+:7 
    7.Inactive: Days Tage zu änderung des Passworts, danach ist Konto gesperrt
-getent shadow USER: zeigt die Gehashten passwörter eines oder aller user aus der /etc/shadow
-sudo getent passwd USER: zeigt die Gehashten passwörter eines oder aller user aus der /etc/passwd
-sudo userdel -r USER: Löscht einen Benutzer vom System
-sudo chage -l USER: zeigt das gleiche wie passwd -S USER
-sudo chage --mindays ZAHL --maxdays ZAHL: ändert die Werte der angegeben Status einheiten


# DAY 14 - Fortführung des Benutzerverwaltung Projektes
-
-
-
-

# DAY 15
## VM-Installation mehrere VMs
-
-
-
-

# DAY 16

## Networking

-ip a: zeigt alle Netzwerkinterfaces und deren IP-Adressen an
-ip r: zeigt die Routing-Tabelle des Systems an
-sudo sysctl -w net.ipv4.ip_forward=1: aktiviert IPv4-Forwarding temporär bis zum nächsten Neustart
-sudo cat /etc/resolv.conf: zeigt die aktuell verwendeten DNS-Server und Resolver-Einstellungen an
-sudo cat /etc/cpuinfo: zeigt detaillierte Informationen zur CPU an (Modell, Kerne, Taktfrequenz usw.)
-lscpu: zeigt CPU-Informationen in kompakter und übersichtlicher Form an; nutzt ebenfalls Daten aus /etc/cpuinfo
-nmtui: textbasierte Benutzeroberfläche zur Verwaltung von Netzwerkverbindungen über den NetworkManager
-nmcli: Kommandozeilenwerkzeug des NetworkManager zum Verwalten von Netzwerkverbindungen, Geräten und Einstellungen
-sysctl:

-nmcli connection modfiy [router] ipv4.gateway [IP]
		ifdown/down: schaltet angegebene verbindung aus
		ifup/ip: schaltet angegebene verbindung ein
		ipv4.method manual: [???]

# DAY 17

## iptables

-Port Forwarding
Technik, User von außerhalb greitft auf einen Dienst in einem privaten Netzwerk zu, normalerweise von außen nicht erreichbar

-iptables
Möglichketi einen Diesnt im privaten Netzwerk öffentlich zugänglich zu machen z.B Web Server, Game Server usw.
- Tool zum Einrichten von Port Forwarding
- IP-Paketfilerregeln der Linux Kernel Firewall weden konfiguriert
als verschiedene Netzfilermodule
- Organisation in verschiedenen Tabellen

-Step1: sudo iptables -L -v -n
Überprüfen der gesetzten Regeln -L Listet die Regeln, -v verbose stellt mehr infos zur Verfügung, -n listet IP-Adressen u. Portnummern im numerischen Format
-Step2: sudo nano /etc/sysctl.conf
Um Weiterleitung auf Kernel Ebene zu erlauben muss IP-Weiterleiung (Forwarding) eingeschaltet werden Diese Zeile muss in der Konfigurationsdatei stehen
net.ipv4.ip_forward=1
-Step3: sudo sysctl -p
-Step4: sudo iptables -t nat -A PREROUTING -p tcp --dport 8080 -j DNAT  --to-destinat IP-Adr:80
8080 wird duch die Portnummer über die der Netzwerkverkehr läuft, ersetzt durch IP-Adr. ist die Adresse auf die sie den Verkehr weiterleiten wollen 80 die Portnummer des Zielrechners
-Step5: sudo iptables -t nat -A POSROUTING -J MASQUERADE
Maskiert die IP-Adresse der ankommenden Pakete mit der IP-Adresse der ausgehenden Netzwerkschnittstellen
-Step6: sudo apt install iptables-persistent [Ubuntu] sudo services iptables [RHEL, Fedora]
Speichern der Regeln, dauerhaft in /etc/sysconfig/iptables
-Step7: Verifizieren der Konfigurationen: verbinden mit dem Quellport von einem anderen Rechner Tools: nc, telnet, curl

- filter
- nat
- mangle
- raw
- security

93-101 Zeitverwaltung + Chrony 


sysctl -w net.ipv4.ip_forward=1 []
sudo iptables -t nat -A POSTROUTING -o ens160 -j MASQUERADE []
sudo iptables -t nat -L -v -n []

makestep
rtcsync
stratum 1
stratum 2
stratum 0

stratum 10
local stratum
sudo ss -tulpn | grep chronyd [Zeigt den Socket an?] oder angegegeben diesnt an?]
sudo cat /etc/services | grep ' 123/udp'

sudo hwclock [zeigt die akutuellen zeit und datums daten des systems]
sudo date 020318012009.30 [ändert diese daten und gibt nach dem . eine zeigt angabe in sekunden an]
sudo chronyc [c steht für config hier]
sudo chronyd [d steht für daemon hier]
sudo chronyc/d makestep [aktuallisiert die akutellen Zeiteinstellungen]
cat /etc/chrony.conf | less [zeigt eine auswahl an Zeitservern]

lsblk aktive Blockdevice
	fdisk -l

lsmod zeigt geladene Module

lscpu gibt informationen zur CPU aus
	/proc/cpuinfo

lsusb  gibt informationen zu aktiven usb devices

lspci Speed: Device Geschwindigkeit IRQ Number (Interrupt Request) Vendor: Hersteller des Devices [LPIC 3 FRAGEN!!!]
	lspci -v

lsof list open files, zeigt eine liste Geöffneter Dateiene an TCP/IP Socket Verbindung
	lsof -i
df Anzeige Partiotionsbelegung, nur aktive Partitionen
	/etc/fstab File System Tabelle

mount eigenhändig von Partitionen, File Systemen
	  -- bind für eigenhängte Geräte

unmount aushängen von Partitionen, File Systemen

/proc/self/mounts aktuell 
/proc/mounts gemountete FS
/etc/mtab dito

cat/proc/swaps Auslagerungsspeicher
swapon/swapoff ein- und auschalten von Swapspace

# DAY x1

## IT-Security
