# Medical Body Atlas 3D v2.2.0 — zakres aktualizacji

Data: 3 listopada 2026.

## Cele
Wersja 2.2.0 rozwija anatomiczne przybliżenie drobnych kości kończyn i warstwy tkanek miękkich bez zmiany danych WordPress.

### Dłonie
Każda dłoń w module `assets/distal.js` zawiera 27 osobno nazwanych kości: 8 nadgarstka (dwa szeregi), 5 śródręcza oraz 14 paliczków, w tym 2 paliczki kciuka i 3 każdego z pozostałych palców. Elementy mają osobne siatki, dzięki czemu mogą być wybrane przez raycasting i przypisane do pinezek.

### Stopy
Każda stopa zawiera 26 osobno nazwanych kości: 7 stępu, 5 śródstopia i 14 paliczków. Dodatkowo zaznaczono orientacyjnie dwie trzeszczki palucha. Powłoka plantarna ma wygładzoną geometrię, osobne podparcie pięty/przodostopia oraz wyższy łuk przyśrodkowy.

### Mięśnie
Zmniejszono wybrane przekroje mięśni w obrębie kończyn, dodano poglądowe, smukłe mięśnie kłębu kciuka, kłębika, mięśnie międzykostne dłoni, mięsień płaszczkowaty oraz przykładowe mięśnie wewnętrzne stopy.

### Zmiany techniczne
- Nowy plik: `assets/distal.js`.
- `assets/joints.js` korzysta z nowego modułu zamiast poprzedniego schematycznego układu drobnych kości.
- `assets/body.js` ma płynniejszą geometrię spodów stóp i dodatkowe mięśnie.
- `medical-body-atlas.php` rejestruje zależność `mba-distal → mba-joints → mba-viewer`.
- Zostają zachowane opcje `mba_atlas_data`, shortcode `[medical_body_atlas]`, CPT schorzeń, kategorie, możliwość wyboru stron/wpisów i dotychczasowe modele GLB.
- Aktualizacja nie zmienia zapisanych pozycji globalnych pinezek. Dawne kotwice wskazujące na siatki zastąpionych paliczków/kości dłoni i stóp mogą wymagać ręcznego ponownego przypięcia.

### Weryfikacja
Uruchomiono testy składni PHP i JS oraz lokalną symulację API geometrii (Node.js): 268 siatek kończyn/stawów, 31 siatek powłoki, 48 siatek mięśniowych. Potwierdzono podział 27 kości na dłoń i 26 na stopę, brak niepoprawnych współrzędnych lub indeksów trójkątów, wyższy łuk przyśrodkowy i obecność niezmienionych kluczy konfiguracji. Paczka ZIP przeszła kontrolę integralności.

Nie wykonano pełnego testu end-to-end w rzeczywistym WordPressie ani wizualnego przeglądu modelu na rzeczywistym silniku Three.js. Przed zastosowaniem produkcyjnym potrzebny jest staging, przegląd anatomiczny i kontrola pinezek.

### Integralność archiwum wydania
SHA-256: `7889b53af181733d8075a1fe10c25c86bdc57d592bbc69dbce56e7b67142f493`

## Materiały referencyjne
- Hand Bones (27): https://www.ncbi.nlm.nih.gov/books/NBK547684/
- Foot and Ankle (26): https://www.ncbi.nlm.nih.gov/books/NBK546698/
- Medial longitudinal arch: https://www.ncbi.nlm.nih.gov/books/NBK562289/

## Ograniczenie dystrybucji
W tej iteracji pełny kod źródłowy v2.2.0 i ZIP pozostają w paczce instalacyjnej przekazanej użytkownikowi w rozmowie. W repozytorium GitHub opublikowano dokumentację wydania, nie pełen kod. Nie oznaczać repozytorium jako gotowego do instalacji.

Model ma charakter ilustracyjno-edukacyjny; nie jest modelem osobniczym 1:1 ani certyfikowaną rekonstrukcją CT/MRI.