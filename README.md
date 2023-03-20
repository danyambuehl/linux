Linux Basic Commends
====

# Übersicht Text Editor 
Das Ziel ist eine Übersicht über einige Grundsätzliche Linux Befehle zu bekommen. 

| Behfehl | Beschreibung |
| ---     | ---   |
| `vi`| Editing Text Files |
| `cat`| Disblay Text File |
| `wc <filename>`| Countsing Words in a File     |
| `1.Spalte > Nr. of Lines`| `2.Spalte > Nr. of Words` |
| `3.Spalte > Nr. of bytes` | `4.Spalte > File Name` |
| `wc <filename>`| Countsing Words in a File     |

## Filesystem                                                                       
| Behfehl        | Beschreibung |
| ---            | ---          |
| `cp [source_file] [destination_file]`| File Koppieren |
| `mv [old_file] [new_file]`           | Umbennenen oder Verschieben |
| `rm [filename]`           | File Löschen |
| `pwd`           | Zeigt dein akutelles Verzeichniss |
| `mkdir [Ordnername]`| Verzeichniss erstellen |
| `rmdir [Ordnername]`           | Verzeichniss Löschen |
| `rm -rf [Ordnername]`           | Verzeichniss mit Inhalt Löschen -> = ohne bestätigung|
| `ll`           | Aktuelles Verzeichniss Liste anzeigen inkl. Berrechtigungen |
| `finde -name [Filename] `   | Sucht nach dem entsprechenden File |
| `$ grep "81.143.211.90" access.log ` | Sucht nach der IP Adresse im angegebenen File |
| `echo hey > welcome` | Erstellt ein File welcome mit dem inhalt hey und überschreibt den alten Inhalt |
| `echo hey >> welcome` | Erstellt ein File welcome mit dem inhalt hey und fügt diesen am ende hinzu |


## Berrechtigungen                                                                       
| Behfehl        | Beschreibung |
| ---            | ---          |
| `chmod o+wx [file]`           | Berrechtigungen hinzufügen |
| `<-> <rwx> <rwx> <r-->  1 amrood   users 1024  Nov 2 00:10  testfile`           | Sets |
| `<Type><owner><group><others><Hardlinks><Groupowner><userowner><Grösse><Änderung>`           | Beschreibung |
| `u`           | Users Owner |
| `g`           | Group |
| `o`           | others |
| `s` or `S`    | SUID and SGID bits wihout or with Execute Rights |
| `t` or `T`    | Sticky bit wihout or with Execute Rights |
| `+`           | Addes |
| `-`           | Removes |
| `=`           | Sets |
| `chmod 775 [file]`           | Berrechtigungen hinzufügen Octal |
| `1`           | Execute |
| `2`           | Write |
| `4`           | Read |
| `4`           | Read |
| `1000`           | Sticky Bit |
| `2000`           | SGID |
| `4000`           | SUID |
| `chown [user] [file]`           | File Owner Ändern  |
| `chgrp [group] [file]`          | File Group Owner Ändern |
| `Set User ID (SUID)`          | File wird mit den File Owner Rechten Ausgeführt |
| `-r-sr-xr-x  1   root   bin  19031 Feb 7 13:47  /usr/bin/passwd*`          | Beispiel SUID |
| `Set Group ID (SGID)`          | Files werden mit den Gorup Owner Rechten Ausgeführt |
| `-r-xr-Sr-x  1   root   bin  19031 Feb 7 13:47  /usr/bin/passwd*`          | Beispiel SGID |
| `s` | Nur SUID oder SGID gesetzt ohne Execute Berrechtigungen |
| `S` | SUID oder SGID gesetzt und Execute Berrechtigungen |
| `Sticky Bit` | If there is a Sticky Bit aktivated just owner and root can delete  |
| `-r-xr-xr-T  1   root   bin  19031 Feb 7 13:47  /usr/bin/passwd*`          | Beispiel Sticky |
| `t` | Nur SUID oder SGID gesetzt ohne Execute Berrechtigungen |
| `T` | SUID oder SGID gesetzt und Execute Berrechtigungen |

## SCP                                                                     
| Behfehl        | Beschreibung |
| ---            | ---          |
| `scp user1@10.10.5.6:Message.txt .`| File Koppieren nach Remote Computer über SSH |
| `scp Message.txt user1@10.10.5.6:`| Andere Variante zum koppieren eines Files nach Remote Computer über SSH |
| `scp -r user1@10.10.5.6:roles /tmp`| Koppiert Verzeichniss "roles" von Remote Computer zu /tmp auf lokalem Computer  |

## Befehl auf Remote Maschine ausfürhen                                                                     
| Behfehl        | Beschreibung |
| ---            | ---          |
| `ssh user2@10.10.5.5 ls -al`| Verbindet über ssh mit user2 und führt "ls -al" aus |
| `ssh user2@10.10.5.6 "echo "Ich bin gut" >> README"`| Erstellt ein File mit Inhalt auf der Remote Maschine |

# Modi von VI Editor

| Behfehl | Beschreibung |
| ---     | ---   |
| `i`| Insert Mode |
| `v`| Visual Mode |
| `ESC`| Command Mode    |
| `Shift + ZZ`| Speichern und schliessen Shortcut    |

![CloudShow](images/vieditor.jpg)

## Befehle Command Mode in VI Editor
| Behfehl        | Beschreibung |
| ---            | ---          |
| `:w[Dateiname]`| Speichert Datei |
| `:q`           | Editor verlassen |
| `:q!`          | Editor verlassen ohne Speichern |
| `:x`           | entspricht :wq |
| `:u`           | nimmt anzahl x rückgängig  Befehl|
| `:set number`  | Zeigt Zeilen Nummer an|
| `[Anzahl]dd`   | löscht die aktuelle Zeile |
| `x`            | löscht aktuelle Zeichen |
| `p`  | Zeile einfügen vor Curser|
| `P`  | Zeile einfügen nach Cruser|

## Navigieren Command Mode in VI Editor
| Behfehl        | Beschreibung |
| ---            | ---          |
| `:set number`  | Zeigt Zeilen Nummer an|
| `:[ZeilenNr]`  | Springt in entsprechende Zeilen Nummer|
| `:G`  | Springt in letzte Zeile|
| `:0`  | Springt zum anfang der Zeile|
| `/[Zeichen]`   | Sucht vorwärts nach Zeichen |
| `n`   | zur nächste Fundstelle |
| `N`   | zur vorherigen Fundstelle |
| `?[Zeichen]`   | Sucht rückwärts nach Zeichen|

## Befehle Visual Mode in VI Editor
| Behfehl        | Beschreibung |
| ---            | ---          |
| `Markiere die Zeile`  | Zeile Marikieren mit Curser |
| `Y`| Koppieren (Yank) |
| `D`  | Delete |

## Starteinstellungen für VI Editor definieren
| Behfehl        | Beschreibung |
| ---            | ---          |
| `vi .vimrc`  | Erstelle das File .vimrc im Homeverzeichniss|
| `set nocp`  | Trage diese Zeile um ?|
| `set number`  | Trage diese Zeile ein um die Zeilennummer anzuzeigen|
| `set ignorecase`  | Trage diese Zeile ein um in der Suche Case Sensitice auszuschalten|

---

> [⇧ **Zurück zur Basic Seite**](/basic/README.md)

---
