# CeneoWebScraperN11

## Analiza struktury opinii w serwisie [Ceneo.pl](https://www.ceneo.pl/)

|Skladowa|Selektor|Zmienna|Typ zmiennej|
|--------|--------|-------|------------|
|opinia|div.js_product-review|review|bs4.element.Tag|
|identyfikator opinii|\["data-entry-id"\]|review_id|str|
|autor|span.user-post__author-name|author|str|
|rekomendacja|span.user-post__author-recomendation > em|recommendation|bool|
|liczba gwiazdek|span.user-post__score-count|stars|float|
|tresc|div.user-post__text|content|str|
|data wystawienia|span.user-post__published > time:nth-child(1)\[datetime\]|publish_date|str|
|data zakupu|span.user-post__published > time:nth-child(2)\[datetime\]|purchase_date|str|
|dla ilu przydatna|button.vote-yes\[data-total-vote\]<br>button.vote-yes > span<br>span\[id^=votes-yes\]|useful|int|
|dla ilu nieprzydatna|button.vote-no\[data-total-vote\]<br>button.vote-no > span<br>span\[id^=votes-no\]|useless|int|
|lista zalet|div.review-feature__title--positives ~ div.review-feature__item <br>div.review-feature__col:has( > div.review-feature__title--positives) > div.review-feature__item<br>div.review-feature__item:has( ~ div.review-feature__title--positives)|pros|str|
|lista wad|div.review-feature__title--negatives ~ div.review-feature__item <br>div.review-feature__col:has( > div.review-feature__title--negatives) > div.review-feature__item<br>div.review-feature__item:has( ~ div.review-feature__title--negatives)|cons|str|

## Etapy pracy nad projektem
1) pobranie skladowych pojedynczej opinii do niezaleznych zmiennych<br>
2) zapisanie wszystkich skladowych pojedynczej opinii do obiektu slownika (dictionary)<br>
3) pobranie wszystkich opinii z pojedynczej strony i zapisanie ich do listy slownikow<br>
4) pobranie wszystkich opinii o wskazanym produkcie i zapisanie ich do pliku<br>
5) optymalizacja kodu<br>
    <p style="text-indent:20px;">A) zdefiniowanie funkcji do ekstrakcji elementow strony HTML<br></p>
    <p style="text-indent:20px;">B) utworzenie slownika selektorow opisujacego pojedyncza opinie<br></p>
    <p style="text-indent:20px;">C) zastapienie ekstrakcji skladowych pojedynczej opinii do niezaleznych zmiennych ekstrakcja tych skladowych w dictionary comprehension w oparciu o slownik selektorow<br></p>
6) analiza opinii o wskazanym produkcie<br>
    <p style="text-indent:20px;">A) wyliczenie podstawowych statystyk<br></p>
        <p style="text-indent:40px;">a) liczba wszystkich opinii o produkcie<br></p>
        <p style="text-indent:40px;">b) liczba opinii z podana lista zalet<br></p>
        <p style="text-indent:40px;">c) liczba opinii z podana lista wad<br></p>
        <p style="text-indent:40px;">d) srednia ocena produktu<br></p>
    <p style="text-indent:20px;">B) narysowanie wykresow<br></p>
        <p style="text-indent:40px;">a) udzial poszczegolncyh rekomendacji w ogolnej liczbie opinii<br></p>
        <p style="text-indent:40px;">b) histogram czestosci wystapien poszczegolnych ocen (liczba gwiazdek)<br></p>
7) przesienie gotowych czesci kodu do wlasciwego projektu<br>
    <p style="text-indent:20px;">A) znalezienie odpowiednich miejsc dla poszczegolnych elementow<br></p>
    <p style="text-indent:20px;">B) polaczenie z routingiem<br></p>
8) uruchomienie flask i jinja<br>
    <p style="text-indent:20px;">A) stworzenie bazy dla plikow jinja<br></p>
    <p style="text-indent:20px;">B) dodanie stron odwolujacych sie do bazy<br></p>
9) dodanie funkcjonalnosci<br>
    <p style="text-indent:20px;">A) dzialajacy ekstraktor<br></p>
    <p style="text-indent:20px;">B) readme pojawiajace sie na stronie glownej<br></p>

## Wykorzystane biblioteki

- flask - Framework, ktory sluzy do tworzenia aplikacji webowej<br>
- json - Umozliwia dzialanie na plikach .json - zapis i odczyt plikow<br>
- requests - Obsluga HTTP, wysylanie zadan i odbieranie odpowiedzi<br>
- bs4 - Iteracja, wyszukiwanie i modyfikacja kodu html<br>
- pandas - Analiza danych, modyfikacja i wczytywanie<br>
- numpy - Analiza danych, glownie liczbowych<br>
- matplotlib - Tworzenie wykresow na podstawie danych<br>
- markdown - Obsluga plikow w uproszczonym formacie HTML<br>
