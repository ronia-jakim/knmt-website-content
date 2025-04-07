# knmt-website-content : instrukcja obsługi

Repozytorium jest podmodułem w repozytorium [knmt-website](https://github.com/ronia-jakim/knmt-website), które jest co 5 minut pobierane i buildowane przez maszynę wirtualną znajdującą się w domenie WMI.

Struktura całego projektu
```
|- knmt-website 
   |- build.sh*        # builds the whole website
   |- local_server.sh* # runs server locally using caddy ( localhost:8080 )
   |- requirements.txt # python libraries
   |- src
   |- assets
   |- content
      |- info.md       # all basic informations about KNMT
      |- book_list.md  # KNMT library
      |- conf_list.md  # upcoming conferences
      |- statut.pdf
      |- news          # posts showed on the main page
         |- example_post
            |- info.md # the content of example_post together with title, author, date etc.
            |- ...     # other files used by example_post, e.g. its icon or images
      |- photos
         |- example_album
            |- info.md # contains title of album 
            |- ...     # all the photos that are inside example_album
```

Wszystkie ścieżki niżej są podane względem `knmt-website` zakładając, że poniższe repozytorium jest submodule w `knmt-webstie`.


> [!CAUTION]
> Wszystkie nazwy folderów nie powinny zawierać spacji ani znaków specjalnych (w tym polskich) różnych od `_` lub `-`. Nieprzestrzeganie tej zasady może skutkować błędami w budowie strony.

## zarządzanie wpisami

Wszystkie wpisy pojawiające się na stronie Aktualności są przechowywane w folderze `content/news` jako **folder z głównym plikiem `info.md` zawierającym** informacje takie jak

- tytuł posta
- autor (dotyczy referatu)
- data (format `YYYY.MM.DD`)
- godzina (dotyczy referatów, format `HH:MM`)
- obrazek poglądowy (jeśli nie jest dołączony, to użyty jest domyślny plik w `/assets/img/post_preview.jpg`

Wszystkie zdjęcia, które mają być zawarte w poście muszą być w folderze posta, a ścieżki w pliku `*.md` mają być względem tegoż foldera.

```yaml
---
    title: 'tytuł posta/referatu'
    author: 'autor referatu'
    date: 'data wpisu lub data referatu w formacie YYYY.MM.DD'
    time: 'godzina referatu w formacie HH:MM'
    preview_image: 'ścieżka do pliku pokazującego się na stronie głównej względem folderu w którym się znajdujemy'
    description: 'opis posta, który pokazuje się na stronie głównej, jeśli pozostawione pustym użyte zostanie pierwsze 100 znaków głównego tekstu posta'
---

Główna treść posta, pisana jak w markdownie możliwe jest użycie latexa, powinna pojawić się tylko w tym miejscu.

```

## zarządzanie albumami

Każdy album ze zdjęciami to osobny folder zawierający plik `info.md` wypełniony jak niżej oraz co najmniej jedno zdjęcie.

```
---
album_title: 'nazwa albumu'
preview: 'obrazek, który ma być miniaturą albumu, pozostaw puste, by wybrać pierwszy w kolejności'
---
```

## informacje o KNMT

Plik `content/info.md` powienien mieć formę

```
---
   prezes: 'imię i nazwisko prezesa'
   wice: '...'
   skarbnik: '...'
   sekretarz: '...'
---
```

Strona [Informacje](https://knmt.wmi.uni.wroc.pl/info/) szuka pliku `content/statut.pdf` i wyświetla go jako `<embed></embed>`. W razie błędów sprawdź, czy plik `content/statut.pdf` istnieje w dobrym miejscu.
