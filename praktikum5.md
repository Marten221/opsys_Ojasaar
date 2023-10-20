# 5. praktikumi aruanne

## Ülesanne 5-1
a) Kataloogis /tmp/kaust oleva faili minufail.txt lugemiseks on minimaalselt vaja kaustal r-x ning failil r-- õiguseid.

b) Kataloogis /tmp/kaust oleva faili minufail.txt kustutamiseks on minimaalselt vaja kaustal -wx ning failil -w- õiguseid.

## Ülesanne 5-2
Selleks, et shellis ilma interpretaatorita skripti käivitada, peab antud skriptifailil olema nii käivitamise, kui ka lugemise õigused. Peale faili loomist on failil kirjutamise ja lugemise õigused. Käsk "chmod a+x Kaust3/skript.sh" lisab kõikidele kasutajatele käivitamise õiguse, ehk peale seda saab skripti ilma interpretaatorita kasutada. Käsuga "chmod a=x Kaust3/skript.sh" me muudame skripti kõigile vaid käivitatavaks. Nüüd puudub meil skripti jaoks lugemisõigus ja enam ei saagi seda ilma interpretaatorita käivitada.

## Ülesanne 5-3
Igal kasutajal on omanimeline grupp, et vaikimisi määrata antud kasutaja õigused mingi faili või kausta jaoks.

## Ülesanne 5-4
![ülesanne5-4](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/a1b44b06-8b70-489f-b573-9b29682edc07)


## Ülesanne 5-5
Setuid on siin vajalik, et skript saaks hinded.txt failile pääseda ligi kui omanik, tänu millele saab ta sealt edukalt infot lugeda.
![ülesanne5-5](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/4dd43d7d-bf5a-4101-802f-9aadf738e6dc)


## Ülesanne 5-6
Jah, setuid võib vähendada süsteemi turvalisust. Selle abil võivad pahatahtlikud programmid või isikud saada tähtsatele failidele omanikuna ligi pääseda.


## Ülesanne 5-7
peeter, root, admin kasutaja kasutades sudo

## Ülesanne 5-8
Märkasin, et peale tavakasutaja õiguseid oli "+", Googeldasin mida see tähendab ning sain vastuseks, et see "+" viitab faili lisaseadete või attribuutide olemasolule, ehk antud faili on seadistatud täiendatavate atribuutidega.
\# file: hinded.txt  
\# owner: opetaja  
\# group: opetaja  
user::rw-  
group::---  
group:direktor:rw-  
mask::rw-  
other::---  

## Ülesanne 5-9
Mitte keegi ei saa chattr +i parameetriga faili sisu modifitseerida seni kuni see atribuut on seadistatud.

testfail-2 kustutamiseks tuleb essmalt sellelt i(immutable) atribuut eemaldada käsklusega: sudo chattr -i testfail-2 . Peale seda saab faili juba vanaviisi kustutada käsklusega rm testfail-2 .
