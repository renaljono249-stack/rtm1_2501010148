# PROYEK AKUISISI DATA PARIWISATA BALI

## 1. Identitas Mahasiswa

- **Nama:** Renala Febrian Jono
- **NIM:** 2501010148
- **Program Studi:** Informatika
- **Mata Kuliah:** Akuisisi dan Manajemen Data

## 2. Judul Proyek

**Akuisisi Data Objek Pariwisata Seluruh Provinsi Bali Menggunakan Overpass API dan Python**

## 3. Sumber Data

- **Nama sumber:** OpenStreetMap (OSM)
- **Penerbit:** OpenStreetMap Contributors
- **Website:** https://www.openstreetmap.org/
- **Tools akuisisi:** Overpass Turbo
- **URL tools:** https://overpass-turbo.eu/
- **Endpoint API:** https://overpass-api.de/api/interpreter
- **Wilayah data:** Seluruh Provinsi Bali
- **Format data mentah:** GeoJSON
- **Lisensi:** Open Database License (ODbL)

Catatan: Endpoint di atas merupakan endpoint publik yang umum digunakan. Pastikan sesuai dengan server yang dipilih pada pengaturan Overpass Turbo.

## 4. Tanggal dan Jam Akses

- **Tanggal akses:** [15-11-2026]
- **Jam akses:** [15:50] WITA
- **Zona waktu:** WITA (UTC+8)

## 5. Metode Akuisisi Data

Metode yang digunakan adalah akuisisi data melalui Overpass API dengan bantuan website Overpass Turbo.

Proses pengambilan data dilakukan menggunakan bahasa query Overpass QL untuk mendapatkan objek pariwisata yang berada di wilayah Provinsi Bali.

Query yang digunakan:

```sql
[out:json][timeout:180];

area["name"="Bali"]["admin_level"="4"]->.bali;

(
  nwr["tourism"](area.bali);
);

out center tags;
```

Keterangan:
- `out:json` : Menentukan format hasil JSON.
- `timeout:180` : Batas waktu proses query.
- `area` : Menentukan wilayah Provinsi Bali.
- `nwr` : Mengambil data node, way, dan relation.
- `tourism` : Memilih objek yang memiliki tag pariwisata.
- `out center tags` : Menghasilkan informasi tag dan koordinat tengah objek.

Hasil akuisisi diunduh dalam format GeoJSON dan disimpan sebagai data mentah.

## 6. Batasan Etika dan Penggunaan Data

Pengambilan data dilakukan dengan memperhatikan ketentuan penggunaan OpenStreetMap dan Overpass API.

1. **Ketentuan penggunaan:** Pengambilan data dilakukan melalui Overpass API, bukan scraping halaman HTML. Pemeriksaan robots.txt tidak menjadi metode utama untuk akses API ini.
2. **Lisensi:** Data OpenStreetMap menggunakan Open Database License (ODbL). Atribusi kepada OpenStreetMap Contributors harus dicantumkan.
3. **Jeda permintaan:** Pengambilan dilakukan menggunakan satu query utama, bukan permintaan berulang secara terus-menerus. Jika server memberikan error pembatasan seperti HTTP 429 atau 406, proses dihentikan sementara sebelum mencoba kembali.
4. **Data yang tidak diambil:** Data pribadi pengguna, informasi sensitif, serta informasi yang tidak berkaitan dengan objek pariwisata tidak menjadi target pengumpulan.
5. **Penggunaan data:** Data digunakan untuk kepentingan pembelajaran dan analisis akademik.

Sumber lisensi:
https://www.openstreetmap.org/copyright

## 7. Penjelasan Kolom Dataset

Dataset hasil pengolahan menggunakan Python memiliki beberapa kolom berikut:

| Nama Kolom | Keterangan |
|---|---|
| id | Identitas objek dari OpenStreetMap |
| nama | Nama objek pariwisata |
| kategori | Jenis atau kategori pariwisata |
| latitude | Koordinat garis lintang |
| longitude | Koordinat garis bujur |

Tidak semua objek pariwisata memiliki informasi nama atau kategori yang lengkap. Nilai yang tidak tersedia dapat ditemukan sebagai data kosong.

## 8. Struktur Folder

```text
rtm1_2501010148/
│
├── notebooks/
│   └── akuisisi_pariwisata_bali.ipynb
│
├── data/
│   └── raw/
│       └── overpass_bali_20261115.geojson
│
├── docs/
│   └── data_ethics_checklist.csv
│
└── README.md
```

## 9. Cara Menjalankan Ulang Notebook

1. Buka Google Colab melalui https://colab.research.google.com/.
2. Buka notebook `akuisisi_overpass.ipynb`.
3. Upload file GeoJSON dari folder `data/raw/`.
4. Pastikan nama file pada kode Python sesuai dengan nama file yang diunggah.
5. Jalankan seluruh cell notebook secara berurutan.
6. Periksa hasil pembacaan dan pengolahan data.
7. Pastikan tidak ada error selama proses eksekusi.

## 10. Tujuan Proyek

Proyek ini bertujuan untuk memperoleh dan mengolah data objek pariwisata di seluruh Provinsi Bali menggunakan Overpass API dan Python.

Data yang diperoleh diharapkan dapat digunakan sebagai bahan pembelajaran akuisisi data, pengolahan data geografis, dan analisis informasi pariwisata.

---

**Atribusi Data:**

© OpenStreetMap Contributors

Data tersedia di bawah lisensi Open Database License (ODbL).
