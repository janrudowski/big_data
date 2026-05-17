# Raport - Zadanie 3

## Część 1 - Wstępna eksploracja
- Shape: (2000, 10)
- Braki danych:
id_oferty                  0
dzielnica                  0
metraz_m2                  0
liczba_pokoi               0
pietro                     0
rok_budowy                 0
ma_balkon                  0
ma_miejsce_parkingowe      0
odleglosc_od_centrum_km    0
cena_pln                   0

Podejrzane obserwacje ze statystyk opisowych:
- Maksymalna cena jest wielokrotnie większa od mediany, co sugeruje drogie penthouse'y lub błędy w cenie.
- Minimalna cena jest bardzo niska względem mediany, co wygląda jak błąd danych albo podejrzana oferta.
- Maksymalny metraż przekracza 300 m2, więc w zbiorze są gigantyczne mieszkania odstające od typowych lokali.
- Lata budowy poza zakresem 1900-2026: 5 wierszy wymagających usunięcia.

## Część 2 - Statystyki opisowe
- Średnia cena: 880961.21 PLN
- Mediana ceny: 809575.50 PLN
- Odchylenie standardowe ceny: 749976.28 PLN
- Skewness ceny: 15.86
- Kurtosis ceny: 404.22
- Komentarz: dodatnia skośność oznacza długi prawy ogon, czyli część ofert ma wyjątkowo wysokie ceny.
- Metraż Q1: 40.80 m2
- Metraż Q3: 69.90 m2
- Metraż IQR: 29.10 m2
- Liczba dzielnic: 11

Liczba ofert w dzielnicach:
dzielnica
Mokotów           210
Targówek          189
Ursynów           189
Śródmieście       189
Ochota            188
Wola              178
Białołęka         177
Bemowo            176
Bielany           174
Praga-Południe    166
Wilanów           164

## Część 3 - Analiza pojedynczych zmiennych
- Histogramy ceny i metrażu pokazują prawostronną skośność oraz obserwacje odstające.
- Boxplot ceny pokazuje bardzo wysokie punkty odstające.
- Countplot dzielnic zapisano z kolejnością malejącą według liczby ofert.

## Część 4 - Analiza zależności
- Najsilniejsza korelacja z ceną: liczba_pokoi (0.42).
- Najwyższa mediana ceny za m2: Śródmieście.

## Część 5 - Detekcja outlierów
- Cena IQR 1.5x: 39 outlierów
- Cena Z-score |z| > 3: 9 outlierów
- Cena Modified Z-score |z_mod| > 3.5: 22 outlierów
- Metraż IQR: 13 outlierów

Top 5 największych metraży:
 id_oferty      dzielnica  metraz_m2  cena_pln
     11598 Praga-Południe 585.187341  614202.0
     11846       Targówek 566.921693  593446.0
     10054      Białołęka 537.356930  595626.0
     11682       Targówek 473.491995  436705.0
     11051 Praga-Południe 324.358377  693470.0

Wiersze z nielogicznym rokiem budowy:
 id_oferty      dzielnica  rok_budowy  cena_pln
     10238       Targówek        1850  660629.0
     10558        Ursynów        2050  568546.0
     10636 Praga-Południe        1800 1323289.0
     11031 Praga-Południe        2050  723745.0
     11955        Wilanów        1800 1624939.0

## Część 6 - Decyzja i czyszczenie
- Liczba wierszy przed czyszczeniem: 2000
- Liczba wierszy po usunięciu nielogicznych lat: 1995
- Dodano kolumnę `cena_pln_capped` z capem na 1 i 99 percentylu.
- Dodano kolumnę `cena_pln_log` = log1p(cena_pln).
- Skewness przed logarytmizacją: 15.86
- Skewness po logarytmizacji: -0.24

## Wykresy
- wykresy_zadanie_3/01_histogramy_cena_metraz.png
- wykresy_zadanie_3/02_boxplot_cena.png
- wykresy_zadanie_3/03_countplot_dzielnice.png
- wykresy_zadanie_3/04_heatmapa_korelacji.png
- wykresy_zadanie_3/05_scatter_metraz_cena.png
- wykresy_zadanie_3/06_boxplot_cena_m2_dzielnice.png
- wykresy_zadanie_3/07_porownanie_log_ceny.png

## Część 7 - Wnioski
- Rozkład cen jest prawostronnie skośny: średnia (880961 PLN) jest wyższa niż mediana (809576 PLN), a skewness wynosi 15.86.
- Najsilniejszy związek z ceną ma zmienna liczba_pokoi (korelacja 0.42), co pokazuje, że cena całkowita zależy głównie od cech ilościowych lokalu.
- Najwyższą medianę ceny za m2 ma dzielnica Śródmieście; porównywanie ceny za m2 jest bardziej uczciwe niż porównywanie cen całkowitych.
- Metody outlierów wykrywają różne skale problemu: IQR dla ceny znalazł 39 obserwacji, Z-score 9, a Modified Z-score 22.
- Po usunięciu nielogicznych lat budowy zostało 1995 ofert; winsoryzacja ogranicza wpływ ekstremalnych cen, a logarytmizacja zmniejsza skośność rozkładu.
