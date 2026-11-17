# Recognizing Cyber Threats Using Simple AI Rules

**ENSP355 – AI in Cyber Security | Lab 1** · K.R. Mangalam University, School of Engineering & Technology

A transparent, keyword-based classifier that labels messages as **Safe**, **Phishing**, **Malware** or **Ransomware**, assigns a **risk level**, recommends a **safe action**, and documents privacy, false-alarm and human-review considerations.

> ⚠️ Educational project. All messages are sanitized samples. Never click or open real suspicious links or files.

## Project structure

```
.
├── data/simple_cyber_messages.csv          # 28 sanitized sample messages
├── notebooks/Lab1_Rule_Based_Threat_Classifier.ipynb   # full executed notebook (Q1–Q5)
├── src/lab1_classifier.py                  # same logic as a standalone script
├── results/
│   ├── Lab1_Final_Result.csv               # final result table (Q5 evidence)
│   └── category_chart.png                  # bar chart (Q4 evidence)
├── docs/lab_report.md                      # lab-file write-up: tables, notes, conclusion, viva Q&A
├── requirements.txt
├── LICENSE
└── README.md
```

## How it works

1. Convert the message to lowercase.
2. Count keyword matches for each threat category (Phishing, Malware, Ransomware).
3. Highest score wins; if every score is 0 the message is **Safe**.
4. Risk level: Safe → **Low**; Ransomware *or* score ≥ 2 → **High**; other threats → **Medium**.
5. Each risk level maps to a cautious recommended action; serious cases go to a human analyst.

## Run it

**Google Colab:** upload `notebooks/Lab1_Rule_Based_Threat_Classifier.ipynb` and `data/simple_cyber_messages.csv`, then *Runtime → Run all*.
Once pushed to GitHub, you can also open it directly with
`https://colab.research.google.com/github/<your-username>/<your-repo>/blob/main/notebooks/Lab1_Rule_Based_Threat_Classifier.ipynb`

**Locally:**
```bash
pip install -r requirements.txt
python src/lab1_classifier.py                      # run from the repo root
jupyter notebook notebooks/Lab1_Rule_Based_Threat_Classifier.ipynb
```

## Results

| Metric | Value |
|---|---|
| Messages | 28 |
| Correct / incorrect | 28 / 0 |
| Accuracy | **100.00 %** |
| Predicted categories | Safe 10 · Phishing 8 · Malware 5 · Ransomware 5 |
| Risk levels | Low 10 · Medium 1 · High 17 |

![Predicted categories](results/category_chart.png)

100 % is expected on a small, clean classroom dataset and **does not** show real-world effectiveness – see the limitations below.

## Limitations & responsible use

- **Privacy:** remove personal identifiers before analysis.
- **Bias:** keyword lists may not cover every writing style or language.
- **False alarms:** safe text can contain warning words (e.g. *"Bank holiday on Monday"* is flagged as Phishing).
- **False negatives:** new wording (e.g. *"your parcel is on hold, pay a small fee"*) is missed and labelled Safe.
- **Accountability / human review:** people stay responsible; high-risk or unclear cases must be checked by an analyst.

## Author

_Your Name_ · _Roll No._ · _Section_
