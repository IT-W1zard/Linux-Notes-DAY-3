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
 -d delimiter z.B. der Doppelpunkt
 -f einzelne Felder
 -s separator, Verhindert die Ausgabe von Feldern ohne Trennzeichen

 cut -d: -f1,5 /etc/passwd
