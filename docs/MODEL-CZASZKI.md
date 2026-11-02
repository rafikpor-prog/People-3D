# Model czaszki — pochodzenie, prawa i integracja

## Zewnętrzny model

- Nazwa: **ScatteringSkull**
- Autor: Vladimir Petkovic, 2025
- Kolekcja: Khronos Group / glTF Sample Assets
- Licencja modelu: **CC0 1.0 Universal**, https://github.com/KhronosGroup/glTF-Sample-Assets/blob/main/Models/ScatteringSkull/LICENSE.md
- Źródło modelu: https://github.com/KhronosGroup/glTF-Sample-Assets/tree/main/Models/ScatteringSkull
- Plik: https://raw.githubusercontent.com/KhronosGroup/glTF-Sample-Assets/c2062ec0766461d601e3f26005f4d19f32247479/Models/ScatteringSkull/glTF-Binary/ScatteringSkull.glb
- Deklarowany rozmiar: 8 959 044 bajtów
- Oczekiwany Git blob SHA-1: `9e1927babc5791067ccf2004bda7e59a40cac753`

Wtyczka v1.5 wprowadza model jako zewnętrzny GLB, pobierany przez przeglądarkę, dopóki administrator nie wybierze instalacji lokalnej. Zapis do katalogu WordPress uploads jest realizowany po stronie PHP metodą `download_url()`, weryfikuje nagłówek `glTF`, limit rozmiaru i SHA-1 Git blob przed zapisaniem URL w `modelUrls.skull`.

Hash liczony jest jako SHA-1 bajtów `blob <size>\0<content>`, zgodnie z formatem obiektów Git. Kontrola integralności nie zastępuje testów zaufania do autorstwa modelu.

## Dlaczego nadal nie „1:1”?

To wysokiej jakości siatka 3D, a nie pozyskane z badań CT/MRI, certyfikowane odwzorowanie osobniczej anatomii. W szczególności wymaga recenzji anatomicznej, odpowiedniego oznaczania indywidualnych kości, tekstur i oceny innych warstw przed deklaracją dokładności medycznej.

## Kontrola regresji

- Aktualizacja z v1.4 nie zmienia nazwy opcji WordPress `mba_atlas_data`.
- Pinezki przetrwają, łącznie z przypisaniami do CPT schorzeń, stron i wpisów.
- Pinezki przypięte do wcześniejszych siatek przechodzą na zapasowe współrzędne globalne, gdy poprzedni `anchor.structureKey` nie istnieje w nowej geometrii.
- Zapisany URL lokalnego modelu ma priorytet przed modelem domyślnym.
- Jeśli model nie wczyta się z Internetu, zostanie wyświetlony ilustracyjny proceduralny zapasowy model czaszki.
- Import pełnego, zewnętrznego modelu szkieletu wyłącza domyślną osobną czaszkę.
- Wersja v1.5 wymaga osobnego testu na rzeczywistym WP/WebGL oraz urządzeniu mobilnym przed produkcją.

