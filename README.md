# AIDA: Automated Data Analyst


**Upload a CSV or Excel file. Get a dashboard, an executive brief, anomaly
flags, a forecast, and answers to plain-English questions — with the calculation
shown under every number.**

## What it does

ADA reads your file, works out which column is the metric, which is the date,
and which is the segment, then builds the analysis around that.

- **Dashboard** — trend, segment breakdown, movement waterfall, segment × period heatmap
- **Ask ADA** — plain-English questions answered locally with pandas, calculation shown
- **Anomaly flags** — periods outside a calibrated band, sized so a stable series false-alarms about once in twenty analyses
- **Forecast** — a guarded baseline that refuses to run on thin history and reports when it was no better than assuming no change
- **Evidence and next steps** — every finding carries its calculation; recommendations are labelled as interpretation, never as cause
- **Downloads** — Markdown executive brief and cleaned CSV

Limits: 25 MB per file, 250,000 rows analyzed. Formats: `.csv`, `.xlsx`, `.xlsm`.

### Nothing to upload? Try a sample

Pick **Try a sample dataset** in the app, or download one from samples

All three are synthetic, so they carry no privacy or licensing baggage.

### Ask a business question. Get the number and its calculation.

![Ask ADA a plain-English question and receive a pandas-backed answer with its calculation](https://github.com/nikithabellary/AIDA/blob/fb2ba3ff532813bd7769f36ce0eab8580f8e0b44/assets/readme/ask-ada.gif)

### Focus on one segment. The whole analysis regroups.

![Drill into one business segment and automatically regroup the dashboard by the next useful dimension](https://github.com/nikithabellary/AIDA/blob/ec77ff4a99351faf7123ecf506de43c1cf8e6227/assets/readme/drilldown.gif)

<p align="center">
  <img src="https://github.com/nikithabellary/AIDA/blob/ec77ff4a99351faf7123ecf506de43c1cf8e6227/assets/readme/anomaly-forecast.png" width="49%" alt="ADA dashboard showing anomaly markers, a guarded forecast, movement waterfall, and segment heatmap">
  <img src="https://github.com/nikithabellary/AIDA/blob/ec77ff4a99351faf7123ecf506de43c1cf8e6227/assets/readme/evidence-ledger.png" width="49%" alt="ADA evidence ledger showing calculations, anomalies, concentration, correlation, and detected schema">
</p>

## Run it

```bash
git clone https://github.com/saineshnakra/automated-data-analyst.git
cd automated-data-analyst
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
python -m pip install -r requirements.txt
streamlit run app.py
```

No API key required. The app opens with a built-in demo dataset.

## Does my data leave my machine?

**Running ADA yourself: no.** Cleaning, schema detection, every chart, and every
Ask ADA answer are computed locally with pandas, with no network call at all.

**Using the hosted demo: your file is uploaded to a Streamlit server**, because
that is what uploading a file to a website means. It is held in memory for the
session and never written to a database. If that matters for your data, run ADA
locally — it is four commands above and needs no key.

An optional AI layer adds two things when you supply a key: a query planner for
questions the rules cannot parse, and a strategic narrative. The planner shows
its proposed calculation and waits for your confirmation before ADA executes it
locally. **Neither ever receives your rows.** They receive column names, types,
and already-computed evidence — and because an evidence sentence names the
segment it is about, a segment label such as a customer or product name can
appear in it. Nothing else from a cell does. Model-generated code is never
executed.

- *Yours could be here.*
