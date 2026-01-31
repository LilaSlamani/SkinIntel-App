FROM python:3.11-slim

WORKDIR /app

# Empêche la création de fichiers .pyc et assure les logs en temps réel
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    AIRFLOW_HOME=/app

# Installation des dépendances système (OCR, OpenCV et outils Airflow)
RUN apt-get update && apt-get install -y --no-install-recommends \
    tesseract-ocr \
    tesseract-ocr-eng \
    tesseract-ocr-fra \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender-dev \
    libgl1 \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# 1. Copie et installe Airflow
COPY requirements.txt ./requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# 2. Copie et installe le Web 
COPY requirements-web.txt ./requirements-web.txt
RUN pip install --no-cache-dir -r requirements-web.txt


COPY . .


EXPOSE 5000 8080

# Commande par défaut (Sera écrasée par Railway pour les services Airflow)
CMD ["gunicorn", "-b", "0.0.0.0:5000", "app:app"]
