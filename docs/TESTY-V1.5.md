# Plan testów przed wydaniem produkcyjnym

1. Użyć środowiska staging, kopii bazy danych i aktywnej wtyczki z wersji v1.4.
2. Zanotować listę pinezek, ich współrzędne oraz powiązania ze schorzeniami, stronami i wpisami.
3. Zainstalować v1.5 bez usuwania danych i porównać konfigurację.
4. Sprawdzić obracanie, przesuwanie celu kamery, zoom czaszki, front/tył, WebGL na mobilnym Safari/Chrome.
5. Potwierdzić, że domyślny GLB ładuje się przy dostępnym Internet i odpowiedniej polityce CSP; zweryfikować awaryjny wygląd przy zablokowanej domenie raw.githubusercontent.com.
6. W edytorze zapisać zmianę pinezki, podpiąć opublikowaną stronę i wpis, przypisać schorzenie/kategorię. Ponownie wczytać stronę i sprawdzić dane.
7. Użyć „Zainstaluj model czaszki lokalnie” i zweryfikować, czy powstał plik .glb w WordPress uploads oraz czy frontend nie pobiera go już z GitHub.
8. Sprawdzić uprawnienia REST — brak uprawnień powinien zwracać 403.
9. Wykonać ręczny przegląd anatomii modelu; nie deklarować zastosowań diagnostycznych bez walidacji.

Dotychczasowe kontrole lokalne: `php -l`, `node --check`, integralność ZIP i testy symulacyjne zachowania istniejących pinezek/taksonomii. Nie zastępują one testu wizualnego end-to-end.
