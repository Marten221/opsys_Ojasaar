# 7. praktikumi aruanne

## Ülesanne 1: Miks andmekandjad vajavad lähtestamist?
Failisüsteemi valik: Andmekandjat tuleb initsialiseerida selleks, et valida sobiv failisüsteem. Failisüsteem määrab, kuidas andmed kandjal salvestatakse ja kuidas neile juurdepääsu saab. Windowsi jaoks kasutatakse tavaliselt NTFS-failisüsteemi, mis toetab suuri faile ja paremat turvalisust. Kui ketas pole initsialiseeritud, ei saa valikut teha.

Partitsioneerimine: Lähtestamise ajal saab valida, kuidas kandja partitsioneeritakse, s.t kuidas ruum jagatakse erinevate draivide vahel. See on oluline, kui soovite luua mitu draivi ühele füüsilisele andmekandjale.

Ühilduvus: Uued andmekandjad võivad olla vaikimisi initsialiseerimata, et tagada nende ühilduvus erinevate süsteemidega, nagu Windows, Linux või Mac. Lähtestamise valikud võimaldavad valida sobiva vormingu.  

## Ülesanne 2: Millised on GPT kasutamise eelised võrreldes MBRiga?
GPT on töökindlam ja võimaldab kasutada andmekandjaid suuremad kui 2TB. MBR suudab hallata kettaid, mille suurus on kuni 2 terabaiti (TB), samas kui GPT võimaldab partitsioneerida kettaid, mis on palju suuremad, 2 terabaidist kuni zettabaitideni. See on eriti oluline tänapäeva suurte andmekandjate ja serverite puhul.

GPT-ga saab kasutada mitmeid erinevad operatsioonisüsteeme, näiteks Linux, MacOS ja Windows.

GPT pakub paremat andmekaitset ja andmete taastamisvõimalusi.

GPT toetab suuremat partitsioonide arvu võrreldes MBR-iga. MBR piirdub tavaliselt nelja primaarse partitsiooniga või kolme primaarse partitsiooniga ja ühe laiendatud partitsiooniga, mis võib sisaldada mitmeid loogilisi partitsioone. GPT võimaldab kasutada kuni 128 partitsiooni.

## Ülesanne 3
https://kodu.ut.ee/~martenoj/hdd.png 

## Ülesanne 4
![Kuvatõmmis 2023-10-23 131509](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/539f01ca-9b3d-4cc3-8e48-628f4c7ee1fc)

## Ülesanne 5: Mida mõjutasid mount-käsu parameetrid -o ro ja -t auto?
-o ro: See parameeter tähistab "read-only" ehk lugemisrežiimi. Kui see parameeter on antud, monteeritakse kettaseade nii, et sellele ei saa kirjutada ega muuta andmeid.

## Ülesanne 6


## Ülesanne 7
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/19f0f98b-821a-4040-8df8-7efe920a6387)


