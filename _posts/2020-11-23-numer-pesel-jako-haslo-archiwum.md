---
layout: post
title: "Numer PESEL jako hasło archiwum"
tags: sec tech
---

Dostałem z placówki medycznej (której nazwa nie jest w tym poście istotna) maila z wynikami badania.
Do otwarcia archiwum 7z potrzebne było hasło.
Jak dowiedziałem się z maila, hasłem był numer PESEL.

Z ciekawości sprawdziłem, czy ktoś (powiedzmy: atakujący) byłby w stanie rozpakować to archiwum, gdyby je przechwycił :)
Na początek założmy, że atakujący - oprócz bycia w posiadaniu archiwum - zna tylko moją datę urodzenia.

## Krótko o formacie numeru PESEL

PESEL składa się z 11 cyfr.
Jego pierwsze 6 cyfr bierze się z daty urodzenia.
Dla osób urodzonych, tak jak ja, między 1900 a 1999 rokiem, początek numery przyjmuje format `YYMMDD`.
Przykładowo dla osoby urodzonej 21 marca 1990 roku, początek numeru PESEL wynosi `900321`.

Zatem atakujący wie, że hasło jest w postaci `YYMMDD?????`, gdzie `YYMMDD` zna (np. `900321`), zaś każdy znak `?` to nieznana cyfra.

## Czas łamania 5 znaków

Sprawdziłem jak długo trwa złamanie hasła metodą _brute-force_, tj. sprawdzając po kolei każdą możliwą kombinację (`90032100000`, `90032100001`, …, aż do `90032199999`).

Obliczenia wykonałem na pojedynczym wątku procesora (i7-8700K, 3.70 GHz).
W praktyce można czas łamania hasła wielokrotnie skrócić, ale o tym później.

Co do wyników…
Hasło do testowego archiwum udało się złamać w jedynie 68 minut.

## A co jeśli atakujący nie zna dokładnej daty urodzenia?

Oczywiście powyżej opisałem dość szczególny przypadek, gdy atakujący zna datę urodzin.
Na pewno atakującemu trudniej jest rozpakować archiwum, gdy jej nie zna, bo wtedy nie zna początku hasła.
Przypuścmy teraz, że atakujący zna tylko rocznik (np. `1990`).

Ile by wtedy zajęło łamanie hasła?
Na początek możemy to oszacować z góry.

Jeśli atakujący nie zna dnia urodzin, ale zna rocznik, to zna 2 z 6 początkowych cyfr numeru PESEL.
Może w takiej sytuacji spróbować wszystkich 4-cyfrowych kombinacji dla `MMDD`.
Wtedy początek hasła ma postać `YY????`.

W takim przypadku do przetestowania jest `10⁴` kombinacji (od `900000` do `909999`).
Sprawdzenie wszystkich kombinacji wydłuża zatem czas ataku maksymalnie 10⁴-krotnie.
Ekstrapolując, jest to ok. 16 miesięcy liczenia na jednym wątku procesora.

Zdecydowanie wolniej, ale wciąż niepokojąco szybko.
A co jeśli atakujący jest sprytniejszy?

Przyjrzyjmy się jeszcze raz początkowi hasła: `YY????`.
Czy atakujący musi rozważać wszystkie 10⁴ kombinacji?
Przecież wiele z nich, np. `907788`, nie ma sensu, bo nie ma miesiąca z 88 dniami, ani 77 miesięcy w roku.

Tak naprawdę do rozważenia jest tyle kombinacji, ile jest dni w roku 1990.
Co daje 365 kombinacji zamiast 10⁴.
W takim przypadku sprawdzenie wszystkich kombinacji wydłuża czas ataku (w stosunku do wersji, gdzie cała data urodzin jest znana) maksymalnie 365-krotnie.
Jest to ok. 17 dni liczenia na jednym wątku procesora.

## Czy można szybciej?

Oczywiście.

Do dyspozycji jest kilka sposobów: szybszy procesor, obliczenia wielowątkowe, a także użycie GPU.
Przy użyciu konsumeckiego sprzętu można bez problemu zejść z czasem łamania hasła - przy znajomości jedynie roku urodzenia - do kilku godzin.

A jeśli atakujący nie zna rocznika?
No cóż, jeśli się domyśla i chciałby sprawdzić - powiedzmy - 10 różnych roczników, to wtedy może hasło złamać w ciągu kilku dni.

Ponadto, oprócz wydajniejszego sprzętu, można jeszcze popracować nad samą metodą.
PESEL to nie są losowe cyfry.
Początek to data urodzenia, ale w dalszej części też są zakodowane informacje.
Jeśli atakujący zna płeć, to dysponuje 1 bitem informacji o haśle, co może skrócić obliczenia 2-krotnie.

Dodatkowo, ostatnia cyfra numeru PESEL to suma kontrolna, więc nie trzeba testować wszystkich możliwych cyfr, co też skraca obliczenia.
(Z drugiej strony, zdarzają się numery PESEL z błędną cyfrą kontrolną, więc być może warto próbować także niewłaściwe numery PESEL.)

## Podsumowanie, wnioski i uwagi końcowe

Jak wskazują powyższe szacunki, numer PESEL jako hasło nie ochroni przed atakującym, który przechwyci archiwum.

Główną wadą takiego zabezpieczenia archiwum jest to, że atakujący prawdopodobnie zna część hasła.
Po drugie, hasło składa się jedynie z cyfr, co daje niewiele kombinacji do sprawdzenia.

Na pewno bezpieczniejszym rozwiązaniem by było użycie losowego, dłuższego hasła, składającego się z małych i dużych liter, cyfr i znaków specjalnych.

I na koniec drobna uwaga: cała analiza w tym poście jest orientacyjna.
Raz czas łamania jest zmierzony, raz liczony teoretycznie.
Ponadto, w praktyce, zazwyczaj można złamać hasło wcześniej (jeśli się trafi na "szczęśliwą" kombinację).
Ja podawałem czasy pesymistycznie, a zazwyczaj liczy się czas średni.
Niemniej jednak rząd wielkości pozostaje ten sam, a o to chodzi w tego typu analizie.

