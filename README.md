## Biblioteka Pandas i h5py.
Co to jest Pandas?
Pandas to potężna biblioteka Pythona do analizy i manipulacji danych. Główne struktury danych to:
Series - jednowymiarowa tablica z etykietami
DataFrame - dwuwymiarowa tabela danych (jak arkusz kalkulacyjny)

#### Podstawowe operacje w Pandas
```Python
import pandas as pd

# Tworzenie DataFrame
data = {
    'Imię': ['Anna', 'Jan', 'Maria', 'Krzysztof'],
    'Wiek': [25, 32, 28, 40],
    'Miasto': ['Warszawa', 'Kraków', 'Gdańsk', 'Wrocław']
}
df = pd.DataFrame(data)
print(df)
```

