# SPIKES CGM Dashboard — Setup Guide

## What is Spikes?

SPIKES is a dashboard that helps clinicians spot glucose spikes and dips in their patients' continuous glucose monitor (CGM) data, without reading through thousands of readings by hand. It was built in 4 days at the University of Birmingham HealthTech AI Hackathon for Gilvray Health, using data from their SPIKES study (24 patients, readings every 5 minutes over 14 days). 

## What it does

- **Detects spikes and dips.** For each patient, it works out their normal glucose level from the previous hour, then flags a spike when glucose rises at least 1 mmol/L above that level, rises fast enough and stays high for at least 15 minutes. Dips work the same way in reverse, with an extra alert whenever glucose falls below 3.9 mmol/L, the usual threshold for low blood sugar.
- **Scores each event.** Every spike or dip gets a confidence score from 0 to 1, based on how big it was, how fast it rose, how long it lasted and whether glucose came back down. This lets clinicians focus on the clear events first.
- **Two sensitivity settings.** "High confidence" only flags clear events. "Sensitive" catches smaller ones too.
- **Shows trends for each patient.** Daily glucose traces with every event marked, and a breakdown of what time of day events happen.
- **Links glucose to lifestyle.** Patients rate their health, sleep, nutrition, movement, stress and connection from 1 to 10. The dashboard shows how these change over time, and a cohort analysis tests which ones move with spikes.

## What you need (one-time install)

**Install Docker Desktop:**
- **Windows:** https://www.docker.com/products/docker-desktop/
- **Mac:** https://www.docker.com/products/docker-desktop/

After installing, open Docker Desktop and wait for it to say **"Docker is running"** in the bottom-left corner. You don't need to create an account.

---

## How to run the app

### Windows
1. Double-click **`run.bat`**
2. A black window will open — wait for it to finish (first time takes ~2 minutes)
3. Your browser will open automatically at `http://localhost:8501`

### Mac
1. Right-click **`run.sh`** → Open With → Terminal
   *(Or open Terminal, drag the file in, and press Enter)*
2. Wait for it to finish (first time takes ~2 minutes)
3. Your browser will open automatically at `http://localhost:8501`

---

## After the first run

The first run downloads and builds everything (~2 minutes). After that, starting the app takes about **10 seconds**.

---

## Stopping the app

- **Windows:** Close the black Command Prompt window
- **Mac:** Press `Ctrl+C` in the Terminal window

---

## Troubleshooting

| Problem | Fix |
|---|---|
| "Docker is not installed" | Install Docker Desktop and make sure it's open and running |
| Browser doesn't open automatically | Go to `http://localhost:8501` manually |
| Port already in use | Restart Docker Desktop and try again |
| App won't build | Make sure all `.py` files are in the same folder as `Dockerfile` |

---

## Files required in the same folder

```
Dockerfile
requirements.txt
SPIKES_app.py
spike_analysis.py
pillar_analysis.py
cohort_level.py
run.bat          ← Windows
run.sh           ← Mac
```
