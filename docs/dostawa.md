# Dostawa (14.10.2026)

## Metody w kasie Shopify

Ustawienia → Wysyłka i dostawa → profil „General profile”, strefa „Domestic” (Polska). Wszystkie metody 0 zł,
zgodnie z obietnicą „Darmowa dostawa” na stronie. Poprzednie metody „Standardowa” (20 zł, darmowa od 200 zł)
i „Ekspresowa” (65 zł) usunięte.

| Metoda (nazwa w kasie) | Opis w kasie |
|---|---|
| InPost Paczkomat 24/7 | – |
| DPD Pickup – punkt lub automat | – |
| DHL POP – punkt lub automat | – |
| ORLEN Paczka | – |
| Poczta Polska – odbiór w punkcie | – |
| Kurier InPost | Doręczenie pod adres dostawy |
| Kurier DPD | Doręczenie pod adres dostawy |
| Kurier DHL | Doręczenie pod adres dostawy |
| Kurier Pocztex | Doręczenie pod adres dostawy |

Strefa „International” (74 zł) została bez zmian; sklep sprzedaje tylko do Polski.

## Wybór punktu odbioru (14.10.2026)

Na życzenie właściciela sposób dostawy wybiera się tylko w kasie. Wybór punktu w koszyku (mapa Furgonetka,
snippet vellano-delivery-picker) został wyłączony: snippets/cart-summary.liquid wrócił do wersji Horizon,
a kod wyboru jest w historii gita (commit 577654b), gdyby był potrzebny. Plik snippets/vellano-delivery-picker.liquid
został w kopii motywu (API nie pozwala usuwać plików), ale nic go nie renderuje.

Plan Basic nie ma w kasie mapy paczkomatów dla Polski, więc przy metodach punktowych kasa nie pyta o konkretny punkt.
Do decyzji właściciela: aplikacja z wyborem punktu po zakupie (np. „InPost Paczkomaty Orlen Paczka” od Codie, działa na Basic),
wyższy plan Shopify z mapą w kasie albo tylko kurierzy.
