# Rice Journey · Dashboard v0.6

**Dashboard analitik distribusi beras Indonesia**
oleh [@aliftowew](https://instagram.com/aliftowew) · Tenaga Ahli Kemenko Pangan RI

Layout 5 section dengan flow naratif top-to-bottom: Ringkasan → **Alur Harga (terpadu)** → Alur Massa → Komparasi Grade → Distribusi HET. Plus **Kalkulator What-If** di sidebar drawer.

Semua angka **100% dari sumber resmi Bapanas** — math reconcile exact ke target Rp 13.544 (medium) dan Rp 15.211 (premium).

---

## Perubahan v0.5 → v0.6

| Aspek | v0.5 | v0.6 |
|---|---|---|
| Section 02 | 2 panel terpisah (Waterfall + Detail) | **1 panel terpadu** — visual chart + data table dalam grafik tunggal, 41 line items |
| Calculator | Section 06 di main grid (selalu visible, panjang) | **Sidebar drawer** — default hidden, FAB button kanan-bawah, slide-in dari kanan |
| Footer credit | "Untuk Tenaga Ahli Kemenko Pangan RI" | "**Oleh @aliftowew · Tenaga Ahli Kemenko Pangan RI**" |
| Layout total | 6 section | 5 section (calculator pindah ke drawer) |

---

## Section 02 · Alur Harga (terpadu)

Sekarang **1 grafik tunggal** dengan 41 line items dari PDF Bapanas. Setiap baris menampilkan:

- **No** — nomor item
- **Item Pembiayaan** — nama (GKP, Calo, Karung, Whitener, Katul Coklat, dst)
- **Bar visual** — proporsional ke posisi cumulative price (warna berbeda per kategori)
- **Biaya** — +/− Rp X (kontribusi ke harga)
- **Susut** — % massa hilang
- **Rdm** — rendemen sisa
- **Harga kumulatif** — running total

**Color coding** bar:
- Gray/gold/indigo — biaya tambahan biasa
- **Rust gelap dengan ▲** — spike susut (pengeringan 16%, PK 25%)
- **Hijau** — side product offset (katul, menir, dll)
- **Garis putus-putus** — checkpoint harga (Harga Diatas Truk, Harga GKG, Harga PK, dst)
- **Hitam tebal** — harga final pengecer

Tidak ada lagi 2 panel duplikat. Visual + data dalam satu reading flow.

---

## Section 06 · Kalkulator (sidebar drawer)

Tombol **⚙ KALKULATOR** floating di kanan-bawah. Klik → drawer slide-in dari kanan dengan:

**Output panel** (atas, hitam, sticky saat scroll):
- Harga di Pengecer real-time (font besar)
- VS Default (delta dari baseline Bapanas)
- VS HET Zona Aktif (over/under, %)

**Input sliders** (bawah, scroll-able):
- 10/11 slider per step waterfall
- Range ±60% dari default
- Indicator merah ● saat dimodifikasi

**Footer**: Reset Default + Tutup buttons.

**Cara tutup**: ✕ button, klik overlay, atau tekan ESC.

---

## 5 Section dashboard

### 01 · Ringkasan
4 KPI cards: Petani Rp 6.500 → Pabrik Rp 12.927/13.420 → Pengecer Rp 13.544/15.211 → Yield 57,4%/52,7%

### 02 · Alur Harga 🎯 (terpadu)
**1 grafik dengan 41 line items** — visual + tabel dalam satu panel.

### 03 · Alur Massa
- Funnel rendemen (1.000 kg GKP → 574/527 kg final)
- Side product treemap

### 04 · Komparasi Grade
Premium vs Medium per kategori — 8 kategori bar berpasangan, gap Rp 1.667/kg.

### 05 · HET per Zona
**Sumber: KepKa Bapanas 299/2025 (PDF page 1)**
- Peta Indonesia geografis akurat (Natural Earth 50m)
- List 8 wilayah lengkap dengan HET per grade

### 06 · Kalkulator What-If (drawer)
Sidebar simulasi, default hidden.

---

## Math reconciliation

| | Hitung | Target | Status |
|---|---|---|---|
| Unified waterfall final medium | 13.544 | 13.544 | ✓ |
| Unified waterfall final premium | 15.211 | 15.211 | ✓ |
| Calculator default sum | 13.544 / 15.211 | exact | ✓ |
| COMPARISON sum | 13.544 / 15.211 | exact | ✓ |

---

## Sumber data

| Komponen | Sumber | Page |
|---|---|---|
| HET 8 zona | KepKa Bapanas 299/2025 | 1 |
| Asumsi dasar | Perhitungan Bapanas Update 12 Aug 2024 | 2 |
| Cost structure premium (41 items) | Idem | 3 |
| Cost structure medium (41 items) | Idem | 4 |
| Geographic outline | Natural Earth 50m, Public Domain | — |

## Tech stack

- **Vanilla HTML/CSS/JS** — single file 3.165 lines
- **No build step**, no external libs (kecuali Google Fonts)
- All visualizations & interactions custom

## Deploy

```bash
cd rice-journey
vercel --prod
```

---

*"Semua bisa dihitung — termasuk kalau-kalau biaya driyer dipangkas."*
