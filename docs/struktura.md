# Struktura sklepu

Architektura premium dla motywu Horizon. Elementy z datami granicznymi, pielęgnacją i bilecikiem zostały wyłączone decyzją właściciela.

## Mapa strony

| Adres | Tytuł | Szablon | Cel |
|---|---|---|---|
| `/` | Strona główna | index.json | Wizytówka marki i rozdzielnia ruchu. W 3 sekundy mówi, co to jest (oficjalna biżuteria kibica w jakości jubilerskiej), dla kogo i jak kupić, a potem prowadzi do wyboru klubu albo prezentu. |
| `/collections/wszystkie-zawieszki` | Wszystkie zawieszki | collection.json (domyślny) | Katalog trzech herbów obok siebie. Cel dla linku „Wszystkie”, dla przekierowania z /collections/all i dla reklam katalogowych (Meta Advantage+, TikTok Catalog). |
| `/collections/real-madryt` | Real Madryt | collection.klub.json | Landing klubu pod reklamy i SEO („zawieszka Real Madryt”). Pokazuje tożsamość Królewskich i pozwala kupić bez przechodzenia na kartę produktu. |
| `/collections/fc-barcelona` | FC Barcelona | collection.klub.json | Landing klubu dla Dumy Katalonii (blaugrana, Spotify Camp Nou, „Més que un club”), działający tak samo jak landing Realu. |
| `/collections/manchester-united` | Manchester United | collection.klub.json | Landing klubu dla Czerwonych Diabłów (Old Trafford, czyli Teatr Marzeń, „Glory Glory Man United”), działający tak samo jak landing Realu. |
| `/collections/prezent-dla-kibica` | Prezent dla kibica | collection.okazja.json | Stały hub prezentowy z hasłem „Nie musisz znać się na piłce – wybierz herb”. Zawiera usługi prezentowe, terminy i FAQ dla osoby, która kupuje prezent. |
| `/collections/prezent-dla-niego` | Prezent dla niego | collection.okazja.json | Wejście z wyszukiwarki i z kampanii do partnerek (20–40 lat). Główny argument: „prezent dla kibica, który ma już koszulkę”. |
| `/collections/prezent-na-mikolajki` | Prezent na Mikołajki | collection.okazja.json | Landing sezonowy (16.11–6.12.2026) dla rodziców, chrzestnych i dziadków, z datą graniczną zamówienia [DP]. |
| `/collections/prezent-na-swieta` | Prezent na Święta | collection.okazja.json | Główny landing sezonu (1.11–23.12.2026): gwarancja dostawy przed Świętami i data graniczna 16.12 [data DP], wzorem kart W.KRUK z konkretną datą. |
| `/collections/prezent-na-walentynki` | Prezent na Walentynki | collection.okazja.json | Landing sezonowy (15.01–14.02.2027) dla partnerek. Poza sezonem znika z menu, ale strona zostaje (SEO na kolejny rok). |
| `/collections/prezent-na-18-urodziny` | Prezent na 18. urodziny | collection.okazja.json | Stały landing dla rodziny (18-stki i inne okazje w ciągu roku), w tonie pamiątki na lata. |
| `/products/zawieszka-real-madryt-z-lancuszkiem` | Oficjalna zawieszka Real Madryt z łańcuszkiem | product.json | Główny cel reklam produktowych i katalogowych. Pełny blueprint karty produktu opisano w sekcji PDP. |
| `/products/zawieszka-fc-barcelona-z-lancuszkiem` | Oficjalna zawieszka FC Barcelona z łańcuszkiem | product.json | Główny cel reklam produktowych i katalogowych. Ten sam szablon; treści klubowe pochodzą z metapól. |
| `/products/zawieszka-manchester-united-z-lancuszkiem` | Oficjalna zawieszka Manchester United z łańcuszkiem | product.json | Główny cel reklam produktowych i katalogowych. Ten sam szablon; treści klubowe pochodzą z metapól. |
| `/pages/o-marce` | O marce Vellano Jubiler | page.o-marce.json | Wartości marki: jubilerska staranność, oficjalne licencje, polska obsługa, dostawa przed Świętami. Piszemy tylko potwierdzoną historię, a brakujące miejsca oznaczamy [do potwierdzenia: historia marki, założyciele, rok założenia]. |
| `/pages/oficjalna-licencja` | Oficjalna licencja | page.licencja.json | Odpowiada na obiekcję „czy to oryginał?”: co oznacza licencja, kto jest licencjodawcą [do potwierdzenia] i jak wygląda oznaczenie licencji w opakowaniu [DP]. |
| `/pages/wykonanie-i-pielegnacja` | Wykonanie i pielęgnacja | page.wykonanie.json | Jubilerski opis materiałów (mosiądz, powłoka rodowana, emalia, ręcznie osadzane cyrkonie, splot linkowy, ucho mieszczące łańcuszek do 5 mm) oraz zasady pielęgnacji [do potwierdzenia z producentem]. |
| `/pages/opakowanie-prezentowe` | Pakowanie na prezent | page.prezent.json | Pokazuje pudełko prezentowe [DP], bilecik z dedykacją i paczkę bez ceny [DP]. To argument dla osób kupujących prezent, wzorem W.KRUK i Ani Kruk. |
| `/pages/dostawa` | Dostawa | page.dostawa.json | Metody dostawy (Paczkomaty InPost i kurier [DP]), koszt (darmowa [DP]) i wysyłka w 2–3 dni robocze. Kotwica #terminy-swiateczne prowadzi do tabeli dat i opisu warunków gwarancji dostawy przed Świętami. |
| `/pages/zwroty` | Zwroty | page.json | Treść pisze właściciel. Motyw zapewnia czytelny układ i linki z karty produktu, koszyka i stopki. W innych miejscach sklepu nie podajemy liczby dni. |
| `/pages/faq` | Najczęstsze pytania | page.faq.json | Zbiera obiekcje: licencja i oryginalność, łańcuszek (w zestawie, ok. 51 cm, ucho do 5 mm), terminy, płatności, pakowanie, zwroty (link), pielęgnacja. Akordeon z danymi strukturalnymi FAQ. |
| `/pages/kontakt` | Kontakt | page.contact.json | Formularz, e-mail w domenie marki, godziny pracy i czas odpowiedzi [do uzupełnienia], dane firmy. Strona podkreśla polską obsługę. |
| `/pages/opinie` | Opinie klientów | page.opinie.json | Wszystkie opinie (Judge.me All Reviews). Publikujemy dopiero po zebraniu co najmniej 5 opinii; wcześniej strona jest ukryta. |
| `/blogs/poradnik` | Poradnik | blog.json | Treści eksperckie w stylu poradnika W.KRUK „Sploty łańcuszków”: SEO i pomoc dla osób kupujących prezent. |
| `/blogs/poradnik/jak-wybrac-prezent-dla-kibica` | Jak wybrać prezent dla kibica | article.json | Dla partnerek i rodziny: „nie musisz znać się na piłce – wybierz herb”. Jak dyskretnie sprawdzić, komu kibicuje, terminy i pakowanie. |
| `/blogs/poradnik/splot-linkowy-lancuszek` | Splot linkowy – co warto wiedzieć o łańcuszku | article.json | Materiał ekspercki o splocie rope i długości 20 cali (ok. 51 cm) oraz o noszeniu zawieszki na własnym łańcuszku (ucho do 5 mm). |
| `/blogs/poradnik/jak-dbac-o-bizuterie-z-powloka-rodowana` | Jak dbać o biżuterię z powłoką rodowaną | article.json | Zasady pielęgnacji [do potwierdzenia z producentem]. Budują zaufanie i zmniejszają liczbę reklamacji. |
| `/pages/real-madryt-125-lat` | 125 lat Realu Madryt (sezonowo, opcjonalnie) | page.landing.json | Landing kampanii jubileuszowej (1.02–6.03.2027, 125-lecie przypada 6.03.2027). Linkowany tylko z kolekcji Real Madryt i z reklam kierowanych do kibiców Realu. |
| `/cart` | Koszyk | cart.json | Zapas dla szuflady koszyka (np. przy wyłączonym JS). Ten sam układ: pozycje, opcje prezentowe, kasa. |
| `/search` | Wyszukiwarka | search.json | Strona systemowa. Przy 3 produktach ikona jest tylko w szufladzie menu, a podpowiedzi pokazują kluby. |
| `/account` | Moje zamówienia | customer accounts (Shopify) | Nowe konta klientów z kodem jednorazowym: status zamówienia bez hasła. Link w stopce. |
| `/policies/terms-of-service` | Regulamin sklepu | policy (Shopify) | Wymagany regulamin sprzedaży konsumenckiej [treść prawna do przygotowania]. |
| `/policies/privacy-policy` | Polityka prywatności i cookies | policy (Shopify) | RODO i pliki cookie. Link w stopce i w banerze zgody. |
| `/policies/shipping-policy` | Polityka wysyłki | policy (Shopify) | Spójna z /pages/dostawa: te same terminy i warunki gwarancji świątecznej. |
| `/policies/refund-policy` | Polityka zwrotów | policy (Shopify) | Treść zgodna z /pages/zwroty pisaną przez właściciela. Linki w sklepie prowadzą do /pages/zwroty. |
| `/policies/contact-information` | Dane sprzedawcy | policy (Shopify) | Firma, adres, NIP, e-mail, telefon [do uzupełnienia]. |
| `/404` | Nie znaleziono strony | 404.json | Uprzejmy komunikat i sekcja „Wybierz swój klub” z 3 kaflami. Ratuje ruch z nieaktualnych linków reklamowych. |
| `/collections/all` | Przekierowanie | brak (przekierowanie) | Przekierowanie 301 do /collections/wszystkie-zawieszki (Nawigacja → Przekierowania URL). |

## Szablon kolekcji klubu

- Szablon collection.klub.json (przypisany do 3 kolekcji klubowych) służy jako landing z reklam Meta i TikTok oraz dla SEO („zawieszka [klub]”). Pozwala kupić bez wchodzenia na kartę produktu. Do testu A/B: reklama → karta produktu kontra reklama → landing klubu.
- 1. Hero klubowy (sekcja Hero, osobny kadr mobile 4:5, wysokość do 60% ekranu): tło w barwach klubu, eyebrow (krój akcentowy) „Królewscy · klub założony w 1902”, H1 „Real Madryt – oficjalna zawieszka z łańcuszkiem”, jedno zdanie tożsamości („Biel Santiago Bernabéu w jubilerskim wydaniu.”) i odznaka „Oficjalny produkt licencjonowany”. Treści pochodzą z metapól kolekcji (custom.przydomek, custom.rok_zalozenia, custom.haslo_tozsamosci, custom.hero_desktop, custom.hero_mobile, custom.kolor_klubu, custom.produkt_klubu), więc jeden szablon obsługuje 3 kluby.
- 2. Featured product (produkt z metapola custom.produkt_klubu): galeria z miniaturami, tytuł, gwiazdki, „149 zł · łańcuszek w zestawie”, blok przewidywanej dostawy, przycisk „Dodaj do koszyka” oraz Apple Pay i Google Pay, ikony płatności. Przycisk widać na 1.–2. ekranie.
- 3. „Co dostajesz” (Section, 4 ikony): zawieszka z herbem · łańcuszek o splocie linkowym, ok. 51 cm · pudełko prezentowe [DP] · oznaczenie oficjalnej licencji [DP].
- 4. Tożsamość klubu (Media with content): zdjęcie lifestyle w barwach klubu i 2–3 zdania o barwach, stadionie i okrzyku. Real Madryt: biel, Santiago Bernabéu, „¡Hala Madrid!”. FC Barcelona: blaugrana, Spotify Camp Nou, „Més que un club”. Manchester United: Old Trafford, Teatr Marzeń, „Glory Glory Man United”. Bez zawodników.
- 5. Detale wykonania: 3 zdjęcia makro (emalia, ręcznie osadzone cyrkonie, splot linkowy i zapięcie) w karuzeli bez autoplay.
- 6. Opinie (blok Judge.me filtrowany dla produktu klubu), ukryte do pierwszej opinii.
- 7. FAQ (4 pytania): oryginalność i licencja, termin dostawy, łańcuszek i ucho do 5 mm, zwroty (link /pages/zwroty).
- 8. Sezonowy pasek terminu (16.11–16.12): „Zamów do 16.12 – dostawę przed Świętami gwarantujemy [data DP]”.
- 9. „Kibicujesz komuś innemu?”: mała lista 2 pozostałych herbów na samym dole, dla osób kupujących prezent. Nigdy wyżej niż FAQ.
- Ustawienia landingu: bez filtrów, sortowania i licznika produktów (w kolekcji jest 1 produkt), okruszki ukryte na mobile. Meta title: „Zawieszka Real Madryt z łańcuszkiem – oficjalny produkt | Vellano Jubiler”. Unikalny opis kolekcji (ok. 80–120 słów) dla SEO. Parametry UTM zachowane w linkach.
- Sekcja jubileuszu tylko dla Realu Madryt (1.02–6.03.2027): baner „125 lat Królewskich” renderuje się wtedy, gdy metapole kolekcji custom.baner_sezonowy jest wypełnione. Wymaga warunku w Custom Liquid, bo szablon jest wspólny dla 3 klubów.
- Szablon collection.json (Wszystkie zawieszki): krótki nagłówek „Wybierz swój klub” z opisem w jednym zdaniu i siatka 1 kolumny na mobile z dużymi kartami (przy 3 produktach 2 kolumny dają nierówny układ). Karta: przydomek, nazwa, cena, gwiazdki. Pod siatką pasek zaufania i FAQ.
- Szablon collection.okazja.json (strony prezentowe): hero okazji („Prezent dla kibica, który ma już koszulkę”) i sekcja „Nie musisz znać się na piłce – wybierz herb” z 3 kartami opisanymi po ludzku (np. „Dla fana Realu – biel i ¡Hala Madrid!”). Dalej usługi prezentowe (pudełko [DP], bilecik w koszyku, paczka bez ceny [DP]), terminy sezonowe, FAQ dla kupującego prezent (Czy w paczce będzie cena? Co, jeśli herb nie trafi? → Zwroty) i link do poradnika. Każdy landing okazji ma własny tekst, żeby nie powielać treści.

## Karta produktu (mobile)

- Cel: na ekranie 375–390 px nad linią zgięcia widać zdjęcie, odznakę, tytuł, gwiazdki, cenę, termin i przycisk zakupu. Dlatego galeria na mobile ma format 1:1, a nie 4:5.
- 1. Galeria (media w Product information): przesuwana, 1:1, zoom po dotknięciu, miniatury pod zdjęciem zamiast samych kropek (Baymard). 6–8 mediów w kolejności: packshot na #F7F5F1 → na szyi (skala) → w dłoni (skala) → makro emalii i cyrkonii → łańcuszek i zapięcie → pudełko i rozpakowanie [DP] → oznaczenie licencji [DP] → wideo 6–10 s (obrót w świetle, bez dźwięku). Teksty alternatywne po polsku.
- 2. Odznaka w kroju akcentowym, ciemny szampan #8A6F45, obrys 1 px: „Oficjalny produkt licencjonowany” (metapole custom.oznaczenie_licencji). Kliknięcie prowadzi do /pages/oficjalna-licencja.
- 3. Tytuł H1 w EB Garamond: „Oficjalna zawieszka Real Madryt z łańcuszkiem”, pod nim przydomek „Dla Królewskich”.
- 4. Gwiazdki i liczba opinii (Judge.me) z kotwicą do sekcji opinii. Przy braku opinii blok jest ukryty; nigdy nie pokazujemy „0 opinii”.
- 5. Cena „149 zł” (20 px, twarda spacja) z dopiskiem „łańcuszek w zestawie · cena zawiera VAT”. Przy każdej obniżce obowiązkowo „Najniższa cena z 30 dni przed obniżką: …” (Omnibus). Bez sztucznych cen przekreślonych.
- 6. Blok terminu (Custom Liquid z JS, dane z metaobiektu terminy_sezonowe): „Zamów dziś – wyślemy w 2–3 dni robocze. Przewidywana dostawa: wt. 13.10 – śr. 14.10” (przykład dla zamówienia z czwartku 8.10.2026; liczone bez weekendów i świąt w PL, plus 1 dzień przewoźnika [DP]). Pod spodem: „Darmowa dostawa do Paczkomatu InPost lub kurierem [DP]”. W sezonie zielona linia #2F6B4F: „Zamów do 16 grudnia – dostawę przed Świętami gwarantujemy [data DP]”. Bez liczników.
- 7. Wariant: jeden rozmiar, więc wybór wariantu jest ukryty. Wybór ilości też ukryty (ilość zmienia się w koszyku).
- 8. Przycisk „Dodaj do koszyka”: pełna szerokość, 52 px, #141414, wersaliki; otwiera szufladę koszyka. Pod nim przyciski ekspresowe Apple Pay i Google Pay (dynamic checkout). Wizualnie dominuje jeden CTA.
- 9. Ikony płatności (BLIK, Przelewy24, Apple Pay, Google Pay, Visa, Mastercard [DP]): małe, w skali szarości, generowane z shop.enabled_payment_types, z dopiskiem „Bezpieczna płatność”.
- 10. Linia prezentowa: „Pudełko prezentowe w zestawie [DP] · bilecik z dedykacją dodasz w koszyku” i link „Jak pakujemy” → /pages/opakowanie-prezentowe.
- 11. „Co dostajesz” (lista z ikonami, metapole custom.co_w_zestawie): zawieszka z herbem · łańcuszek o splocie linkowym, ok. 51 cm (20 cali) · pudełko prezentowe [DP] · oznaczenie oficjalnej licencji [DP].
- 12. Akordeon „O produkcie”, domyślnie otwarty. Układ wzorowany na Cernucci, treść własna: (a) licencja, (b) wykonanie, (c) idea, (d) okrzyk. Przykład dla Realu Madryt. (a) „Oficjalna zawieszka Realu Madryt, przygotowana na licencji klubu [do potwierdzenia: pełna nazwa licencjodawcy]. Herb Królewskich w formie, którą możesz nosić na co dzień, nie tylko w dniu meczu.” (b) „Herb odwzorowaliśmy emalią i ręcznie osadzanymi cyrkoniami na mosiężnej bazie z powłoką rodowaną, która nadaje zawieszce jasny, chłodny połysk.” (c) „Koszulkę zakładasz na mecz. Zawieszkę – kiedy chcesz: dyskretnie pod koszulą albo na wierzchu, gdy gra Real. To spokojniejszy, bardziej osobisty sposób, by pokazać, że biel Realu to Twój kolor.” (d) „¡Hala Madrid!”. Zakończenia dla pozostałych: FC Barcelona – „Més que un club.”, Manchester United – „Glory Glory Man United.”
- 13. Akordeon „Specyfikacja” (z metapól, w punktach). Metal: mosiądz. Powłoka: rodowana. Kamienie: cyrkonie osadzane ręcznie, herb z emalią. Łańcuszek: splot linkowy (rope), 20 cali (ok. 51 cm), w zestawie. Rozmiar: jeden. Wymiary zawieszki: [do uzupełnienia]. Waga: [do uzupełnienia]. UWAGA: ucho zawieszki mieści łańcuszek o grubości do 5 mm, więc zawieszkę założysz też na własny łańcuszek.
- 14. Akordeon „Dostawa i terminy świąteczne” (z metaobiektu): metody dostawy, czas wysyłki, tabela dat (Mikołajki – zamów do 1.12 [DP]; Święta – do 16.12 [DP]) i link do /pages/dostawa.
- 15. Akordeon „Zwroty”: jedno zdanie i link „Zasady zwrotów” → /pages/zwroty, bez liczby dni.
- 16. Akordeon „Pielęgnacja” (metapole custom.pielegnacja, [do potwierdzenia z producentem]).
- 17. Akordeon „Oficjalna licencja”: co oznacza licencja, gdzie jest oznaczenie [DP], link do strony licencji.
- 18. Blok „Bezpieczeństwo produktu” (statyczny blok ujawnień w Horizon, metapola shopify.disclosure i custom.producent_gpsr): producent i podmiot odpowiedzialny w UE [do uzupełnienia], ostrzeżenie o drobnych elementach [do potwierdzenia].
- 19. Sekcja opinii (Judge.me): średnia ocena, zdjęcia klientów na górze, filtr „ze zdjęciami”, przycisk „Napisz opinię”. Prośba o opinię wysyłana e-mailem 7–10 dni po doręczeniu, żeby jak najszybciej zebrać pierwsze 5 opinii.
- 20. FAQ produktu (metaobiekty z custom.faq, 3–4 pytania, np. o noszeniu na własnym łańcuszku).
- 21. „Kupujesz dla kibica innej drużyny?”: 2 pozostałe zawieszki (custom.inne_kluby) na samym dole strony.
- 22. Przyklejony pasek zakupu na mobile, który pojawia się po przewinięciu poza główny przycisk: miniatura, „149 zł”, „Dodaj do koszyka”. Horizon nie ma tego natywnie, więc potrzebny jest lekki Custom Liquid z JS albo sprawdzona aplikacja. Pasek nie może zasłaniać banera cookies.
- SEO karty: meta title „Zawieszka Real Madryt z łańcuszkiem – oficjalny produkt | Vellano Jubiler”, meta description z ceną i terminem wysyłki, dane strukturalne Product z oceną (Judge.me).

## Koszyk wysuwany

- Typ koszyka: szuflada, otwierana automatycznie po dodaniu produktu (ustawienie Horizon). Na mobile 100% szerokości, na desktopie ok. 420 px. Tło #FFFFFF, nagłówek „Twój koszyk (1)” w EB Garamond, przycisk zamknięcia 44×44 px.
- Kolejność elementów: 1) linia obietnic „Darmowa dostawa [DP] · wysyłka w 2–3 dni robocze”, w sezonie na zielono: „Zdążysz przed Świętami – zamów do 16.12 [DP]”; 2) pozycje; 3) opcje prezentowe; 4) najwyżej jedna rekomendacja (warunkowo); 5) przyklejone podsumowanie z przyciskiem.
- Pozycja w koszyku: miniatura 1:1 (80 px), nazwa, „Łańcuszek w zestawie”, cena, przyciski ilości −/+ (44 px), link tekstowy „Usuń”.
- Przycisk „Przejdź do kasy” (pełna szerokość, 52 px, #141414) w przyklejonej stopce szuflady, zawsze widoczny bez przewijania; to odpowiednik „kasy na górze”. Nad nim „Razem: 149 zł · dostawa 0 zł [DP]”, pod nim Apple Pay i Google Pay oraz rząd ikon BLIK, Przelewy24 i kart [DP].
- Opcje prezentowe: checkbox „To prezent – nie dołączaj dowodu zakupu z ceną [DP]” (atrybut koszyka, przez własny snippet albo aplikację) oraz pole „Bilecik z dedykacją (opcjonalnie, do 150 znaków)” (notatka do zamówienia, ustawienie Horizon). Oba trafiają do zamówienia i na listę pakowania.
- Rekomendacja: najwyżej jedna i tylko trafna. Przy obecnym katalogu (3 herby) NIE pokazujemy automatycznie innego klubu, bo fan Realu nie chce widzieć Barçy przy kasie. Gdy pojawi się produkt komplementarny (np. ściereczka do biżuterii albo torebka prezentowa [do decyzji]), ustawiamy go ręcznie jako „complementary” w aplikacji Shopify Search & Discovery.
- Kod rabatowy: pole ukryte w szufladzie (ustawienie Horizon), żeby nie wysyłać klienta na poszukiwanie kuponów. Pole jest dostępne w checkoucie.
- Pusty koszyk: „Twój koszyk jest pusty”, 3 kafle „Wybierz swój klub” i link „Prezent dla kibica”.
- Krótkie teksty uspokajające pod przyciskiem: link „Zasady zwrotów” (/pages/zwroty) i „Pytania? Napisz do nas” (/pages/kontakt).
- Bez paska postępu darmowej dostawy, bo dostawa jest darmowa od pierwszej sztuki [DP]. Jeśli właściciel wprowadzi próg, Horizon nie ma takiego paska natywnie i potrzebny będzie kod albo aplikacja.
- Wydajność: szuflada otwiera się natychmiast, a rekomendacje i skrypty aplikacji ładują się dopiero po jej otwarciu.

## Checkout i strona Dziękujemy

- Plan Basic: jednostronicowy checkout Shopify. Rozszerzenia UI w krokach informacje, dostawa i płatność są dostępne tylko w planie Plus. Wygląd ustawiamy w edytorze checkoutu (logo, kolory, czcionki w zakresie dostępnym dla planu); pełne Checkout Branding API też jest tylko w Plus.
- Branding: logo SVG lub PNG na białym tle, akcent i przyciski #141414, tło #FFFFFF, pola z obrysem #E6E2DA, minimalne zaokrąglenia. Checkout ma wyglądać jak dalszy ciąg salonu.
- Zakupy bez konta domyślnie; nowe konta klientów z kodem jednorazowym. Zgoda marketingowa domyślnie niezaznaczona (RODO).
- Pola: telefon wymagany (powiadomienia SMS InPost), firma i NIP opcjonalnie (faktura przez aplikację fakturującą [do decyzji]), druga linia adresu opcjonalna. Język polski, waluta PLN, ceny z VAT.
- Metody dostawy: „Paczkomat InPost – 0 zł [DP]” i „Kurier – 0 zł [DP]”, w nazwie metody „wysyłka w 2–3 dni robocze”. Wybór Paczkomatu na Basic: większość aplikacji InPost wymaga Carrier Calculated Shipping, którego nie ma w planie Basic. Opcje: (a) aplikacja z wyborem punktu po płatności na stronie Dziękujemy (np. InPost Paczkomaty Orlen Paczka od Codie), (b) zapytanie do supportu Shopify o CCS jako dodatek, (c) wybór punktu w koszyku, jeśli aplikacja to oferuje. Przetestuj przed sezonem.
- Płatności: BLIK, Przelewy24, Apple Pay, Google Pay, karta [DP]. Sprawdź w Ustawienia → Płatności, czy Shopify Payments oferuje BLIK i Przelewy24 dla Twojego konta w Polsce. Jeśli nie, użyj oficjalnej aplikacji Przelewy24 z BLIK wysoko na liście.
- Przycisk końcowy Shopify „Zapłać teraz” jasno informuje o obowiązku zapłaty. W stopce checkoutu są linki do Regulaminu, Polityki prywatności, Polityki wysyłki i Zwrotów.
- Strona Dziękujemy (rozszerzenia Thank you i Order status działają na Basic): 1) potwierdzenie i „co dalej”: „Twoja zawieszka wyruszy w ciągu 2–3 dni roboczych. Numer przesyłki wyślemy e-mailem i SMS-em.”; 2) ankieta „Skąd o nas wiesz?” z odpowiedziami: Instagram, TikTok, Facebook, Google, Polecenie znajomego, Inne (aplikacja, np. AfterCart lub OrderSurvey; sprawdź limity darmowych planów); 3) opcjonalnie pytanie „Dla kogo kupujesz?” (Dla siebie / Na prezent); 4) jeśli wybór Paczkomatu odbywa się po płatności, ten blok jest na pierwszym miejscu.
- Bez agresywnej sprzedaży po zakupie, bo premium oznacza spokój. Co najwyżej link „Obserwuj nas na Instagramie”.
- Powiadomienia e-mail i SMS po polsku, w stylu marki: potwierdzenie zamówienia (z sekcją „co dalej” i terminem), wysyłka (link do śledzenia), doręczenie, prośba o opinię 7–10 dni po doręczeniu (Judge.me).
- Lista pakowania: przy atrybucie „To prezent” szablon bez cen [DP] oraz wydrukowany bilecik z treścią dedykacji.
- Analityka: ankieta, parametry UTM i zdarzenia klienta (Meta, TikTok). Porównujemy deklaracje klientów z atrybucją reklam.

## Tokeny designu

- Zasada palety 80/15/5: 80% biel i kość słoniowa, 15% czerń i grafit (tekst, przyciski, stopka), najwyżej 5% akcentu szampańskiego. Kolory klubów pojawiają się tylko na zdjęciach, kaflach klubów i landingach klubowych.
- --color-bg: #FFFFFF. Tło główne: czysta witryna jubilerska, w której zdjęcia „oddychają”; zgodne z jasnym tłem packshotów.
- --color-bg-ivory: #F7F5F1. Tło sekcji naprzemiennych, kart i szuflad. Daje ciepło salonu zamiast sterylnej bieli i oddziela sekcje bez linii.
- --color-text: #141414. Tekst i przycisk główny. Prawie czerń (kontrast ok. 18:1 na białym), miększa niż #000, spójna z czarnym logo.
- --color-text-muted: #5E5E5E. Opisy pomocnicze i krótkie teksty; kontrast ok. 6,5:1 (WCAG AA).
- --color-graphite: #2B2B2B. Stopka i ciemne sekcje; kontrast z białym ok. 14:1, daje wieczorowy, elegancki ton.
- --color-line: #E6E2DA. Linie 1 px, obramowania pól, separatory; ciepła szarość zgodna z kością słoniową.
- --color-accent: #B89B6A (szampan). Tylko elementy dekoracyjne: cienkie linie, ikony paska zaufania, gwiazdki ocen, obrys odznaki. Kontrast ok. 2,6:1, więc nigdy nie służy do tekstu.
- --color-accent-text: #8A6F45 (ciemny szampan). Tekst odznaki „Oficjalny produkt licencjonowany” i eyebrow; kontrast ok. 4,7:1 (AA).
- --color-success: #2F6B4F. Komunikaty terminowe („Zdążysz przed Świętami”) i potwierdzenia; spokojna zieleń, kontrast ok. 6,3:1.
- --color-error: #A1302B. Błędy formularzy; stonowana czerwień, która nie kojarzy się z wyprzedażą.
- --color-overlay: rgba(20,20,20,0.45). Przyciemnienie tła pod szufladą koszyka i menu.
- Kolory klubów (tylko kafle i landingi, do weryfikacji z brandbookiem licencjodawcy): Real Madryt – biel #FFFFFF z niebieskim #00529F; FC Barcelona – #A50044 i #004D98; Manchester United – #DA291C z czernią #141414.
- Schematy kolorów Horizon: S1 „Biel” (tło #FFFFFF, tekst #141414, przycisk #141414 z tekstem #FFFFFF, przycisk drugorzędny z obrysem #141414); S2 „Kość słoniowa” (tło #F7F5F1, reszta jak S1); S3 „Grafit” (tło #2B2B2B, tekst #F7F5F1, przycisk #FFFFFF z tekstem #141414); S4 „Pasek” (tło #141414, tekst #F7F5F1); S5 „Na zdjęciu” (tekst #FFFFFF, gradient 0→40% czerni tylko pod tekstem).
- Odstępy w skali 4 px: 4, 8, 12, 16, 24, 32, 48, 64, 96. Margines boczny 20 px na mobile i 48 px na desktopie; pionowy odstęp sekcji 48 px na mobile i 96 px na desktopie; odstęp między kartami 12 px i 24 px; akapit najwyżej 34em szerokości.
- Zaokrąglenia: przyciski 2 px (zamiast domyślnych 100 px w kształcie pigułki w Horizon), pola formularzy 2 px (domyślnie 8 px), karty i zdjęcia 0, odznaki 2 px, popovery i szuflady 0. Ostre krawędzie przypominają gabloty salonu jubilerskiego.
- Przyciski. Główny: tło #141414, tekst #FFFFFF, wysokość 52 px na mobile (cel dotyku co najmniej 44 px), pełna szerokość na karcie produktu, krój Inter 500, 14 px, wersaliki z odstępem 0,08em, hover #2B2B2B. Drugorzędny: przezroczysty, obrys 1 px #141414, hover z tłem #F7F5F1. Tekstowy: podkreślenie 1 px z odsunięciem 3 px. Jeden przycisk główny na ekran.
- Obramowania i cienie: linie 1 px #E6E2DA; karty bez cieni (płasko, jak w galerii). Jedyny cień ma szuflada: 0 0 24px rgba(0,0,0,0.08).
- Ikony: liniowe, grubość 1,25 px, rozmiar 20–24 px, kolor #141414, a w pasku zaufania szampan. Bez ikon wypełnionych i bez emoji.
- Ruch: przejścia 200–250 ms ease-out, bez sprężynowania; żadna karuzela nie przewija się sama; respektujemy prefers-reduced-motion.
- Zdjęcia: packshot 1:1 na #F7F5F1 lub #FFFFFF z tym samym światłem i kątem dla 3 herbów; lifestyle 4:5 w świetle dziennym; makro emalii i cyrkonii; przy każdym produkcie ujęcie w skali (na szyi, w dłoni).
- Focus: obrys 2 px #141414 z odsunięciem 2 px, czytelny przy nawigacji klawiaturą.

## Typografia

- Krój nagłówków: EB Garamond z biblioteki fontów Shopify (uchwyty ebgaramond_n4 do ebgaramond_n8 oraz kursywy). To klasyczny Garamond najbliższy logo VELLANO i na telefonie czyta się lepiej niż Cormorant, którego cienkie kreski znikają w małych rozmiarach.
- Krój tekstu: Inter (inter_n4, inter_n5). Neutralny, bardzo czytelny bezszeryfowy krój na małych ekranach, z pełnym zestawem polskich znaków.
- Mapowanie 4 ról typograficznych Horizon. Heading (H1–H3): EB Garamond 500. Subheading (H4–H6): Inter 500. Body: Inter 400. Accent: EB Garamond 500 w wersalikach z rozstrzeleniem 0,18em, nawiązujący do rozstrzelonego „J U B I L E R” z logo (eyebrow, odznaka licencji, nazwy klubów na kaflach).
- Rozmiary mobile / desktop: H1 32/48 px (interlinia 1,1); H2 26/36 px (1,15); H3 20/26 px (1,2); tekst 16/16 px (1,6), bo 16 px zapobiega automatycznemu powiększaniu pól na iOS; drobne teksty 13–14 px; eyebrow 12 px w wersalikach z odstępem 0,18em; cena 20 px Inter 500 z cyframi tabelarycznymi. Domyślne H1 w Horizon to 72 px, więc trzeba je zmniejszyć.
- Najwyżej 2 rodziny i 4 pliki fontów (EB Garamond 500, Inter 400 i 500, opcjonalnie kursywa EB Garamond 400 do cytatów), żeby utrzymać szybkie LCP na 4G.
- Alternatywy z biblioteki Shopify: Cormorant (cormorant_n3–n7) tylko do bardzo dużych tytułów w hero, od 40 px; Marcellus (marcellus_n4), czyli rzymskie kapitały, jeśli eyebrow ma mocniej nawiązywać do logo; Garamond (garamond_n4/n7), Cardo, Gilda Display. Nie wybieraj krojów wycofanych (np. Monotype Sabon, ITC Galliard, Laurentian), które Shopify i tak zastępuje EB Garamond.
- Polskie znaki: pliki z biblioteki Shopify zawierają zakres Latin Extended-A, jeśli krój go obsługuje. Przed publikacją sprawdź zdanie „Zażółć gęślą jaźń” w każdym kroju i grubości: w nagłówkach, przyciskach, pasku i koszyku.
- Logo zawsze jako plik SVG, nigdy składane fontem. Szerokość 120–132 px w nagłówku na mobile i 170–190 px na desktopie; wersja biała na grafitowej stopce.
- Zasady składu: nagłówki zdaniowe, wersaliki tylko w eyebrow i przyciskach. Wykrzyknik wyłącznie w okrzyku klubu. Twarda spacja w „149 zł”, „ok. 51 cm”, „2–3 dni”; półpauza w zakresach; polskie cudzysłowy „ ”. Poprawne zapisy: „Més que un club”, „¡Hala Madrid!”, „Santiago Bernabéu”.
- Fallback: 'EB Garamond', Georgia, 'Times New Roman', serif oraz Inter, -apple-system, 'Segoe UI', Roboto, Arial, sans-serif; font-display: swap.
- Checkout: w edytorze checkoutu ustaw najbliższe dostępne kroje (szeryfowe nagłówki i bezszeryfowy tekst), jeśli plan na to pozwala.

## Notatki techniczne Horizon

- NOTES, czyli założenia DO POTWIERDZENIA, oznaczone w całym dokumencie jako [DP]: darmowa dostawa (Paczkomaty InPost i kurier); pudełko prezentowe w każdym zamówieniu; daty graniczne 1.12 (Mikołajki) i 16.12.2026 (Wigilia 24.12 to czwartek i dzień wolny); płatności BLIK, Przelewy24, Apple Pay, Google Pay i karta; certyfikat lub oznaczenie licencji w opakowaniu; paczka bez ceny dla prezentów; dane GPSR producenta; nazwy licencjodawców; wymiary i waga; zasady pielęgnacji; termin InPost na 2026; dane firmy i kontaktowe. Potwierdzone przez właściciela: wysyłka w 2–3 dni robocze i gwarancja dostawy przed Świętami (zakres gwarancji do opisania na stronie Dostawa).
- Architektura: Horizon opiera się na theme blocks, czyli blokach, które można zagnieżdżać w grupach i używać w różnych sekcjach. Szablon JSON mieści najwyżej 25 sekcji, a sekcja najwyżej 50 bloków. Menu ma maksymalnie 3 poziomy; my używamy 2.
- Szablony alternatywne do utworzenia: collection.klub.json, collection.okazja.json, page.dostawa.json, page.faq.json, page.licencja.json, page.wykonanie.json, page.prezent.json, page.o-marce.json, page.opinie.json, page.landing.json. Przypisujesz je w panelu: kolekcja lub strona → Szablon motywu.
- Dane zamiast tekstu wpisanego na sztywno: metapola produktu i kolekcji podpinasz w edytorze jako dynamiczne źródła. Metaobiekty widoczne na storefroncie („klub”, „terminy_sezonowe”, „faq”, „podmiot_gpsr”) są dostępne jako źródła w każdym ustawieniu motywu, więc jedna zmiana daty aktualizuje pasek, kartę produktu, koszyk i FAQ.
- Nagłówek: według dokumentacji Horizon na desktopie (od 750 px) działa mega menu, a na mobile szuflada. Dla pozycji Pomoc i O marce ustaw styl menu „tekst”; mega menu z obrazami tylko dla „Wybierz swój klub”. Nagłówek przyklejony i nieprzezroczysty. Użytkownicy zgłaszali, że po aktualizacji mega menu zamykało się zbyt szybko, więc testuj je po każdej aktualizacji.
- Pasek ogłoszeń: sekcja Header announcements. Pomoc Shopify mówi o maksymalnie 12 komunikatach; my używamy 1–3. Jeśli tekst jest przycięty, pomaga line-height 1.5.
- Koszyk: Ustawienia motywu → Koszyk: typ „szuflada”, automatyczne otwieranie, notatka do zamówienia włączona, pole kodu rabatowego w szufladzie wyłączone, przyciski ekspresowe włączone. Horizon nie ma natywnego paska darmowej dostawy ani sterowanych rekomendacji w szufladzie. W razie potrzeby pomoże własny kod (Horizon używa elementu <cart-drawer-component>) albo aplikacja.
- Karta produktu: sekcja Product information z blokami: tytuł, cena, wybór wariantu, przyciski zakupu z szybką płatnością, opis, akordeon, tekst z dynamicznymi źródłami, Custom Liquid. Ujawnienia bezpieczeństwa (disclosures) Horizon wyświetla jako statyczny blok na dole Product information. Przyklejonego paska zakupu nie ma natywnie.
- Opinie: Judge.me w planie darmowym. Włącz app embed i dodaj blok gwiazdek w kartach produktów Horizon. Wyłącz domyślne gwiazdki motywu, żeby się nie dublowały.
- Ustawienia motywu: zaokrąglenie przycisków z domyślnych 100 px na 2 px, obrys przycisku głównego 0, drugorzędnego 1 px, krój przycisków „body” w wersalikach; zaokrąglenie pól 2 px, popoverów 0, odznak 2 px; typografia w 4 rolach (body, subheading, heading, accent).
- Daty: filtr date z 'now' pokazuje czas ostatniego renderowania strony (cache). Logikę terminów (pasek, przewidywana dostawa) licz w JS po stronie przeglądarki, w strefie Europe/Warsaw, z listą polskich świąt (m.in. 11.11, 24–26.12, 1.01, 6.01).
- Ikony płatności na karcie produktu: Custom Liquid z shop.enabled_payment_types i filtrem payment_type_svg_tag. Jeśli w zestawie nie ma ikony BLIK, dodaj własne SVG.
- Teksty systemowe: Motyw → Edytuj domyślną treść (PL): „Dodaj do koszyka”, „Przejdź do kasy”, „Twój koszyk”, „Chwilowo niedostępna” zamiast „Wyprzedane”. Usuń „Powered by Shopify”.
- Wydajność: obraz hero na mobile do 200 KB (WebP przez CDN Shopify), wideo do 2 MB bez dźwięku, najwyżej 3 aplikacje ładujące skrypty na karcie produktu, fonty w 2 rodzinach i 4 plikach. Cel: LCP poniżej 2,5 s na 4G.
- Ruch z social: testuj w przeglądarkach wbudowanych Instagrama i TikToka. Apple Pay może tam nie działać, więc BLIK i karta muszą być pod ręką. Piksele (zdarzenia klienta) i synchronizację katalogu obsłużą aplikacje Facebook & Instagram oraz TikTok. Opcjonalny popup newslettera: mały dolny panel (do 30% ekranu), po 8–15 s albo po przewinięciu połowy strony, nie przy pierwszej odsłonie karty produktu z reklamy, najwyżej raz na 7 dni.
- Rynki: tylko Polska, PLN, ceny z VAT. Baner zgody na cookies Shopify po polsku, kompaktowy na mobile.
- SEO: handle bez polskich znaków (jak w sitemapie) i przekierowanie /collections/all → /collections/wszystkie-zawieszki. Każdy landing okazji ma unikalny opis. Po sezonie landingów nie usuwamy, tylko wyjmujemy je z menu (Dzień Ojca 23.06 i Dzień Chłopaka 30.09 dodasz w 2027 według tego samego wzoru).
- Proces: pracuj na duplikacie motywu (edycja, podgląd, publikacja). Po każdej aktualizacji Horizon sprawdź własny kod: przyklejony pasek zakupu, terminy, opcje prezentowe.
- Licencje: sprawdź wytyczne licencjodawców dotyczące herbów, nazw, okrzyków i kolorów w reklamach, na kaflach i w meta tagach. Mogą wymagać konkretnej formułki o licencji.
- Źródła: shopify.dev/docs/storefronts/themes/architecture/settings/fonts; shopify.dev/docs/storefronts/themes/architecture/blocks; shopify.dev/docs/storefronts/themes/architecture/settings/dynamic-sources; shopify.dev/docs/storefronts/themes/architecture/templates/json-templates; shopify.dev/docs/storefronts/themes/architecture/templates/alternate-templates; shopify.dev/docs/api/liquid/objects/linklist; shopify.dev/docs/api/liquid/filters/date; shopify.dev/docs/apps/build/checkout/technologies; shopify.dev/docs/apps/build/checkout/thank-you-order-status; shopify.dev/docs/apps/build/product-merchandising/product-disclosures; shopify.dev/docs/storefronts/themes/product-merchandising/recommendations; shopify.dev/docs/api/storefront-events-and-actions/actions/configure; shopify.dev/docs/apps/build/metafields/conditional-metafield-definitions; shopify.dev/docs/api/admin-graphql/latest/objects/checkoutbranding; help.shopify.com/en/manual/online-store/themes/theme-structure/theme-features; mintlify.com/Shopify/horizon (customization/settings, customization/typography, features/navigation, components/sections/overview, components/blocks/product-info); community.shopify.com/t/sticky-add-to-cart-horizon-theme/590833; community.shopify.com/t/horizon-theme-megamenu-to-normal-dropdown/415671; judge.me/help/en/articles/8263435-adding-the-star-rating-badge-on-collection-pages-2-0-themes; apps.shopify.com/paczkomaty-inpost; apps.shopify.com/inpost-paczkomaty-1; apps.shopify.com/inpost-4; apps.shopify.com/aftercart-post-purchase-survey; apps.shopify.com/ordersurvey; przelewy24.pl/en/news/shopify-news-przelewy24-blik-integration-with-cart-highlighting; cs-cart.com/blog/shopify-payments-supported-countries; spidersweb.pl/2025/12/inpost-gwarancja-dostawy-przed-swietami-do-kiedy-wyslac-paczke.html; android.com.pl/tech/999386-inpost-gwarancja-paczki-swieta-wigilia; nssmag.com/en/sports/27213/cernucci-pendants-juventus-milan.

## Checklista premium

- Logo w SVG, ostre, wyśrodkowane na mobile, z polem ochronnym; favicon z monogramem V; obraz udostępniania (OG) z logo.
- Jedna spójna sesja zdjęciowa dla 3 herbów (to samo tło, światło i kąt); co najmniej 6 zdjęć i krótkie wideo na produkt.
- Przy każdym produkcie zdjęcia w skali (na szyi, w dłoni), bo bez nich klient nie oceni wielkości.
- Makro emalii i ręcznie osadzonych cyrkonii jako dowód jakości jubilerskiej.
- Paleta 80/15/5; kolory klubów tylko na kaflach, zdjęciach i landingach klubowych.
- Szeryfowe nagłówki zgodne z logo i Inter 16 px w tekście; polskie znaki sprawdzone w każdej grubości.
- Prostokątne czarne przyciski z zaokrągleniem 2 px; jeden główny przycisk na ekran.
- Dużo bieli: sekcje 48/96 px, akapity do 34em szerokości.
- Ton jak w salonie jubilerskim (Apart, W.KRUK): spokojny, ciepły, konkretny, w formie „Ty”; bez krzyku promocyjnego i bez emoji. Emocja kibica tylko w okrzykach klubów.
- Każda obietnica ma stronę z wyjaśnieniem: licencja, dostawa i gwarancja świąteczna, zwroty, pakowanie.
- Konkretna data dostawy na karcie produktu i w koszyku, identyczna jak w pasku, na stronie Dostawa i w FAQ.
- Usługi prezentowe jak u W.KRUK i Ani Kruk: pudełko [DP], bilecik z dedykacją, paczka bez ceny [DP], widoczne na zdjęciu rozpakowania.
- „Łańcuszek w zestawie” przy cenie, bo u jubilerów męskie wisiorki zwykle są sprzedawane bez łańcuszka i to nasza przewaga.
- Informacja, że ucho mieści łańcuszek do 5 mm, dla osób z własnym łańcuszkiem.
- Opinie z prawdziwymi zdjęciami i automatyczne prośby o opinię od pierwszego zamówienia; nigdzie nie widać „0 opinii”.
- Przed startem gotowe wszystkie strony informacyjne: Dostawa, Zwroty (treść właściciela), FAQ, Kontakt, Regulamin, Polityka prywatności, Dane sprzedawcy (firma, adres, NIP [do uzupełnienia]).
- Realny kontakt: e-mail w domenie marki, godziny pracy i czas odpowiedzi [do uzupełnienia], wyraźnie zaznaczona polska obsługa.
- Własna domena .pl [do potwierdzenia] i e-maile transakcyjne wysyłane z tej domeny.
- Spolszczone wszystkie teksty systemowe: koszyk, checkout, e-maile, komunikaty błędów, strona 404, pusty koszyk.
- Poprawne formatowanie: „149 zł” z twardą spacją i bez „,00”, półpauzy w zakresach, zapisy „Més que un club”, „¡Hala Madrid!”, „Bernabéu”.
- Szybkość: LCP poniżej 2,5 s i CLS poniżej 0,1 na 4G; testy na iPhonie SE i małym Androidzie.
- Dostępność: kontrast AA, widoczny focus, teksty alternatywne, cele dotyku 44 px, tekst 16 px.
- Bez „Powered by Shopify”, odznak aplikacji i tanich „tarcz bezpieczeństwa”.
- Rozpakowanie jako część marki: pudełko, karta z podziękowaniem, karta pielęgnacji, oznaczenie licencji [DP], w kolorach strony.
- Informacje GPSR (producent lub podmiot odpowiedzialny w UE, ostrzeżenia) na każdej karcie produktu.
- Uczciwe ceny: bez sztucznych przekreśleń, a przy promocji najniższa cena z 30 dni (Omnibus).
- Sezonowe landingi gotowe co najmniej 3 tygodnie przed okazją (Mikołajki od 16.11, Święta od 1.11).
- Strona 404 i pusty koszyk z sekcją „Wybierz swój klub”.
- Popup, jeśli w ogóle: mały, po 8–15 s, łatwy do zamknięcia, najwyżej raz na 7 dni.
- Testy w przeglądarkach wbudowanych Instagrama i TikToka: BLIK i karta działają bez logowania, szuflada koszyka otwiera się poprawnie.

## Antywzorce

- Liczniki odliczające czas, „ostatnie sztuki”, „X osób ogląda teraz”, wyskakujące powiadomienia „ktoś właśnie kupił”. To fałszywa presja, zakazana w briefie i ryzykowna wobec UOKiK.
- Sztuczne ceny przekreślone, stałe „-50%”, hasła typu „Black Friday -70%” i czerwone banery wyprzedaży.
- Pełnoekranowy popup zaraz po wejściu na mobile, koło fortuny, prośby o powiadomienia push.
- Cross-sell rywala w koszyku (Barça dla kibica Realu) i automatyczne „Może Ci się spodobać” z innym klubem przy przycisku zakupu.
- Nazwy metali szlachetnych i ich przymiotniki (także jako nazwy kolorów), oznaczenia cechy probierczej i liczby z cech. Produkt to mosiądz z powłoką rodowaną; kolor opisujemy jako „jasny, chłodny połysk”.
- Superlatywy („naj…”), twierdzenia o byciu jedynym oficjalnym sprzedawcą, „luksus” na każdym kroku, „hipoalergiczna” bez badań.
- Nazwiska i wizerunki zawodników w treściach, grafikach i reklamach; grafiki AI stadionów i herbów.
- Wymyślona historia marki, rok założenia czy „rodzinna pracownia”. Piszemy tylko fakty, a braki oznaczamy [do potwierdzenia: …].
- Kopiowanie zdań z opisów Cernucci. Wzorujemy się na układzie opisu, nie na tekście.
- Informacje o modelu logistycznym lub zewnętrznym dostawcy, zdjęcia z hurtowni, znaki wodne.
- Kolory klubowe w interfejsie (przyciski, tła sekcji, pasek ogłoszeń), przez które strona zaczyna wyglądać jak stragan z gadżetami.
- Emoji, wersaliki w akapitach, kilka wykrzykników z rzędu, slang.
- Slider w hero z autoplay, pasek marquee z promocjami, karuzele przewijające się same.
- Kilka konkurujących CTA (Kup teraz, Dodaj, Lista życzeń, Porównaj) i wyeksponowany wybór ilości.
- Mgliste „szybka wysyłka” zamiast dat oraz obietnice typu „dostawa jutro”, których nie da się dotrzymać.
- Podawanie liczby dni na zwrot poza stroną Zwroty, której treść należy do właściciela.
- Widżet „0 opinii”, fałszywe lub kupione opinie, opinie bez weryfikacji zakupu.
- Bąbel czatu i baner cookies zasłaniające przycisk zakupu na mobile.
- Pole kodu rabatowego wyeksponowane w koszyku, które wysyła klienta na poszukiwanie kuponów.
- Tanie „tarcze 100% bezpieczeństwa”, odznaki aplikacji, „Powered by Shopify”.
- Cienkie, powielone landingi okazji z tym samym tekstem na kilku stronach.
- Przezroczysty nagłówek na zdjęciu (nieczytelne logo) i menu mobilne z więcej niż 4 pozycjami.
- Ciężkie aplikacje i wideo z dźwiękiem w hero, które spowalniają stronę dla ruchu z social.
- Kopiowanie haseł konkurencji („Z miłości do piękna” Apart, „od 1840” W.KRUK). Przejmujemy mechanikę, nie hasła.
- Komunikaty jednego klubu w globalnym pasku (np. jubileusz Realu widoczny dla kibiców Barçy).
- „Gwarantujemy” bez opisanych warunków gwarancji, w tym obiecywanie terminu świątecznego dla kuriera, gdy przewoźnik gwarantuje go tylko dla Paczkomatów.

## Strona główna – sekcje

1. **Pasek ogłoszeń (grupa nagłówka: Header announcements)** – Jeden komunikat według kalendarza z sekcji logiki paska, np. teraz: „Oficjalnie licencjonowana biżuteria kibica”, a od 2.12: „Zamów do 16 grudnia – dostawę przed Świętami gwarantujemy”. _(To najtańsze miejsce na dwie obietnice, które decydują o zakupie z social: oficjalność i termin. Działa jak pasek Apart „Dostawa GRATIS | Wysyłka w 24 h”, ale spokojniej.)_
2. **Header (przyklejony, nieprzezroczysty)** – Mobile: hamburger po lewej, logo VELLANO JUBILER (SVG, 120–132 px) na środku, koszyk po prawej; konto i wyszukiwarka w szufladzie menu, jeśli ustawienia na to pozwalają. Desktop: logo na środku, 4 pozycje menu, mega menu „Wybierz swój klub” z 3 kaflami herbów. Tło #FFFFFF, linia 1 px #E6E2DA. _(Symetryczny, cichy nagłówek wygląda jak w salonie jubilerskim. Mniej ikon to więcej uwagi na produkt, a przezroczysty nagłówek na zdjęciu psuje czytelność szeryfowego logo.)_
3. **Hero (osobny kadr dla mobile)** – Jedno zdjęcie lifestyle: zawieszka na szyi, światło dzienne, jasne tło; kadr mobile 4:5, wysokość do 70% ekranu. Eyebrow: „Oficjalnie licencjonowane”. H1: „Herb klubu w jubilerskim wydaniu”. Tekst: „Zawieszki z łańcuszkiem: Real Madryt, FC Barcelona, Manchester United. Wysyłka w 2–3 dni robocze.” Główny przycisk „Wybierz swój klub” (kotwica do sekcji 5) i link tekstowy „Prezent dla kibica”. Bez slidera. _(Osoba z Instagrama lub TikToka w 3 sekundy musi wiedzieć, co to jest, że jest oficjalne i gdzie kliknąć. Jedno mocne zdjęcie działa lepiej niż rotujący slider, a CTA zostaje nad linią zgięcia.)_
4. **Pasek zaufania (Section z grupami: ikona i tekst)** – 4 punkty w układzie 2×2 na mobile: Oficjalna licencja klubu · Wysyłka w 2–3 dni robocze · Darmowa dostawa [DP] · Pudełko prezentowe w zestawie [DP]. Od 16.11 punkt 2 zamieniamy na „Dostawa przed Świętami – zamów do 16.12 [DP]”. Cienkie ikony liniowe w kolorze szampańskim. _(Zdejmuje ryzyko zakupu u nieznanej marki tuż po pierwszym ekranie: oficjalność, czas, koszt, gotowość na prezent.)_
5. **Product list „Wybierz swój klub” (karty produktów, nie kolekcji)** – 3 karty: zdjęcie na tle w barwach klubu (jedyne miejsce koloru klubowego na stronie głównej), eyebrow z przydomkiem z metapola (Królewscy / Duma Katalonii / Czerwone Diabły), nazwa klubu, „149 zł · łańcuszek w zestawie”, gwiazdki (ukryte przy braku opinii). Na mobile karuzela z widocznym fragmentem kolejnej karty, bez autoplay; na desktopie 3 kolumny. Bez szybkiego dodawania. _(Jedno dotknięcie ze strony głównej prowadzi na kartę produktu. Przydomek buduje identyfikację kibica, a barwy pozwalają znaleźć swój klub w ułamku sekundy.)_
6. **Media with content: Wykonanie** – Zdjęcie makro emalii i cyrkonii. H2: „Jubilerska precyzja w każdym detalu”. Tekst: „Herb odwzorowujemy emalią i ręcznie osadzanymi cyrkoniami. Podstawą jest mosiądz z powłoką rodowaną, a całość uzupełnia łańcuszek o splocie linkowym, ok. 51 cm.” Link „Poznaj wykonanie” → /pages/wykonanie-i-pielegnacja. _(Odróżnia nas od gadżetu z pchlego targu i uzasadnia cenę 149 zł językiem jubilera, a nie sklepu kibica.)_
7. **Media with content (układ odwrócony): Prezent** – Zdjęcie rozpakowania (pudełko [DP]). H2: „Prezent dla kibica, który ma już koszulkę”. Tekst: „Nie musisz znać się na piłce – wystarczy, że wiesz, komu kibicuje. Wybierz herb, a my zadbamy o resztę: zawieszka przyjedzie w eleganckim pudełku [DP], gotowa do wręczenia.” Przycisk „Wybierz prezent” → /collections/prezent-dla-kibica oraz link „Jak wybrać prezent”. _(Obsługuje drugą i trzecią personę (partnerka, rodzina), które nie znają herbów i potrzebują pewności, że prezent wypadnie dobrze.)_
8. **Section „Terminy świąteczne” (sezonowa, 16.11–16.12)** – Dwie linie osi czasu z danych metaobiektu: „Mikołajki – zamów do 1 grudnia [DP]” oraz „Święta – zamów do 16 grudnia, dostawę gwarantujemy [data DP]”. Link do /pages/dostawa#terminy-swiateczne. W sezonie przenosimy ją na pozycję 4, poza sezonem ukrywamy. _(Konkretna data działa lepiej niż „dni robocze” (Baymard), a W.KRUK pokazuje datę i godzinę. To główny wyzwalacz zakupów w Q4 bez fałszywej presji.)_
9. **Opinie (blok aplikacji Judge.me)** – Karuzela opinii ze zdjęciami klientów, średnia ocena i link „Wszystkie opinie”. Pokazujemy dopiero przy co najmniej 5 opiniach (sprawdź, czy widżet karuzeli jest w darmowym planie); wcześniej ukryta, a sekcja 10 przesuwa się wyżej. _(Pierwsze 5 opinii zwiększa prawdopodobieństwo zakupu o ok. 270% (Spiegel). Pusty widżet obniża zaufanie.)_
10. **Media with content: Oficjalna licencja** – Zdjęcie oznaczenia licencji w opakowaniu [DP]. H2: „Oficjalnie licencjonowane”. Tekst: „Każdy wzór powstaje na licencji klubu [do potwierdzenia: nazwy licencjodawców]. Oznaczenie licencji znajdziesz w opakowaniu [DP].” Link „Jak rozpoznać oryginał” → /pages/oficjalna-licencja. _(Odpowiada na główną obiekcję przy biżuterii klubowej (podróbki) i wspiera pozycjonowanie „oficjalna biżuteria kibica”.)_
11. **FAQ (Section z blokiem Accordion)** – 5 pytań: Czy to oficjalny produkt? Czy łańcuszek jest w zestawie? (tak, splot linkowy, ok. 51 cm; ucho mieści łańcuszek do 5 mm) Kiedy otrzymam zamówienie? Czy zapakujecie na prezent? [DP] Jak zwrócić? (link /pages/zwroty, bez liczby dni). Link do pełnego FAQ. _(Zbiera obiekcje przed decyzją, a dane strukturalne FAQ pomagają w SEO.)_
12. **Footer (grupa stopki)** – Logo w wersji białej na grafitowym tle #2B2B2B, 4 kolumny menu (na mobile zwijane, jeśli motyw to umożliwia), krótki zapis do newslettera („Nowe herby i terminy świąteczne jako pierwszy”, bez rabatu jako przynęty), ikony płatności (BLIK, Przelewy24, Apple Pay, Google Pay, karty [DP]), dane firmy [do uzupełnienia], bez „Powered by Shopify”. _(Kompletna, uporządkowana stopka to sygnał wiarygodnej marki jubilerskiej i spełnienie wymogów informacyjnych sklepu.)_
