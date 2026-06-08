# Tautan ke Docker Hub

Docker image dibangun dan dipush otomatis oleh workflow GitHub Actions setelah proses retraining MLflow Project berhasil.

Format image:

```text
<DOCKERHUB_USERNAME>/student-learning-classifier:latest
```

Tautan Docker Hub:

```text
https://hub.docker.com/r/<DOCKERHUB_USERNAME>/student-learning-classifier
```

Username Docker Hub diambil dari secret GitHub Actions `DOCKERHUB_USERNAME`, sedangkan token login diambil dari `DOCKERHUB_TOKEN`.
