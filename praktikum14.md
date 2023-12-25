# 14.praktikumi aruanne

## Ülesanne 1 & 2
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/3f4fc8a3-a335-4885-a8e7-fb6b218d3d24)


## Ülesanne 3
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/43a27c3f-0abb-4e0c-8d40-3007fdfc58b1)

## Ülesanne 4
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/3e1e2266-2401-43c7-a106-4537b271c92b)

## Ülesanne 5
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/88617524-6cc7-4d4c-811a-553742bd53aa)

## Ülesanne 6
![image](https://github.com/Marten221/opsys_Ojasaar/assets/144438767/4e337161-5517-4d94-8810-177e996c256e)

```
kausta_tee="accident"

if [ -d "$kausta_tee" ]; then
  cd "$kausta_tee"

  for fail in *.md; do
    if [ -f "$fail" ] && [ -s "$fail" ]; then
      echo "Fail, mis sisaldab parooli: $fail"
      cat "$fail"
      echo -e "\n-----------------\n"
    fi
  done

  cd -
else
  echo "Viga: Kausta pole olemas - $kausta_tee"
fi
```
