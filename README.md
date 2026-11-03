# People-3D — Medical Body Atlas

Repozytorium projektu interaktywnego atlasu 3D dla WordPress. Projekt rozwijany na potrzeby prezentowania obszarów ciała, schorzeń i powiązanych informacji kliniki w języku polskim.

## Stan: 2 listopada 2026

Opracowana paczka instalacyjna **Medical Body Atlas 3D v1.5.0** (testowa) zachowuje schemat konfiguracji `mba_atlas_data`, typ wpisu `mba_condition`, taksonomię `mba_condition_category`, zarządzanie pinezkami i powiązania z wpisami i stronami WordPress.

**Uwaga:** w tym momencie repozytorium służy do dokumentowania architektury, źródeł zewnętrznych modeli i zakresu aktualizacji. Cały historyczny kod wtyczki v1.0–1.5 nie został jeszcze przeniesiony do repozytorium. Nie traktuj tego repo jako kompletnego wydania instalacyjnego.

### Model czaszki

Aktualizacja v1.5 wykorzystuje jako domyślną siatkę GLB projekt [ScatteringSkull](https://github.com/KhronosGroup/glTF-Sample-Assets/tree/main/Models/ScatteringSkull) (Vladimir Petkovic, **CC0 1.0**). Geometria jest importowana przez Three.js, skalowana względem wymiarów głowy w atlasie, zastępuje proceduralną czaszkę i używa materiału matowej kości. W panelu administrator może pobrać i zainstalować plik we własnej bibliotece WordPress. Źródło i identyfikator SHA-1 Git znajdują się w [dokumentacji](docs/MODEL-CZASZKI.md).

Nie jest to rekonstrukcja TK pacjenta ani certyfikowany atlas diagnostyczny; poszczególne kości czaszki nie muszą być niezależnymi siatkami.

### Konwencje

- WordPress 6.x, PHP 7.4+ (testy syntaktyczne), Three.js / WebGL.
- Pin: `id`, `title`, `position` [x, y, z], `anchor` (warstwa, ścieżka siatki, lokalne położenie), `conditionIds`, `contentIds`, `enabled`.
- Typy warstw: `bones`, `skull`, `muscles`, `organs`, `skin`.
- Shortcode: `[medical_body_atlas]`.
- Nie udostępniać osobowych danych pacjentów przez pinezki ani katalog schorzeń.

### Następny krok rozwoju

Przenieść do repozytorium kompletny kod wtyczki, dodać ciągłą integrację testów PHP/JS, lokalne bundlowanie Three.js, osobne licencjonowane warstwy anatomiczne i procedurę przeglądu merytorycznego przez anatoma.

Licencja kodu repozytorium: GPL-3.0 (plik LICENSE). Licencje zewnętrznych modeli pozostają niezależne.


## Aktualizacja 1.7.0 (2 listopada 2026)

W przygotowanej paczce instalacyjnej WordPress 1.7.0 ulepszono proceduralną powłokę ciała (płynne przekroje tułowia i kończyn), rozbudowano geometrię kości ramiennych, promieniowych, łokciowych, udowych, piszczelowych i strzałkowych oraz dodano przełączaną warstwę 34 poglądowych struktur mięśniowych. Zachowano pinezki, katalog schorzeń, kategorie i import GLB.

Weryfikacja lokalna: składnia PHP/JS, test siatek 3D (31 siatek powłoki, 34 siatki mięśni; wszystkie współrzędne skończone, prawidłowe indeksy), kontrole regresyjne funkcji WordPress oraz integralność ZIP. **Brak jeszcze pełnych testów wizualnych i instalacyjnych na WordPressie**. Geometryczny model proceduralny nie jest rekonstrukcją anatomiczną 1:1 ani narzędziem diagnostycznym.

**Status repozytorium:** na razie dokumentacja projektu; pełnego kodu wtyczki i paczki ZIP v1.7.0 nie opublikowano jeszcze w repo. Wydanie ZIP przekazano bezpośrednio w rozmowie, a źródła mogą zostać przeniesione do repo w następnym kroku.


## Aktualizacja 1.8.0 — kości kończyn i stawy (2026-11-02)

Nowa paczka instalacyjna WordPress Medical Body Atlas 3D v1.8.0 została przygotowana na bazie v1.7.0. Zawiera osobny moduł `assets/joints.js`, który zastępuje uproszczone kończyny procedurami z indywidualnymi głowami i nasadami kości, kłykciami, rzepką, strukturami nadgarstka i stępu oraz delikatnymi powierzchniami stawowymi. Dodano subtelną kontrolkę `Zbliż staw…` i obsługę wybierania nazwanych struktur przy pinezkach.

Zachowano dane `mba_atlas_data`, dotychczasowe modele czaszki, skóry i mięśni, typ wpisów schorzeń, kategorie oraz przypisania stron/wpisów. Zapis konfiguracji i jego schemat nie zostały zmienione.

**Weryfikacja techniczna:** składnia PHP/JS, symulowane testy generowania 198 siatek kończyn i stawów (176 kości + 22 powierzchnie stawowe), indeksy trójkątów, skończone współrzędne, integralność ZIP. **Nie wykonano pełnego testu wizualnego w działającym WordPress.**

**Dokładność:** kończyny są rekonstrukcją poglądową, nie certyfikowanym modelem medycznym 1:1. Dokumentacja techniczna znajduje się w [docs/WYDANIE-1.8.0.md](docs/WYDANIE-1.8.0.md).

**Źródła:** paczka ZIP i kod `assets/joints.js` nie zostały jeszcze przesłane do GitHub; repozytorium wciąż zawiera dokumentację. Kolejny etap to przeniesienie całych źródeł, testów i workflow GitHub Actions.


## Aktualizacja 2.2.0 — dłonie, stopy i mięśnie (2026-11-03)

Przygotowano kolejną instalacyjną paczkę WordPress Medical Body Atlas 3D. Zawiera niezależnie nazwane kości dłoni (27/dłoń) i stopy (26/stopę), wygładzony spód stopy z łukiem przyśrodkowym i wybrane mięśnie wewnętrzne dłoni/stopy. Pozostają dotychczasowe schorzenia, kategorie, pinezki, import GLB i shortcode. Wyniki testów lokalnych i ograniczenia opisano w [dokumentacji wydania 2.2.0](docs/WYDANIE-2.2.0.md).

**Repozytorium nadal zawiera dokumentację, a nie kompletny kod źródłowy gotowy do instalacji.** Pełna paczka ZIP została przekazana w rozmowie i przed wdrożeniem wymaga testów staging i wizualnych.
