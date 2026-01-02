# 🎲 Rozpoznawanie Sumy Oczek na Kostkach: CNN vs XGBoost

**Klasyfikacja sumy oczek na wielu kostkach przy użyciu komputerowej wizji i uczenia maszynowego**

Porównawcze studium tradycyjnego uczenia maszynowego (XGBoost z ręczną inżynierią cech) oraz głębokiego uczenia (CNN) do rozpoznawania sumy oczek na wielu kostkach z obrazów w skali szarości.

---

## 📋 Spis Treści

- [Opis Projektu](#-opis-projektu)
- [Zbiór Danych](#-zbiór-danych)
- [Funkcjonalności](#-funkcjonalności)
- [Modele](#-modele)
- [Wyniki](#-wyniki)
- [Instalacja](#-instalacja)
- [Użycie](#-użycie)
- [Struktura Projektu](#-struktura-projektu)
- [Kluczowe Wnioski](#-kluczowe-wnioski)

---

## 🎯 Opis Projektu

Projekt rozwiązuje problem **automatycznego rozpoznawania sumy oczek na kostkach** z obrazów 100×100 pikseli w skali szarości zawierających wiele kostek. Celem jest predykcja łącznej liczby widocznych oczek.

**Sformułowanie problemu:**
- **Wejście**: Obraz 100×100 w skali szarości przedstawiający kostki
- **Wyjście**: Suma wszystkich widocznych oczek (zakres: 5-30)
- **Wyzwania**: Zmienna liczba kostek, różne orientacje, warunki oświetleniowe

---

## 📊 Zbiór Danych

- **Źródło**: `dice5_sum_balanced.csv`
- **Rozmiar**: Zbalansowany zbiór danych z równą reprezentacją klas sum
- **Format**: CSV z pierwszą kolumną jako etykietą (suma), pozostałe 10,000 kolumn to spłaszczone wartości pikseli
- **Rozdzielczość obrazu**: 100×100 pikseli (skala szarości, 0-255)
- **Klasy**: 26 klas (sumy od 5 do 30)
- **Podział**: 
  - XGBoost: 80% treningowy / 20% testowy
  - CNN: 70% treningowy / 15% walidacyjny / 15% testowy

### Przykładowe obrazy:

Zbiór danych zawiera obrazy kostek o różnej jasności, kontraście i liczbie widocznych ścianek.

---

## ✨ Funkcjonalności

### **Etap 1: Eksploracyjna Analiza Danych**
- ✅ Analiza rozmiaru i rozkładu zbioru danych
- ✅ Rozkład jasności obrazów
- ✅ Wizualizacja równowagi klas
- ✅ Wizualizacja przykładowych obrazów dla każdej klasy

### **Etap 2: XGBoost z Inżynierią Cech**
- ✅ Ekstrakcja ręcznie zdefiniowanych cech (26 cech):
  - Momenty statystyczne (średnia, odch. std., mediana, min, max)
  - Metryki rozkładu (skośność, kurtoza)
  - Cechy histogramu (10 binów)
  - Detekcja krawędzi (Sobel poziomy/pionowy)
  - Proporcje ciemnych/jasnych pikseli
  - Kontrast i entropia
- ✅ Normalizacja StandardScaler
- ✅ Stratyfikowany podział train-test
- ✅ Ewaluacja modelu i analiza błędów

### **Etap 3: Głębokie Uczenie CNN**
- ✅ Niestandardowa architektura CNN (`SumDiceNet`)
- ✅ Architektura wielogłowicowa (ważność, liczba oczek, predykcja sumy)
- ✅ Trening z early stopping i learning rate scheduling
- ✅ Porównanie z baseline XGBoost

---

<img width="548" height="405" alt="Zrzut ekranu 2025-11-23 o 13 19 53" src="https://github.com/user-attachments/assets/8b8b94c1-c550-46c5-b434-2967dc60c296" />

<img width="1389" height="490" alt="image" src="https://github.com/user-attachments/assets/2fbdd3c1-884b-403d-99e8-a713f6f87cae" />


<img width="1540" height="500" alt="image" src="https://github.com/user-attachments/assets/a3490a6c-6374-4534-bf5b-d25cb77e39f2" />

