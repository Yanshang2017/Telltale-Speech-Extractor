MP3FileUtils Demo-Programme
--------------------------------------------

Falls immer nur "?" und "K�stchen" angezeigt werden, m�ssen unter Windows die 
entsprechenden Schriften nachinstalliert werden:

Systemsteuerung 
   -> Datums- ,Zeit-, Sprach- und Regionaleinstellungen
      -> Regions- und Sprachoptionen
         -> Reiter Sprachen: Beide H�kchen bei "Zus�tzliche Sprachunterst�tzung" setzen

--------------------------------------------

Im Programmverzeichnis m�ssen die Dateien "demo_Ansi.mp3" und "demo_Unicode.mp3" liegen. 
  - bei demo_Ansi wurde der ID3v2Tag per HexEditor zusammengefriemelt
  - bei demo_Unicode wurde der ID3v2Tag mit Hilfe von M3FileUtils beschrieben 
    (mit dieser Demo ist aber nur lesen m�glich)

--------------------------------------------


Hinweise f�r Programmierer:
--------------------------
Ein derartig chaotisch getaggtes File wird es kaum in freier Wildbahn geben. In der Regel 
kommt pro Datei nur ein Zeichensatz vor. Dieser kann in gewissen Grenzen mit der Funktion
GetCodePage ermittelt werden.
Diese Demo zeigt hoffentlich, dass das unm�glich ist, wenn man nicht gewisse Zusatzinfos liefert,
da unterschiedliche Zeichens�tze inkompatibel zueinander sind.

GetCodePage untersucht den Dateinamen und erkennt dabei Arabische, Chinesische, etc. Schriftzeichen.
Von welcher Schrift am meisten vorkommt, liefert z.b. die Erkenntnis "Ah...ein mp3-File aus Japan".
Nun gibt es verschiedene Zeichens�tze f�r japanisch. Welcher dann zur�ckgeliefert werden soll, bestimmt
die Variable "Options" vom Typ "TConvertOptions", in der f�r jeden Sprachraum der gew�nschte
Zeichensatz eingestellt werden kann.

Bei der Datei "demo_Ansi.mp3" bringt die Funktion GetCodePage gar nichts, weil 
1. Im Namen nur "normale Buchstaben" vorkommen und
2. in der Datei bekloppterweise mehrere Zeichens�tze vorkommen

Bei der Datei "demo_Unicode.mp3" bringt die Funktion GetCodePage auch nichts, weil 
1. Im Namen nur "normale Buchstaben" vorkommen und
2. in der Datei beim Taggen Unicode verwendet wurde

Hinweis: Damit keine Verwirrung entsteht,warum man so einen Unsinn �berhaupt zul�sst:
         Eigentlich sollte das auch nicht so sein. Eigentlich sollte in einem ID3v2-Tag
         nur ein Zeichensatz verwendet werden: ISO-8859-1 (Westeurop�isch). F�r Zeichen,
         die dort nicht drin vorkommen, ist Unicode vorgesehen.
         Daran wird sich aber leider l�ngst nicht immer gehalten.

--------------------------------------------

Ben�tigte Zusatz-Komponenten/Units
(nur f�r Delphi 2007 oder fr�her)

- TntWare Delphi Unicode Controls 
      Download unter: http://www.tntware.com/delphicontrols/unicode/

