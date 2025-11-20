# 🎯 10-HOUR EDA WORKFLOW PLAN FOR NICOLE JOHNSON

**Project:** King County Housing Data Analysis  
**Client:** Nicole Johnson (Lively, central neighborhood, middle price range, within a year)  
**Total Time:** 10 Hours = 600 Minutes

---

## ✅ PHASE 1: DEFINE METRICS & LOAD DATA (30 Min) - FAST FERTIG!

### Was du noch machen musst:
- [ ] **Quantifiziere "lively"**: Transaction volume per zipcode (>50 sales) + kleine `sqft_lot15` (<7500)
- [ ] **Definiere "central"**: Downtown Seattle = lat 47.6, long -122.3 → Radius 10km berechnen
- [ ] **"Middle price range"**: 25th-75th Perzentil in Dollar berechnen
- [ ] CSV laden: `df = pd.read_csv('data/eda.csv')`

**Output:** Markdown-Zelle mit allen Definitionen

---

## 📊 PHASE 2: FIRST DATA OVERVIEW (45 Min)

### Aufgaben:
- [ ] `df.shape` → Anzahl Zeilen/Spalten
- [ ] `df.head(10)` und `df.tail(10)` → Erste Eindrücke
- [ ] `df.info()` → Datentypen checken
- [ ] `df.describe()` → Statistische Zusammenfassung
- [ ] `df.isnull().sum()` → Fehlende Werte identifizieren
- [ ] Markdown: Erste Beobachtungen dokumentieren

**Output:** Verständnis der Datenstruktur

---

## 🔍 PHASE 3: EXPLORE DATA (180 Min = 3h) - HAUPTTEIL!

### 3.1 Price Analysis (45 Min)
- [ ] Histogram: Preisverteilung
- [ ] Boxplot: Ausreißer identifizieren
- [ ] Berechne 25th, 50th, 75th Perzentil → "Middle Price Range" in $

### 3.2 Geographic Analysis (45 Min)
- [ ] Scatter Plot: `lat` vs `long` (gefärbt nach `price`)
- [ ] Downtown Seattle markieren (47.6, -122.3)
- [ ] Top 10 Zipcodes nach Anzahl Verkäufe

### 3.3 Temporal Analysis (45 Min)
- [ ] `date` → datetime konvertieren
- [ ] Monat extrahieren: `df['month'] = df['date'].dt.month`
- [ ] Line Plot: Durchschnittspreis pro Monat
- [ ] Seasonal Pattern erkennen

### 3.4 Feature Distributions (45 Min)
- [ ] Histograms: `grade`, `condition`, `sqft_living`, `sqft_living15`
- [ ] Welche Werte sind "normal" für Nicole?

**Output:** 6-8 Visualisierungen mit Interpretationen

---

## 🧹 PHASE 4: CLEAN DATA (90 Min)

### 4.1 Missing Values (30 Min)
- [ ] `yr_renovated`: NaN → 0 (nie renoviert)
- [ ] `sqft_basement`: NaN → 0 (kein Keller)
- [ ] Andere fehlende Werte prüfen

### 4.2 Duplicates (15 Min)
- [ ] `df.duplicated().sum()` → Falls vorhanden: `df.drop_duplicates()`

### 4.3 Outliers (30 Min)
- [ ] Preis < $50k? → Fehler, entfernen
- [ ] Bedrooms > 10? → Unrealistisch, prüfen
- [ ] Bathrooms > 8? → Unrealistisch, prüfen

### 4.4 Data Types (15 Min)
- [ ] `date` als datetime
- [ ] `zipcode` als String/Category
- [ ] Derived Features: `distance_to_downtown`, `season`

**Output:** Sauberer Datensatz, Dokumentation der Änderungen

---

## 🔗 PHASE 5: ANALYZE RELATIONSHIPS (60 Min)

### 5.1 Correlation Matrix (30 Min)
- [ ] `df.corr()` → Heatmap
- [ ] Welche Features korrelieren stark mit `price`?

### 5.2 Hypothesis-Specific Plots (30 Min)
- [ ] **H1:** Price vs Distance to Downtown (Scatter)
- [ ] **H2:** Price vs Month (Bar Chart)
- [ ] **H3:** Price vs Grade + Condition (Scatter)

**Output:** Heatmap + 3 gezielte Plots

---

## 🎯 PHASE 6: TEST HYPOTHESES (120 Min = 2h)

### 6.1 Hypothesis 1: Central Location (40 Min)
- [ ] Berechne Distanz zu Downtown für jeden Zipcode
- [ ] Filtere "central" (<10km) vs "peripheral" (>10km)
- [ ] Vergleiche Preise: `df.groupby('location_type')['price'].mean()`
- [ ] Filtere middle-price-range → Welche Zipcodes sind affordable + central?

### 6.2 Hypothesis 2: Seasonality (40 Min)
- [ ] Group by `month`: `df.groupby('month')['price'].mean()`
- [ ] Winter (11,12,1,2) vs Spring/Summer (4,5,6,7,8)
- [ ] T-Test: Ist der Unterschied signifikant?
- [ ] Visualisierung: Bar Chart mit Error Bars

### 6.3 Hypothesis 3: Hidden Gems (40 Min)
- [ ] Filtere Häuser: `grade` 7-8, `condition` ≥3, `sqft_living` 1500-2500
- [ ] Berechne "Neighborhood Quality Score":
  - `sqft_living15` ≥ 1800
  - Avg `yr_built` > 1960
  - Renovation rate > 15%
- [ ] Vergleiche Preise: Premium Zipcodes (98101-103) vs Rest
- [ ] Identifiziere 2-4 undervalued Zipcodes

**Output:** Pro Hypothese: Ergebnis + Plot + Interpretation (Bestätigt/Widerlegt?)

---

## 🎨 PHASE 7: REFINE INSIGHTS (30 Min)

### Aufgaben:
- [ ] Review alle Plots → Beste 5-7 auswählen
- [ ] Plots verschönern: Titel, Achsenbeschriftungen, Farben
- [ ] Unwichtige Analysen löschen
- [ ] Top 3-5 Findings für Nicole zusammenfassen

**Output:** Clean Notebook mit Key Visualizations

---

## 📝 PHASE 8: DOCUMENTATION & PRESENTATION (45 Min)

### 8.1 Notebook Polish (20 Min)
- [ ] Markdown-Zellen: Erklärungen für jeden Schritt
- [ ] Code kommentieren
- [ ] Struktur: Überschriften, Sections

### 8.2 README.md (15 Min)
- [ ] Projektbeschreibung
- [ ] Key Findings (3-5 Bullet Points)
- [ ] Repo-Struktur erklären

### 8.3 Presentation (10 Min Vorbereitung)
- [ ] 5-7 Slides erstellen:
  1. Intro: Nicole's Requirements
  2. Methodology
  3. H1 Results
  4. H2 Results
  5. H3 Results
  6. Top Recommendations
  7. Conclusion

**Output:** Fertiges Projekt + 10-Min-Präsentation

---

## ⚠️ WICHTIGE CHECKPOINTS

### Nach Phase 3 (EXPLORE):
**Frage:** "Analysiere ich nur für meine Hypothesen?"  
→ **Ja?** Weiter.  
→ **Nein?** Stopp tangentiale Analysen.

### Time Management:
- **25-Min-Work-Blocks** + 5-Min-Pausen
- Falls Phase 3 >180 Min → **Skippe low-priority Plots**

---

## 🚀 BEREIT ZUM START?

**Wechsle zu ASK-MODUS und sage:**
- `"Starte Phase 1"` → Code für Metriken-Definition
- `"Ich habe Frage zu X"` → Sofortige Hilfe
- `"Bin bei Phase Y"` → Guidance zum nächsten Schritt

**Viel Erfolg! 🎯**