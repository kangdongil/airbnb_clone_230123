# Online Booking Site(a.k.a Airbnb) with Django
<p align='center'>
    <!-- <img width="80%" alt="airbnb-clone" src="#" /> -->
    Preview Photo
</p>

## Tech Stack
<div align='center' style="margin-bottom: 0px;">
    <img src="https://img.shields.io/badge/Visual Studio Code-dodgerblue?logo=Visual Studio Code"/>
    <img src="https://img.shields.io/badge/Gitpod-gold?logo=Gitpod"/>
</div>
<div align='center'>
    <img src="https://img.shields.io/badge/Python-^3.8.16-cornflowerblue?logo=Python"/>
    <img src="https://img.shields.io/badge/Poetry-^1.3.1-mediumslateblue?logo=Poetry"/>
    <img src="https://img.shields.io/badge/Django-^4.1.5-darkgreen?logo=Django"/>
</div>

## Python && Poetry 개발환경 구축하기
### Python 개발환경 만들기
- `flake8`와 `black` 설치하기
  ```shell
  pip install flake8 black
  ```
- `.vscode/settings.json` 설정하기
  ```yaml
  {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": null,
    "python.languageServer": "None",
    "python.linting.enabled": true,
    "python.linting.lintOnSave": true,
    "python.linting.flake8Enabled": true,
    "python.linting.pylintEnabled": false,
    "python.linting.flake8Args": ["--max-line-length=88", "--ignore=F401,E402,E501"],
    "python.formatting.provider": "black",
    "[python]": {
        "editor.defaultFormatter": null
    }
  }
  ```
- `.gitignore`하기
  [`python.django gitignore.io`](https://www.toptal.com/developers/gitignore/api/python,django)
### Poetry로 Python Virtual Environment 설정하기
- `poetry init`: 프로젝트를 poetry가 관리하게 하기
- `poetry add PACKAGE_NAME`: poetry로 python package 설치하기
- `poetry add --dev PACKAGE_NAME`: 개발 전용 package 설치하기
- `poetry shell`: console을 poetry 환경에 진입하기
- `exit`: shell 나가기
- `poetry run COMMAND`: shell에 직접 들어가지 않고 command 실행하기
- `pyproject.toml`: 프로젝트 명세와 의존성을 관리하는 파일

## Django Project 준비하기
### Django Project 시작하기
1. `poetry add django`: poetry로 django 설치하기
2. `django-admin startproject config .`: 현재 위치에서 프로젝트 시작하기
3. GitPod에서 Django 서버 허용하기
  ```python
  # config.settings
  ALLOWED_HOSTS = ["localhost"]
  CSRF_TRUSTED_ORIGINS = ["https://*.ws-us**.gitpod.io"]
  ```
4. Django 서버를 한국 시간대(GMT+9)로 변경하기
  ```python
  # config.settings
  TIME_ZONE = "Asia/Seoul"
  ```

## Django Project 살펴보기
### Django Project 구조 알아보기
- `manage.py`
  - terminal에서 django command를 실행할 수 있게 함
- `db.sqlite3`
  - development 단계에서 django가 임시로 사용하는 DB 파일
  - 첫 `runserver` 명령 후 자동으로 빈 파일이 생성됨
  - `migration` 명령은 DB 형태를 코드에 알맞게 동기화해줌.
- `config/`
  - `config.settings`
    - django project에 관한 모든 설정이 이뤄지는 파일
  - `config.urls`
    - django project의 url을 관리하는 파일
    - `include`를 사용하여 App별로 url을 묶어 관리하면 수월하다
### Django Project Command(`manage.py`) 사용하기
  - `python manage.py COMMAND`로 django command를 호출할 수 있다
  - `runserver`: django 서버를 시작한다
  - `createsuperuser`: admin 계정을 생성한다
    - admin 계정을 저장할 DB파일과 migration을 필요로 한다
    - DB를 초기화(삭제)할 때마다 admin 계정을 새로 만들어야 한다
  - `makemigrations` >> `migrate`: data model의 변경사항을 DB에 반영한다
    - `makemigrations`은 파일을 생성하고, `migrate`는 변경된 내용을 적용한다
  - `shell`: console에서 django를 다룰 수 있게 해준다
    - `ORM` 등 Django 코드를 콘솔에서 테스트하기 좋다
### Django Migration 다루기
### Django Server 시작하기
1. `python manage.py runserver`
2. `python manage.py makemigrations`
3. `python manage.py migrate`
4. `python manage.py createsuperuser`