# yolo_roboflow

Roboflow 기반 YOLO 활용 프로젝트

## 목차

- [환경 설정](#환경-설정)
  - [1. 가상환경 만들기](#1-가상환경-만들기)
  - [2. 주피터 노트북 커널 등록](#2-주피터-노트북-커널-등록)
  - [3. PyTorch CUDA 버전 설치](#3-pytorch-cuda-버전-설치)
  - [4. 라이브러리 설치](#4-라이브러리-설치)
  - [5. JupyterLab 사용](#5-jupyterlab-사용)

## 환경 설정

### 1. 가상환경 만들기

현재 PowerShell 세션에서 스크립트 실행을 허용합니다.

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

`uv`로 Python 3.12 기반 가상환경을 생성합니다.

```powershell
uv init --bare --python 3.12 --name yolo-ex
uv python pin 3.12
```

### 2. 주피터 노트북 커널 등록

```powershell
uv add ipykernel
uv run python -m ipykernel install --user --name .venv
```

### 3. PyTorch CUDA 버전 설치

`pyproject.toml`에 아래 인덱스 설정을 추가합니다.

```toml
[[tool.uv.index]]
name = "pytorch-cu126"
url = "https://download.pytorch.org/whl/cu126"
explicit = true

[tool.uv.sources]
torch = { index = "pytorch-cu126" }
torchvision = { index = "pytorch-cu126" }
```

torch를 설치합니다.

```powershell
uv add torch torchvision
```

### 4. 라이브러리 설치

```powershell
uv add inference-sdk
uv add python-dotenv
uv add roboflow
uv add "opencv-python==4.12.0.88"
```

### 5. JupyterLab 사용

JupyterLab을 설치합니다.

```powershell
uv add jupyterlab
```

JupyterLab을 실행합니다.

```powershell
uv run jupyter lab
```
