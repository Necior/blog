---
layout: post
title: Konwersja kodowania z Windows-1250 na UTF-8 w Linuksie
tags: tech
---

Jeśli masz ściągnięte polskie napisy do filmu to dosyć często nie będą one w kodowaniu UTF-8, ale raczej w Windows-1250.

Jak sprawnie, używając tylko konsoli, przekonwertować taki plik? To proste.

Przypuśćmy, że chcemy plik `input.txt`, w kodowaniu Windows-1250, zapisać do pliku `output.txt` w UTF-8. Wystarczy:

```bash
iconv --from-code=windows-1250 --to-code=utf-8 --output=output.txt input.txt
```

Ekwiwalentnie można `iconv` wywołać tak:

```bash
iconv -f windows-1250 -t utf-8 input.txt > output.txt
```

Dla dociekliwych, `iconv` jest częścią pakietu `libc6` (przynajmniej pod Debianem). Co więcej, samo `iconv` jest dostępne w praktycznie każdym systemie uniksopodobnym, zatem nie powinno być problemu z dostępnością tego polecenia.
