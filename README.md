# 📊 Projekt: OpVaR i Model Mertona

Autor: **Mateusz Strojek**  
Data: **21 kwietnia 2024**  
Język: **R** 🧮

---

## 🧩 Zadanie 1 – Obliczanie OpVaR i OpES (75%)

Celem zadania było wyznaczenie rocznego **99.9% OpVaR (Operational Value at Risk)** oraz **OpES (Expected Shortfall)** zgodnie z podejściem **Advanced Measurement Approach (AMA)**. Dane dotyczyły strat operacyjnych banku z podziałem na lata i typy ryzyka.

### 🧪 Etapy:

1. **🔍 Eksploracyjna analiza danych (EDA)**  
   - Statystyki wg kategorii ryzyka.  
   - Liczba zdarzeń i straty roczne – wizualizacje i wnioski.

2. **📐 Modelowanie częstości i dotkliwości strat**  
   - **Częstość strat**:
     - Dopasowano rozkład **ujemny dwumianowy (Negative Binomial)** oraz **dwumianowy (Binomial)**.
     - Ocena dopasowania rozkładów przy pomocy testów zgodności i logiki.
   - **Dotkliwość strat**:
     - Przetestowano i dopasowano rozkłady (np. Gamma, Lognormal, Weibull).
     - Estymacja parametrów odbyła się metodą największej wiarygodności (MLE).

3. **🎲 Symulacja strat i wyznaczenie miar ryzyka**  
   - Wygenerowano 20 000 rocznych scenariuszy strat.  
   - W każdej iteracji:
     - Losowano liczbę zdarzeń z rozkładu częstości.
     - Sumowano wygenerowane straty z rozkładu dotkliwości.
   - Wyznaczono:
     - 📍 **OpVaR na poziomie 99.9%**
     - 📍 **OpES (średnia strata powyżej OpVaR)**
   - Symulację powtórzono wiele razy — wyliczono średni OpVaR/OpES oraz odchylenia standardowe.

---

## 🏛️ Zadanie 2 – Model Mertona i szacowanie PD (25%)

Celem było wyjaśnienie strukturalnego modelu Mertona oraz wyznaczenie **prawdopodobieństwa niewypłacalności (PD)** dla rzeczywistej spółki na podstawie jej danych rynkowych.

### 📘 Opis i implementacja:

1. **🧠 Teoria modelu Mertona**  
   - Wartość firmy traktowana jako opcja call na aktywach.  
   - Default następuje, gdy wartość aktywów < wartość długu w terminie.  
   - Założenia:
     - Rynek doskonały, brak wypłat dywidend.
     - Wartość aktywów podąża za procesem geometrycznego ruchu Browna (lognormalny rozkład).

2. **🧮 Obliczenia i dane**  
   - Przyjęto dane spółki giełdowej: kapitalizacja, zmienność akcji, zadłużenie.  
   - Iteracyjnie wyznaczono:
     - Wartość aktywów.
     - Zmienność aktywów.
   - Finalnie obliczono **PD (Probability of Default)** z wykorzystaniem wzoru Mertona.

3. **📌 Wnioski**  
   - Otrzymane PD znajduje się w realistycznym zakresie.
   - Model uwzględnia zależność między strukturą kapitału a ryzykiem kredytowym.

---

## 🛠️ Narzędzia i biblioteki:
- Język: **R** 🧮
- Pakiety: `fitdistrplus`, `MASS`, `actuar`, `ggplot2`, `data.table` i inne

---

## 📁 Pliki:
- `AMA.html` — szczegółowy raport z obliczeń i kodem w R
- `README.md` — ten plik

---

# 🇬🇧 ENGLISH VERSION ⬇️

# 📊 Project: OpVaR and Merton Model

Author: **Mateusz Strojek**  
Date: **April 21, 2024**  
Language: **R** 🧮

---

## 🧩 Task 1 – OpVaR and OpES Calculation (75%)

Objective: Estimate the annual **99.9% Operational VaR** and **Expected Shortfall (OpES)** using the **Advanced Measurement Approach (AMA)**, based on historical operational loss data.

### 🧪 Steps:

1. **🔍 Exploratory Data Analysis (EDA)**  
   - Category-based analysis of operational losses.  
   - Visualizations to understand event frequency and loss distributions.

2. **📐 Frequency and Severity Modeling**  
   - **Frequency**:
     - Used **Negative Binomial** and **Binomial** distributions (not Poisson).
     - Fitting verified via goodness-of-fit tests and empirical inspection.
   - **Severity**:
     - Evaluated Lognormal, Gamma, Weibull distributions.
     - Parameters estimated using **MLE**.

3. **🎲 Simulation & Risk Estimation**  
   - Simulated 20,000 annual loss scenarios:
     - Number of events ~ chosen frequency distribution.
     - Losses per event ~ chosen severity distribution.
   - Computed:
     - 📍 **99.9% OpVaR**
     - 📍 **OpES**
   - Repeated simulations to calculate average values and standard deviations.

---

## 🏛️ Task 2 – Merton Model & PD Estimation (25%)

Objective: Explain the **Merton structural model** and estimate the **Probability of Default (PD)** using real market data.

### 📘 Approach:

1. **🧠 Theoretical Overview**  
   - Firm’s equity = call option on asset value.  
   - Default if asset value < debt at maturity.  
   - Assumptions:
     - No dividends, perfect markets.
     - Asset value follows a lognormal process.

2. **🧮 Real Data Implementation**  
   - Used real-world data: market cap, equity volatility, liabilities.  
   - Iteratively estimated:
     - Asset value and volatility.
   - PD calculated using the **Merton formula**.

3. **📌 Conclusion**  
   - Resulting PD was within a realistic range.  
   - Shows relationship between capital structure and credit risk.

---

## 🛠️ Tools:
- Language: **R**
- Libraries: `fitdistrplus`, `MASS`, `actuar`, `ggplot2`, `data.table`

---

## 📁 Files:
- `AMA.html` — full R analysis and simulation report.
- `README.md` — this file.

---
