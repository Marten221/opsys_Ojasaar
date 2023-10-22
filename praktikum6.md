# 6. praktikumi aruanne
See praktikum läks palju libedamalt kui eelmine. Päris tore oli erinevatest käsklustest torude abil teha kompleksemaid käske. Juhend oli ka hästi koostatud. Oli meeldiv.

## 6-1
![Kuvatõmmis 2023-10-23 013400](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/ff81d0a3-d71b-4125-a0a3-ca9305d45ee5)

## 6-2
![ülesanne 2](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/b321addd-d0b9-4a1b-b90d-e113b25f99a1)

## 6-3
ps -axu | grep daemon | sort | tr -s " " | cut -d" " -f11-
![ülesanne 3](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/20c3c7b8-efe4-4692-9896-fd39e6736b09)

## 6-4
ip a | sort | tr -s " " | cut -d" " -f3 | tail -n+3 | head -1 | cut -d"/" -f1
ip a | sort | tr -s " " | cut -d" " -f3 | tail -n+3 | head -1 | cut -d"/" -f1 > ipaddress.txt

![ülesanne 4](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/22169144-9899-4b57-bfb8-c9d75953214c)
