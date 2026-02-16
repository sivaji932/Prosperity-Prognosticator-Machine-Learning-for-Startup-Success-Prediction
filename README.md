# Prosperity Prognosticator (Startup Success Prediction)

Simple Flask app that loads a trained Random Forest model (`startup_rf_model.pkl`) to predict startup success probability from form inputs.

## Prerequisites (Windows 11)
- Python 3.9+ installed and on PATH (`python --version` to verify)
- Git (optional if you already have the folder)
- PowerShell terminal

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

Then open the app in your browser at `http://127.0.0.1:5000/`.

## Notes
- The app binds to `0.0.0.0` in `app.py`, so it is reachable via your local IP as well (e.g., `http://<your-LAN-ip>:5000`).
- For production use, prefer a WSGI server like gunicorn or waitress behind a reverse proxy. For local development, `python app.py` is sufficient.
- The model file `startup_rf_model.pkl` is already included in the repo; no extra download is needed.

## Common issues
- **Execution policy blocks venv activation:** Run PowerShell as Administrator and execute `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`, then reactivate the venv.
- **Port already in use:** Stop whatever is using port 5000 or change the port via `app.run(host='0.0.0.0', port=5001)` when running locally.
