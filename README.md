# 📊 Status tygodniowy projektu

Narzędzie dla PM-ów do przygotowania tygodniowego raportu RAG przed Portfolio Meeting.
Działa w całości w przeglądarce — brak backendu, brak instalacji.

---

## Jak używać

### 1. Otwórz plik
Otwórz `index.html` w dowolnej przeglądarce. Narzędzie działa offline.

### 2. Oceń 6 kryteriów
Dla każdego kryterium wybierz jedną z trzech opcji:

| Kolor | Znaczenie |
|---|---|
| 🟢 Zielony | Pod kontrolą, brak odchyleń |
| 🟡 Żółty | Wymaga uwagi, jest plan naprawczy |
| 🔴 Czerwony | Zagrożone, wymagana eskalacja |

Kryteria i ich wagi:

| Kryterium | Waga | Kiedy pominąć |
|---|---|---|
| 📋 Postęp prac | 30% | — |
| 🗂 Zakres (Scope) | 20% | — |
| ⚠️ Ryzyka | 20% | — |
| 👥 Zespół | 15% | — |
| 🤝 Interesariusze | 10% | — |
| ✅ Jakość | 5% | Wybierz **N/D** jeśli QA jeszcze nie weszło |

### 3. Dodaj komentarz PM
Wpisz kluczowe ustalenia, blokery i decyzje wymagające eskalacji.

> ⚠️ **Komentarz jest wymagany gdy ogólny status to 🔴 ZAGROŻONY.**

### 4. Kliknij „Oblicz status projektu"
Narzędzie wyświetli:
- **Ogólny status RAG** (Dobry / Uwaga / Zagrożony)
- **Wynik liczbowy 0–100** — ważona suma kryteriów
- **Listę ryzyk** gotową do wklejenia do risk logu

### 5. Skopiuj raport
Kliknij **„Kopiuj raport do schowka"** i wklej do Confluence, e-maila lub Teams.

---

## Jak liczony jest wynik

$$\text{score} = \left\lfloor \frac{\sum_{i} p_i \cdot w_i}{\sum_{i} w_i} \times 100 \right\rfloor$$

Gdzie:
- $p_i = 1.0$ dla 🟢, $p_i = 0.5$ dla 🟡, $p_i = 0.0$ dla 🔴
- $w_i$ = waga kryterium
- Kryteria oznaczone **N/D** są wyłączone z obliczeń,
  a wagi pozostałych są automatycznie renormalizowane do 100%

## Jak wyznaczany jest status RAG

| Warunek | Status |
|---|---|
| 2 lub więcej 🔴 | 🔴 ZAGROŻONY |
| 1 🔴 i 2 lub więcej 🟡 | 🔴 ZAGROŻONY |
| 1 🔴 lub 2 lub więcej 🟡 | 🟡 UWAGA |
| Pozostałe przypadki | 🟢 DOBRY |

> Status RAG i wynik liczbowy są niezależne — status wykrywa
> koncentrację problemów, wynik mierzy ogólną kondycję projektu.

---

## Wymagania

- Dowolna nowoczesna przeglądarka (Chrome, Firefox, Edge, Safari)
- Połączenie z internetem tylko przy pierwszym otwarciu (fonty Google)
- Brak dodatkowych zależności
