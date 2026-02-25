# Prosperity Prognosticator (Startup Success Prediction)

Simple Flask app that loads a trained Random Forest model (`startup_rf_model.pkl`) to predict startup success probability from form inputs.

## Prerequisites (Windows 11)

- Python 3.9+ installed and on PATH (`python --version` to verify)
- Git (optional if you already have the folder)
- PowerShell terminal

## Prerequisites (Linux)

- Python 3.9+ (`python3 --version`)
- `python3-venv` (for virtual environments)
- Git

## Quick start (fresh clone)

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

## Quick start (Linux)

### Ubuntu / Debian

```bash
# 1) Install system packages
sudo apt update
sudo apt install -y python3 python3-venv python3-pip git

# 2) Clone
git clone https://github.com/sivaji932/Prosperity-Prognosticator-Machine-Learning-for-Startup-Success-Prediction.git
cd Prosperity-Prognosticator-Machine-Learning-for-Startup-Success-Prediction

# 3) Create & activate virtual env
python3 -m venv env
source env/bin/activate

# 4) Install dependencies
pip install -r reqiurements.txt

# 5) Run the app (dev server)
python app.py
```

### Amazon Linux

```bash
# 1) Install system packages
sudo yum update -y
sudo yum install -y python3 git

# 2) Clone
git clone https://github.com/sivaji932/Prosperity-Prognosticator-Machine-Learning-for-Startup-Success-Prediction.git
cd Prosperity-Prognosticator-Machine-Learning-for-Startup-Success-Prediction

# 3) Create & activate virtual env
python3 -m venv env
source env/bin/activate

# 4) Install dependencies
pip install -r reqiurements.txt

# 5) Run the app (dev server)
python app.py
```

Then open the app in your browser at `http://127.0.0.1:5000/`.

## Notes

- The app binds to `0.0.0.0` in `app.py`, so it is reachable via your local IP as well (e.g., `http://<your-LAN-ip>:5000`).
- For production use, prefer a WSGI server like gunicorn or waitress behind a reverse proxy. For local development, `python app.py` is sufficient.
- The model file `startup_rf_model.pkl` is already included in the repo; no extra download is needed.

## Sample input and expected output

Use these values in the form to verify everything is wired correctly. The exact probability may vary slightly between systems due to library versions, but the label (success/failure) should match.

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

**Expected output:**

```
the startup has 75.76% of success, likely to be success
```

If you see a similar percentage (around 70–85%) and the label `success`, the app is working. If you get `failure`, double-check the input order and ensure the model file is present.

## Common issues

- **Execution policy blocks venv activation:** Run PowerShell as Administrator and execute `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`, then reactivate the venv.
- **Port already in use:** Stop whatever is using port 5000 or change the port via `app.run(host='0.0.0.0', port=5001)` when running locally.
