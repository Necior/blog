---
layout: post
title: Stos a sterta
tags: tech c
---

Stos (ang. _stack_). Sterta (ang. _heap_). Te dwa terminy są nieraz mylone. Może dlatego, że na co dzień postrzega się te słowa jako synonimy?

Jednakże każdy, kto chce się nazywać developerem, powinien rozróżniać te pojęcia.

# Stos

Na stosie (_stacku_) przechowywane są zmienne lokalne. Stos jest buforem LIFO (ang. _last-in, first-out_).

Stos jest obsługiwany automatycznie z punktu widzenia programisty, nie ma potrzeby ręcznego zwalniania pamięci.

W poniższym przykładzie, `in` oraz `result` są zmiennymi przechowywanymi na stosie.

```c
int triple(int in) {
    int result = in * 3;
    return result;
}
```

Podczas wywoływania funkcji na stos kładzione są kolejno zmienne `in` i `result`, natomiast podczas powrotu do funkcji wywołującej, są one zdejmowane (w odwrotnej kolejności, niż były kładzione, ponieważ jest to bufor LIFO).

# Sterta

Sterta (_heap_) służy do przechowywania zmiennych dynamicznych, które są widoczne dla całego programu. Nie ma gwarancji, aby dane przechowywane na stercie leżały na ciągłym obszarze pamięci. Inaczej mówiąc, może nastąpić fragmentacja.

Zarządzanie zmiennymi na stercie należy do zadań programisty. W języku C służą do tego funkcje `malloc` (aby zaalokować pamięć) oraz `free` (aby zwolnić pamięć). [^1]

[^1]: Do tej samej rodziny funkcji należą jeszcze `calloc` oraz `realloc`, które służą odpowiednio do alokacji (z jednoczesnym zerowaniem) pamięci oraz do zmiany rozmiaru uprzednio zaalokowanego bloku pamięci.

W poniższym przykładzie, ściśle mówiąc, `result` jest zmienną lokalną, która zawiera adres komórki pamięci do danych, które są na stercie. Jednak nieraz używa się skrótu myślowego i mówi się, że `result` jest na stercie.

```c
int *triple(int in) {
    int *result = malloc(sizeof(int));
    *result = in * 3;
    return result;
}
```

(Warto też zauważyć, że zamiast konstrukcji `int *result = malloc(sizeof(int))` można użyć `int *result = malloc(sizeof(*result))`, ale nie będę tutaj rozważał wyższości któregoś rozwiązania nad innym.)

Należy pamiętać, aby zwolnić pamięć zaalokowaną przy pomocy `malloc`, używając `free` w miejscu, w którym wynik funkcji `triple` przestaje być istotny.

Dostęp do danych na stercie jest wolniejszy niż do danych ze stosu, jednak pozwala nam - jako developerom - dostosować rozmiar danych w pamięci do danych wejściowych. Ponadto, stos jest z reguły wyraźnie mniejszy, zatem duże bloki danych przechowuje się na stercie.
