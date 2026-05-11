# Diabetes Prediction ML Project

## Projektkontext
- Seminar: Advanced Applied Data Science, Goethe Universität Frankfurt
- Professor: Prof. Dr. Kevin Bauer
- Dataset: CDC BRFSS 2015 - Diabetes Health Indicators (UCI #891)
- Quelle: https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators
- Vorgehen: CRISP-DM
- Umgebung: Python, Google Colab, GitHub

## Team
- 4 Personen, Rollen noch nicht festgelegt

## Abgabetermine
- 02.06.2026: Intermediary Meeting (optional)
- 16.06.2026: Abgabe Thesis & Präsentation (23:59)
- 23.06.2026: Finale Präsentation (RuW 2.202, 9:30–17:30)

## Dataset
- ~253.680 Samples, 21 Features
- Zielvariable laut Prof: no diabetes vs. prediabetes/diabetes (binär)
- Verfügbare Versionen: binary unbalanced (~253k), binary balanced 50/50 (~70k), 3-Klassen (012)
- Genutzte Version: **binary unbalanced (~253k Samples)**
- Class Imbalance wird selbst behandelt (z.B. SMOTE, Class Weights)
- Fehlende Werte: keine

## Offene Teamentscheidungen
- Hauptmetrik (AUC-ROC, F1, Recall?) — Begründung muss in Thesis
- Arbeitsteilung & Timeline

## Projektstruktur
```
diabetes-prediction-ml/
├── notebooks/    # Jupyter Notebooks pro CRISP-DM Phase
├── src/          # Wiederverwendbare Python-Module
├── data/         # Datensätze (nicht in Git)
├── results/      # Plots und Modelle (nicht in Git)
├── CLAUDE.md     # Diese Datei
├── .gitignore
├── requirements.txt
└── README.md
```

## Coding-Konventionen
- Python 3.10+
- Kommentare und Variablennamen auf Englisch
- Keine hardcoded Pfade, immer relative Pfade
- Notebooks numerisch benennen: 01_, 02_, 03_...
