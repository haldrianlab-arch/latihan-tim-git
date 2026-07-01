# Panduan Konsep Statistik Probabilitas II — Persiapan UAS

Tujuan panduan ini: supaya kamu paham **kenapa** rumus itu dipakai, bukan cuma hafal rumus. Kita mulai dari fondasi paling dasar, baru naik ke tiap topik yang muncul di quiz kamu.

---

## 0. Kenapa Kita Butuh "Uji Hipotesis"?

Bayangkan sebuah perusahaan bilang "rata-rata waktu respon server kami 120 ms". Kamu tidak mungkin mengukur SEMUA request yang pernah terjadi (itu namanya **populasi**). Kamu cuma ambil sebagian, misalnya 49 pengukuran (itu **sampel**).

Masalahnya: hasil sampel hampir pasti tidak akan persis 120 ms, walaupun klaim itu benar — karena namanya juga sampel, pasti ada variasi acak. Pertanyaannya jadi:

> "Selisih yang saya lihat di sampel ini (116 vs 120) — itu wajar karena kebetulan/variasi acak, atau itu bukti bahwa klaimnya salah?"

**Uji hipotesis** adalah prosedur formal untuk menjawab pertanyaan itu. Ini intinya semua soal di quiz kamu (soal 1, 2, 4, 5).

Istilah penting:
- **Parameter** = nilai populasi yang sebenarnya, tidak pernah kita tahu persis (μ, p, β, ρ — pakai huruf Yunani)
- **Statistik** = nilai yang kita hitung dari sampel (x̄, p̂, b, r — pakai huruf Latin)

Logika dasarnya mirip sistem hukum: **anggap tidak bersalah dulu (H0)**, baru kita cari apakah bukti (data sampel) cukup kuat untuk menolaknya.

---

## 1. Empat Pilar Uji Hipotesis (Kerangka yang Sama untuk Semua Soal)

Semua soal uji hipotesis — soal 1, 2, 4, 5 — punya struktur IDENTIK:

### Pilar 1: Rumuskan H0 dan H1
- **H0 (Hipotesis Nol)** = pernyataan status quo / klaim awal / "tidak ada perbedaan/pengaruh". Ini yang kita anggap benar sampai terbukti sebaliknya.
- **H1 (Hipotesis Alternatif)** = apa yang ingin kita buktikan, lawan dari H0.

Contoh cara mikirnya:
- Soal 1: klaimnya "rata-rata = 120 ms" → H0: μ = 120. Administrator curiga waktunya BEDA (bisa lebih cepat/lambat) → H1: μ ≠ 120 (**dua arah / two-tailed**, karena tidak ada dugaan arah tertentu, cuma "berbeda")
- Soal 2: klaim "90% berhasil login" → H0: p = 0,90. Ditemukan datanya *di bawah* klaim → biasanya diuji **satu arah**: H1: p < 0,90

> Tips: kalau kata-katanya "berbeda dari / tidak sama dengan" → dua arah (≠). Kalau "lebih besar dari" atau "lebih kecil dari" → satu arah (> atau <).

### Pilar 2: Taraf Signifikansi (α)
α = 5% artinya: **kita mengizinkan diri salah menolak H0 padahal H0 sebenarnya benar, maksimal 5% dari waktu.** Ini disebut *Type I Error*.

Kebalikannya, 1 − α = 95% adalah **tingkat kepercayaan (confidence level)**.

α ini yang nanti menentukan **seberapa ekstrim** hasil sampel harus, sebelum kita berani bilang "ini bukan kebetulan, klaimnya salah".

### Pilar 3: Statistik Uji (Test Statistic)
Ini adalah **angka tunggal** yang mengukur: "seberapa jauh data sampel saya dari yang diklaim H0, dalam satuan standard error?"

Rumus umumnya SELALU berbentuk:

```
Statistik Uji = (Nilai yang diamati − Nilai yang dihipotesiskan) / (Standard Error)
```

Konsepnya seperti "skor-Z" biasa: kalau hasilnya 0, sampel persis sama dengan klaim. Kalau hasilnya besar (jauh dari 0, positif atau negatif), sampel jauh menyimpang dari klaim.

Ada dua "alat ukur" yang dipakai tergantung situasi:
- **Uji Z** → dipakai kalau simpangan baku **populasi (σ) diketahui**, atau n besar
- **Uji t** → dipakai kalau simpangan baku populasi **tidak diketahui** (pakai simpangan baku sampel), biasanya n kecil

### Pilar 4: Daerah Penolakan & Keputusan
Setelah dapat angka statistik uji, kita bandingkan dengan **nilai kritis** dari tabel (Z atau t). Nilai kritis ini adalah "batas" yang ditentukan oleh α.

- **Daerah penolakan** = area di ekor kurva distribusi yang mewakili hasil "terlalu ekstrim untuk kebetulan"
- Kalau statistik uji jatuh **di dalam** daerah penolakan → **Tolak H0**
- Kalau statistik uji jatuh **di luar** daerah penolakan → **Gagal tolak H0** (bukan berarti H0 terbukti benar, cuma "belum ada cukup bukti untuk menolaknya")

Bayangkan kurva lonceng (distribusi normal). Untuk uji dua arah dengan α = 5%, daerah penolakan dibagi dua ekor, masing-masing 2,5%. Untuk uji satu arah, semua 5% dikumpulkan di satu ekor saja.

```
Dua arah (≠):     [5% dibagi 2 ekor]
   Tolak H0  |          Terima H0          |  Tolak H0
  ←—— 2.5% ——|←———————— 95% ————————→|—— 2.5% ——→
           -Zα/2                        +Zα/2

Satu arah (< atau >):   [5% di satu ekor saja]
        Tolak H0  |              Terima H0
       ←—— 5% ——|←———————————— 95% ————————————→
                Zα (atau -Zα)
```

---

## 2. Cara Membaca Tabel Z (Distribusi Normal Baku)

Tabel Z dipakai untuk mencari **nilai kritis** (batas daerah penolakan) berdasarkan α, ATAU mencari peluang dari suatu nilai Z.

Untuk keperluan uji hipotesis, kamu biasanya cuma perlu **hafal/cari nilai kritis umum** ini (dari tabel distribusi normal baku):

| α (total) | Satu arah (Zα) | Dua arah (Zα/2) |
|---|---|---|
| 10% | 1,28 | 1,645 |
| 5% | 1,645 | 1,96 |
| 1% | 2,33 | 2,575 |

Cara baca tabel Z manual (kalau diminta cari sendiri, bukan dari tabel nilai kritis siap pakai):
1. Tabel Z berisi luas area di bawah kurva dari **tengah (0) sampai nilai Z tertentu**, atau kadang dari kiri sampai Z (cek keterangan di tabelmu — ada dua versi).
2. Baris = digit pertama & kedua di belakang koma dari Z (misal Z=1,64 → baris "1,6")
3. Kolom = digit ketiga (misal 0,04 → kolom "0,04")
4. Perpotongan baris-kolom = luas/peluangnya.
5. Untuk α = 5% dua arah, kita cari Z yang membuat luas di satu ekor = 2,5% → itulah asal angka **1,96**.

> Untuk soal 1 dan 2 di quiz kamu, cukup pakai tabel nilai kritis di atas karena α = 5%.

---

## 3. Cara Membaca Tabel t (Distribusi t-Student)

Tabel t dipakai saat n kecil / σ populasi tidak diketahui (soal 4). Bentuknya sedikit beda dari tabel Z: butuh **derajat bebas (df / degrees of freedom)**.

- **df** = "berapa banyak informasi bebas" yang tersisa setelah kita estimasi parameter dari data. Biasanya:
  - Uji rata-rata 1 sampel: df = n − 1
  - Uji koefisien regresi: df = n − 2 (karena 2 parameter diestimasi: a dan b)
  - Uji korelasi: df = n − 2

Cara baca tabel t:
1. **Baris** = nilai df (n−1 atau n−2, tergantung konteks)
2. **Kolom** = nilai α — tapi HATI-HATI, banyak tabel t punya 2 baris header: satu untuk "uji satu arah" satu untuk "uji dua arah". Pastikan kamu lihat kolom yang sesuai dengan H1-mu.
3. Perpotongan baris df & kolom α = nilai kritis t.

Contoh baca: n = 18, df = 18−2 = 16, uji dua arah α = 5% → cari baris df=16, kolom "0,025" (karena dua arah, tiap ekor 2,5%) → dapat nilai kritis ≈ **2,120**.

> Semakin besar df (sampel makin besar), tabel t makin mendekati tabel Z. Itu logis — kalau sampel besar, ketidakpastian karena "menaksir σ dari data" makin kecil.

---

## 4. Uji Hipotesis Rata-rata — dasar untuk Soal 1

**Kapan dipakai:** menguji apakah rata-rata populasi (μ) sama dengan suatu nilai klaim, dan **σ populasi diketahui**.

**Rumus statistik uji (Z):**

```
Z = (x̄ − μ0) / (σ / √n)
```

- x̄ = rata-rata sampel (yang kamu ukur)
- μ0 = nilai yang diklaim/dihipotesiskan (di H0)
- σ = simpangan baku **populasi**
- n = ukuran sampel
- σ/√n = **standard error** — ukuran "seberapa besar rata-rata sampel biasanya menyimpang dari rata-rata populasi asli", karena rata-rata dari sampel besar lebih stabil (lebih kecil SE-nya) daripada sampel kecil.

**Alur mengerjakan (a–d di soal kamu):**
- (a) H0: μ = nilai klaim, H1: μ ≠ / < / > nilai klaim (lihat kata kunci di soal)
- (b) Masukkan angka ke rumus Z di atas
- (c) Tentukan nilai kritis dari tabel Z sesuai α dan arah H1 → itu daerah penolakannya
- (d) Bandingkan |Z hitung| dengan Z kritis → putuskan tolak/gagal tolak H0, lalu simpulkan dalam kalimat sesuai konteks soal (bukan cuma "tolak H0" tapi apa artinya buat cerita di soal)

*Mini contoh beda angka biar kebayang:* kalau x̄=50, μ0=52, σ=8, n=64 → Z = (50−52)/(8/√64) = −2/1 = **−2**. Lalu bandingkan −2 ini dengan ±1,96 (dua arah, α=5%). Karena |−2| > 1,96, jatuh di daerah penolakan → tolak H0.

---

## 5. Uji Hipotesis Proporsi — dasar untuk Soal 2

**Kapan dipakai:** data berbentuk "berhasil/gagal", "ya/tidak" (bukan angka kontinu), dan kita menguji klaim tentang **persentase populasi (p)**.

**Rumus statistik uji (Z):**

```
p̂ = x / n        (proporsi sampel: jumlah "sukses" dibagi total sampel)

Z = (p̂ − p0) / √( p0(1 − p0) / n )
```

- p̂ = proporsi yang diamati di sampel
- p0 = proporsi yang diklaim (di H0)
- p0(1−p0)/n di dalam akar = standard error untuk proporsi

Konsepnya **identik** dengan uji rata-rata di atas — bedanya cuma bentuk data (proporsi, bukan rata-rata) sehingga rumus standard error-nya beda. Tabel dan cara baca daerah penolakan **sama persis** dengan bagian 4.

*Mini contoh:* klaim p0=0,80, dari n=100 didapat 70 berhasil → p̂=0,70. Z = (0,70−0,80)/√(0,8×0,2/100) = −0,10/0,04 = **−2,5**. Bandingkan dengan nilai kritis sesuai arah H1.

---

## 6. Regresi Linear Sederhana — dasar untuk Soal 3

**Konsep inti:** kita ingin membuat **garis lurus terbaik** yang menggambarkan hubungan antara variabel X (misal: lama belajar) dan Y (misal: nilai). Persamaannya:

```
ŷ = a + bx
```

- **b (slope/koefisien regresi)** = seberapa besar perubahan rata-rata pada Y untuk setiap kenaikan 1 unit X. Ini yang paling sering ditanya "artinya apa" — jawabannya selalu dalam bentuk: *"setiap penambahan 1 [satuan X], nilai [Y] rata-rata naik/turun sebesar b"*
- **a (intercept)** = nilai prediksi Y saat X = 0 (titik potong garis dengan sumbu Y)

**Rumus mencari b dan a** (metode kuadrat terkecil / least squares — garis yang meminimalkan total jarak kuadrat antara data asli dan garis prediksi):

```
b = ( n·Σxy − Σx·Σy ) / ( n·Σx² − (Σx)² )
a = ȳ − b·x̄     (atau: a = (Σy − b·Σx) / n)
```

**Langkah kerja:**
1. Buat tabel bantu: kolom x, y, xy, x²
2. Jumlahkan tiap kolom → dapat Σx, Σy, Σxy, Σx²
3. Masukkan ke rumus b, lalu a
4. Tulis persamaan ŷ = a + bx
5. Untuk prediksi: tinggal substitusi nilai x yang diminta ke persamaan itu

**Intuisi kenapa harus "kuadrat terkecil":** kalau cuma jumlah selisih biasa, selisih positif dan negatif bisa saling meniadakan padahal garis belum tentu pas. Dikuadratkan supaya semua penyimpangan (baik di atas maupun di bawah garis) dihitung sebagai "jarak", lalu dicari garis yang total jaraknya paling kecil.

---

## 7. Uji Hipotesis Koefisien Regresi — dasar untuk Soal 4

**Pertanyaan yang dijawab:** "Apakah X *benar-benar* mempengaruhi Y di populasi, atau kemiringan garis (b) yang kita hitung dari sampel itu cuma kebetulan?"

- H0: β = 0 → artinya **X tidak berpengaruh** terhadap Y (garis populasi sebenarnya datar)
- H1: β ≠ 0 → X berpengaruh terhadap Y

**Rumus statistik uji (pakai t, bukan Z — karena b diestimasi dari sampel, error-nya ditaksir juga dari sampel):**

```
t = b / SE(b)
```

- b = koefisien regresi dari sampel (sudah dihitung di bagian 6, atau langsung diberikan di soal)
- SE(b) = standard error dari b (biasanya sudah diberikan di soal, seperti Soal 4 kamu)
- df = n − 2

**Alur:** hitung t, cari t kritis dari tabel t dengan df = n−2 dan α sesuai (dua arah kalau H1: β≠0), bandingkan, putuskan, simpulkan dalam konteks: "berarti lama belajar coding [berpengaruh/tidak berpengaruh] signifikan terhadap nilai praktikum."

---

## 8. Korelasi Pearson & Uji Signifikansinya — dasar untuk Soal 5

**Beda korelasi vs regresi:** regresi bicara "prediksi & pengaruh arah" (X → Y), korelasi cuma bicara **seberapa erat hubungan linear** dua variabel, tanpa asumsi mana sebab-mana akibat. Koefisien korelasi disimbolkan **r** (sampel) atau **ρ/rho** (populasi), nilainya antara −1 dan +1.

**Interpretasi kekuatan hubungan (pedoman umum yang biasa dipakai di banyak buku ajar Indonesia):**

| Nilai \|r\| | Kekuatan Hubungan |
|---|---|
| 0,00 – 0,199 | Sangat rendah |
| 0,20 – 0,399 | Rendah |
| 0,40 – 0,599 | Sedang |
| 0,60 – 0,799 | Kuat |
| 0,80 – 1,00 | Sangat kuat |

Tanda (+/−) menunjukkan arah: positif = naik bareng, negatif = berlawanan arah.

**Tapi** r besar di sampel tidak otomatis berarti signifikan di populasi (bisa saja kebetulan, apalagi kalau n kecil) — makanya tetap perlu **diuji**:

- H0: ρ = 0 (tidak ada korelasi di populasi)
- H1: ρ ≠ 0 (ada korelasi)

**Rumus statistik uji:**

```
t = r √(n − 2) / √(1 − r²)
```
df = n − 2, dibandingkan ke tabel t seperti biasa.

**Alur soal 5:** (a) rumuskan H0/H1 → (b) hitung t pakai rumus di atas → (c) bandingkan dengan t kritis (df = n−2, α=5%) → (d) lihat tabel kekuatan hubungan di atas untuk deskripsi kekuatannya → (e) simpulkan dua hal sekaligus: apakah hubungannya signifikan (dari uji hipotesis) DAN seberapa kuat hubungannya (dari nilai r).

---

## 9. Peta Ringkas: Soal ↔ Konsep yang Dipakai

| Soal | Topik | Statistik Uji | Tabel yang dipakai | df |
|---|---|---|---|---|
| 1 | Uji rata-rata (σ diketahui) | Z = (x̄−μ0)/(σ/√n) | Tabel Z | — |
| 2 | Uji proporsi | Z = (p̂−p0)/√(p0(1−p0)/n) | Tabel Z | — |
| 3 | Regresi linear sederhana | b, a (least squares) | — (tidak perlu tabel) | — |
| 4 | Uji koefisien regresi | t = b/SE(b) | Tabel t | n−2 |
| 5 | Korelasi Pearson | t = r√(n−2)/√(1−r²) | Tabel t | n−2 |

---

## 10. Checklist "Sistematis" yang Diminta di Petunjuk Soal

Untuk tiap soal uji hipotesis (1, 2, 4, 5), selalu tulis 5 hal ini berurutan supaya nilai maksimal:
1. **Hipotesis** — H0 dan H1, tulis dengan simbol yang benar
2. **Rumus** — tulis rumus umumnya dulu sebelum substitusi angka
3. **Perhitungan** — substitusi angka, tunjukkan langkah, jangan cuma hasil akhir
4. **Nilai kritis / daerah penolakan** — sebutkan dari tabel mana, α berapa, satu/dua arah, nilainya berapa
5. **Keputusan & kesimpulan** — keputusan statistik (tolak/gagal tolak H0) HARUS diterjemahkan jadi kalimat kesimpulan sesuai konteks cerita soal (bukan cuma "H0 ditolak" tapi apa artinya buat perusahaan/dosen di soal itu)

Untuk soal 3 (regresi tanpa uji): tulis tabel bantu Σx, Σy, Σxy, Σx² → rumus b, a → persamaan → interpretasi b → prediksi.

---

Kalau kamu sudah baca ini dan mau coba kerjakan salah satu soal, kirim saja hasil hitunganmu (H0/H1 dan angka-angkanya) — saya bisa cek logikanya tanpa langsung kasih jawaban jadi, biar konsepnya benar-benar nempel buat UAS.
