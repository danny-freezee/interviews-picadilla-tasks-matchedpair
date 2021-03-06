# Matched Pair algorithm (how-to)

## Opis zastosowanego podejścia do rozwiązania zadania:

Opis szczegółowy zastosowanego podejścia oraz przebieg algorytmu dla przykładowych danych znajduje się pod adresem:

* https://daniel-fryze-matchedpair-task.herokuapp.com

## Krótki opis klas znajdujących się w projekcie:

Klasa z implementacją algorytmu:

* _MatchedPair_ - główna klasa zawierająca implementację algorytmu zgodnie z treścią zadania

#### Metoda algorytmu do zaimplementowania **(uwaga: zmiana)**:

Pierwotna sygnatura wymaganej do zaimplementowania metody wyglądała tak:
```
int matchedPair(int[] P, int[] Q)
```
Musiała ona zostać zmieniona na następującą sygnaturę:
```
long matchedPair(int[] P, int[] Q)
```
Bowiem, zgodnie z opisem algorytmu, oraz zadanymi ograniczeniami dla liczby danych wejściowych, maksymalna wartość wyniku do uzyskania przez algorytm: **4.999.950.000**.

Na przykład dla danych wejściowych w postaci:

>P - tablica 100.000 liczb o takiej samej wartości: 10, czyli [10, 10, 10 ... 10]

>Q - tablica 100.000 liczb o takiej samej wartości: 10, czyli [1, 1, 1 ... 1]

Wynik algorytmu to suma ciągu arytmetycznego w postaci: 99.999 + 99.998 + ... + 1, czyli: **4.999.950.000**.

Natomiast w Javie maksymalna wartość dla typu prostego _int_ wynosi: **2.147.483.647**.

Zatem, aby poprawnie zwrócić wynik z algorytmu musimy użyc typu prostego o większym zakresie, np. zastosowany _long_, którego maksymalna wartość wynosi już **9.223.372.036.854.775.807**. 

Od strony logicznej, zmiana ta nie wpływa na działanie samego algorytmu.

Ponadto, dodano również opcjonalny argument dodatkowy w postaci flagi logicznej (typ _boolean_) na końcu listy argumentów wywołania metody:
```
long matchedPair(int[] P, int[] Q, boolean ... args)
```
Działa on w sposób następujący:
* podanie wartości 'true' dla tego argument dezaktywuje walidację danych wejściowych (tablic z liczbami)
* pominięcie go w wywołaniu metody lub podanie wartości 'false' pozostaia aktywną walidację

Jego zastosowanie ma miejsce w testach, gdzie dla celów wydajnościowych można wyłączyć walidację danych wejściowych, przyjmując, że wartości te spełniają wymóg zadany w opisie algorytmu. 

Jako że jest opcjonalny, to de facto nie wpływa na sygnaturę metody.

Klasy pomocnicze:

* _MatchedPairBruteForce_ - zawiera implementację 'brute-force' dla zadanego algorytmu (do celów testowych)
* _BigDecimalConverter_ - konwersja danych wejściowych na listę liczb zmiennoprzecinkowych dla bazowego modułu
* _MatchedPairInputValidator_ - zawiera logikę walidacji danych wejściowych zgodnie z regułami opisanymi w opisie

Klasy z testami:

* _MatchedPairInputInvalidTest_ - klasa z testami pokrywającymi przypadki danych wejściowych niezgodnych ze specyfikacją (sprawdzają walidację danych wejściowych algorytmu)
* _MatchedPairInputValidTest_ - klasa z testami pokrywającymi przypadki danych wejściowych poprawnych (sprawdzją de facto faktyczne działanie algorytmudla poprawnych danych wejściowych)
* _MatchedPairRandomInputsTest_ - klasa z testami algortymu dla losowych danych wejściowych (punktem odniesienia dla wyników algorytmu jest wynik algorytmu 'brute-force' dla tych samych danych wejściowych)

Szczegółowe opisy klas znajdują się w dokumentacji _java-doc_ w kodzie projektu.

## Uruchomienie projektu:

#### Warunki wstępne:

Aby uruchomić kod projektu, wymagane jest posiadanie: komputera z dowolnym systemem operacyjnym, zainstalowaną Javą 8, Mavenen'em i Git'em, oraz połączeniem do internetu.

#### Kroki:

1) Sklonowanie kodu z repozytorium na lokalny dysk twardy:

```
git clone https://github.com/daniel-fryze/inteview-medications-app-daniel-fryze.git
```

2) Nawigacja do katalogu głównego projektu:

```
cd interviews-picadilla-tasks-matchedpair
cd task.matchedpair
```

3) Uruchomienie wszystkich testów dla projektu:

```
mvn clean test
```

Powodzenia :)
