# Sarcina 1: Baza de Date Multi-Omics pentru Artrită Reumatoidă

## 📋 Descriere Proiect

Acest proiect creează o bază de date cu **150 observații** (120 reale + 30 sintetice) pentru studii multi-omice în artrita reumatoidă (RA), bazându-se pe datele din repository-ul `RA_ACPA_multiomics`.

## 📁 Structura Repository-ului

```
windsurf-project/
├── README.md                          # Acest fișier
├── Sarcina1_BazaDate.ipynb           # Notebook principal (Python)
├── .gitignore                        # Fișiere excluse din Git
├── output/                           # Fișiere generate (CSV, Excel)
│   ├── Sarcina1_BazaDate_RA_150obs.csv
│   └── Sarcina1_BazaDate_RA_150obs.xlsx
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
   - pandas
   - numpy
   - matplotlib
   - seaborn
   - openpyxl (pentru export Excel)

### Instalare Pachete

```bash
pip install pandas numpy matplotlib seaborn openpyxl
```

### Rulare Notebook

#### Opțiunea 1: Jupyter Notebook
```bash
jupyter notebook Sarcina1_BazaDate.ipynb
```

#### Opțiunea 2: JupyterLab
```bash
jupyter lab Sarcina1_BazaDate.ipynb
```

#### Opțiunea 3: VS Code
Deschide fișierul `.ipynb` direct în VS Code cu extensia Jupyter instalată.

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

## 📝 Referințe

- **Dataset original:** [RA ACPA Multiomics Repository](https://github.com/hurben/RA_ACPA_multiomics)
- **Paper:** Ben-Hur et al., "Machine learning for prediction of clinical outcomes in RA patients"

## 🤝 Contribuții

Proiect realizat în cadrul cursului de Biostatistică și Bioinformatică.

---

**Ultima actualizare:** Martie 2026
