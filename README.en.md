# Traveller (Capstone Project) - English

[한국어](README.ko.md) | [日本語](README.ja.md) | [Main README](README.md)

This repository contains a university capstone team project: a location-based travel web application built with Django.

## Repository Info
- Fork source: `HSMighty7/Main`
- Current repository: `adgk2349/Traveller-Capstone_Project`
- Fork relation and commit history are preserved.

## 1) Overview
`Traveller (Capstone Project)` helps users search places and visualize routes from their current location to selected destinations.

## 2) Core Features
1. User features
- Sign up, log in, and log out
- My page profile view
- Username/password update

2. Search features
- Keyword search by name or address
- Category-based results (attractions, restaurants, cafes)
- Per-user search history view

3. Map/route features
- Current location lookup and save
- Route visualization from origin to destination
- Folium-based map rendering

## 3) Tech Stack
- Backend: `Python`, `Django 5`
- Geospatial: `OSMnx`, `NetworkX`, `Folium`, `GeoPandas`
- Database: Django ORM (configured in `mighty7/my_settings.py`)
- Frontend: Django Templates, Bootstrap, CSS, JavaScript

## 4) Project Structure
```text
capstone-project/
├── main/                    # Core app (views, models, templates)
├── mighty7/                 # Django project settings/urls/wsgi
├── map/                     # Route graph script and graph data
├── static/                  # Static resources (css/js/img)
├── manage.py
├── requirements.txt
├── README.md
├── README.ko.md
├── README.en.md
└── README.ja.md
```

## 5) Local Setup
1. Clone repository
```bash
git clone https://github.com/adgk2349/Traveller-Capstone_Project.git
cd Traveller-Capstone_Project
```

2. Create virtual environment and install dependencies
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

3. Create `mighty7/my_settings.py`
```python
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent.parent

SECRET_KEY = {
    "secret": "replace-with-your-secret-key"
}

DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.sqlite3",
        "NAME": BASE_DIR / "db.sqlite3",
    }
}
```

4. Run migrations and start server
```bash
python3 manage.py migrate
python3 manage.py runserver
```

5. Open in browser
```text
http://127.0.0.1:8000
```

## 6) Main Routes
- `/` : Home
- `/search` : Place search
- `/location` : Current location lookup/save
- `/map` : Route visualization
- `/users/login/` : Login
- `/users/join/` : Registration
- `/users/mypage/` : My page
- `/users/update/` : Account update

## 7) Notes
- `map/graph.osm` is the graph data file used for route visualization.
- Run `python3 map/map.py` to regenerate the graph data.
