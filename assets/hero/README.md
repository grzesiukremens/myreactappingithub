# Animowane hero na stronie głównej (13.10.2026)

Trzy warstwy z przezroczystym tłem, wycięte przez właściciela w ChatGPT z obrazu z trzema zawieszkami, dopasowane do siebie (skala i przesunięcie) i oczyszczone z półprzezroczystej mgiełki (alfa < 12 → 0).

| Plik w Shopify | Warstwa | Ustawienie sekcji `vellano-hero` |
|---|---|---|
| vellano-hero-warstwa-mu.webp | z tyłu, środek (Manchester United) | `layer_back` |
| vellano-hero-warstwa-rm.webp | z przodu, lewa (Real Madryt) | `layer_front_1` |
| vellano-hero-warstwa-fcb.webp | z przodu, prawa (FC Barcelona) | `layer_front_2` |

Wspólne płótno 1326 × 1254 px. Kadr pokazuje płótno od 78 px w dół (proporcja 1326:1176), żeby łańcuszki zawsze wychodziły poza górną krawędź także w ruchu. `geometria.json` zawiera punkty zawieszenia (oś kołysania) i miejsca błysków; te same liczby (w procentach płótna) są wpisane w `theme/snippets/vellano-hero-layers.liquid`. Po podmianie plików na inne trzeba je przeliczyć.

Ruch: głębia przy przewijaniu (tył prawie stoi, przód jedzie w górę), kołysanie na łańcuszkach, pas światła maskowany kształtem zawieszek (przy przewijaniu i co 7 s w spoczynku), drobne błyski na kamieniach, na komputerze lekki ruch za kursorem. Przy systemowym „ogranicz ruch” zostaje nieruchomy obraz.
