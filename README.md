# Rozpoznawanie tożsamości na podstawie tęczówki oka

## Opis projektu
Ten projekt implementuje pełny łańcuch przetwarzania obrazu do rozpoznawania osób na podstawie zdjęć oczu. System wykorzystuje algorytm Daugmana do kodowania tęczówki i odległość Hamminga do porównywania kodów tęczówek.

## Funkcjonalności
- Automatyczna segmentacja źrenicy
- Automatyczna segmentacja tęczówki
- Rozwinięcie tęczówki do postaci prostokątnej 
- Ekstrakcja cech z tęczówki metodą Daugmana
- Porównywanie kodów tęczówek przy użyciu odległości Hamminga
- Wyczerpująca analiza eksperymentalna na zbiorze danych MMU Iris Dataset

## Technologie
- Python jako główny język programowania
- OpenCV-Python do operacji przetwarzania obrazów
- NumPy do obliczeń macierzowych 
- Matplotlib i Seaborn do wizualizacji wyników
- Jupyter Notebook jako środowisko eksperymentalne

## Struktura projektu
- `detekcja_teczowki.ipynb` - główny notebook z kompletną logiką biznesową
- `MMU-Iris-Database/` - zbiór danych z obrazami oczu (nie jest zawarty w repozytorium)
- `renamed_photos/` - katalog tworzony podczas wykonywania skryptu, zawierający przetworzone obrazy
- Pozostałe katalogi to efekty wywoływań poszczególnych komórek, niezbędne do sprawozdania.  

## Metodologia
1. **Segmentacja źrenicy**:
   - Konwersja do skali szarości
   - Wyrównanie kontrastu (CLAHE) i gaussian blur
   - Filtrowanie, binaryzacja i operacje morfologiczne
   - Lokalizacja środka i promienia

2. **Segmentacja tęczówki**:
   - Gaussian blur i binaryzacja
   - Operacje morfologiczne
   - Wyznaczanie promienia tęczówki metodą histogramu radialnego oraz projekcji

3. **Rozwinięcie tęczówki**:
   - Transformacja z układu biegunowego do kartezjańskiego
   - Uzyskanie prostokątnej reprezentacji tęczówki

4. **Kodowanie tęczówki**:
   - Podział na radialne pasma
   - Filtrowanie falkami Gabora
   - Generowanie binarnego kodu tęczówki

5. **Porównywanie kodów**:
   - Obliczanie odległości Hamminga
   - Klasyfikacja na podstawie progu odległości

## Wydajność
- Precyzja: 98.95%
- Czułość (Recall): 52.44%
- F1-Score: 68.55%
- Dokładność: 99.57%

System jest zoptymalizowany pod kątem minimalizacji fałszywych dopasowań kosztem odrzucenia niektórych prawidłowych dopasowań, co czyni go odpowiednim do zastosowań związanych z bezpieczeństwem.

## Instalacja i uruchomienie
1. Sklonuj repozytorium
   ```
   git clone https://github.com/JakubPoltorak147/Biometria_Projekt2.git
   ```
2. Zainstaluj wymagane zależności
   ```
   pip install numpy opencv-python matplotlib seaborn jupyter
   ```
3. Niezbędny będzie zbiór danych MMU-Iris-Database. Jeśli wystąpią jakieś problemy z klonowaniem, pobierz go z internetu i skopiuj zawartość do katalogu o tej nazwie.
4. Uruchom notebook
   ```
   jupyter notebook detekcja_teczowki.ipynb
   ```

## Autorzy
- Jakub Półtorak [@JakubPoltorak147](https://github.com/JakubPoltorak147)
- Michał Pytel [@MichalPytel](https://github.com/MichalPytel)

## Uwagi
System pokazuje potencjał do dalszej optymalizacji parametrów - autorzy zauważają, że podczas eksperymentów uzyskali F1-score powyżej 0.70, który później spadł do 0.685 z powodu nieudanych modyfikacji parametrów.
