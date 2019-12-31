---
layout: post
title: "GNU Emacs: pierwsze wrażenia"
tags: tech
---

# Tylna część okładki (zachęcająca do kupna książki)

Stało się.

Dlaczego wieloletni Vimowiec napisał `sudo apt install emacs`?

Dlaczego nie wycofał się po zobaczeniu skrótów klawiaturowych, z których [`C-x M-c M-butterfly`](https://www.xkcd.com/378/) by był najprostszym?

Co nim kierowało?

I najważniejsze -- czy nawróci się na Jedyną Słuszną Drogę, pokutując poprzez `sudo apt purge emacs`?

# Akt I: zwątpienie

Z 10 lat korzystam z Vima.
Nie chciałem się angażować w kolejny edytor ze stromą krzywą uczenia.
[Wojna edytorowa](https://en.wikipedia.org/wiki/Editor_war) zaowocowała w niejedno zestawienie porównawcze i dla mnie wniosek był prosty: skoro czuję się komfortowo z Vimem, niech tak zostanie.

I nie byłoby tego wpisu, gdybym nie szukał lepszego zestawu narzędzi do trzymania listy zadań, spotkań czy notatek okraszonych okazyjną flagą `TODO`.
Zastanowiłem się nad wyglądem mojego przepływu pracy.
Spisałem wymagania i preferencje.
Przeszukałem internet w poszukiwaniu odpowiednich narzędzi i je porównałem.

Wniosek był dość prosty: użyję [`org-mode`](https://orgmode.org/) i będę zadowolony.

> Org is a mode for keeping notes, maintaining TODO lists, and project planning with a fast and effective plain-text markup language.

([Źródło](https://orgmode.org/manual/Summary.html#Summary).)

Innymi słowy: dostaję możliwość pisania notatek, w ramach których mogę jednym skrótem klawiaturowym dodać `TODO`.
Mogę dodać zadania w stylu „odkurz mieszkanie co najwyżej raz na 2 dni, ale co najmniej raz na 5 dni”.
Mogę wygenerować rozkład dnia czy tygodnia.
Narzędzie jest klawiaturocentryczne, więc nie odrywa od pisania.
A dodatkowo format danych jest tekstowy i jak najbardziej _human-readable_.

Przez lata przeczytałem wiele dobrych opinii fanatyków Emacsa, opinii Vimowców, którzy poszli tą ścieżką, a także komentarze osób, którym wejście w świat `org-mode` nie udał się.

Dlatego musiałem spróbować.

# Akt II: upadek

Co się stało dalej?

1. Zainstalowałem Emacsa;
2. Przeszedłem wbudowany tutorial. Dwa razy;
3. Wyznawca Kościoła Emacsa przekonał mnie, że [jeśli Emacs, to z GUI](https://blog.aaronbieber.com/2016/12/29/don-t-use-terminal-emacs.html) (nie rzucajcie jeszcze kamieniami, proszę);
4. Zacząłem korzystać z Emacsa jako głównego edytora;
5. Poznałem [`evil-mode`](https://github.com/emacs-evil/evil) oraz kilka innych paczek;
6. Zacząłem korzystać z pamięci mięśniowej i odstawiać [_duckduckgowe_](https://duckduckgo.com/?q=cheat+sheet+org+mode&t=canonical&ia=cheatsheet&iax=1) _cheat sheety_.

Najważniejsze z powyższego jest użycie `evil-mode`.
W największym skrócie jest to Vim w Emacsie.

Wiele aplikacji ma skróty klawiaturowe w stylu Vima, głównie nawigację za pomocą `h`/`j`/`k`/`l`.
Większość z tych „emulatorów” jest niepełna i w niespodziewanych momentach zachowuje się inaczej, niż byśmy oczekiwali.

I tutaj `evil-mode` błyszczy.
Jestem skłonny stwierdzić, że to najlepsza emulacja Vima jaka istnieje.

A nie oszukujmy się: edycja tekstu w czystym Vimie jest zdecydowanie wygodniejsza niż w czystym Emacsie.

Doprowadziło to do sytuacji, w której mogę korzystać z `org-mode` pisząc jak w Vimie, zatem bez walki z własnymi nawykami dot. skrótów klawiaturowych.

## Co oprócz `org-mode`?

Wygodniejsza modyfikacja edytora.
Czy jest na tym świecie ktokolwiek, kto z przyjemnością pisze w VimL (Vim script?)?
Szczerze wątpię.
Za to pisanie w jednym z dialektów Lispa wywołuje uśmiech u niejednego programisty.
U mnie na pewno :)

Ledwie poznałem podstawowe możliwości [`magit`a](https://magit.vc/) (emacsowy interfejs do Gita), a już widzę, że ma potencjał.
Czy to będzie pierwszy raz, gdy porzucę zarządzanie repozytoriami z poziomu konsoli?
Być może i bynajmniej nie jest mi z tego powodu smutno.

Emacs posiada również wiele paczek: od wyspecjalizowanych trybów pod konkretne rodzaje plików czy języki programowania, poprzez integracje z narzędziami do statycznej analizy kodu, aż do przeglądarek internetowych.
Odnoszę również wrażenie, że te dodatki lepiej się integrują z edytorem (tudzież ze sobą nawzajem) niż w vimowym świecie.

# Akt III: przyszłość

Czy mam zamiar kontynuować eksperyment?
Tak.

Czy brakuje mi czegoś z Vima?
Co najwyżej krótszej nazwy.

Czy polecam przesiadkę?
Jeszcze nie wiem.
W moim przypadku -- póki co -- sprawdza się wyśmienicie.

Wiele osób się śmieje, że Emacs to świetny system operacyjny, ale brakuje mu porządnego edytora tekstu.
Pierwsza część jest solidnie podparta liczbą i jakością paczek do mnóstwa rzeczy.
A co do drugiej części…
Tutaj właśnie wkracza `evil-mode`.

# Posłowie

_(Post został napisany przy użyciu GNU Emacs 25.2.2 wraz z [`markdown-mode`](https://jblevins.org/projects/markdown-mode/) tudzież `evil-mode`, zaś dodany do repozytorium przy użyciu `magit`a. Grafomańską wenę zawdzięczam św. IGNUcemu.)_
