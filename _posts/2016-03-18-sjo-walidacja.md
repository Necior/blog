---
layout: post
title: Brak walidacji danych po stronie serwera SJO PW
tags: life sec
---

Zaczęło się niewinnie. Jak każdego semestru, przyszedł dzień rejestracji na lektoraty. Angielski dobrałem do planu tak, aby zmniejszyć liczbę wolnych godzin między zajęciami, zaś rosyjski - w piątek z rana. Dzień tygodnia jak w poprzednim semestrze, godzina również.

Chciałem też ten sam moduł.

Nie czułem się na siłach, aby kontynuować naukę rosyjskiego. Chciałem przerobić ten sam materiał ponownie, tym razem wiedząc, na co zwrócić szczególną uwagę. Edukacja nie raz mnie nauczyła jak ważne są fundamenty.

Przyszła godzina rejestracji (na zasadzie "kto pierwszy, ten lepszy"). Przez pierwszy kwadrans serwery Studium Języków Obcych w ogóle nie radziły sobie z ruchem. Przeczekałem, gorliwie odświeżając stronę. Na angielski starczyło miejsc; po kilku próbach wysłania formularza serwer potwierdził, że zostałem dodany do listy uczestników wybranych zajęć.

"Teraz już z górki", pomyślałem uśmiechając się. Wybrałem drugi język obcy, pokazała mi się lista możliwych zajęć.

I na tej liście **nie było** modułu, który chciałem wybrać. Odświeżyłem stronę, sprawdziłem raz jeszcze - to samo. Powstało pytanie - wziąć trudniejszy moduł i kontynować naukę (czego wolałem uniknąć), czy wybrać inny język?

Już rozważałem hiszpański w równie dogodnych godzinach, gdy zauważyłem, że URL do zapisów ma poniższą postać.

```
https://ssl.sjo.pw.edu.pl/(...)/1696
```

Domyśliłem się, że liczba na końcu była zwyczajnie identyfikatorem modułu, na który studenci się zapisują. Szybko powstała myśl, czy mógłbym się zapisać na inny kurs, jeśli bym podał odpowiedni identyfikator? Ciekawość zwyciężyła i postanowiłem spróbować.

Zakładając, że oszukanie systemu by było możliwe, przeszkodą do pokonania było znalezienie prawidłowego identyfikatora, aby dostać się na dany poziom języka w odpowiedniej godzinie i dniu. W przeglądarce miałem do wyboru kolejne kursy. Okazało się, że ich identyfikatory były kolejnymi liczbami (przyjmijmy, że `1696`, `1697`, `1698` itd.).

"Pewnie poprzedni moduł na mniejsze identifykatory", zabrzmiało w mojej głowie i wysłałem do serwera żądanie z zapisaniem się na moduł o identyfikatorze `1695`, tj. o jeden mniejszym niż najmniejszy z wyświetlanych.

Udało się. Otrzymałem komunikat, że zostałem zapisany na ten moduł, których chciałem. Tylko... Godzina zła.

Tym samym musiałem dalej szukać upragnionego identyfikatora. Otworzyłem PDF-a z ofertą języków na letni semestr, znalazłem ten, na który się zapisałem. Zauważyłem, że wybrany przeze mnie moduł znajduje się dwie pozycje niżej.

"To może wystarczy dwukrotnie zdekrementować identyfikator i to będzie to?", pomyślałem.

Wypisałem się z rosyjskiego i wysłałem ponownie żądanie, tym razem z identyfikatorem `1693`. Otrzymałem komunikat, że zostałem pomyślnie dodany do danej grupy zajęciowej.

Zadanie wykonane.

(Odpowiednie zgłoszenie błędu zostało wysłane do osób zajmujących się technicznymi sprawami SJO miesiąc przed publikacją tego wpisu.)
