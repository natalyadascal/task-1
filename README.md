# Proiect Biostatistică — Artrită Reumatoidă (Multi-Omics)

## 📋 Descriere Proiect

Acest proiect creează o bază de date cu **150 observații** (120 reale + 30 sintetice) pentru studii multi-omice în artrita reumatoidă (RA), bazându-se pe datele din repository-ul `RA_ACPA_multiomics`.

## 📁 Structura Repository-ului

```
windsurf-project/
├── README.md                          # Acest fișier
├── Sarcina1_BazaDate.ipynb                       # Sarcina 1 — generare bază de date (150 obs.)
├── Sarcina2_analiza_RA.ipynb                     # Sarcina 2 — analiză descriptivă + vizualizări 1D–5D
├── Sarcina3_inferenta_RA.ipynb                   # Sarcina 3 — inferență statistică (6 teste)
├── Sarcina4_ANOVA_supravietuire_RA.ipynb         # Sarcina 4 — ANOVA + RM-ANOVA + Kaplan-Meier
├── .gitignore                                    # Fișiere excluse din Git
├── output/                                       # Fișiere generate (CSV, Excel)
│   ├── Sarcina1_BazaDate_RA_150obs.{csv,xlsx}
│   ├── Sarcina4_BazaDate_RA_extinsa.{csv,xlsx}  # DB cu 5 coloane sintetice noi
│   └── Sarcina4_rezultate_sumar.{csv,xlsx}
├── figures/                                      # Grafice generate de Sarcina 2/3/4
├── RA_ACPA_multiomics/             # ⚠️ REPOSITORY MULTI-OMICS (vezi mai jos)
└── data/                             # Date suplimentare (opțional)
```

## ⚠️ IMPORTANT: Clonarea Repository-ului Multi-Omics

**Este OBLIGATORIU ca repository-ul multi-omics să fie clonat în interiorul acestui repository, în directorul rădăcină!**

### Pași de clonare:

```bash
# Navighează în directorul rădăcină al acestui proiect
cd /Users/nataliadascal/CascadeProjects/windsurf-project

# Clonează repository-ul multi-omics ca subdirector
git clone https://github.com/hurben/RA_ACPA_multiomics.git
```

### Verificare:

După clonare, structura trebuie să arate astfel:
```
windsurf-project/
├── Sarcina1_BazaDate.ipynb
├── RA_ACPA_multiomics/              # ← AICI trebuie să fie!
│   ├── preprocessed_data_public/
│   │   └── meta/
│   │       └── patient_info_for_statistics.tsv
│   └── ...
└── ...
```

**Notă:** Directorul `RA_ACPA_multiomics/` este inclus în `.gitignore` și NU va fi urcat pe GitHub (datele sunt preluate din repository-ul original).

## 🚀 Cum să Rulezi Proiectul

### Cerințe Preliminare

1. **Python 3.7+** instalat
2. **Jupyter Notebook** sau **JupyterLab**
3. **Pachete Python necesare:**
   - pandas, numpy, matplotlib, seaborn, openpyxl
   - scipy (Sarcina 2 / 3)
   - statsmodels (Sarcina 3)
   - **pingouin** (Sarcina 4 — ANOVA, RM-ANOVA, sfericitate Mauchly, GG, post-hoc, effect sizes)
   - **lifelines** (Sarcina 4 — Kaplan-Meier, log-rank, Cox PH)

### Instalare Pachete

```bash
pip3 install pandas numpy matplotlib seaborn openpyxl scipy statsmodels pingouin lifelines
```

> **Notă:** Dacă folosești VS Code cu Jupyter, poți instala direct din notebook rulând celula `%pip install scipy --quiet` (inclusă ca prima celulă de cod în `Sarcina2_analiza_RA.ipynb`).

### Rulare Notebook

#### Opțiunea 1: Jupyter Notebook
```bash
jupyter notebook Sarcina1_BazaDate.ipynb
jupyter notebook Sarcina2_analiza_RA.ipynb
```

#### Opțiunea 2: JupyterLab
```bash
jupyter lab
```

#### Opțiunea 3: VS Code
Deschide fișierele `.ipynb` direct în VS Code cu extensia Jupyter instalată.

### Executare Celule

Rulează celulele în ordine, de sus în jos:
1. **Importuri** - încarcă librăriile
2. **Citire date** - citește din `RA_ACPA_multiomics/preprocessed_data_public/meta/patient_info_for_statistics.tsv`
3. **Funcții de procesare** - definește funcțiile de transformare
4. **Creare bază de date** - generează cele 150 observații
5. **Analiză și vizualizări** - creează grafice și statistici
6. **Export** - salvează fișierele în `output/`

## 📊 Variabile în Baza de Date

### 6 Variabile Dihotomice
- Fumator (0/1)
- ACPA_Pozitiv (0/1)
- Sex_Feminin (0/1)
- RF_Prezent (0/1)
- CRP_Ridicat (0/1)
- Boala_Activa (0/1)

### 4 Variabile Ordinale
- Nivel_RF (0/1/2)
- Nivel_ACPA (0/1/2)
- Activitate_Boala (0/1/2/3)
- Categorie_Varsta (0/1/2)

### 16 Variabile Continue
- Varsta, BMI, CRP_mgL, ESR_mmh
- CDAI, SDAI, DAS28_ESR, DAS28_CRP
- RF_Titru, ACPA_Titru
- **6 Variabile Omice:** Proteina_CRP, IL6_Nivel, TNF_Nivel, Homocysteine, Spermidine, Kynurenine

### 3 Variabile Text
- Pacient_ID, Grup_Studiu, Observatii_Clinice

### 1 Variabilă Indicator
- Data_Sintetica (0=reală, 1=sintetică)

---

# Sarcina 2: Analiză Descriptivă și Vizualizări Multi-Dimensionale

## 📋 Descriere

Notebook-ul `Sarcina2_analiza_RA.ipynb` realizează o analiză descriptivă completă a setului de date generat la Sarcina 1, cu vizualizări 1D–5D, exclusiv în limba română.

## 📊 Conținut Analiză

### Statistici Descriptive — Variabile Numerice
Pentru toate cele **16 variabile numerice**: media, mediana, abaterea standard, varianța, min, max, Q1/Q2/Q3, asimetrie (skewness), curtosis.

### Variabile Categoriale
Pentru cele **11 variabile categoriale**: frecvențe absolute, frecvențe relative (%), modă — cu grafice de bare.

### Vizualizări Multi-Dimensionale

| Tip | Grafic | Variabile |
|-----|--------|-----------|
| **1D** | Histogramă + KDE — CRP_mgL | 1 variabilă |
| **1D** | Boxplot — Vârsta | 1 variabilă |
| **2D** | Scatter + regresie — DAS28-ESR vs CRP | 2 variabile |
| **2D** | Violin plot — IL-6 pe Grup Studiu | 2 variabile |
| **3D** | Scatter — DAS28-CRP vs VSH, culoare: Grup | 3 variabile |
| **3D** | Scatter — RF_Titru vs ACPA_Titru, culoare: Activitate Boală | 3 variabile |
| **4D** | Scatter — IL-6 vs TNF-α, culoare: Grup, mărime: Vârstă | 4 variabile |
| **4D** | Boxplot stratificat — DAS28 pe Sex × CRP | 4 variabile |
| **5D** | Scatter — DAS28 vs CRP, culoare: IL-6, mărime: Vârstă, formă: Sex | 5 variabile |

## 🚀 Rulare Sarcina 2

1. Asigură-te că `output/Sarcina1_BazaDate_RA_150obs.csv` există (rulează mai întâi Sarcina 1)
2. Deschide `Sarcina2_analiza_RA.ipynb` în VS Code / Jupyter
3. Rulează **celula 1** (`%pip install scipy`) dacă scipy nu este instalat
4. Rulează toate celulele în ordine
5. Graficele se salvează automat în directorul `figures/`

---

# Sarcina 4: ANOVA și Analiza de Supraviețuire

## 📋 Descriere

Notebook-ul `Sarcina4_ANOVA_supravietuire_RA.ipynb` formulează și testează patru ipoteze cu proceduri statistice distincte:

| # | Procedură | Variabile | Test principal | Post-hoc |
|---|---|---|---|---|
| §1 | ANOVA unifactorială | CRP_mgL ~ Activitate_Boala (3 niveluri) | Fisher F / Welch | Tukey HSD / Games-Howell |
| §2 | ANOVA cu măsurători repetate | DAS28-CRP la M0, M3, M6 (within-subjects) | RM-ANOVA + Greenhouse-Geisser | Bonferroni pairwise |
| §3 | Kaplan-Meier (descriptiv) | Timp până la remisie, întreaga cohortă | — (un singur grup) | — |
| §4 | Kaplan-Meier (comparativ) | Timp până la remisie, stratificat ACPA± | Log-rank Mantel-Cox + HR Cox | Wilcoxon (Breslow) ca senzitivitate |

Sunt verificate ipotezele fiecărei proceduri (normalitate, omogenitate, sfericitate), sunt calculate mărimile efectului (η², ω², η²_p, HR) și sunt raportate concluziile ca **asocieri statistice** (fără limbaj cauzal).

## 📦 Extensie a bazei de date

Pentru a permite RM-ANOVA și Kaplan-Meier, baza de date este extinsă în §0 cu **5 coloane sintetice** calibrate clinic pe baza literaturii:
- `DAS28_CRP_M0`, `DAS28_CRP_M3`, `DAS28_CRP_M6` — evoluția DAS28 sub DMARD pe 6 luni
- `Timp_pana_remisie_luni`, `Eveniment_remisie` — timp până la remisie + cenzura administrativă la 12 luni

DB extinsă: `output/Sarcina4_BazaDate_RA_extinsa.{csv,xlsx}` (150 × 33 variabile). Reproductibilitate `RNG seed=42`.

## 🚀 Rulare Sarcina 4

1. Asigură-te că Sarcina 1 a generat `output/Sarcina1_BazaDate_RA_150obs.csv`.
2. Instalează `pingouin` și `lifelines` (vezi secțiunea Instalare Pachete).
3. Deschide `Sarcina4_ANOVA_supravietuire_RA.ipynb` și rulează toate celulele în ordine.
4. Figurile (`figures/RA_ANOVA_*.png`, `RA_RM_*.png`, `RA_KM_*.png`) și tabelul sumar (`output/Sarcina4_rezultate_sumar.{csv,xlsx}`) se salvează automat.

## 📝 Referințe

- **Dataset original:** [RA ACPA Multiomics Repository](https://github.com/hurben/RA_ACPA_multiomics)
- **Paper:** Ben-Hur et al., "Machine learning for prediction of clinical outcomes in RA patients"

## 🤝 Contribuții

Proiect realizat în cadrul cursului de Biostatistică și Bioinformatică.

---

**Ultima actualizare:** Mai 2026
