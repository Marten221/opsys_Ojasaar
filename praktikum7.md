# 7. praktikumi aruanne

## Ülesanne 1: Miks andmekandjad vajavad lähtestamist?
Failisüsteemi valik: Andmekandjat tuleb initsialiseerida selleks, et valida sobiv failisüsteem. Failisüsteem määrab, kuidas andmed kandjal salvestatakse ja kuidas neile juurdepääsu saab. Windowsi jaoks kasutatakse tavaliselt NTFS-failisüsteemi, mis toetab suuri faile ja paremat turvalisust. Kui ketas pole initsialiseeritud, ei saa valikut teha.

Partitsioneerimine: Lähtestamise ajal saab valida, kuidas kandja partitsioneeritakse, s.t kuidas ruum jagatakse erinevate draivide vahel. See on oluline, kui soovite luua mitu draivi ühele füüsilisele andmekandjale.

Ühilduvus: Uued andmekandjad võivad olla vaikimisi initsialiseerimata, et tagada nende ühilduvus erinevate süsteemidega, nagu Windows, Linux või Mac. Lähtestamise valikud võimaldavad valida sobiva vormingu.  

## Ülesanne 2: Millised on GPT kasutamise eelised võrreldes MBRiga?
GPT on töökindlam ja võimaldab kasutada andmekandjaid suuremad kui 2TB. MBR suudab hallata kettaid, mille suurus on kuni 2 terabaiti (TB), samas kui GPT võimaldab partitsioneerida kettaid, mis on palju suuremad, 2 terabaidist kuni zettabaitideni. See on eriti oluline tänapäeva suurte andmekandjate ja serverite puhul.

GPT-d saavad kasutada mitmeid erinevad operatsioonisüsteemid, näiteks Linux, MacOS ja Windows.

GPT pakub paremat andmekaitset ja andmete taastamisvõimalusi.

GPT toetab suuremat partitsioonide arvu võrreldes MBR-iga. MBR piirdub tavaliselt nelja primaarse partitsiooniga või kolme primaarse partitsiooniga ja ühe laiendatud partitsiooniga, mis võib sisaldada mitmeid loogilisi partitsioone. GPT võimaldab kasutada kuni 128 partitsiooni.

