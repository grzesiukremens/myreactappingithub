# Horizon – notatki techniczne dla motywu Vellano Jubiler

Motyw roboczy: `gid://shopify/OnlineStoreTheme/208574808406`, „Vellano Jubiler – premium (w budowie)”, rola UNPUBLISHED.
Bazą jest **Horizon 4.2.0** (Shopify), według `config/settings_schema.json` → `theme_info`.
Motywu MAIN (`208533717334`) nie ruszamy. Nie publikujemy.

Lokalne kopie 1:1 (Admin API, `OnlineStoreThemeFileBodyText.content`) leżą w `theme/`: `config/settings_data.json`,
`templates/{product,index,collection,page}.json` oraz `sections/{header,footer}-group.json`.
Każdy JSON zaczyna się od komentarza `/* ... */`. Przed `json.load` trzeba ten komentarz wyciąć. Wszystkie pliki przeszły walidację.

> Uwaga: `config/settings_data.json` jest w Shopify zapisany jako zminifikowany JSON bez komentarza (7873 B, md5 `3eccf92f…`).
> API zwraca go sformatowanego i z komentarzem (9663 B). Treść jest identyczna, różni się tylko formatowanie. Upload każdej z tych wersji jest poprawny.

---

## 1. Najważniejsze zasady z AGENTS.md

- **Architektura**: `layout/` (powłoka), `templates/` (JSON), `sections/`, `blocks/` (theme blocks), `snippets/` (`render`), `assets/` (płaski katalog), `config/`, `locales/`.
  Najpierw szukaj istniejącej sekcji, bloku, snippetu lub klasy. Rozszerzaj kontrakt, który już odpowiada za dane zachowanie.
- **Stabilne ID**: nie zmieniaj ID sekcji i bloków w szablonach ani ID, typów i wartości opcji ustawień, bo od nich zależą zapisane dane.
- **Ustawienia to publiczne API dla sprzedawcy**. Globalne decyzje trafiają do `settings_schema`, treść i prezentacja kontekstowa do ustawień sekcji lub bloku.
  Dla produktu, kolekcji, strony, menu, mediów i linków używaj resource pickerów. Pokazuj warunkowo przez `visible_if`, z sensownymi wartościami domyślnymi.
  ID paddingów są w kebab-case (`padding-block-start`), pozostałe w snake_case. Bez ustawień pomijaj klucz `settings`.
- **Presety** mają być użytecznymi kompozycjami startowymi. Klucze bloków, `block_order` i `static` muszą odpowiadać renderowanemu drzewu.
- **Liquid**: logika wielolinijkowa w `{% liquid %}` (komentarze przez `#`). Do snippetów wywoływanych przez `render` przekazuj jawnie wszystkie zmienne lokalne.
  Treść opcjonalną renderuj tylko wtedy, gdy ma wartość. Escapuj zwykłe stringi, rich text zostaw bez zmian.
  `{{ block.shopify_attributes }}` dawaj na wrapperze bloku. ID w DOM dopisuj z `section.id` lub `block.id`.
- **Dokumentacja**: w snippetach i blokach `{% doc %}` (opis, `@param`, `@example`). W sekcjach komentarz kontraktowy:
  ```liquid
  {% comment %}
    Section contract.
    Opis regionu i odpowiedzialności.
    @example
    <!-- jak sekcja jest konfigurowana -->
  {% endcomment %}
  ```
- **CSS**: statyczne reguły trzymaj w jednym `{% stylesheet %}` pliku, który je posiada (stylesheet subsetting działa per plik; **wewnątrz `{% stylesheet %}` nie ma Liquida**).
  Wartości dynamiczne przekazuj inline przez custom properties albo przez `{% style %}` z zasięgiem `#shopify-section-{{ section.id }}` lub `.color-custom-<id>`.
  Konwencja BEM, niska specyficzność, logiczne właściwości (`padding-inline`, `margin-block`), `min-width: 0`.
  Animuj tylko `transform` i `opacity`, zawsze z obsługą reduced motion. Kolory bierz z tokenów (`var(--color-foreground)`).
  Alfę ustawiaj tak: `rgb(var(--color-foreground-rgb) / var(--opacity-70))`.
- **JS**: najpierw natywne `<a>`, `<button>`, `<form>`, `<details>` i `<dialog>`.
  Komponenty z zachowaniem buduj na `Component` z `@theme/component` (refy `ref="x"`, zdarzenia `on:click="/handler"`). Nie dodawaj nowych zależności.
  Moduł: `<script src="{{ 'x.js' | asset_url }}" type="module" fetchpriority="low">`. Import przez `@theme/*` wymaga wpisu w importmapie w `snippets/scripts.liquid`.
- **Dostępność**: semantyczny HTML, każda kontrolka ma nazwę, widoczny focus, cele dotyku ≥ 44 px (`--minimum-touch-target`),
  alt dla obrazów informacyjnych i `alt=""` dla dekoracyjnych, `aria-hidden="true"` na ikonach SVG, poprawne działanie bez JS.
- **Wydajność**: obrazy z intrinsic `width` i `height`, `widths` i `sizes` dopasowanymi do layoutu.
  Obrazy poniżej linii zgięcia `loading: 'lazy'`, obraz LCP `eager` + `fetchpriority: 'high'`.
- **Teksty**: UI storefrontu idzie do `locales/*.json` przez filtr `t` (jest `locales/pl.json`), etykiety schematu do `locales/*.schema.json` przez klucze `t:`.
  Treść sklepu (copy, media, linki) siedzi w ustawieniach, blokach i metapolach.
  *Dla plików `vellano-*`* Shopify przyjmuje też etykiety schematu jako zwykłe stringi po polsku. Pełna zgodność z AGENTS.md wymaga kluczy
  `t:vellano.*` w `locales/en.default.schema.json` i `locales/pl.schema.json`. Wybierz jeden wariant i trzymaj się go we wszystkich plikach.
- **Weryfikacja**: Theme Check (jeśli dostępny), podgląd na wąskim viewporcie, puste i wypełnione ustawienia, długie teksty, brak mediów.

---

## 2. Sekcje i bloki w Horizon

### 2.1 Rodzaje bloków
- **Theme blocks**: pliki `blocks/*.liquid` z własnym `{% schema %}`. Zwykle mają `"tag": null` (bez wrappera Shopify), dlatego `{{ block.shopify_attributes }}` musi być na własnym elemencie.
  Bloki z `presets` pojawiają się w menu „Dodaj blok”.
- **Bloki prywatne**: nazwa zaczyna się od `_` (`_accordion-row`, `_announcement`, `_divider`, `_product-details`…).
  `@theme` ich nie obejmuje, więc rodzic musi wymienić je z nazwy, np. `{"type": "_accordion-row"}`.
- **`@theme`** w `"blocks"` schematu: przyjmuje wszystkie publiczne theme blocks. **`@app`**: bloki aplikacji.
- **Bloki statyczne**: osadzone w kodzie w stałym miejscu:
  ```liquid
  {% content_for 'block', type: '_product-details', id: 'product-details', closest.product: closest.product %}
  ```
  W szablonie JSON mają `"static": true`, a ich ID **nie występuje** w `block_order`. Typ i ID muszą zostać stabilne.
- **Bloki dynamiczne** (kolejność ustala sprzedawca): `{% content_for 'blocks' %}` jest **jeden raz na plik**.
  Gdy jest potrzebny w kilku gałęziach, robisz `capture` raz i wypisujesz zmienną.
- Kontekst zasobu przekazujesz przez `closest.product: …` / `closest.collection: …`. W ustawieniach i tekstach działa składnia `{{ closest.product.title }}`.

### 2.2 Wzorzec sekcji ogólnej (`sections/section.liquid`)
```liquid
{% capture children %}{% content_for 'blocks' %}{% endcapture %}
{% render 'section', section: section, children: children, section_id: section.id, background_color: section.settings.background_color %}
```
Schema: `"name": "t:names.section"`, `"class": "section-wrapper"`, `"blocks": [@theme, @app, _divider]`, `"disabled_on": {"groups": ["header"]}`.
Ustawienia sekcji (te same ID warto powielać w sekcjach `vellano-*`):
`content_direction` (column/row), `vertical_on_mobile`, `horizontal_alignment`, `vertical_alignment`, `align_baseline`,
`horizontal_alignment_flex_direction_column`, `vertical_alignment_flex_direction_column`, `gap` (0–100 px),
`section_width` (`page-width`/`full-width`), `section_height` (``/small/medium/large/full-screen/custom), `section_height_custom`,
`background_media` (none/image/video), `background_color`, `video`, `video_position`, `background_image`, `background_image_position`,
`toggle_overlay`, `overlay_color`, `overlay_style`, `gradient_direction`, `border`, `border_width`, `border_opacity`, `border_color`, `border_radius`,
`padding-block-start`, `padding-block-end` (0–100 px).
Gotowe presety „section”: custom_section, rich_text_section, faq_section, video_section, pull_quote, contact_form, email_signup,
icons_with_text, split_showcase, image_with_text, multicolumn, image_compare, large_logo.

`snippets/section.liquid` robi kolejno:
1. `render 'contrast-override'` (tło i kontrast) dla `section_id`.
2. `<div class="section-background color-custom-{{ section_id }}">`, czyli warstwę tła pod sekcją.
3. `<div class="section section--{{ section_width }} color-custom-{{ id }}">` → `.custom-section-background` (media) → `.border-style.custom-section-content` → `.spacing-style.layout-panel-flex.layout-panel-flex--{dir}.section-content-wrapper[.mobile-column]` ze stylem `{% render 'layout-panel-style' %}` i `{% render 'spacing-style' %}`.

### 2.3 Zalecany szkielet sekcji `vellano-*` (własny markup)
```liquid
{% comment %}
  Section contract.
  …
{% endcomment %}
{% render 'contrast-override', background_color: section.settings.background_color, section_id: section.id %}
<div class="section-background color-custom-{{ section.id }}"></div>
<div
  class="section section--{{ section.settings.section_width }} color-custom-{{ section.id }} spacing-style"
  style="{% render 'spacing-style', settings: section.settings %}"
>
  <div class="vellano-x">…</div>   {%- # dzieci .section trafiają do środkowej kolumny siatki strony -%}
</div>
{% stylesheet %} .vellano-x { … } {% endstylesheet %}
{% schema %}
{
  "name": "…", "class": "section-wrapper", "tag": "section",
  "disabled_on": { "groups": ["header", "footer"] },
  "settings": [
    { "type": "select", "id": "section_width", "options": [{"value":"page-width","label":"…"},{"value":"full-width","label":"…"}], "default": "page-width", "label": "…" },
    { "type": "color", "id": "background_color", "label": "…", "default": "{{ settings.color_palette.background }}" },
    { "type": "range", "id": "padding-block-start", "min": 0, "max": 100, "step": 4, "unit": "px", "default": 48, "label": "…" },
    { "type": "range", "id": "padding-block-end",   "min": 0, "max": 100, "step": 4, "unit": "px", "default": 48, "label": "…" }
  ],
  "presets": [{ "name": "…" }]
}
{% endschema %}
```
- `spacing-style` dla wartości > 20 px wypisuje `--padding-block-start: max(20px, calc(var(--spacing-scale) * Npx))`, gdzie `--spacing-scale` wynosi 0.7 poniżej 990 px i 1.0 od 990 px.
  Przykład: 48 → ok. 34 px na mobile i 48 px na desktopie. Bez skalowania użyj `{% render 'spacing-padding', settings: … %}` albo własnych zmiennych.
- `.section` to siatka 3-kolumnowa (margines | treść | margines). Margines strony `--page-margin` wynosi 16 px poniżej 750 px i 40 px od 750 px.
  `section--full-width` rozciąga dzieci na całą szerokość. Pojedynczy element można wyrwać na pełną szerokość klasą `.force-full-width`.
- Tło sekcji maluje `.section-background` (absolutnie pod sekcją). Samo `.section` ma przezroczyste tło.

### 2.4 Obrazy (wzorzec)
```liquid
{{ image | image_url: width: 1500 | image_tag:
   widths: '375, 550, 750, 1000, 1500', sizes: '(min-width: 750px) 50vw, 100vw',
   loading: 'lazy', alt: image.alt | default: product.title | escape, class: 'vellano-x__img' }}
```
Obrazy z ustawień motywu wskazujesz w JSON wartością `"shopify://shop_images/<plik>"`. Media produktu bierzesz przez `product.media[n].preview_image`.

---

## 3. Ustawienia globalne (ID → wartość obecna → cel Vellano)

### 3.1 Kroje pisma (`font_picker`, są tylko 4)
| ID | obecnie | cel (docs/struktura.md) |
|---|---|---|
| `type_body_font` | `inter_n4` | `inter_n4` |
| `type_subheading_font` | `inter_n5` | `inter_n5` |
| `type_heading_font` | `inter_n7` | `ebgaramond_n5` |
| `type_accent_font` | `inter_n7` | `ebgaramond_n5` (eyebrow w wersalikach, rozstrzelenie przez CSS) |

Wartość ma format `<handle>_<n|i><waga/100>`, np. `ebgaramond_n4`, `ebgaramond_i4`. Przyjmowane są wyłącznie uchwyty z biblioteki Shopify.
Po zapisie sprawdź w podglądzie, czy `--font-heading--family` to „EB Garamond”.
CSS: `--font-{body|subheading|heading|accent}--family|--style|--weight`. Pogrubienia i kursywy dogrywa `font_modify` w `theme-styles-variables`.

Presety typografii (generują `--font-{paragraph|h1..h6}--size|family|style|weight|case|line-height|letter-spacing` oraz klasy `.paragraph`, `.h1`…`.h6`):
- `type_size_paragraph` (10/12/14/16/18; obecnie **14** → cel **16**), `type_line_height_paragraph` (body-tight/normal/loose; obecnie body-loose = 1.6).
- `type_font_hN`: h1 i h2 przyjmują `heading|accent`, h3–h6 `heading|accent|subheading|body`.
  Obecnie h1–h4 = heading, h5–h6 = subheading.
- `type_size_hN`: tylko wartości `10,12,14,16,18,20,24,32,40,48,56,72,88,120,152,184` (brak 26 i 36).
  Obecnie h1 56, h2 48, h3 32, h4 24, h5 14, h6 12.
  **Rozmiary ≥ 48 są płynne**: `clamp(min, size*0.1vw, size)`, przy czym `min` = najbliższy mniejszy rozmiar + 4 px (gdy ten jest < 48).
  Przykład: h1 = 48 i h2 = 32 dają H1 = 36 px na 375 px i 48 px na desktopie. Rozmiary < 48 są stałe.
- `type_line_height_hN` (display-tight 1.0 / display-normal 1.1 / display-loose 1.2), `type_letter_spacing_hN` (heading-tight −0.03em / normal 0 / loose 0.03em), `type_case_hN` (none/uppercase).

### 3.2 Kolory: w tej wersji Horizon NIE MA `color_schemes`
- Globalna paleta to ustawienie `color_palette` (typ `color_palette`). Przyjmuje 2–20 kolorów hex bez alfy, klucze z liter, cyfr i `_`.
  Obecnie: `{"background":"#ffffff","foreground":"#000000","color1":"#333333","color2":"#DFDFDF"}`.
  W ustawieniach typu `color` odwołujesz się do palety przez `"{{ settings.color_palette.color2 }}"`, a w Liquid przez `settings.color_palette.color2`.
- Proponowane mapowanie Vellano: `background #FFFFFF`, `foreground #141414`, `color1 #5E5E5E` (tekst drugorzędny), `color2 #E6E2DA` (linie),
  `color3 #F7F5F1` (kość słoniowa), `color4 #E9EAEC` (szarość opakowania). Opcjonalnie `color5 #2B2B2B` (grafit, wg struktura.md).
  **Schematy S1–S5 z docs/struktura.md realizujemy przez ustawienie `background_color` każdej sekcji lub bloku, a nie przez schematy.**
- Kolory strony: `page_background_color`, `page_text_color` (obie domyślnie wskazują paletę).
- Mechanizm kontekstu: `snippets/contrast-override.liquid`.
  Przy niepustym `background_color` emituje dla `.color-custom-<id>` zmienne `--color-background(-rgb)`, `--color-foreground(-rgb)`, `--color`, `--color-border`, `--color-foreground-muted` i `-subdued` oraz `color` i `background-color`.
  Tekst = `page_text_color`, jeśli kontrast ≥ 4,5. W przeciwnym razie najciemniejszy lub najjaśniejszy kolor palety.
  Parametry snippetu: `background_color`, `text_color`, `border_color`, `section_id` (unikalny), `skip_contrast`, `preset` (`content`|`ui`).
- Przyciski: `palette_primary_button_background|text|border`, `palette_secondary_button_background|text|border`.
  Pola: `palette_input_background|text|border`. Warianty: `palette_variant_*`, `palette_selected_variant_*`.
  Szuflady: `drawer_background_color|text_color|border_color`. Popovery: `popover_background_color|text_color|border_color`, `popover_shadow_color`.
  Odznaki: `badge_sale_background_color|text_color`, `badge_sold_out_background_color|text_color`. Quick add: `quick_add_background|text`.

### 3.3 Zaokrąglenia, obrysy, przyciski
| ID | obecnie | cel |
|---|---|---|
| `button_border_radius_primary` / `_secondary` (0–100) | 14 / 14 | **2 / 2** |
| `primary_button_border_width` / `secondary_button_border_width` (0–4) | 0 / 1 | 0 / 1 |
| `type_font_button_primary` / `_secondary` (body/accent) | (domyślnie body) | body |
| `button_text_case_primary` / `_secondary` (default/uppercase) | (default) | **uppercase** |
| `inputs_border_radius` (0–32) / `input_border_width` | 4 / 1 | **2** / 1 |
| `badge_corner_radius` (0–100) | 100 | **2** |
| `pills_border_radius` (0–40) | (40) | 2 |
| `variant_button_radius` / `variant_swatch_radius` | 14 / 32 | 2 / wg potrzeb |
| `popover_border_radius` (0–16) / `popover_border_width` / `popover_drop_shadow` | 14 / 1 / (true) | **0** / 1 / wg potrzeb |
| `card_corner_radius` (0–16) / `product_corner_radius` / `cart_thumbnail_border_radius` | 4 / 0 / (0) | 0 / 0 / 0 |

Rozstrzelenie liter w przyciskach (0,08em) nie ma ustawienia, trzeba je dodać w CSS (`.button { letter-spacing: … }`).
Wysokość: `--button-padding-block` = 16 px, `--height-buy-buttons` = `calc(var(--padding-lg)*2 + var(--icon-size-sm))`.
Pozostałe: `badge_position`, `badge_font_family`, `badge_text_transform`, `icon_stroke` (thin/default/heavy), `card_hover_effect`, `show_second_image_on_hover`, `product_card_carousel`, `quick_add`, `mobile_quick_add`.

### 3.4 Logo i favicon
`logo` (image_picker), `logo_inverse` (logo na ciemnym tle lub przy przezroczystym nagłówku), `logo_height` (obecnie 36 px), `logo_height_mobile` (28 px), `favicon`.
Przykład wartości: `"logo": "shopify://shop_images/vellano-logo-black.png"`, `"logo_inverse": "shopify://shop_images/vellano-logo-white.png"`, `"favicon": "shopify://shop_images/vellano-favicon-v.png"`.
Favicon renderuje `layout/theme.liquid` w rozmiarze 32×32. Nagłówek bierze logo z `settings.logo` (blok `_header-logo`).

### 3.5 Koszyk, szuflada, ceny
`cart_type` (`page`|`drawer`; obecnie **drawer**), `auto_open_cart_drawer` (widoczne tylko dla drawer; nieustawione, czyli false, cel true),
`product_title_case`, `cart_price_font`, `show_cart_note`, `cart_note_open_by_default`, `show_add_discount_code`, `show_installments`,
`show_accelerated_checkout_buttons`, `empty_cart_button_link`, `cart_thumbnail_border*`.
Waluta przy cenie: `currency_code_enabled_product_pages|product_cards|cart_items|cart_total`.
Pozostałe: `page_width` (narrow/normal/wide; obecnie narrow = 90rem), `page_transition_enabled`, `transition_to_main_product`, `add_to_cart_animation`.
`color-palette.liquid` czyta też `drawer_drop_shadow` i `drawer_shadow_color`, których nie ma w schemacie, więc cień szuflady jest wyłączony.

---

## 4. Karta produktu (`templates/product.json`)

Kolejność sekcji: `["main", "product_recommendations_qggXJq"]`.

- **`main`** (`product-information`). Ustawienia: `content_width` (content-center-aligned/content-full-width), `desktop_media_position` (left/right),
  `equal_columns`, `limit_details_width`, `gap` (obecnie 48), `enable_sticky_add_to_cart` (true), `background_color`, `padding-block-start|end`.
  Schema przyjmuje `"blocks": [@theme, @app]`, czyli w `block_order` może się znaleźć każdy publiczny theme block, także `blocks/vellano-*.liquid`.
  Bloki dynamiczne renderują się przez `{{ additional_blocks }}` **pod siatką galeria + szczegóły, w obrębie tej samej sekcji**.
  - Blok statyczny `media-gallery` (`_product-media-gallery`): `media_presentation: grid`, `media_columns: two`, `aspect_ratio: adapt`,
    `media_fit: contain`, `slideshow_mobile_controls_style: dots`, `zoom: true`, `hide_variants: true`…
  - Blok statyczny `product-details` (`_product-details`): `gap 28`, `sticky_details_desktop`, `padding-block 24`.
    Przyjmuje: @theme, @app, text, icon, image, button, video, group, spacer, accordion, product-recommendations, price, variant-picker, buy-buttons,
    product-description, review, accelerated-checkout, _divider, product-inventory, product-custom-property.
    Obecna kolejność: `group_icgrde` (text H1 `{{ closest.product.title }}` z presetem h3 + `price_tVjtKg`) → `divider_VJhene` → `variant_picker_R3rGDr` →
    `buy_buttons_eYQEYi` (statyczne bloki `quantity`, `add-to-cart`, `accelerated-checkout`, `block_order: []`) → `text_aEtTtq` (`{{ closest.product.description }}`).
  - Blok dynamiczny `disclosures_g9mWze` (`disclosures`, nagłówek „Disclosures” po angielsku) czyta `product.metafields.shopify.disclosure`.
    Bez tych danych nic nie wyświetla. Usuń go albo przetłumacz.
- **`product_recommendations_qggXJq`** (`product-recommendations`): `product: "{{ closest.product }}"`, `recommendation_type: related`, `max_products 4`,
  `columns 4`, `mobile_columns 2`, nagłówek text `<h3>You may also like </h3>` (do tłumaczenia) i statyczny `_product-card`.
- **Nowa treść „pod produktami”** ma dwie możliwe drogi:
  - (a) nowa sekcja `sections/vellano-*.liquid` wstawiona w `order` po `main` (zalecane dla pełnej szerokości i własnego tła).
  - (b) theme block `blocks/vellano-*.liquid` dodany do `main.block_order`.
  W sekcji szablonu produktu dostępne są `product` i `closest.product`. Metapola: `product.metafields.custom.zanim_zapytasz.value` (lista `{question, answer, photo}`) i `product.metafields.custom.przydomek.value`.
  Media: `product.media[0..3]` (0 = na łańcuszku, 1 = przód, 2 = pod kątem, 3 = opakowanie).

## 5. Bloki tekstu i akordeonu

- **`blocks/text.liquid`** (`render 'text'`, `"tag": null`). Ustawienia: `text` (richtext), `width` (fit-content/100%), `max_width` (narrow/normal/none),
  `alignment` (gdy width 100%), `type_preset` (rte domyślny/paragraph/h1–h6/custom).
  Przy custom dochodzą: `font` (`var(--font-body--family)` itd.), `font_size` (rem), `line_height`, `letter_spacing`, `case`, `wrap`.
  Dalej: `text_color`, `background`, `background_color`, `corner_radius`, `padding-*`. Presety: „Text” i „Heading”. Klasy: `.text-block`, `.text-block--{id}`, `.rte`, `.{type_preset}`.
- **`blocks/accordion.liquid`** (publiczny). Przyjmuje tylko `_accordion-row`.
  Ustawienia: `icon` (caret/plus), `dividers` (true), `divider_color`, `type_preset` nagłówków wierszy (domyślnie h6), `background_color`, `text_color`,
  `border*`, `border_radius`, `padding-*`. Renderuje `{% content_for 'blocks' %}` oraz `render 'accordion-styles'`.
  Klasy: `.accordion`, `.accordion--{icon}`, `.accordion--dividers`.
- **`blocks/_accordion-row.liquid`**. Przyjmuje `@theme` i `@app` (np. text w środku).
  Ustawienia: `heading` (text), `open_by_default`, `icon` (lista ikon, np. `box`, `truck`, `return`, `question_mark`, `lock`, `heart`…),
  `image_upload`, `width` (12–200 px). Markup: `<details class="details">`, `<summary class="details__header">` (ikony caret i plus), `<div class="details-content">`.
  Wszystko jest opakowane w `render 'accordion-custom-component'` (`open_by_default_on_desktop|mobile`).
- FAQ z metapola: własny blok lub sekcja `vellano-*` z natywnymi `<details>` i `<summary>`.
  Możesz użyć `{% render 'accordion-styles' %}` i tych samych klas (`details`, `details__header`, `details-content`, ikona `icon-caret.svg` przez `inline_asset_content`).
  JS nie jest potrzebny. `answer` zawiera HTML (`<a>`), więc wypisuj go bez escapowania.

## 6. Header i pasek ogłoszeń (`sections/header-group.json`)

- `header_announcements_9jGBFp` (`header-announcements`, `enabled_on: header`). Ustawienia: `speed` (2–10 s), `section_width`, `background_color`,
  `divider_width` (obecnie 1), `divider_color` (`{{ settings.color_palette.color2 }}`), `padding-block-start|end` (15/15).
  Bloki: tylko `_announcement`. Przy więcej niż 1 bloku włącza się autoplay i strzałki (`announcement-bar.js`).
  `_announcement` ma: `text` (inline_richtext), `link` (url, nakłada `<a>` na cały slajd), `font`, `font_size` (rem), `weight`, `letter_spacing`, `case`, `text_color`.
  Obecnie jeden blok `announcement_BxgCk9`: „Welcome to our store” (font subheading, 0.75rem).
- `header_section` (`header`). Statyczne bloki `header-logo` (`_header-logo`, `hide_logo_on_home_page`) i `header-menu` (`_header-menu`, `menu: "main-menu"`, `menu_style: featured_products`,
  `drawer_accordion`, `drawer_dividers`…).
  Ustawienia sekcji: `logo_position`, `menu_position`, `menu_row`, `show_search`, `search_position`, `show_country`, `show_language`,
  `section_height`, `enable_sticky_header` (always), `divider_width`, `border_width`, `background_color_top`, `enable_transparent_header_*` (false).

## 7. Stopka (`sections/footer-group.json`)

- `footer_m9NzUG` (`footer`, `enabled_on: footer`). Ustawienia: `section_width`, `gap` (20), `background_color` (domyślnie foreground, obecnie background), `padding-block-start|end` (30/30).
  Dozwolone bloki: `_divider`, `@app`, `button`, `follow-on-shop`, `group`, `icon`, `image`, `menu`, `payment-icons`, `text`, `logo`, `jumbo-text`, `social-links`, `email-signup`.
  Siatka: na mobile 1 kolumna. W zakresie 750–989 px `min(N, 3)` kolumn, a przy 4 blokach 2 kolumny. Od 990 px `min(N, 4)` kolumn, gdzie N to liczba bloków.
  Obecnie: `group_H6VpwJ` (texts „Join our email list” i „Get exclusive deals…”) oraz `email_signup_crihX7` (label „Sign up”, `border_radius 100`). Wszystko do przetłumaczenia lub zastąpienia.
- **Blok `menu`**. Ustawienia: `menu` (link_list, wartością jest **handle menu**), `heading` (pusty = tytuł menu), `menu_spacing` (12), `show_as_accordion` (akordeon na mobile),
  `accordion_icon`, `accordion_dividers`, `background_color`, `text_color`, `heading_preset` (h3), `link_preset` (paragraph), `padding-*`. Przykład:
  ```json
  "menu_marka": { "type": "menu", "settings": { "menu": "footer-marka", "heading": "Vellano Jubiler", "show_as_accordion": true, "accordion_dividers": true, "heading_preset": "h6", "link_preset": "paragraph", "menu_spacing": 12 } }
  ```
  Pozostałe menu: `footer` (Obsługa klienta), `footer-kolekcja` (Kolekcja), `main-menu`.
- `footer_utilities_jLGE8U` (`footer-utilities`). Bloki: `footer-copyright` (`show_powered_by: true`, ustaw false), `footer-policy-list`, `social-links`
  (obecnie zastępcze adresy facebook.com, instagram.com…, które trzeba usunąć lub podmienić).
  Ustawienia: `gap`, `divider_thickness`, `divider_color`, `background_color`, `padding-*`.

## 8. Inne szablony (stan obecny)

- `index.json`: `hero_jVaWmY` (hero: text „Browse our latest products”, button „Shop all” → `shopify://collections/all`) i `product_list_fa6P9H`
  (`collection: all`; statyczne `static-header` z „View all” oraz `static-product-card`).
- `collection.json`: `section` (text H1 `{{ closest.collection.title }}` i opis) oraz `main` (`main-collection`, statyczne bloki `filters` i `product-card`).
  Metapola `custom.hero_*` nie są jeszcze użyte.
- `page.json`: `main` (`main-page`: `heading` text `<h1>{{ closest.page.title }}</h1>` i `page-content`). Jest też `page.contact.json`.

## 9. Tokeny CSS i klasy

- **Kolory**: `--color-background(-rgb)`, `--color-foreground(-rgb)`, `--color-border(-rgb)`, `--color-foreground-muted`, `--color-foreground-subdued`,
  `--color` (lokalny tekst), `--palette-lightest|darkest(-rgb)`, `--color-primary-button-{text|background|border|hover-*}`, `--color-secondary-button-*`,
  `--color-input-{background|text|border}`, `--color-variant-*`, `--color-error` (#8B0000), `--color-success` (#006400), `--color-white`,
  `--border-color` (= border 50%).
  Przezroczystość: `--opacity-5…90`, `--opacity-muted-text`, `--opacity-subdued-text`.
- **Typografia**: `--font-{paragraph|h1..h6}--{size|family|style|weight|case|line-height|letter-spacing}`, `--font-size--{3xs…6xl}` (0.625–3.5rem),
  `--line-height--{display|heading|body}-{tight|normal|loose}`, `--letter-spacing--*`, `--letter-spacing-sm` (0.06em),
  `--max-width--body-normal` (32.5em), `--max-width--body-narrow`.
- **Odstępy**: `--padding-{3xs…6xl}` (0.125–4rem), `--gap-{3xs…3xl}`, `--margin-{3xs…6xl}`, `--spacing-scale` (w `.spacing-style`), `--page-margin`.
- **Kształt**: `--style-border-radius-{buttons-primary|buttons-secondary|inputs|pills|popover|xs|sm|md|lg|50}`, `--style-border-width` (1px),
  `--style-border-width-{primary|secondary|inputs}`.
- **Ruch**: `--animation-speed` (0.125s), `-fast`, `-slow`, `-medium`, `--animation-easing`, `--ease-out-cubic|quad`, `--animation-timing-*`.
  Animacje owijaj w `@media (prefers-reduced-motion: no-preference)`.
- **Inne**: `--minimum-touch-target` (44px), `--button-size`, `--button-padding-inline` (24px) i `-block` (16px), `--icon-size-{2xs…lg}`, `--layer-*` (z-index),
  `--safe-area-inset-*`, `--narrow-content-width` (36rem), `--normal-content-width` (42rem), `--section-height-*`.
- **Klasy**: `.section`, `.section--page-width`, `.section--full-width`, `.section-background`, `.force-full-width`, `.spacing-style`, `.size-style`, `.border-style`,
  `.layout-panel-flex`, `.layout-panel-flex--row` i `--column`, `.mobile-column`, `.text-block`, `.rte`, `.paragraph`, `.h1`…`.h6`, `.custom-typography`,
  `.button`, `.button-secondary`, `.button-unstyled`, `.button-custom`, `.visually-hidden`, `.list-unstyled`, `.hidden`, `.mobile:hidden` / `.desktop:hidden`
  (w HTML `class="mobile:hidden"`), `.text-left|center|right`, `.svg-wrapper`, `.wrap-text`, `.color-custom-<id>`, `.details*`, `.accordion*`.
  `<body>` ma klasy `page-width-{narrow|normal|wide}` i `card-hover-effect-*`.
- **Breakpointy**: 750 px (tablet), 990 px (desktop), 1200, 1400 i 1600 px.
  Mobile-first: style bazowe dla telefonu, rozszerzenia przez `@media screen and (min-width: 750px)` i `(min-width: 990px)`.
- Style globalne pochodzą z `assets/base.css` (link w `snippets/stylesheets.liquid`). Zmienne generują `snippets/theme-styles-variables.liquid` i `snippets/color-palette.liquid` w `<head>`.

## 10. Pułapki

- Szablony i grupy mają dużo angielskich tekstów domyślnych: „You may also like”, „Browse our latest products”, „Shop all”, „View all”,
  „Disclosures”, „Welcome to our store”, „Join our email list”, „Get exclusive deals…”, „Sign up”. Wszystkie trzeba przepisać według `content/copy-edited.json`.
- `docs/struktura.md` zakłada schematy kolorów S1–S5. W Horizon 4.2.0 odpowiada im `background_color` na sekcji lub bloku plus paleta (pkt 3.2).
- `type_size_hN` przyjmuje tylko wartości z listy (pkt 3.1). Pośrednie rozmiary z makiety (26, 36) wymagają CSS w sekcji albo najbliższej wartości z listy.
- W `{% stylesheet %}` nie ma Liquida ani `{{ }}`. Wartości z ustawień przekazuj przez `style="--x: {{ … }}"`.
- `content_for 'blocks'` wolno użyć tylko raz w pliku.
- Bloki prywatne (`_…`) trzeba wymieniać w `blocks` schematu z nazwy.
- Edycja `settings_data.json` przez API nadpisuje całość. Przed uploadem zawsze pobierz aktualną wersję, bo edytor motywu mógł ją zmienić.
