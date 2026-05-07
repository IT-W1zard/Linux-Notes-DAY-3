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


