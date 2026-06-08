# Workflow CI

Repository ini dibuat untuk memenuhi Kriteria 3: Membuat Workflow CI pada proyek MSML.

## Struktur Repository

- `.github/workflows/ci.yml`: Konfigurasi GitHub Actions untuk menjalankan MLflow Project, build Docker image, dan push ke Docker Hub.
- `MLProject/`: Folder yang berisi file terkait proyek MLflow.
  - `MLproject`: Konfigurasi entry point dan parameter.
  - `conda.yaml`: Konfigurasi environment.
  - `modelling.py`: Skrip untuk melatih model.
  - `requirements.txt`: Dependencies.
  - `namadataset_preprocessing/`: Folder berisi dataset (`student_cleaned.csv`).
  - `Tautan ke Docker Hub.md`: Berisi tautan repository Docker Hub.

## Cara Menggunakan

1. Konfigurasikan secret di repository GitHub ini:
   - `MLFLOW_TRACKING_URI`: URL DagsHub MLflow tracking
   - `DAGSHUB_USERNAME`: Username DagsHub
   - `DAGSHUB_TOKEN`: Token/password DagsHub
   - `DOCKERHUB_USERNAME`: Username Docker Hub
   - `DOCKERHUB_TOKEN`: Token Docker Hub
2. Jalankan workflow di tab **Actions** -> **Train Build Deploy** -> **Run workflow**.
