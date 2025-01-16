<h1 align="center">Javper</h1>
<p align="center">Database Grabber untuk Mirror Cyber Vandalism Global (beta)</p>

> Versi Beta Tester

## Gambaran Umum

Javper adalah proyek berbasis Python yang dirancang untuk mengambil tautan mirror dari situs seperti:

- https://zone-h.org
- https://zone-xsec.com
- https://haxor.id

Javper memungkinkan pengguna untuk menentukan halaman atau rentang halaman untuk diambil, mendapatkan tautan mirror berdasarkan penyerang, dan memfilter hasil menggunakan data cache untuk menghindari pengambilan data berlebihan. Proyek ini juga menawarkan berbagai opsi baris perintah untuk fleksibilitas.

### Fitur

- **Dukungan untuk beberapa situs**: Mengambil tautan mirror dari Zone-H dan semua situs lainnya.
- **Scraping rentang halaman**: Tentukan opsi `-p/--page` untuk mengambil data dari rentang halaman tertentu.
- **Scraping berdasarkan penyerang**: Gunakan `--attacker` untuk mengambil tautan berdasarkan penyerang tertentu.
- **Hasil cache**: Hindari pengambilan ulang URL yang sudah diambil menggunakan cache lokal.
- **Antarmuka baris perintah**: Mudah digunakan dengan argparse untuk opsi baris perintah.

## Instalasi

### Prasyarat

Pastikan Anda sudah menginstal:

- Python 3.x
- pip (manajer paket Python)

### Instalasi Dependensi yang Dibutuhkan

```bash
pip install -r requirements.txt
```

**Catatan**: Scraper ini membutuhkan pustaka eksternal seperti `colorama`, `bs4` (BeautifulSoup), dan `requests` untuk scraping dan styling output.

## Penggunaan

### Penggunaan Dasar

Anda dapat menjalankan scraper dari baris perintah dengan berbagai opsi.

```bash
python main.py --zone-h --archive --page 1-5
```

Perintah ini akan mengambil data dari halaman 1 hingga 5 di Zone-H.

### Opsi Baris Perintah

- `-zh/--zone-h`: Mengambil tautan dari situs https://www.zone-h.org
- `-zx/--zone-xsec`: Mengambil tautan dari situs https://www.zone-xsec.com
- `-hx/--haxorid`: Mengambil tautan dari situs https://www.haxor.id
- `-p/--page`: Nomor halaman yang ingin diambil (jika hanya ingin mengambil 1 halaman, gunakan `-p/--page 1`, tetapi jika ingin beberapa halaman, gunakan `-p/--page 1-10`)
- `--attacker`: Mengambil tautan berdasarkan penyerang tertentu.
- `-s/--special`: Mengambil dari daftar mirror `special`.
- `-a/--archive`: Mengambil dari daftar mirror `archive`.
- `-o/--onhold`: Mengambil dari daftar mirror `onhold`.

#### Khusus untuk mengambil tautan menggunakan Zone-H

- `--zh-zhe`: Atur cookie `ZHE` untuk dapat mengambil situs di Zone-H.
- `--zh-phpsessid`: Atur cookie `PHPSESSID` untuk dapat mengambil situs di Zone-H.

Perintah ini akan menghasilkan satu file bernama **zone-h.cookie** yang berisi format cookie ZHE dan PHPSESSID yang akan digunakan untuk permintaan HTTP.

```text
ZHE=value
PHPSESSID=value
```

Anda dapat mengedit nilai cookie secara langsung dengan mengedit isi file atau menggunakan opsi yang tersedia.

### Contoh

Untuk mengambil data dari Zone-H pada bagian arsip halaman 1 hingga 10 dan memfilter hasil berdasarkan penyerang `anonymous`:

```bash
python main.py --zone-h --archive --page 1-10 --attacker "anonymous"
```

Ini akan secara otomatis menghasilkan output yang disimpan di folder output dan juga di folder berdasarkan bagian yang diambil.

### Cache
Javper menggunakan cache lokal untuk menyimpan URL yang sudah diambil. Ini mencegah pengambilan ulang yang tidak perlu, menghemat waktu dan sumber daya. Pengelolaan cache dilakukan secara otomatis, dan file cache diperbarui setiap kali dijalankan.

### Penanganan Kesalahan
Javper mencakup penanganan kesalahan untuk memastikan eksekusi yang lancar. Kesalahan seperti pustaka yang hilang atau masalah jaringan akan ditangkap dan dilaporkan ke pengguna.

## Pengaturan dan Distribusi

Anda dapat menginstal scraper sebagai alat baris perintah menggunakan setup.py. Ini akan memungkinkan Anda menjalankannya menggunakan perintah `Javper` secara langsung.

```bash
python setup.py install
```

atau

```bash
pip install .
```

## Kontributor

Kontribusi sangat diterima! Jika Anda menemukan masalah atau memiliki saran untuk perbaikan, jangan ragu untuk mengirimkan pull request atau membuka issue.

