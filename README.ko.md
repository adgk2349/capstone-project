# Traveller (Capstone Project) - 한국어

[English](README.en.md) | [日本語](README.ja.md) | [Main README](README.md)

대학교 캡스톤 디자인 팀 프로젝트로 개발된 위치 기반 여행 지원 웹 애플리케이션입니다.

## 저장소 정보
- Fork source: `HSMighty7/Main`
- Current repository: `adgk2349/Traveller-Capstone_Project`
- 포크 관계 및 커밋 히스토리 유지

## 1) 프로젝트 소개
`Traveller (Capstone Project)`는 사용자 위치와 목적지를 기반으로 경로를 시각화하고, 여행지 정보를 검색할 수 있도록 설계된 Django 기반 서비스입니다.

## 2) 핵심 기능
1. 회원 기능
- 회원가입, 로그인, 로그아웃
- 마이페이지 조회
- 아이디/비밀번호 수정

2. 검색 기능
- 키워드 검색 (이름, 주소)
- 카테고리별 결과 제공 (명소, 식당, 카페)
- 사용자별 이전 검색 이력 조회

3. 지도/경로 기능
- 현재 위치 조회 및 저장
- 현재 위치에서 목적지까지 경로 시각화
- Folium 기반 지도 렌더링

## 3) 기술 스택
- Backend: `Python`, `Django 5`
- Geospatial: `OSMnx`, `NetworkX`, `Folium`, `GeoPandas`
- Database: Django ORM (설정은 `mighty7/my_settings.py`)
- Frontend: Django Template, Bootstrap, CSS, JavaScript

## 4) 프로젝트 구조
```text
capstone-project/
├── main/                    # 핵심 앱 (views, models, templates)
├── mighty7/                 # Django project settings/urls/wsgi
├── map/                     # 경로 그래프 생성 스크립트 및 그래프 데이터
├── static/                  # 정적 리소스 (css/js/img)
├── manage.py
├── requirements.txt
├── README.md
├── README.ko.md
├── README.en.md
└── README.ja.md
```

## 5) 로컬 실행 방법
1. 저장소 클론
```bash
git clone https://github.com/adgk2349/Traveller-Capstone_Project.git
cd Traveller-Capstone_Project
```

2. 가상환경 생성 및 의존성 설치
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

3. `mighty7/my_settings.py` 생성
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

4. 마이그레이션 및 실행
```bash
python3 manage.py migrate
python3 manage.py runserver
```

5. 접속
```text
http://127.0.0.1:8000
```

## 6) 주요 페이지
- `/` : 메인 페이지
- `/search` : 여행지 검색
- `/location` : 현재 위치 조회/저장
- `/map` : 경로 시각화
- `/users/login/` : 로그인
- `/users/join/` : 회원가입
- `/users/mypage/` : 마이페이지
- `/users/update/` : 회원정보 수정

## 7) 참고
- `map/graph.osm`은 경로 시각화용 그래프 데이터 파일입니다.
- 그래프를 다시 생성하려면 `python3 map/map.py`를 실행하세요.
