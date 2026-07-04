# Raport — Zadanie 4: Wizualizacja rynku koncertów w Polsce

Interaktywne wykresy (HTML, plotly) znajdują się w katalogu `wykresy_zadanie_4/`.

## Komentarz do części 4 (histogram + boxplot)

Testowane wartości `nbins`: 20, 50 i 100. Wartość **50** najlepiej pokazuje
kształt rozkładu — 20 koszy zlewa szczegóły, a 100 daje poszarpany wykres.
Rozkład cen biletów jest **prawostronnie skośny**: większość biletów kosztuje
do ~250 PLN, a długi ogon tworzą drogie koncerty stadionowe i festiwalowe.

Najwyższe przychody z pojedynczego koncertu generują obiekty typu
**stadion** (mediana ~6,654,800 PLN) — duża pojemność
mnoży się przez wysokie ceny biletów. Kluby i teatry, mimo największej liczby
imprez, mają o rzędy wielkości niższe przychody jednostkowe.

## Komentarz do części 5 (scatter)

Współczynnik korelacji między ceną biletu a wypełnieniem sali wynosi
**0.009** — praktycznie brak zależności. Wypełnienie sali jest
podobne w całym zakresie cen, co sugeruje, że popyt zależy od artysty
i wydarzenia, a nie od samej ceny biletu.

## Wnioski (część 8)

1. **Warszawa dominuje na rynku** — najwięcej koncertów
   (241) i najwyższy łączny przychód; kolejne są Kraków i Wrocław,
   co odpowiada wielkości tych miast.
2. **Najwyższe ceny biletów są na stadionach** (średnio
   ~251 PLN) i festiwalach — mnożnik prestiżu i skali;
   najtańsze są koncerty klubowe (~101 PLN).
3. **Przychody napędzają wielkie obiekty**: stadiony i festiwale to tylko
   17% imprez, ale generują 81% przychodu.
4. **Brak wyraźnej sezonowości** — liczba koncertów w miesiącach waha się
   losowo (od 86 do 112 rocznie na miesiąc),
   bo daty w zbiorze są losowane jednostajnie; w prawdziwych danych
   spodziewalibyśmy się szczytu festiwalowego latem.
5. **Cena nie steruje frekwencją** — brak korelacji ceny z wypełnieniem sali
   oznacza, że organizatorzy mają przestrzeń do optymalizacji cen bez ryzyka
   pustych sal.
