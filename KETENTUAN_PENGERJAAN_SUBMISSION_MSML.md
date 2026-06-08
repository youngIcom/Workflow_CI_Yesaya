# Ketentuan Pengerjaan Submission MSML

## Kriteria

Setiap kriteria dapat bernilai **0 sampai 4 points (pts)**. Untuk lulus dari submission ini, Anda **harus mendapatkan 2 points dari setiap kriteria**. Submission akan ditolak jika masih terdapat kriteria dengan **0 points**.

> **WAJIB DIPERHATIKAN!**  
> Mohon periksa tab **"Lainnya"** untuk memeriksa ketentuan pengiriman submission lebih lanjut.

---

## Kriteria 1: Melakukan Eksperimen terhadap Dataset Pelatihan

Kriteria pertama merupakan senjata utama untuk menyelesaikan submission kelas ini. Hal ini sangat berguna sebagai eksplorasi dan eksperimen awal sebelum Anda melakukan otomatisasi pada kriteria berikutnya.

Pada tahap ini, Anda **wajib menggunakan Template Eksperimen MSML** sebagai panduan awal sebelum membuat file untuk melakukan otomatisasi data preprocessing. Pastikan template tersebut diikuti dengan benar untuk memastikan proses berjalan sesuai standar yang ditetapkan.

Setelah melakukan eksplorasi, Anda telah memiliki panduan utama untuk membuat file yang dapat melakukan preprocessing data secara otomatis. Selanjutnya, silakan konversi langkah-langkah yang ada pada notebook eksperimen untuk membuat file otomatisasi tersebut.

Pada akhirnya agar dapat memenuhi kriteria ini, Anda harus membuat sebuah repository GitHub dan lokal dengan struktur seperti berikut.

```text
Eksperimen_SML_Nama-siswa
├── .workflow (jika menerapkan advance)
├── namadataset_raw (bisa berupa file atau folder)
├── preprocessing
│   ├── Eksperimen_Nama-siswa.ipynb
│   └── automate_Nama-siswa.py (jika menerapkan skilled)
└── namadataset_preprocessing (bisa berupa file atau folder)
```

### Penilaian Kriteria 1

- **Reject (0 pts)**
  - Tidak melakukan seluruh tahapan experimentation yang ada pada template secara manual.
  - Tidak melakukan data loading pada notebook.
  - Tidak melakukan EDA pada notebook.
  - Tidak melakukan preprocessing pada notebook.

- **Basic (2 pts)**
  - Melakukan tahapan experimentation secara manual.
  - Melakukan data loading pada notebook.
  - Melakukan EDA pada notebook.
  - Melakukan preprocessing pada notebook.

- **Skilled (3 pts)**
  - Tahap basic terpenuhi.
  - Membuat sebuah file `automate_Nama-siswa.py` yang berisikan fungsi untuk melakukan preprocessing secara otomatis sehingga mengembalikan data yang siap dilatih.
  - Pada tahap ini Anda harus melakukan konversi dari proses eksperimen sebelumnya, sehingga tahapannya harus sama tetapi memiliki struktur yang berbeda.

- **Advance (4 pts)**
  - Tahap skilled terpenuhi.
  - Membuat sebuah workflow pada GitHub Actions agar dapat melakukan preprocessing setiap kali trigger terpantik.
  - Anda harus membuat sebuah repository dengan nama `Eksperimen_SML_Nama-siswa` berisi seluruh file yang sama dengan rekomendasi struktur folder pada kriteria 1.
  - Pastikan Actions yang dibuat mengembalikan sebuah dataset terbaru yang sudah diproses sedemikian rupa.

---

## Kriteria 2: Membangun Model Machine Learning

Setelah selesai melalui tahapan preprocessing, Anda harus melatih model menggunakan dataset yang sudah siap digunakan, bukan raw. Nantinya Anda harus membuat sebuah folder yang berisikan file `modelling.py` beserta dependencies-nya dengan struktur seperti berikut.

```text
Membangun_model
├── modelling.py
├── modelling_tuning.py (jika menerapkan skilled/advanced)
├── namadataset_preprocessing (bisa berupa file atau folder)
├── screenshoot_dashboard.jpg
├── screenshoot_artifak.jpg
├── requirements.txt
└── DagsHub.txt (berisikan tautan DagsHub jika menerapkan advanced)
```

Sebagai informasi, tahapan ini dapat Anda jalankan pada local environment sebagai jembatan penghubung ke kriteria tiga.

### Penilaian Kriteria 2

- **Reject (0 pts)**
  - Tidak membuat model machine learning/deep learning menggunakan MLflow dan menyimpan artefak di MLflow Tracking UI.
  - Tidak menyimpan informasi apa pun pada logging.

- **Basic (2 pts)**
  - Melatih model machine learning menggunakan Scikit-Learn menggunakan MLflow Tracking UI yang disimpan secara lokal tanpa menggunakan hyperparameter tuning.
  - Menggunakan autolog dari MLflow pada file `modelling.py`.
  - Mengirimkan screenshot yang valid.

- **Skilled (3 pts)**
  - Kriteria Basic wajib terpenuhi.
  - Melatih model machine learning/deep learning menggunakan MLflow Tracking UI yang disimpan secara lokal dengan menerapkan hyperparameter tuning.
  - Alih-alih menggunakan autolog, Anda diharapkan menggunakan manual logging dengan metriks yang sama dengan autolog.
  - Pastikan checklist ini dilakukan pada file `modelling_tuning.py`, bukan pada `modelling.py`.

- **Advance (4 pts)**
  - Melatih model machine learning/deep learning menggunakan MLflow Tracking UI yang disimpan secara online dengan DagsHub.
  - Alih-alih menggunakan autolog, siswa diharapkan menggunakan manual logging dengan metriks yang tidak hanya tercover pada autolog, yaitu autolog ditambah minimal 2 artefak tambahan.

---

## Kriteria 3: Membuat Workflow CI

Setelah membuat dan memastikan file `modelling.py` berjalan dengan baik, selanjutnya Anda harus membuat workflow CI menggunakan MLflow Project agar dapat melakukan re-training model secara otomatis ketika trigger dipantik.

Silakan buat sebuah project repository baru di GitHub dengan struktur seperti berikut.

```text
Workflow-CI
├── .workflow
├── MLProject (folder)
│   ├── modelling.py
│   ├── conda.yaml
│   ├── MLProject
│   └── namadataset_preprocessing (bisa berupa file atau folder)
├── Tautan ke Docker Hub
└── (file tambahan jika diperlukan)
```

Anda dapat menggunakan file `modelling.py`, `conda.yaml`, serta dataset yang sudah siap dilatih dari hasil eksperimen sebelumnya. Pada tahap ini, Anda hanya perlu membuat struktur yang diminta beserta file `MLProject`-nya saja. Namun, tidak menutup kemungkinan Anda harus menyesuaikan file `modelling.py` ketika masuk ke tahap ini.

### Penilaian Kriteria 3

- **Reject (0 pts)**
  - Tidak membuat folder MLProject.
  - Tidak membuat workflow CI menggunakan GitHub Actions.

- **Basic (2 pts)**
  - Membuat folder MLProject.
  - Membuat workflow CI yang dapat membuat model machine learning ketika trigger terpantik.

- **Skilled (3 pts)**
  - Membuat workflow CI dan menyimpan artefak ke suatu repositori, misalnya GitHub yang sama atau Google Drive.

- **Advance (4 pts)**
  - Membuat workflow CI dan menyimpan artefak ke suatu repositori, misalnya GitHub yang sama atau Google Drive, serta membuat Docker Images ke Docker Hub menggunakan fungsi `mlflow build-docker`.

---

## Kriteria 4: Membuat Sistem Monitoring dan Logging

Monitoring dan logging merupakan tahapan yang tidak bisa berdiri sendiri karena membutuhkan artefak yang dihasilkan oleh kriteria tiga. Nantinya, Anda hanya akan mengumpulkan tangkapan layar mengenai skill yang diampu dengan struktur seperti berikut.

```text
Monitoring dan Logging
├── 1.bukti_serving
├── 2.prometheus.yml
├── 3.prometheus_exporter.py
├── 4.bukti monitoring Prometheus (folder)
│   ├── 1.monitoring_<metriks>
│   ├── 2.monitoring_<metriks>
│   └── dst (sesuaikan dengan poin yang diraih)
├── 5.bukti monitoring Grafana (folder)
│   ├── 1.monitoring_<metriks>
│   ├── 2.monitoring_<metriks>
│   └── dst (sesuaikan dengan poin yang diraih)
├── 6.bukti alerting Grafana (folder)
│   ├── 1.rules_<metriks>
│   ├── 2.notifikasi_<metriks>
│   ├── 3.rules_<metriks>
│   ├── 4.notifikasi_<metriks>
│   └── dst (sesuaikan dengan poin yang diraih)
├── 7.inference.py
└── folder/file tambahan
```

> **Penting:** pastikan untuk membuat dashboard dengan nama **username akun Dicoding** sehingga tangkapan layar yang Anda kirimkan akan berisikan kredensial.

### Penilaian Kriteria 4

- **Reject (0 pts)**
  - Tidak melakukan serving model pada environment local.
  - Tidak melakukan monitoring performa sistem machine learning menggunakan Prometheus.
  - Tidak menggunakan Grafana sebagai tools visualisasi dan alerting sistem machine learning.

- **Basic (2 pts)**
  - Melakukan serving model baik melalui artefak yang sudah dibuat maupun pull images jika menerapkan kriteria CI untuk melakukan push ke Docker Hub.
  - Serving dapat dilakukan melalui `mlflow model serve`, `mlflow deployments`, atau pull images jika memenuhi kriteria 3 advanced.
  - Melakukan monitoring menggunakan Prometheus minimal dengan tiga metriks yang berbeda.
  - Melakukan monitoring menggunakan Grafana dengan metriks yang sama dengan Prometheus.

- **Skilled (3 pts)**
  - Melakukan monitoring menggunakan Grafana dengan minimal 5 metriks yang berbeda.
  - Membuat satu alerting menggunakan Grafana.

- **Advance (4 pts)**
  - Melakukan monitoring menggunakan Grafana dengan minimal 10 metriks yang berbeda.
  - Membuat tiga alerting menggunakan Grafana.

---

## Tips dan Trik

- Anda disarankan menggunakan environment berikut untuk menunjang submission:
  - Python 3.12.7
  - `mlflow==2.19.0`

- Jika Anda menggunakan data unstructured dan menggunakan framework TensorFlow, silakan sesuaikan beberapa tahapan, tetapi tetap mengacu ke masing-masing objektif kriteria.

- Format pengiriman submission:

```text
SMSML_Nama-siswa
├── Eksperimen_SML_Nama-siswa.txt
├── Membangun_model
│   ├── modelling.py
│   ├── modelling_tuning.py (skilled/advanced)
│   ├── namadataset_preprocessing (bisa berupa file atau folder)
│   ├── screenshoot_dashboard.jpg
│   ├── screenshoot_artifak.jpg
│   ├── requirements.txt
│   └── DagsHub.txt (berisikan tautan DagsHub jika menerapkan advanced)
├── Workflow-CI.txt
├── Monitoring dan Logging
│   ├── 1.bukti_serving
│   ├── 2.prometheus.yml
│   ├── 3.prometheus_exporter.py
│   ├── 4.bukti monitoring Prometheus (folder)
│   │   ├── 1.monitoring_<metriks>
│   │   ├── 2.monitoring_<metriks>
│   │   └── dst (sesuaikan dengan poin yang diraih)
│   ├── 5.bukti monitoring Grafana (folder)
│   │   ├── 1.monitoring_<metriks>
│   │   ├── 2.monitoring_<metriks>
│   │   └── dst (sesuaikan dengan poin yang diraih)
│   ├── 6.bukti alerting Grafana (folder)
│   │   ├── 1.rules_<metriks>
│   │   ├── 2.notifikasi_<metriks>
│   │   ├── 3.rules_<metriks>
│   │   ├── 4.notifikasi_<metriks>
│   │   └── dst (sesuaikan dengan poin yang diraih)
│   ├── 7.Inference.py
│   └── folder/file tambahan
```

### Catatan Format Pengiriman

- `Eksperimen_SML_Nama-siswa.txt` berisikan tautan ke repository GitHub kriteria pertama dengan format seperti yang sudah disampaikan pada halaman kriteria 1.
- `Workflow-CI.txt` berisikan tautan ke repository GitHub kriteria ketiga dengan format seperti yang sudah disampaikan pada halaman kriteria 3.
- Pastikan Anda mengatur visibilitas **public** pada kedua repository tersebut.

---

## Detail Tambahan per Kriteria

### Kriteria 1

- Silakan buat sebuah repository GitHub dengan visibilitas **Public** agar bisa diperiksa oleh tim reviewer.
- Pastikan Anda mengerjakan dan menjalankan seluruh tahapan tanpa ada error pada seluruh cell.
- Jika Anda menerapkan **skilled**, silakan buat satu buah file `.py` berdasarkan workflow preprocessing yang dilakukan pada tahap eksperimen.
- Jika Anda menerapkan **Advance**, silakan buat workflow yang sudah dijalankan dan minimal satu kali berhasil tanpa menghasilkan error.

**Konversi gambar halaman 7 ke teks:** gambar menunjukkan contoh GitHub Actions yang berhasil dijalankan. Terdapat status centang hijau pada workflow bernama `test`, branch `main`, serta informasi commit. Inti bukti visual: workflow berhasil minimal satu kali tanpa error.

### Kriteria 2

- Pastikan Anda menyimpan seluruh artefak pada MLflow Tracking UI dengan alamat `localhost` atau `127.0.0.1`.

**Konversi gambar halaman 8 ke teks:** gambar pertama menunjukkan contoh konfigurasi MLflow lokal sebagai berikut.

```python
mlflow.set_tracking_uri("http://127.0.0.1:5000/")

# Create a new MLflow Experiment
mlflow.set_experiment("Latihan Credit Scoring")
```

- Jika menerapkan **skilled**, pastikan Anda membuat file `modelling_tuning.py` dan melakukan logging model yang menghasilkan struktur artefak seperti berikut.

```text
model
├── MLmodel
├── conda.yaml
├── model.pkl
├── python_env.yaml
└── requirements.txt
estimator.html
metric_info.json
training_confusion_matrix.png
```

- Jika menerapkan **advanced**, pastikan Anda menambahkan minimal dua artefak selain pada tahapan skilled. Selain itu, Anda harus menyimpan file artefak MLflow ke DagsHub agar dapat diakses secara online.

**Konversi gambar halaman 8 ke teks:** gambar DagsHub menunjukkan halaman experiment DagsHub yang berisi beberapa eksperimen MLflow, parameter, dan metric seperti `accuracy`. Inti bukti visual: artefak dan log eksperimen berhasil tersimpan secara online di DagsHub.

Sebagai contoh, Anda dapat menggunakan kode berikut agar dapat menyimpan artefak pelatihan ke DagsHub.

```python
import dagshub
import mlflow

dagshub.init(repo_owner='<nama_owner>', repo_name='<nama_repo>', mlflow=True)

with mlflow.start_run():
    # Your training code here...
```

- Jika Anda belum memasukkan kredensial apa pun, silakan login terlebih dahulu dengan mengikuti dokumentasi DagsHub.

### Kriteria 3

- Silakan buat sebuah repository GitHub dengan visibilitas **Public** agar bisa diperiksa oleh tim reviewer.
- Pastikan Anda membuat workflow dari nol agar dapat memastikan semuanya berjalan dengan baik.
- Jangan lupa untuk memasukkan secrets agar informasi akun tidak disalahgunakan orang lain.

Jika menerapkan **basic**, pastikan workflow CI yang dibuat memuat tahapan inti berikut: setup job, checkout repository, setup Python, install dependencies, menjalankan MLflow project, dan menyelesaikan job tanpa error.

Jika menerapkan **skilled**, pastikan workflow CI yang dibuat memuat tahapan berikut.

**Konversi gambar halaman 10 ke teks:** screenshot GitHub Actions menunjukkan seluruh step berhasil dengan centang, yaitu:

```text
Set up job
Run actions/checkout@v3
Set up Python 3.12.7
Check Env
Install dependencies
Set MLflow Tracking URI
Run mlflow project
Install Python dependencies
Upload to Google Drive
Post Set up Python 3.12.7
Post Run actions/checkout@v3
Complete job
```

Silakan sesuaikan tahapan **"Upload to Google Drive"** dengan metode penyimpanan yang Anda pilih, seperti **"Upload to GitHub"** atau **"Upload to GitHub LFS"**.

Jika menerapkan **advanced**, pastikan workflow CI yang dibuat memuat tahapan berikut.

**Konversi gambar halaman 11 ke teks:** screenshot GitHub Actions menunjukkan seluruh step berhasil dengan centang, yaitu:

```text
Set up job
Run actions/checkout@v3
Set up Python 3.12.7
Check Env
Install dependencies
Run mlflow project
Get latest MLflow run_id
Install Python dependencies
Upload to Google Drive
Build Docker Model
Log in to Docker Hub
Tag Docker Image
Push Docker Image
Post Log in to Docker Hub
Post Set up Python 3.12.7
Post Run actions/checkout@v3
Complete job
```

Silakan sesuaikan tahapan **"Upload to Google Drive"** dengan metode penyimpanan yang Anda pilih, seperti **"Upload to GitHub"** atau **"Upload to GitHub LFS"**.

### Kriteria 4

- Pastikan tangkapan layar yang Anda kirim memiliki nama dashboard yang berisikan username akun Dicoding Anda.

**Konversi gambar halaman 12 ke teks:** screenshot Grafana menunjukkan dashboard bernama `dashboard-<username>`. Panel yang terlihat mencakup contoh throughput, latensi API model, jumlah request API model dengan gauge bernilai sekitar `5000`, penggunaan CPU, serta penggunaan RAM. Inti bukti visual: nama dashboard harus memuat username Dicoding dan dashboard harus menampilkan metrik monitoring sistem/model.

- Jika menerapkan **basic**, silakan lakukan serving model menggunakan MLflow serve, membuat API menggunakan framework, dan lain sebagainya. Namun, pastikan Anda menyertakan bukti serving.

**Konversi gambar halaman 12 ke teks:** contoh bukti serving MLflow memperlihatkan perintah dan log bahwa model disajikan melalui alamat lokal berikut.

```text
mlflow models serve -m "models:/credit-scoring/1" --port 5002 --no-conda
...
INFO:waitress:Serving on http://127.0.0.1:5002
```

Atau ketika menggunakan Docker Images, bukti dapat berupa container yang berjalan.

**Konversi gambar halaman 12 ke teks:** contoh Docker menunjukkan container `credit-scoring-hub`, image `rafyardhani/cc:latest`, port mapping `5005:8080`, status berjalan, serta penggunaan resource rendah.

- Anda harus menyertakan bukti Prometheus sudah berjalan dengan membuat minimal tiga buah metriks monitoring.

**Konversi gambar halaman 13 ke teks:** screenshot Prometheus menunjukkan tiga query metrik, yaitu:

```text
http_requests_total
request_cpu_usage
system_ram_usage
```

Nilai yang terlihat pada contoh kurang lebih menunjukkan jumlah request, penggunaan CPU, dan penggunaan RAM. Inti bukti visual: Prometheus berhasil menerima minimal tiga metrik berbeda.

- Selanjutnya silakan konversi metriks yang sudah Anda buat menggunakan Prometheus ke Grafana agar visualisasinya lebih baik.

- Jika menerapkan Alerting, silakan sisipkan dua file seperti berikut.

#### Bukti rules yang dibuat

**Konversi gambar halaman 13 ke teks:** screenshot Grafana Alert Rule menunjukkan konfigurasi rule bertipe Grafana-managed, menggunakan Expression `Threshold`, input `A`, kondisi `IS ABOVE 0`, dan status `Alert condition`. Inti bukti visual: terdapat rule alert yang aktif dan memiliki kondisi ambang batas.

#### Bukti notifikasi

**Konversi gambar halaman 14 ke teks:** screenshot notifikasi Grafana menunjukkan notifikasi alert dengan informasi:

```text
Grafana
Grouped by
alertname=TestAlert instance=Grafana
1 firing instances
Status: Firing
Alert name: TestAlert
Summary: Notification test
Labels:
  alertname: TestAlert
  instance: Grafana
```

Inti bukti visual: notifikasi alert dari Grafana berhasil terkirim dan menampilkan status `Firing`.

---

## Ketentuan Pengiriman Berkas Submission

Berkas submission yang dikirimkan merupakan folder berisi kumpulan berkas yang diminta dalam bentuk ZIP seperti contoh berikut.

```text
SMSML_Nama-siswa.zip
├── Eksperimen_SML_Nama-siswa.txt
├── Membangun_model
│   ├── modelling.py
│   ├── modelling_tuning.py (skilled/advanced)
│   ├── namadataset_preprocessing (bisa berupa file atau folder)
│   ├── screenshoot_dashboard.jpg
│   ├── screenshoot_artifak.jpg
│   ├── requirements.txt
│   └── DagsHub.txt (berisikan tautan DagsHub jika menerapkan advanced)
├── Workflow-CI.txt
├── Monitoring dan Logging
│   ├── 1.bukti_serving
│   ├── 2.prometheus.yml
│   ├── 3.prometheus_exporter.py
│   ├── 4.bukti monitoring Prometheus (folder)
│   │   ├── 1.monitoring_<metriks>
│   │   ├── 2.monitoring_<metriks>
│   │   └── dst (sesuaikan dengan poin yang diraih)
│   ├── 5.bukti monitoring Grafana (folder)
│   │   ├── 1.monitoring_<metriks>
│   │   ├── 2.monitoring_<metriks>
│   │   └── dst (sesuaikan dengan poin yang diraih)
│   ├── 6.bukti alerting Grafana (folder)
│   │   ├── 1.rules_<metriks>
│   │   ├── 2.notifikasi_<metriks>
│   │   ├── 3.rules_<metriks>
│   │   ├── 4.notifikasi_<metriks>
│   │   └── dst (sesuaikan dengan poin yang diraih)
│   ├── 7.Inference.py
│   └── folder/file tambahan
```

Pastikan Anda **tidak melakukan ZIP dalam ZIP**.

---

## Ketentuan Submission Ditolak

Submission Anda akan ditolak bila kondisi berikut terjadi.

### Setiap Kriteria Submission Tidak Terpenuhi

#### Kriteria 1

- Tidak menggunakan template sebagai struktur dasar notebook.
- Tidak melakukan tahapan experimentation secara manual.
- Tidak melakukan data loading pada notebook.
- Tidak melakukan EDA pada notebook.
- Tidak melakukan preprocessing pada notebook.

#### Kriteria 2

- Tidak membuat model machine learning menggunakan MLflow dan menyimpan artefak di MLflow Tracking UI.
- Tidak menyimpan informasi apa pun pada logging.

#### Kriteria 3

- Tidak membuat folder MLProject.
- Tidak membuat workflow CI menggunakan GitHub Actions.

#### Kriteria 4

- Tidak melakukan serving model pada environment local.
- Tidak menggunakan username Dicoding sebagai nama dashboard.
- Tidak melakukan monitoring performa sistem machine learning menggunakan Prometheus.
- Tidak menggunakan Grafana sebagai tools visualisasi dan alerting sistem machine learning.

### Penyebab Penolakan Lainnya

- Mengirimkan tautan kriteria 1 dan 3 tetapi dengan visibilitas **Private** pada pengaturan GitHub.
- Ketentuan berkas submission tidak terpenuhi.
- Melakukan kecurangan, seperti tindakan plagiasi.
