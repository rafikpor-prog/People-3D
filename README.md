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
