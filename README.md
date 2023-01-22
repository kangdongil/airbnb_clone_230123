# Online Booking Site(a.k.a Airbnb) with Django
<p align='center'>
    <!-- <img width="80%" alt="airbnb-clone" src="#" /> -->
    Preview Photo
</p>

## Tech Stack
<p align='center'>
    <img src="https://img.shields.io/badge/Python-^3.8.16-cornflowerblue?logo=Python"/>
    <img src="https://img.shields.io/badge/Poetry-^1.3.1-mediumslateblue?logo=Poetry"/>
    <img src="https://img.shields.io/badge/Django-^4.1.5-darkgreen?logo=Django"/>
</p>

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