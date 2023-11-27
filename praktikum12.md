# 12.praktikumi aruanne

## Ülesanne 3
### Skripti sisu
```
#!/bin/sh -x

echo "Sisesta oma nimi:"
read nimi

echo "Sisesta oma eriala:"
read eriala

echo "Sisesta oma matriklinumber:"
read matriklinumber

echo "Nimi: $nimi, eriala: $eriala, matriklinumber: $matriklinumber"
```
### Skripti käsurea väljund
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/540b0d4b-d76b-4deb-9536-1579493800e6)

## Ülesanne 4
### Skripti sisu
```
#!/bin/bash
IFS=$'\n'

echo "Sisestage faililaiend, mida soovite muuta:"
read laiend1

echo "Sisestage faililaiend, milleks soovite muuta:"
read laiend2

valjund=$(ls)

for fail in $valjund
do
    if [ .${fail##*.} = $laiend1 ]
    then
        echo $fail
        mv $fail ${fail/$laiend1/$laiend2}
    fi
done
```
### Skripti käsurea väljund
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/1c5eea18-b4d8-47a1-b52b-286feaf2cd4f)

## Ülesanne 3

## Ülesanne 4
