# how to setup env for mkdocs

Pobierz sobie lokalnie repozytorium ACI-Automation z mojego githuba:
Dodalem Cie jako kolaboranta xD

https://github.com/marcinduma/ACI-Automation

sklonuj go, Ja na windzie uzywam github desktop do pullowania, pushowania itp.

Jak juz masz swój clon repo, czas to uruchomic. Do tego wykorzystasz mkdocs:

Musisz zainstalować sobie mkdocs uzywając do tego pythona:
https://www.mkdocs.org/getting-started/

instalujesz, a potem odpalasz sobie 'mkdocs serve' w folderze gdzie wczesniej pobralas repozytorium.

Powinien Ci sie uruchomic lokalny web-server: ""Serving on http://127.0.0.1:8000/ ""
W przeglądarce na bierząco bedziesz widzieć zmiany w wygladzie strony.

Struktura tego LABguida jest w folderze: docs
folderze głównym znajdziesz plik: mkdocs.yml - tam jest cala struktura strony. Zobaczysz które pliki markdown są przypisane do Ciebie (DAY2 LAB)

te markdown pliki edytujesz w notepad++. W folderze docs zostawilem intencjonalnie wszystko co mialem z CiscoLive, tak dla referencji. Wyglad kazdej stronki sprawdzisz tutaj: acikrklabguide.cisco.com:82

Mając caly czas wlaczony ten mkdocs serve, lokalnie strona aktualizuje sie automatycznie.

Potem, deploy na github:
https://www.mkdocs.org/user-guide/deploying-your-docs/
mkdocs gh-deploy

W tym samym root folderze gdzie odpalilas mkdocs serve

potem juz tylko git push obu branchów - master i gh-deploy.

Pozdrawiam :)
