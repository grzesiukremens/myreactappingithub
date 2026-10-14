# Dostawa (14.10.2026)

## Metody w kasie Shopify

Ustawienia → Wysyłka i dostawa → profil „General profile”, strefa „Domestic” (Polska). Wszystkie metody 0 zł,
zgodnie z obietnicą „Darmowa dostawa” na stronie. Poprzednie metody „Standardowa” (20 zł, darmowa od 200 zł)
i „Ekspresowa” (65 zł) usunięte.

| Metoda (nazwa w kasie) | Opis w kasie |
|---|---|
| InPost Paczkomat 24/7 | Paczkomat wybrany w koszyku |
| DPD Pickup – punkt lub automat | Punkt wybrany w koszyku |
| DHL POP – punkt lub automat | Punkt wybrany w koszyku |
| ORLEN Paczka | Punkt wybrany w koszyku |
| Poczta Polska – odbiór w punkcie | Punkt wybrany w koszyku |
| Kurier InPost | Doręczenie pod adres dostawy |
| Kurier DPD | Doręczenie pod adres dostawy |
| Kurier DHL | Doręczenie pod adres dostawy |
| Kurier Pocztex | Doręczenie pod adres dostawy |

Strefa „International” (74 zł) została bez zmian; sklep sprzedaje tylko do Polski.

## Wybór punktu w koszyku

Plan Basic nie ma w kasie mapy paczkomatów dla Polski, więc punkt wybiera się w koszyku:
`theme/snippets/vellano-delivery-picker.liquid`, renderowany w `theme/snippets/cart-summary.liquid` nad przyciskiem
do kasy (działa w szufladzie koszyka i na stronie koszyka; „Kup teraz” otwiera szufladę, przyciski szybkiej płatności są wyłączone).

- „Paczkomat lub punkt” otwiera mapę Furgonetka (InPost, DPD, DHL, ORLEN Paczka, Poczta Polska). Metoda wynika z rodzaju punktu.
- „Kurier”: InPost, DPD, DHL, Pocztex.
- Bez wyboru przycisk do kasy pokazuje komunikat i nie przechodzi dalej.
- Podpowiedź „W kasie zaznacz: …” mówi, którą metodę kliknąć w kasie.

Wybór zapisuje się w atrybutach koszyka, widocznych w zamówieniu w „Dodatkowe szczegóły”:
`Dostawa` (nazwa metody), `Punkt odbioru` (kod punktu, np. WAW123M), `Adres punktu`.
Wysyłkę nadaje się według tych pól (wszystkie metody są darmowe, więc ewentualna rozbieżność z metodą zaznaczoną w kasie nic nie zmienia w cenie).

## Klucz mapy Furgonetka

Mapa wymaga klucza API: konto firmowe Furgonetka → https://furgonetka.pl/api/mapa → „Zarządzaj klientami mapy” →
dodaj klienta z domenami `0ui2yq-ix.myshopify.com` i docelową domeną sklepu → wygeneruj token.
Token zapisuje się w metapolu sklepu `custom.furgonetka_map_key` (tekst jednowierszowy). Bez klucza przycisk mapy
pokazuje komunikat „Mapa punktów jest chwilowo niedostępna”, kurierzy działają normalnie.
