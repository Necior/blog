---
layout: post
title: Canon EOS 70D jako kamerka pod Linuksem
tags: tech
---

Chciałem użyć lustrzanki (w moim przypadku Canon EOS 70D) jako kamerki internetowej.
Jednak po podłączeniu do laptopa miałem dostęp tylko do zawartości karty pamięci.
Nie było możliwości robienia zdjęć czy nagrywania filmów.

Na szczęście, przy użyciu kilku narzędzi, można dotrzeć do właściwych możliwości lustrzanki.

Poniżej instrukcje dla pochodnych Debiana.

Instalujemy potrzebne narzędzia: `apt-get install gphoto2 v4l2loopback-utils`.
Dodajemy odpowiedni moduł kernela: `modprobe v4l2loopback`.

Teraz, gdy chcemy wysokiej jakości kamerkę, wystarczy podpiąć urządzenie pod port USB i użyć poniższego, zacnego _onelinera_ (w razie potrzeby zmień `/dev/video0` na inne urządzenie):

```
gphoto2 --stdout --capture-movie | gst-launch-1.0 fdsrc ! decodebin name=dec ! queue ! videoconvert ! v4l2sink device=/dev/video0
```

W tym momencie, programy do obsługi kamer (np. Cheese czy OBS Studio) zaczęły dostrzegać urządzenie.

W moim przypadku konieczne było zmniejszenie rozdzielczości poszczególnych klatek, aby uzyskać zadowolającą liczbę FPS-ów.
Dlatego poniżej zamieszczam kilka przydatnych funkcji:

* `gphoto2 --summary` -- podsumowanie ogólnych informacji o podłączonym urządzeniu;
* `gphoto2 --list-config` -- lista opcji konfiguracyjnych (tak, możemy konfigurować aparat z poziomu linii poleceń!);
* `gphoto2 --get-config=imageformat` (przykładowo) -- szczegóły wybranej opcji konfiguracyjnej;
* `gphoto2 --set-config imageformat=6` (przykładowo) -- ustawienie wybranej opcji konfiguracyjnej.

Po szczegóły odsyłam do `man gphoto2`.

Udanego _streamowania_!
