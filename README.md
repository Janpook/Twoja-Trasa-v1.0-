# TwojaTrasa.online - Wersja 1.0 (Archiwalna)

![Logo Aplikacji](https://twojatrasa.online/favicons.png)

Aplikacja webowa do śledzenia komunikacji miejskiej w Poznaniu w czasie rzeczywistym. Projekt w wersji 1.0 został stworzony w oparciu o czysty HTML, CSS i JavaScript, intensywnie wykorzystując dane GTFS i GTFS-Realtime.

* **Licencja:** GNU AGPLv3
* **Link do aktualnej wersji aplikacji:** [https://twojatrasa.online](https://twojatrasa.online)

## O Projekcie

`TwojaTrasa.online` to niezależny projekt hobbystyczny, którego celem jest dostarczenie mieszkańcom Poznania i okolic interaktywnego narzędzia do monitorowania lokalizacji pojazdów komunikacji miejskiej. Aplikacja pozwala na żywo śledzić autobusy i tramwaje, przeglądać informacje o opóźnieniach, planować podróże oraz personalizować wygląd i działanie interfejsu.

## Dlaczego Open Source?

Udostępniam kod źródłowy wersji 1.0 z kilku powodów:

* **Edukacja i Transparentność:** Chcę pokazać, jak aplikacja działa "od kuchni". Mam nadzieję, że ktoś, kto stawia pierwsze kroki w programowaniu aplikacji webowych lub pracy z danymi GTFS, znajdzie tu coś dla siebie i czegoś się nauczy.
* **Społeczność i Pasja:** Projekt narodził się z pasji do komunikacji miejskiej i technologii. Wierzę, że dzielenie się kodem może pomóc w budowaniu społeczności o podobnych zainteresowaniach.
* **Archiwum:** Ten kod to zapis początków i fundamentu, na którym wyrosła `TwojaTrasa.online`. To ciekawy wgląd w to, jak projekt ewoluował.

## Informacja o Wersji 2.0

**Ważne:** Kod w tym repozytorium reprezentuje **historyczną wersję 1.0 aplikacji** i ma charakter archiwalny.

Obecnie rozwijana jest **wersja 2.0**, która nie jest jeszcze publicznie dostępna. Została ona przepisana od podstaw i używa zupełnie innej, nowocześniejszej struktury oraz technologii, które pozwoliły na znaczną poprawę wydajności, skalowalności i dodanie wielu nowych funkcji.

To repozytorium pozostaje jako pamiątka, wgląd w początki projektu oraz jako zasób edukacyjny. Nie jest ono już aktywnie rozwijane.

## Główne Funkcje (v1.0)

Projekt w tej wersji składa się z kilku zintegrowanych modułów:

#### 🗺️ Mapa i Śledzenie (`index.html`)
* Interaktywna mapa (Leaflet) z pozycjami pojazdów aktualizowanymi na żywo.
* Grupowanie pojazdów na mapie (Marker Clustering) dla większej czytelności.
* Szczegółowe informacje w dymkach (popup) po kliknięciu na pojazd: linia, kierunek, numer taborowy, model, prędkość, status i opóźnienie.
* Filtrowanie pojazdów (wszystkie, tramwaje, autobusy, ulubione).
* Wyszukiwarka linii, przystanków i numerów taborowych.
* Możliwość wyświetlenia pełnej trasy kursu oraz historii przejazdu (śladu GPS) na mapie.

#### 规划 Planowanie Trasy (`zaplanuj.html`)
* Interfejs do planowania podróży z punktu A do punktu B.
* Autouzupełnianie nazw przystanków w oparciu o dane statyczne GTFS.
* Wyświetlanie linii odjeżdżających z wybranych przystanków.
* Przekazywanie wybranych przystanków do widoku mapy w celu ich podświetlenia.
* *Funkcjonalność automatycznego wyszukiwania połączeń jest zaplanowana na przyszłe wersje.*

#### 📊 Informacje i Statystyki
* **Statystyki Systemu (`stats.html`):** Panel wyświetlający na żywo dane o systemie, m.in. liczbę aktywnych pojazdów, kursów, statusy komponentów i jakość danych GPS.
* **Lista Pojazdów (`pojazdy.html`):** Katalog dostępnego taboru z podziałem na modele, listą numerów rejestracyjnych i informacjami o udogodnieniach (klimatyzacja, rampy, USB itp.). Możliwość filtrowania i eksportu danych do CSV.

#### ⚙️ Personalizacja (`menu.html`)
* Centralne menu nawigacyjne.
* Przełącznik motywu (jasny/ciemny).
* Ustawienia widoczności przystanków i grupowania ikon na mapie.
* Możliwość zmiany stylu ikon pojazdów (pełna ikona lub minimalistyczna kropka).
* Personalizacja kolorów dla rysowanej trasy i śladu pojazdu.

## Technologie

* **Frontend:** HTML5, CSS3, JavaScript (ES6+)
* **Mapy:** [Leaflet.js](https://leafletjs.com/), [Leaflet.markercluster](https://github.com/Leaflet/Leaflet.markercluster)
* **Przetwarzanie Danych:** [Protobuf.js](https://github.com/protobufjs/protobuf.js) (dla GTFS-RT), [PapaParse](https://www.papaparse.com/) (dla plików .txt/.csv)
* **Dane:** ZTM Poznań (GTFS i GTFS-RT)

## Struktura Projektu

Główne pliki aplikacji w wersji 1.0:

* `index.html`: Główny widok mapy na żywo.
* `menu.html`: Strona z menu głównym i ustawieniami.
* `zaplanuj.html`: Dedykowana strona do planowania trasy.
* `pojazdy.html`: Katalog taboru.
* `stats.html`: Strona ze statystykami systemu.
* `proxy.php`: Skrypt po stronie serwera do pobierania danych GTFS-RT (nieudostępniony w kodzie).
* `*.txt`, `*.js` (dane): Pliki statyczne GTFS oraz dane o trasach i modelach.

## Jak Uruchomić Lokalnie

1.  Sklonuj repozytorium:
    ```bash
    git clone [URL_DO_TWOJEGO_REPOZYTORIUM]
    ```
2.  Upewnij się, że masz działający serwer WWW (np. Apache, Nginx, lub prosty serwer Pythona/Node.js), ponieważ przeglądarka blokuje żądania `fetch()` do plików lokalnych (CORS).
3.  Umieść pliki projektu w głównym katalogu serwera.
4.  Aplikacja wymaga działającego `proxy.php` do pobierania danych na żywo. Należy go skonfigurować tak, aby pobierał i zwracał dane binarne GTFS-Realtime ze źródła ZTM Poznań.
5.  Otwórz stronę w przeglądarce.

---
