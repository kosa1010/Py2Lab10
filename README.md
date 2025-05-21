## Biblioteka [Pandas](https://pandas.pydata.org/docs/user_guide/index.html) i [h5py](https://docs.h5py.org/en/latest/quick.html).

Co to jest Pandas?
Pandas to potężna biblioteka Pythona do analizy i manipulacji danych. Główne struktury danych to:
Series - jednowymiarowa tablica z etykietami
DataFrame - dwuwymiarowa tabela danych (jak arkusz kalkulacyjny)

### Podstawowe operacje w Pandas
```Python
import pandas as pd

# Tworzenie DataFrame
df = pd.DataFrame({
    'Imię': ['Anna', 'Jan', 'Kasia', 'Piotr'],
    'Wiek': [23, 35, 29, 40],
    'Miasto': ['Warszawa', 'Kraków', 'Poznań', 'Warszawa']
})

print(df)

# Filtrowanie danych
print(df[df['Wiek'] > 30])

# Grupowanie
grupa = df.groupby('Miasto')['Wiek'].mean()
print(grupa)
```

#### Zadanie 1: Podstawowe operacje
- Stwórz DataFrame z danymi o produktach (nazwa, cena, ilość)
- Wyświetl tylko produkty droższe niż 50 zł
- Oblicz całkowitą wartość magazynu (cena * ilość dla każdego produktu)


### HDF5 i h5py
Co to jest HDF5?
HDF5 (Hierarchical Data Format) to format plików do przechowywania i organizowania dużych ilości danych. Biblioteka h5py umożliwia pracę z tym formatem w Pythonie.

Podstawowe operacje z h5py
```python
import h5py

# Tworzenie pliku HDF5
with h5py.File('przyklad.h5', 'w') as plik:
    # Tworzenie datasetu
    plik.create_dataset('temperatury', data=[20.5, 21.3, 19.8, 22.1])
    
    # Tworzenie grupy
    grupa = plik.create_group('pomiary')
    grupa.create_dataset('wilgotność', data=[45, 47, 42, 43])
```
#### Zadanie 2:
- Stwórz plik HDF5 z danymi pogodowymi (temperatura, wilgotność, ciśnienie)
- Odczytaj dane z pliku
- Dodaj nowe dane do istniejącego pliku


### Integracja Pandas i h5py
Zapisywanie DataFrame do HDF5
```python
# Zapisywanie DataFrame do HDF5
df_produkty.to_hdf('magazyn.h5', key='produkty', mode='w')

# Odczyt z HDF5 do DataFrame
df_odczyt = pd.read_hdf('magazyn.h5', key='produkty')
print(df_odczyt)
```
#### Zadanie 3: Integracja
- Stwórz DataFrame z danymi o sprzedaży dowolnych produktów zawierający datę tranzakcji, nazwę produktu ilość sprzedanych sztuk oraz cenę jednostkową produktu
- Zapisz go do pliku HDF5
- Odczytaj dane z pliku i wykonaj analizę (np. kwotę sprzedaży wszystkich produktów i z podziałem na ich rodzaj)


#### Zadanie 4: Analiza danych
Masz następujące dane:

```python
dane = {
    'Pracownik': ['Jan', 'Anna', 'Piotr', 'Maria'],
    'Dział': ['IT', 'HR', 'IT', 'Finanse'],
    'Wynagrodzenie': [8500, 7200, 9000, 6800],
    'Staż': [3, 5, 2, 4]
}
```
- Oblicz średnie wynagrodzenie w każdym dziale
- Znajdź pracownika z najdłuższym stażem
- Dodaj kolumnę z premią (10% wynagrodzenia dla stażu >3 lata, 5% dla pozostałych)

#### Zadanie 5: Praca z HDF5
Stwórz plik HDF5 z danymi sensorów (temperatura, wilgotność, czas odczytu)
- Zapisz dane z tygodnia (możesz użyć danych losowych)
- Odczytaj tylko dane z temperaturą powyżej 25 stopni
