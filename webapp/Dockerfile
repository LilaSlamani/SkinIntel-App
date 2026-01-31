FROM python:3.11-slim

WORKDIR /app

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    AIRFLOW_HOME=/app

# Installation des dépendances système
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

# ON COPIE LES DEUX FICHIERS EN MÊME TEMPS
COPY requirements.txt requirements-web.txt ./

# ON FORCE UNE INSTALLATION PROPRE ET COMPATIBLE
# On force numpy < 2.0 pour éviter l'erreur que tu as reçue
RUN pip install --no-cache-dir "numpy<2.0" && \
    pip install --no-cache-dir -r requirements.txt -r requirements-web.txt

COPY . .

EXPOSE 5000 8080

CMD ["gunicorn", "-b", "0.0.0.0:5000", "app:app"]
