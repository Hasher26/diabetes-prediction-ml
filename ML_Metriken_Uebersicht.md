# ML Metriken Übersicht — Diabetes Prediction Project

## Was bedeutet "Performance"?

Laut den Seminar-Slides ist das Ziel: **"Optimize relevant OOS (Out-of-Sample) Performance"**. Das heißt: Wie gut sagt unser Modell auf **neuen, ungesehenen Daten** vorher, ob eine Person Diabetes hat oder nicht.

Bei allen Metriken gilt: **höher = besser** (Ausnahme: Log Loss, da niedriger = besser).

---

## Grundlage: Die Confusion Matrix

Unser Modell sagt für jede Person vorher: **Diabetes (1)** oder **Kein Diabetes (0)**.

Dabei gibt es 4 mögliche Ergebnisse:

```
                          MODELL SAGT
                    Diabetes        Kein Diabetes
                 ┌──────────────┬──────────────────┐
  Wirklich       │  TP           │  FN              │
  Diabetes       │  Richtig      │  ÜBERSEHEN!      │
                 │  erkannt      │  (gefährlich)    │
  WAHRHEIT       ├──────────────┼──────────────────┤
                 │  FP           │  TN              │
  Wirklich       │  Fehlalarm    │  Richtig         │
  Gesund         │  (unnötiger   │  erkannt         │
                 │   Test)       │                  │
                 └──────────────┴──────────────────┘
```

- **TP** (True Positive): Diabetiker richtig als Diabetiker erkannt
- **TN** (True Negative): Gesunder richtig als gesund erkannt
- **FP** (False Positive): Gesunder fälschlich als Diabetiker markiert → Fehlalarm
- **FN** (False Negative): Diabetiker fälschlich als gesund markiert → **übersehen**

---

## Alle Metriken im Überblick

### 1. Accuracy

**Formel**: (TP + TN) / (TP + TN + FP + FN)

**Frage**: Wie oft liegt das Modell insgesamt richtig?

**Beispiel**: 1000 Personen, 920 richtig vorhergesagt → Accuracy = 92%

**Vorsicht bei unserem Dataset**: Wenn ~86% gesund sind, erreicht ein Modell, das IMMER "gesund" sagt, schon 86% Accuracy — ohne einen einzigen Diabetiker zu erkennen. **Accuracy allein ist deshalb bei unbalancierten Daten irreführend.**

---

### 2. Precision

**Formel**: TP / (TP + FP)

**Frage**: Wenn das Modell "Diabetes" sagt — wie oft stimmt das?

**Beispiel**: Modell sagt 100x Diabetes, 70 davon sind wirklich krank → Precision = 70%

**Bedeutung**: Hohe Precision = wenige Fehlalarme.

---

### 3. Recall (= Sensitivity / True Positive Rate)

**Formel**: TP / (TP + FN)

**Frage**: Von allen Diabetikern im Dataset — wie viele findet das Modell?

**Beispiel**: 100 Diabetiker vorhanden, Modell erkennt 80 → Recall = 80%, 20 werden übersehen.

**Bedeutung**: Hoher Recall = wenige übersehene Kranke.

---

### 4. F1-Score

**Formel**: 2 × (Precision × Recall) / (Precision + Recall)

**Frage**: Wie gut ist die Balance zwischen Precision und Recall?

**Bedeutung**: Harmonisches Mittel — ist nur hoch, wenn BEIDE Werte gut sind. Ein Modell mit 99% Recall aber 10% Precision hat trotzdem einen schlechten F1-Score.

---

### 5. AUC-ROC (Area Under the Receiver Operating Characteristic Curve)

**Frage**: Wie gut trennt das Modell generell die beiden Klassen — über alle möglichen Schwellenwerte hinweg?

**Interpretation**:
- AUC = 0.5 → Modell rät zufällig (nutzlos)
- AUC = 0.7–0.8 → akzeptabel
- AUC = 0.8–0.9 → gut
- AUC = 0.9–1.0 → exzellent

**Vorteil**: Funktioniert gut bei unbalancierten Daten, unabhängig vom gewählten Schwellenwert.

---

### 6. Specificity (= True Negative Rate)

**Formel**: TN / (TN + FP)

**Frage**: Von allen Gesunden — wie viele erkennt das Modell als gesund?

**Bedeutung**: Das Gegenstück zu Recall, aber für die gesunde Klasse.

---

### 7. Log Loss

**Frage**: Wie sicher/unsicher ist das Modell bei seinen Vorhersagen?

**Besonderheit**: Einzige Metrik, bei der **niedriger = besser**. Bestraft unsichere Vorhersagen stärker.

---

## Der Trade-Off: Precision vs. Recall

Man kann nicht beides gleichzeitig maximieren. Es gibt immer einen Kompromiss:

```
Strategie A — Hoher Recall (vorsichtig):
  → Bei jedem Verdacht "Diabetes" sagen
  → 95% der Diabetiker erkannt ✓
  → Aber viele Gesunde fälschlich markiert ✗ (niedrige Precision)

Strategie B — Hohe Precision (konservativ):
  → Nur bei sehr hoher Sicherheit "Diabetes" sagen
  → Wenn Diabetes gesagt wird, stimmt es fast immer ✓
  → Aber viele Diabetiker werden übersehen ✗ (niedriger Recall)
```

---

## Unsere Empfehlung für dieses Projekt

### Hauptmetrik: AUC-ROC

**Warum**: Sauberste Gesamtbewertung für binäre Klassifikation, funktioniert gut bei Class Imbalance, Standard im Healthcare-Bereich.

### Zusätzlich berichten: F1-Score, Precision, Recall

**Warum**: Zeigt, dass wir den Trade-Off verstehen und bewusst entscheiden.

### Argumentation in der Thesis:

**Im medizinischen Screening-Kontext priorisieren wir Recall über Precision:**

- **FN (Diabetiker übersehen)** = schlimm → Person bleibt unbehandelt, Krankheit verschlimmert sich
- **FP (Fehlalarm)** = akzeptabel → Person macht einen Bluttest und bekommt Entwarnung

Ein übersehener Diabetiker hat reale gesundheitliche Konsequenzen. Ein Fehlalarm verursacht nur einen unnötigen Arztbesuch.

---

## Zusammenfassung als Tabelle

| Metrik | Formel | Frage | Höher = besser? | Gut bei Imbalance? |
|--------|--------|-------|-----------------|-------------------|
| Accuracy | (TP+TN) / Alle | Wie oft insgesamt richtig? | Ja | **Nein** |
| Precision | TP / (TP+FP) | Wenn Diabetes gesagt, stimmt es? | Ja | Ja |
| Recall | TP / (TP+FN) | Wie viele Diabetiker gefunden? | Ja | Ja |
| F1-Score | Harmonic Mean | Balance Precision & Recall? | Ja | Ja |
| AUC-ROC | Fläche unter ROC | Wie gut trennt das Modell? | Ja | **Ja** |
| Specificity | TN / (TN+FP) | Wie viele Gesunde erkannt? | Ja | Ja |
| Log Loss | -log(p) | Wie sicher ist das Modell? | **Nein (niedriger!)** | Ja |

---

## Für die Note wichtig

Der Professor will sehen, dass wir:

1. **Nicht blind Accuracy reporten** (zeigt Verständnis des Imbalance-Problems)
2. **Die Metrik-Wahl begründen können** (warum AUC-ROC? warum Recall wichtig?)
3. **Den Trade-Off verstehen** (Precision vs. Recall im medizinischen Kontext)
4. **Mehrere Metriken berichten** (Gesamtbild statt einer einzelnen Zahl)
