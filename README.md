# CeneoWebScraperN11

## Analiza struktury opinii w serwisie [Ceneo.pl](https://www.ceneo.pl/)

|Składowa|Selektor|Zmienna|Typ zmiennej|
|--------|--------|-------|------------|
|opinia|div.js_product-review|review|bs4.element.Tag|
|identyfikator opinii|\["data-entry-id"\]|review_id|str|
|autor|span.user-post__author-name|author|str|
|rekomendacja|span.user-post__author-recomendation > em|recommendation|bool|
|liczba gwiazdek|span.user-post__score-count|stars|float|
|treść|div.user-post__text|content|str|
|data wystawienia|span.user-post__published > time:nth-child(1)\[datetime\]|publish_date|str|
|data zakupu|span.user-post__published > time:nth-child(2)\[datetime\]|purchase_date|str|
|dla ilu przydatna|button.vote-yes\[data-total-vote\]<br>button.vote-yes > span<br>span\[id^=votes-yes\]|useful|int|
|dla ilu nieprzydatna|button.vote-no\[data-total-vote\]<br>button.vote-no > span<br>span\[id^=votes-no\]|useless|int|
|lista zalet|div.review-feature__title--positives ~ div.review-feature__item <br>div.review-feature__col:has( > div.review-feature__title--positives) > div.review-feature__item<br>div.review-feature__item:has( ~ div.review-feature__title--positives)|pros|str|
|lista wad|div.review-feature__title--negatives ~ div.review-feature__item <br>div.review-feature__col:has( > div.review-feature__title--negatives) > div.review-feature__item<br>div.review-feature__item:has( ~ div.review-feature__title--negatives)|cons|str|

## Etapy pracy nad projektem
1) pobranie składowych pojedynczej opinii do niezależnych zmiennych<br>
2) zapisanie wszystkich składowych pojedynczej opinii do obiektu słownika (dictionary)<br>
3) pobranie wszystkich opinii z pojedynczej strony i zapisanie ich do listy słowników<br>
4) pobranie wszystkich opinii o wskazanym produkcie i zapisanie ich do pliku<br>
5) optymalizacja kodu<br>
    1) zdefiniowanie funkcji do ekstrakcji elementów strony HTML<br>
    2) utworzenie słownika selektorów opisującego pojedynczą opinię<br>
    3) zastąpienie ekstrakcji składowych pojedynczej opinii do niezależnych zmiennych ekstrakcją tych składowych w dictionary comprehension w oparciu o słownik selektorów<br>
6) analiza opinii o wskazanym produkcie<br>
    1) wyliczenie podstawowych statystyk<br>
        1) liczba wszystkich opinii o produkcie<br>
        2) liczba opinii z podaną listą zalet<br>
        3) liczba opinii z podaną listą wad<br>
        4) średnia ocena produktu<br>
    2) narysowanie wykresów<br>
        1) udział poszczególncyh rekomendacji w ogólnej liczbie opinii<br>
        2) histogram częstości wystąpień poszczególnych ocen (liczba gwiazdek)<br>

## Wykorzystane biblioteki

- flask - Framework, który służy do tworzenia aplikacji<br>
- json - Umożliwia działanie na plikach .json - zapis i odczyt plików<br>
- requests - Obsługa HTTP, wysyłanie żądań i odbieranie odpowiedzi<br>
- bs4 - Iteracja, wyszukiwanie i modyfikacja kodu html<br>
- pandas - Analiza danych, modyfikacja i wczytywanie<br>
- numpy - Analiza danych, głównie liczbowych<br>
- matplotlib - Tworzenie wykresów na podstawie danych<br>
- markdown - uproszczony format HTML<br>

