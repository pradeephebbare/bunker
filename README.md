# BunkMeter 🎓

BunkMeter is a modern attendance tracker and bunk calculator built for students who want to monitor their class attendance and predict how many classes they can skip while still staying above their required percentage.

## Features
- Real-time attendance percentage calculation
- Safe skip analysis for each subject
- Required attendance target control
- Subject-wise dashboard with attendance status
- Modern dashboard UI with dark/light theme toggle
- CSV upload support for bulk subject data
- Responsive layout for desktop use
- Vercel-compatible Flask deployment setup

## Project Overview
This app calculates:
- current attendance percentage
- how many classes can be skipped safely
- how many classes are needed to reach a target attendance
- overall subject performance summary

The math is driven by the attendance logic in the Flask app and is designed to work without needing a login screen.

## Tech Stack
- Python
- Flask
- HTML, CSS, JavaScript
- Chart.js
- Vercel-ready Python server entry

## Folder Structure
- `app_level3.py` – main Flask app and attendance logic
- `app.py` – Vercel-compatible Python entry point
- `api/index.py` – serverless route handler for Vercel
- `templates/` – HTML dashboard templates
- `static/` – CSS and JavaScript frontend files
- `requirements.txt` – project dependencies
- `vercel.json` – Vercel deployment config

## Local Setup

1. Create and activate a virtual environment
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Run the app:

```bash
python app_level3.py
```

4. Open the app in your browser:

```text
http://localhost:5000
```

## Vercel Deployment
This project includes a Vercel-compatible Python entrypoint.

### Required config in Vercel
Set these environment variables in the Vercel dashboard:
- `SECRET_KEY`
- `SUPABASE_URL`
- `SUPABASE_ANON_KEY`

### Build and start settings
- Build Command: `pip install -r requirements.txt`
- Output Directory: leave blank unless required by your project setup
- Start Command for Python runtime: `gunicorn app_level3:app --bind 0.0.0.0:$PORT`

If using the Vercel Python integration, the project includes the serverless wrapper in `api/index.py` and `vercel.json` for routing.

## How Attendance Logic Works
Each subject is evaluated with:
- total classes attended
- total classes held
- required attendance target percentage

The app calculates:
- current percentage
- safe skips remaining
- total classes needed to reach the target
- subject status such as safe, warning, or danger

## Example Use
Add subjects like:
- Math: 45 attended / 56 total
- Physics: 36 attended / 50 total
- Chemistry: 28 attended / 40 total

The app then calculates your likely attendance performance and suggests how many classes you can miss without falling below the target threshold.

## Notes
- The project is kept simple and lightweight for easier deployment.
- The login system was removed to keep the app focused on attendance tracking and fast access.
- The app is designed primarily for direct browser use as a personal academic planning tool.

## License
This project is for educational and personal use.
