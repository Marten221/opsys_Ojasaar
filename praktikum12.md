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

## Ülesanne 5
### Skripti sisu
```
#!/bin/bash
IFS=$'\n'

echo "Sisesta protsessi nimi:"
read nimi

pid=$(ps -A | grep bash | tr -s ' ' | cut -d ' ' -f2)
echo "Protsessi-ID: $pid"
echo "Protsessi nimi: $nimi"
```
### Skripti käsurea väljund
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/675db3c0-1eb1-4d5b-99ee-5444e7a5fb6a)

## Ülesanne 6
### Skripti sisu
```
#!/bin/bash
a=9
b=9
astendamine () {
    b=$(($b * $a ))
    echo $b
}


for i in {1..4}
do
    b=$(astendamine $b $a)
done

echo $b
```
### Skripti käsurea väljund
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/c184e052-3f5a-4587-a1d7-10095247a404)

## Ülesanne 7
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/05c93852-dc59-45bb-8b0d-cb6e17440922)
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/f49b553c-b9df-4524-b4a1-3d1ba880c010)

