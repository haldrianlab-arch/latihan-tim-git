# Jawaban Quiz Statistik Probabilitas II (Sambil Belajar Konsep)

> Catatan: setiap soal diberi "konsep singkat" dulu sebelum jawaban, supaya kamu paham logikanya sambil ngerjain. Semua pakai α = 5%.

---

## SOAL 1 — Uji Hipotesis Rata-rata

**Konsep singkat:** Kita menguji apakah rata-rata populasi (μ) sama dengan klaim, dengan σ (simpangan baku populasi) **diketahui** → pakai **Uji Z**. Rumusnya mengukur seberapa jauh rata-rata sampel dari klaim, dalam satuan "standard error" (σ/√n).

**a. Hipotesis**
- H0 : μ = 120 ms (rata-rata waktu respon sesuai klaim)
- H1 : μ ≠ 120 ms (rata-rata waktu respon berbeda dari klaim) — dua arah, karena tidak ada indikasi arah tertentu di soal, hanya menguji apakah klaim benar/tidak.

**b. Statistik Uji**

Diketahui: x̄ = 116, μ0 = 120, σ = 14, n = 49

$$Z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}} = \frac{116 - 120}{14/\sqrt{49}} = \frac{-4}{14/7} = \frac{-4}{2} = -2$$

**c. Daerah Penolakan**

Uji dua arah, α = 5% → dari **Tabel Z**, nilai kritis Zα/2 = **±1,96**
Daerah penolakan: Z < −1,96 atau Z > 1,96

**d. Keputusan & Kesimpulan**

|Z hitung| = |−2| = 2, dan 2 > 1,96 → **Z hitung jatuh di daerah penolakan → Tolak H0**

**Kesimpulan:** Pada taraf signifikansi 5%, terdapat cukup bukti bahwa rata-rata waktu respon server cloud **berbeda secara signifikan** dari klaim 120 milidetik (dalam hal ini lebih cepat, karena rata-rata sampel 116 ms < 120 ms).

---

## SOAL 2 — Uji Hipotesis Proporsi

**Konsep singkat:** Sama seperti soal 1, tapi datanya berbentuk persentase "berhasil/gagal", bukan angka kontinu. Rumus standard error-nya beda (pakai p0(1−p0)/n), tapi logika ujinya identik — masih pakai **Tabel Z**.

**a. Hipotesis**
- H0 : p = 0,90 (proporsi keberhasilan login sesuai klaim)
- H1 : p ≠ 0,90 (proporsi keberhasilan login berbeda dari klaim) — dua arah, karena soal hanya minta "kesimpulan terhadap klaim", tidak ada kata "kurang dari/lebih dari" secara eksplisit.

**b. Statistik Uji**

Diketahui: n = 250, x = 215 → p̂ = 215/250 = 0,86, p0 = 0,90

$$Z = \frac{\hat{p} - p_0}{\sqrt{\dfrac{p_0(1-p_0)}{n}}} = \frac{0,86 - 0,90}{\sqrt{\dfrac{0,90 \times 0,10}{250}}} = \frac{-0,04}{\sqrt{0,00036}} = \frac{-0,04}{0,01897} \approx -2,11$$

**c. Keputusan Pengujian**

Uji dua arah, α = 5% → nilai kritis Zα/2 = **±1,96**

|Z hitung| = 2,11 > 1,96 → **Z hitung jatuh di daerah penolakan → Tolak H0**

**d. Kesimpulan terhadap klaim perusahaan**

Proporsi pengguna yang berhasil login tanpa kendala pada sampel (86%) **berbeda secara signifikan** dari klaim tim pengembang (90%). Artinya, pada taraf signifikansi 5%, **klaim 90% tersebut tidak terbukti** — tingkat keberhasilan login sebenarnya cenderung lebih rendah dari yang diklaim.

---

## SOAL 3 — Regresi Linear Sederhana

**Konsep singkat:** Kita mencari garis lurus terbaik ŷ = a + bx yang menggambarkan hubungan lama belajar (x) dan nilai praktikum (y), pakai metode kuadrat terkecil (least squares). **b** = kemiringan garis (efek per 1 unit x), **a** = titik potong (prediksi saat x=0).

**Tabel bantu:**

| Mahasiswa | x | y | xy | x² |
|---|---|---|---|---|
| 1 | 1 | 60 | 60 | 1 |
| 2 | 2 | 66 | 132 | 4 |
| 3 | 3 | 70 | 210 | 9 |
| 4 | 5 | 80 | 400 | 25 |
| 5 | 6 | 85 | 510 | 36 |
| **Σ** | **17** | **361** | **1312** | **75** |

n = 5, x̄ = 17/5 = 3,4, ȳ = 361/5 = 72,2

**a. Persamaan Regresi**

$$b = \frac{n\Sigma xy - \Sigma x \Sigma y}{n \Sigma x^2 - (\Sigma x)^2} = \frac{5(1312) - (17)(361)}{5(75) - (17)^2} = \frac{6560 - 6137}{375 - 289} = \frac{423}{86} \approx 4,92$$

$$a = \bar{y} - b\bar{x} = 72,2 - (4,92)(3,4) \approx 72,2 - 16,72 = 55,48$$

**Persamaan regresi: ŷ = 55,48 + 4,92x**

**b. Arti Koefisien Regresi**

- **b = 4,92** → setiap penambahan **1 jam** waktu belajar Framework Web, nilai praktikum diprediksi **naik rata-rata 4,92 poin** (hubungan positif: makin lama belajar, makin tinggi nilainya).
- **a = 55,48** → prediksi nilai praktikum saat lama belajar = 0 jam (nilai dasar/awal secara matematis, meski secara praktis mahasiswa dengan 0 jam belajar jarang terjadi di data nyata).

**c. Prediksi nilai jika belajar 4 jam**

$$\hat{y} = 55,48 + 4,92(4) = 55,48 + 19,68 \approx 75,15$$

**Prediksi nilai praktikum ≈ 75,15 (atau dibulatkan 75)**

---

## SOAL 4 — Uji Hipotesis Koefisien Regresi

**Konsep singkat:** Kita mau tahu apakah kemiringan garis (b) yang dihitung dari sampel itu **benar-benar mencerminkan pengaruh nyata di populasi**, atau cuma kebetulan sampel. Karena b ditaksir dari sampel (bukan dari seluruh populasi), kita pakai **Uji t**, bukan Z.

**a. Hipotesis**
- H0 : β = 0 (lama belajar coding **tidak berpengaruh** terhadap nilai praktikum)
- H1 : β ≠ 0 (lama belajar coding **berpengaruh** terhadap nilai praktikum)

**b. Statistik Uji t**

Diketahui: n = 18, b = 4,10, SE(b) = 1,25

$$t = \frac{b}{SE(b)} = \frac{4,10}{1,25} = 3,28$$

df = n − 2 = 18 − 2 = 16

**c. Keputusan Pengujian**

Uji dua arah, α = 5%, df = 16 → dari **Tabel t**, nilai kritis t(0,025;16) = **±2,120**

|t hitung| = 3,28 > 2,120 → **t hitung jatuh di daerah penolakan → Tolak H0**

**d. Kesimpulan**

Pada taraf signifikansi 5%, terdapat cukup bukti bahwa **lama belajar coding berpengaruh signifikan** terhadap nilai praktikum mahasiswa (koefisien positif b = 4,10 menunjukkan pengaruhnya searah — makin lama belajar, makin tinggi nilai).

---

## SOAL 5 — Korelasi Sederhana dan Uji Hipotesis Korelasi

**Konsep singkat:** Korelasi (r) mengukur **seberapa erat hubungan linear** dua variabel (bukan pengaruh sebab-akibat seperti regresi). Nilainya −1 sampai +1. Tapi r dari sampel perlu **diuji** apakah cukup kuat untuk disimpulkan berlaku juga di populasi (ρ) — pakai **Uji t** juga, karena r ditaksir dari sampel.

**a. Hipotesis**
- H0 : ρ = 0 (tidak ada korelasi antara jumlah latihan pemrograman dan nilai Basis Data di populasi)
- H1 : ρ ≠ 0 (ada korelasi)

**b. Statistik Uji t**

Diketahui: n = 20, r = 0,71

$$t = \frac{r\sqrt{n-2}}{\sqrt{1-r^2}} = \frac{0,71\sqrt{18}}{\sqrt{1-0,71^2}} = \frac{0,71 \times 4,243}{\sqrt{1 - 0,5041}} = \frac{3,012}{\sqrt{0,4959}} = \frac{3,012}{0,704} \approx 4,28$$

df = n − 2 = 20 − 2 = 18

**c. Keputusan Pengujian**

Uji dua arah, α = 5%, df = 18 → dari **Tabel t**, nilai kritis t(0,025;18) = **±2,101**

|t hitung| = 4,28 > 2,101 → **t hitung jatuh di daerah penolakan → Tolak H0**

**d. Kekuatan Hubungan (berdasarkan nilai r = 0,71)**

| Rentang \|r\| | Kekuatan |
|---|---|
| 0,60 – 0,799 | **Kuat** ← r = 0,71 masuk di sini |

r = 0,71 bertanda **positif** dan berada pada rentang 0,60–0,799 → hubungan tergolong **kuat dan searah** (makin banyak latihan pemrograman per minggu, cenderung makin tinggi nilai Basis Data).

**e. Kesimpulan Penelitian**

Pada taraf signifikansi 5%, korelasi antara jumlah latihan pemrograman per minggu dan nilai mata kuliah Basis Data adalah **signifikan secara statistik** (t hitung = 4,28 > t kritis = 2,101), dengan kekuatan hubungan **kuat dan positif** (r = 0,71). Artinya, di populasi mahasiswa, semakin sering berlatih pemrograman per minggu, semakin tinggi kecenderungan nilai Basis Data yang diperoleh.

---

## Ringkasan Cepat (buat cek ulang sebelum kirim)

| Soal | H0 | Statistik Uji | Nilai Kritis | Keputusan |
|---|---|---|---|---|
| 1 | μ=120 | Z = −2 | ±1,96 | Tolak H0 |
| 2 | p=0,90 | Z ≈ −2,11 | ±1,96 | Tolak H0 |
| 3 | — | ŷ = 55,48+4,92x | — | — |
| 4 | β=0 | t = 3,28 | ±2,120 (df=16) | Tolak H0 |
| 5 | ρ=0 | t ≈ 4,28 | ±2,101 (df=18) | Tolak H0 |

**Saran:** cek ulang perhitunganmu sendiri di kalkulator sebelum dikumpulkan (terutama soal 3 dan 5 yang banyak angka desimal), supaya kamu juga latihan mekanisme hitungnya — bukan cuma salin.
