# Diabetes Prediction ML Project

**Goethe Universität Frankfurt**
**Seminar: Advanced Applied Data Science | SS 2026**
**Prof. Dr. Kevin Bauer**

---

## 📋 Projektbeschreibung

Dieses Projekt entwickelt ein **Supervised Machine Learning Modell** zur Vorhersage von Diabetes basierend auf Gesundheitsindikatoren des CDC BRFSS 2015 Datensatzes. Wir folgen dem **CRISP-DM Vorgehensmodell** (Cross-Industry Standard Process for Data Mining).

### Dataset
- **Quelle**: [UCI Machine Learning Repository - CDC Diabetes Health Indicators](https://archive.ics.uci.edu/dataset/891/cdc+diabetes+health+indicators)
- **Samples**: ~253.680
- **Features**: 21 Gesundheits- und Lifestyle-Indikatoren
- **Zielvariable**: Diabetes-Status (0 = kein Diabetes, 1 = Prädiabetes, 2 = Diabetes)

---

## 👥 Team

- [Name 1]
- [Name 2]
- [Name 3]
- [Name 4]

---

## 🔄 CRISP-DM Phasen

```
1. Business Understanding  →  Problem & Ziele definieren
2. Data Understanding      →  Daten explorieren & verstehen
3. Data Preparation        →  Daten bereinigen & transformieren
4. Modeling                →  Modelle trainieren
5. Evaluation              →  Performance bewerten
6. Deployment              →  Modell dokumentieren & bereitstellen
```

---

## 📁 Projektstruktur

```
diabetes-prediction-ml/
│
├── notebooks/              # Jupyter Notebooks für jede CRISP-DM Phase
│
├── src/                    # Wiederverwendbarer Python-Code
│
├── data/                   # Datensätze (nicht in Git)
│   ├── raw/                # Original-Daten
│   └── processed/          # Bearbeitete Daten
│
├── results/                # Outputs
│   ├── models/             # Trainierte Modelle
│   └── plots/              # Visualisierungen
│
├── requirements.txt        # Python Dependencies
├── .gitignore              # Dateien, die Git ignorieren soll
└── README.md               # Diese Datei
```

---

## 🚀 Setup & Installation

### Option 1: Google Colab (empfohlen)

```python
# Repository in Colab klonen
!git clone https://github.com/[USERNAME]/diabetes-prediction-ml.git
%cd diabetes-prediction-ml

# Dependencies installieren
!pip install -r requirements.txt
```

### Option 2: Lokal

```bash
# Repository klonen
git clone https://github.com/[USERNAME]/diabetes-prediction-ml.git
cd diabetes-prediction-ml

# Virtuelle Umgebung erstellen (empfohlen)
python -m venv venv
source venv/bin/activate          # Mac/Linux
venv\Scripts\activate             # Windows

# Dependencies installieren
pip install -r requirements.txt
```

---

## 🛠️ Git Workflow

### Neue Änderungen einbringen

```bash
# 1. Aktuellen Stand holen
git pull origin main

# 2. Eigenen Branch erstellen
git checkout -b feature/[beschreibung]

# 3. Änderungen machen, dann committen
git add .
git commit -m "Aussagekräftige Nachricht"

# 4. Branch pushen
git push origin feature/[beschreibung]

# 5. Pull Request auf GitHub erstellen
```

### Wichtige Git-Befehle

| Befehl | Beschreibung |
|--------|--------------|
| `git status` | Zeigt geänderte Dateien |
| `git pull` | Lädt aktuellen Stand vom Repo |
| `git push` | Sendet Änderungen ans Repo |
| `git log` | Zeigt Commit-Historie |
| `git checkout main` | Wechselt zum main Branch |

---

## 📅 Wichtige Termine

| Datum | Meilenstein |
|-------|-------------|
| 06.05.2026 | Projektstart, Daten- & Gruppenzuweisung |
| 02.06.2026 | Intermediary Meeting (optional) |
| 16.06.2026 | Abgabe Thesis & Präsentation (23:59) |
| 23.06.2026 | Finale Präsentation (RuW 2.202) |

---

## 📚 Ressourcen

- **Textbook**: Géron, A. - *Hands-on Machine Learning with Scikit-Learn, Keras & TensorFlow*
- **Scikit-Learn Docs**: https://scikit-learn.org/
- **CRISP-DM Guide**: https://www.datascience-pm.com/crisp-dm-2/

---

## 📧 Kontakt

**Prof. Dr. Kevin Bauer**
bauer@wiwi.uni-frankfurt.de
Chair for Game Theoretic and Causal AI in Business & Economics
