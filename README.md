# Prosperity-Prognosticator-Machine-Learning-for-Startup-Success-Prediction

## Abstract

This project is a machine-learning–powered web application for predicting a startup’s likelihood of success from early measurable signals. It serves a Flask interface where a user enters key startup parameters—funding and milestone timing (age at first/last funding, age at first/last milestone), network/traction proxies (relationships, milestones), and financing intensity (funding rounds, total funding, average participants). These features are passed to a pre-trained Random Forest classification model (loaded via `joblib`) which returns a probability of success using `predict_proba`. The application then presents an interpretable result to the user as a success percentage and a “likely success/failure” label based on a probability threshold.

## Project artifacts

- **Web app:** `Project Files/app.py` (Flask)
- **UI templates:** `Project Files/templates/index.html`, `Project Files/templates/result.html`
- **Trained model:** `Project Files/startup_rf_model.pkl`
- **Dependencies:** `Project Files/reqiurements.txt`
- **Report:** see `Document/Project Report.pdf`
- **Video demo:** see `Video Demo/Startup_Prediction.mp4`

## How to run (Windows / PowerShell)

```powershell
# 1) Clone
 git clone https://github.com/sivaji932/Prosperity-Prognosticator-Machine-Learning-for-Startup-Success-Prediction.git
 cd Prosperity-Prognosticator-Machine-Learning-for-Startup-Success-Prediction

# 2) Create & activate virtual env
 python -m venv env
 .\env\Scripts\Activate.ps1

# 3) Install dependencies
 pip install -r reqiurements.txt

# 4) Run the app (dev server)
 python app.py

```

Open `http://127.0.0.1:5000/` in your browser.

## Sample input (quick check)

Use these values in the form to verify everything is wired correctly:

| Field                       | Sample value |
| --------------------------- | ------------ |
| Age at First Funding Year   | 2            |
| Age at Last Funding Year    | 5            |
| Age at First Milestone Year | 1            |
| Age at Last Milestone Year  | 4            |
| Number of Relationships     | 10           |
| Number of Funding Rounds    | 3            |
| Total Funding (in USD)      | 1500000      |
| Number of Milestones        | 2            |
| Average Participants        | 5            |

**Expected output (example):**

```
the startup has 75.76% of success, likely to be success
```

## Common issues

- **PowerShell blocks venv activation:** run `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser` then re-activate.
- **Port 5000 already in use:** change to `app.run(host='0.0.0.0', port=5001)` for local runs.
