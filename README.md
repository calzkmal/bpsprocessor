````markdown
# 📊 BPSDataProcessor

`BPSDataProcessor` adalah skrip Python yang digunakan untuk **mengambil, memproses, dan menyimpan data statistik dari Web API BPS (Badan Pusat Statistik Indonesia)**. Skrip ini dirancang untuk memudahkan analisis data pengeluaran per kapita berdasarkan **kelompok komoditas dan daerah tempat tinggal** (perkotaan/perdesaan) di setiap provinsi.

---

## 🚀 Fitur

- 🔗 Mengambil data secara langsung dari [API BPS](https://webapi.bps.go.id).
- 📦 Mengekstrak dan membersihkan data dari format gabungan unik.
- 🏷️ Melabeli data dengan metadata seperti nama komoditas, tahun, dan wilayah.
- 📈 Mengonversi hasil menjadi `pandas.DataFrame`.
- 📁 Menyimpan output ke dalam format **Excel (.xlsx)**.

---

## 🧰 Teknologi yang Digunakan

- Python 3.7+
- `pandas`
- `requests`
- `json`
- `re`
- `os`

---

## 🛠️ Instalasi

1. **Clone repositori:**
   ```bash
   git clone https://github.com/yourusername/BPSDataProcessor.git
   cd BPSDataProcessor
````

2. **Install dependencies:**
   Pastikan environment Python Anda aktif, lalu:

   ```bash
   pip install pandas requests
   ```

---

## ⚙️ Penggunaan

Edit dan jalankan bagian berikut di akhir file `bps_processor.py`:

```python
if __name__ == "__main__":
    API_KEY = "API_KEY_ANDA"
    DOMAIN = "7100"         # Kode domain provinsi (contoh: Sulawesi Utara)
    VAR = "1759"            # Kode variabel (contoh: pengeluaran per kapita)
    PROVINCE = "Sulawesi Utara"
    DIRECTORY = r"D:\\folder\\lokasi\\penyimpanan"

    processor = BPSDataProcessor(API_KEY, DOMAIN, VAR, PROVINCE)
    processor.process_raw_data()
    processor.process_data()
    processor.save_to_excel(DIRECTORY)
```

📌 Output file akan disimpan dengan nama:

```
(Sulawesi Utara) Rata-rata Pengeluaran per Kapita Sebulan Menurut Kelompok Komoditas dan Daerah Tempat Tinggal.xlsx
```

---

## 🧪 Contoh Output

Contoh struktur data dalam file Excel:

| komoditas     | tahun | provinsi       | perkotaan | perdesaan | total   |
| ------------- | ----- | -------------- | --------- | --------- | ------- |
| Makanan       | 2022  | Sulawesi Utara | 1200000   | 950000    | 1075000 |
| Bukan Makanan | 2022  | Sulawesi Utara | 800000    | 600000    | 700000  |

---

## 📝 Catatan

* Pola pemecahan data dari kunci `datacontent` menggunakan regex khusus yang sesuai dengan struktur API BPS.
* Data yang tidak valid, kosong, atau tidak teridentifikasi akan diabaikan secara otomatis.
* Pastikan API key Anda aktif dan domain/variabel benar sesuai dokumentasi BPS.

---

## 📬 Kontribusi & Lisensi

Feel free to fork, modify, and contribute. Untuk penggunaan skala besar atau integrasi lanjutan, silakan cek [dokumentasi API BPS](https://webapi.bps.go.id).

Lisensi: **MIT License**

---

## 🙋‍♂️ Kontak

Dibuat oleh: **Calzy Akmal Indyramdhani**
Universitas Pendidikan Indonesia – Rekayasa Perangkat Lunak
📧 Email: *\[[calzkmal@gmail.com](mailto:calzkmal@gmail.com)]*
🔗 LinkedIn: *\[linkedin.com/in/calzkmal]*
