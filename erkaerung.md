if ls ;then 
echo ja;
else echo nein
Fi 

echo $?

# letzter exit code
# ls Output wird geprüft fallskorrekt (exit0) dan wirds true sein. 

[ test = test ] 
echo $?
Fehlercode:0 = true 

------------------------------
[ 1 -ne 0 ]  -> 1 -not equel 0
echo $?
fehlercode 127 

-----------------------------
https://linuxhint.com/compare-numbers-bash/

man test -> Beschreib die Hilfe
-d File exist and is a directory 
-f True if file exists and is a regular file
-x File exists and is executible 
! Existiert nicht / Negation

---------------------------

[ -f /etc/hosts ]

Wenn file vorhanden dann 
if [ -f /etc/hosts ]; then cat /etc/hosts;fi

Wenn nicht vorhanden dann 
if [ ! -f /etc/hosts ]; then cat /etc/hosts;fi

if ! [ a = b ] ; then echo whaaat; fi 

Oder und and 
-o = oder -a = and 
[ a = b or b = c and a = b ]
if ! [ a = b -o b = c -a a = b ] ; then echo whaaat; fi 

Wenn LS nicht OK dann 
if ! ls ; then echo nicht gut; fi 

Wenn LS nicht OK dann
if ! ls /gohome ; then echo nicht gut; fi

------------------------------

Variablen vergleichen wie folgt

[ "$a" = "$b"]


--------------------
# Loops For 
Zweiters Wort wird immer eine Variable 

for variable in liste word2 word3 ; do echo $variable; done 


Sucht in allen files im /etc die mit h beginnen nach dem localhost 
for variable in /etc/h* ; do grep localhost $variable; done 

Wiedergibt die liste {1-20} einmal jede zahl aus als echo 
for i in {1..20} ; do echo $i; done

Zeigt auf das file und wiederholt jedes wort im test.txt
for i in $(cat /etc/test.txt) ; do echo $i ;done

--------------------------
# While Loop

while 1 = 0 ; do echo text ; done 

while ! [ 1 = 0 ] ; do echo text ; done

count=10
while [ $count -ne 0 ] ; 
do newcount=$(($count -1)) 
if [ -f test.log.$newcount ] ; then
mv test.log.$newcount test.log.$count 
fi 
count=$newcount 
mv test.log test.log.0
done

-------------------
# Read
Nimmt mvlist als input für read und setzt diese in die variablen ein. 

#!/bin/bash

while read var_d1 var_d2
do
        echo "dany1=var_d1"
        echo "dany2=var_d2"
done < mvlist

----------------------

# Read
Wechselt den Delilimineter definieren auf ; 

#!/bin/bash

while IFS=";" read var_d1 var_d2
do
        echo "dany1=var_d1"
        echo "dany2=var_d2"
done < mvlist

---------
enc = zeigt alle umgebungsvariablen an 
