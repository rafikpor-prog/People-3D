# Medical Body Atlas 3D v1.8.0 — aktualizacja stawów

Data: 2 listopada 2026

## Zakres

Wtyczka zachowuje shortcode `[medical_body_atlas]`, schemat danych `mba_atlas_data`, pinezki, katalog i kategorie schorzeń oraz warstwy GLB.

Nowy moduł JavaScript `assets/joints.js` przyjmuje argumenty `THREE`, `skeletonGroup` oraz `boneMaterial`. Generuje niezależne struktury kości ramiennej, promieniowej, łokciowej, udowej, piszczelowej, strzałkowej, nadgarstka, dłoni i stóp. Do stawów dodano osobne obiekty dla barku, łokcia, nadgarstka, biodra, kolana i stawu skokowego. Materiał kości jest matowy, a struktury chrząstkowe są lekko odróżnione.

W `viewer.js` dodano grupę `detailedLimbs` oraz rejestrację jej nazwanych siatek w indeksie struktur służącym do precyzyjnego przypinania punktów. Dodano niewielki selektor zbliżeń do sześciu obszarów stawowych.

W `medical-body-atlas.php` zarejestrowano skrypt `mba-joints` i uzależniono od niego skrypt `mba-viewer` oraz zwiększono wersję do 1.8.0. Zachowano dotychczasowe dane oraz konfigurację.

## Testy wykonane

- `php -l medical-body-atlas.php`: bez błędów.
- `node --check`: poprawna składnia wszystkich plików JS.
- Izolowany test siatek z atrapą API Three.js: 176 siatek kości i 22 powierzchnie stawowe, łącznie 198.
- Sprawdzenie skończoności współrzędnych i poprawnego indeksowania trójkątów.
- Test integralności archiwum ZIP: pozytywny.

### Testy nieprzeprowadzone

Nie zweryfikowano jeszcze wizualnie modelu w działającym WordPress ani na urządzeniach mobilnych. Testy API Three.js były symulowane, nie stanowią pełnej integracji WebGL. Przed wdrożeniem produkcyjnym należy uruchomić testy manualne i wykonać kopię bazy.

## Ograniczenia

Model proceduralny jest poglądowy. Proporcje, geometrię nasad, powierzchni stawowych i układ drobnych kości należy zweryfikować u anatoma przed oznaczeniem produktu jako pełnego atlasu medycznego 1:1. Wykorzystane elementy nie służą diagnostyce ani planowaniu zabiegów.

Pełne źródła aktualizacji nie zostały w tym kroku opublikowane w repozytorium GitHub; są w paczce ZIP przekazanej użytkownikowi w rozmowie.
