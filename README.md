# CeneoScraper

## Kod produktu do testow
84514582

## Algorytm pobierania opinii o produkcie z serwisu ceneo
1. Wysłanie żądania do strony internetowej z opiniami o produkcie
2. Jeżeli operacja zakończy się powodzeniem, wyodrębnienie z kodu strony opinii o produkcie
3. Dla każej opinii wyodrębnienie z kodu HTML poszczególnych składowych i przypisanie ich do elementu złozonej struktury danych.
4. Jeśli istnieje kolejna strona z opiniami, przejscie do niej i powtórzenie kroków 1-4
5. Zapisanie wyników do bazy danych


## Struktura opinii w serwisie Ceneo.pl
|składowa|zmienna|selektor|
|--------|-------|--------|
|opinia|review|div.js_product-review:not(.user-post--highlight)|
|identyfikator opinii|opinion_id|['data-entry-id']|
|autora|author|span.user-post__author-name|
|rekomendację|recommendation|span.user-post__author-recomendation > em|
|liczbę gwiazdek|stars|span.user-post__score-count|
|treść opinii|content|div.user-post__text|
|listę zalet|pros|div.review-feature__item--positive|
|listę wad|cons|div.review-feature__item--negative|
|ile osób uznało opinię za przydatną|useful|button.vote-yes > span|
|ile osób uznało opinię za nieprzydatną|unuseful|button.vote-no > span|
|data wystawienia opinii|post_date|span.user-post__published > time:nth-child(1)['datetime']|
|data zakupu produktu|purchase_date|span.user-post__published > time:nth-child(2)['datetime']|