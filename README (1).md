# Cinepolis BSC

Dashboard Balanced Scorecard per cinema (bulanan + YTD) untuk Cinema Manager.

Link: https://micaelivansaputra-blip.github.io/cinepolis-bsc/ · English: https://micaelivansaputra-blip.github.io/cinepolis-bsc/?lang=en

## Isi folder
- `index.html` — dashboard (HTML + CSS + JS, tanpa build step)
- `data.js` — data BSC 6 KPI per cinema dan region (dari Google Sheet "BSC Raw Data – Cinepolis Ops")
- `scripts/` — skrip untuk membuat dan mengenkripsi data bulanan


## Fitur
- Bahasa Indonesia / English (tombol ID | EN, atau tambahkan `?lang=en` di link)
- Cari site langsung dari bar atas (nama, singkatan, nomor site, provinsi)

Tampilan **Cinema**:
- Filter Region, Cinema, Periode (bulan atau YTD)
- Total Score, rank nasional & rank region
- 6 KPI: Ops Audit (30%), SPH (20%), GSAT (20%), % OI (15%), % Payroll (10%), % Electricity (5%)
- Tren Total Score vs median nasional, skor per region, tabel peringkat nasional
- Unduh PNG scorecard dan Excel (Scorecard, Riwayat Bulanan, Peringkat)

Tampilan **Region**:
- Total Score region, rank dari 6 region, selisih vs tahun lalu
- Cinema teratas & terbawah, pencapaian 6 KPI
- Peta Ops Income per provinsi + tabel, radar Total Score per cinema
- Tabel skor KPI per cinema (vs Budget / vs Tahun Lalu); klik baris → detail cinema
- Unduh PNG dan Excel

## Deploy ke GitHub Pages
1. Buat repo baru, upload `index.html` dan `data.js`.
2. Settings → Pages → Source: `Deploy from a branch`, branch `main`, folder `/root`.
3. Buka `https://micaelivansaputra-blip.github.io/cinepolis-bsc/`.

## Update data bulanan
1. Isi bulan baru di file raw (`New_BSC_Raw.xlsx`, sheet Cinema).
2. Jalankan (butuh Python 3):
   ```
   pip install openpyxl
   python scripts/build_data.py New_BSC_Raw.xlsx data.js data.js "2026-11 (closing November 2026)"
   ```
   Skrip menghitung LY, skor, Total Score, rank, region, dan YTD dengan aturan yang sama seperti Google Sheet.
3. Upload `data.js` yang baru ke repo (nama file harus persis `data.js`).

Cinema baru harus ditambahkan dulu ke daftar `cinemas` di `data.js` (kode, nama, alias, region, provinsi).
