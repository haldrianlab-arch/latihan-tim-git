# Materi UAS — Pengantar Keamanan Cyber

> Catatan: file ini akan terus di-update seiring kisi-kisi lain dibahas dan disetujui.

---

## Tujuan Utama SSL/TLS

Tujuan utama SSL/TLS adalah mengamankan komunikasi data antara dua sistem (misal: client-server) di jaringan. SSL/TLS memiliki 3 fungsi utama:

### Autentikasi (Membangun Kepercayaan)

Memastikan sistem terhubung ke tujuan aslinya, misal client terhubung ke server asli dan mencegah serangan spoofing/MITM.

**Cara kerja:**
* Saat fase handshake, server mengirimkan sertifikat digital yang ditandatangani oleh CA, kemudian client akan memverifikasi chain of trust sertifikat ini.
* Terdapat juga opsi mTLS jika diperlukan autentikasi dua arah.

### Kerahasiaan Data (Enkripsi)

Mencegah pihak tidak berwenang membaca/menyadap isi komunikasi antara client dan server.

**Cara kerja:**
* Saat fase handshake, klien dan server melakukan key exchange untuk menghasilkan session key.
* Session key ini digunakan mengenkripsi (dan dekripsi) data yang dipertukarkan dengan mengubah plaintext menjadi ciphertext.

### Integritas Data (Mencegah Modifikasi)

Memastikan bahwa data yang dikirim dan diterima sama persis, tanpa mengalami perubahan selama proses transmisi.

**Cara kerja:**
* Setelah proses handshake selesai, setiap data yang dikirim dilindungi dengan mekanisme pemeriksaan integritas kriptografis.
* Penerima (klien maupun server) akan memverifikasi integritas data tersebut.
* Jika data terdeteksi telah diubah atau dirusak selama transmisi, data akan ditolak dan koneksi dapat dihentikan.
---

## 2. Siklus Virus

### Siklus Virus Komputer — 4 Fase

**1. Dormant (Fase Tidur)**

Virus berhasil masuk ke dalam sistem, tetapi belum menjalankan aktivitas apa pun. Virus hanya berada di komputer sambil menunggu kondisi tertentu agar dapat mulai bekerja, misalnya tanggal tertentu, program dijalankan beberapa kali, atau kondisi lain yang telah ditentukan. Fase ini bersifat opsional karena tidak semua virus diprogram untuk menunda aktivasinya — jika pembuat virus tidak menambahkan syarat tunggu, virus bisa langsung menyebar begitu file inangnya dijalankan.

**2. Propagation (Fase Penyebaran)**

Fase ini dimulai begitu file inang yang terinfeksi dijalankan, dan bersifat tidak opsional — hampir semua virus melewati fase ini karena replikasi diri adalah ciri utama sebuah virus. Virus mulai menggandakan dirinya dengan menyalin kode virus ke file, program, atau media penyimpanan lain, sehingga jumlah file yang terinfeksi semakin banyak dan virus lebih mudah bertahan serta menyebar ke sistem lain. Tujuan utama fase ini adalah memperluas penyebaran infeksi, bukan menjalankan aksi utama (payload), sehingga pada fase ini virus umumnya belum merusak atau menghapus data.

**3. Triggering (Fase Pemicu)**

Setelah berhasil menyebar, virus akan menunggu hingga syarat (trigger) yang telah diprogram sebelumnya terpenuhi. Trigger dapat berupa tanggal tertentu, jumlah eksekusi program, pengguna membuka file tertentu, atau kondisi lainnya. Ketika syarat tersebut terpenuhi, virus siap menjalankan aksi utamanya.

**4. Execution (Fase Eksekusi)**

Setelah pemicu terpenuhi, virus menjalankan payload, yaitu aksi utama yang telah dirancang oleh pembuatnya. Payload dapat berupa tindakan ringan, seperti menampilkan pesan atau mengubah tampilan layar, hingga tindakan berbahaya, seperti menghapus data, merusak file, mencuri informasi, atau mengganggu kinerja sistem.

---

## 3. Kategori Cyber Crime

Berdasarkan PPT kuliah, cyber crime dibagi menjadi 3 kategori berdasarkan **jenis pelanggaran yang dilakukan pelaku terhadap sistem/data** (bukan berdasarkan siapa korbannya). Ketiganya sama-sama soal tindakan **tanpa izin (unauthorized)**, tapi beda di objek yang dilanggar: hak cipta, hak akses, atau keutuhan sistem.

**1. Cyber Piracy**

Cyber piracy adalah tindakan **menggandakan atau mendistribusikan** karya digital (software, musik, film, data) **tanpa izin** dari pemilik hak cipta. Pelaku tidak merusak atau mengakses secara ilegal — pelanggarannya ada pada **hak kepemilikan intelektual**. Contoh: membajak software berbayar, menyebarkan film/musik secara ilegal lewat internet, menggunakan lisensi software bajakan.

**2. Cyber Trespass**

Cyber trespass adalah tindakan **memasuki/mengakses sistem, jaringan, atau data milik orang lain tanpa izin (unauthorized access)**. Pelaku "masuk ke wilayah" yang bukan haknya — mirip konsep *trespassing* di dunia fisik (masuk properti orang lain tanpa izin). Contoh: hacking ke akun/sistem orang lain, membobol database perusahaan, mengakses jaringan WiFi tanpa izin.

**3. Cyber Vandalism**

Cyber vandalism adalah tindakan **merusak, mengubah, atau menghancurkan** data/sistem milik orang lain secara sengaja. Pelanggarannya ada pada **keutuhan/integritas dan fungsi** dari data atau sistem. Contoh: menyebarkan virus/malware yang merusak file, defacement website (mengubah tampilan situs tanpa izin), menghapus data penting milik orang lain.

---

**Catatan konseptual:** ketiga kategori ini bisa **saling tumpang tindih** dalam satu kasus nyata. Misalnya, seorang hacker bisa melakukan trespass (masuk sistem) lalu vandalism (merusak data) di kejadian yang sama.

---

## 4. Kelebihan dan Kekurangan Sidik Jari dan Pola Retina

### Sidik Jari (Fingerprint)

**Kelebihan:**
- **Biaya perangkat murah** sehingga banyak digunakan pada HP, laptop, dan mesin absensi.
- **Proses verifikasi cepat** dan mudah digunakan, cukup menempelkan jari pada sensor.
- **Ukuran sensor kecil** sehingga mudah diintegrasikan ke berbagai perangkat.
- **Pola sidik jari unik** pada setiap individu.

**Kekurangan:**
- **Sensitif terhadap kondisi jari**, seperti basah, kotor, terluka, atau aus sehingga dapat menurunkan akurasi.
- **Berpotensi dipalsukan (spoofing)** karena sidik jari yang tertinggal pada permukaan benda dapat diduplikasi dengan teknik tertentu.
- **Memerlukan kontak fisik**, sehingga kurang higienis jika digunakan bersama.
- **Tidak dapat diubah** jika data biometriknya bocor.

---

### Pola Retina (Retina Scan)

**Kelebihan:**
- **Akurasi dan keamanan sangat tinggi** karena pola pembuluh darah pada retina sangat unik.
- **Sangat sulit dipalsukan** karena pola pembuluh darah retina berada di dalam mata dan tidak dapat ditiru dengan foto atau cetakan.
- **Tidak mudah rusak oleh faktor eksternal** karena letaknya di bagian dalam mata.
- **Cocok untuk sistem dengan keamanan tingkat tinggi**.

**Kekurangan:**
- **Biaya perangkat mahal** karena menggunakan teknologi pemindaian optik khusus.
- **Kurang nyaman digunakan**, pengguna harus memosisikan mata dengan tepat saat pemindaian.
- **Proses autentikasi relatif lebih lambat** dibanding sidik jari.
- **Dapat dipengaruhi kondisi kesehatan mata**, seperti katarak atau gangguan retina.

---

### Perbandingan Singkat

| Aspek | Sidik Jari | Pola Retina |
|---|---|---|
| Keamanan | Tinggi | Sangat tinggi |
| Akurasi | Tinggi | Sangat tinggi |
| Kecepatan | Cepat | Lebih lambat |
| Biaya | Murah | Mahal |
| Kemudahan penggunaan | Mudah | Kurang nyaman |

**Kesimpulan:**
- **Sidik jari** lebih cocok untuk penggunaan sehari-hari karena murah, cepat, dan praktis.
- **Pola retina** lebih cocok untuk sistem yang membutuhkan keamanan sangat tinggi karena akurasinya lebih baik dan sangat sulit dipalsukan, meskipun biaya implementasinya lebih mahal.

---

## 5. WLAN (Wireless Local Area Network)

### 1. Pengertian Wireless LAN

WLAN adalah jaringan komputer lokal yang menghubungkan perangkat tanpa kabel, menggunakan gelombang radio sebagai media transmisi data, mengacu pada standar **IEEE 802.11**. WLAN memungkinkan perangkat seperti laptop, HP, atau printer saling terhubung dan mengakses jaringan/internet dalam suatu area tanpa perlu kabel fisik.

**Spesifikasi standar 802.11:**

| Standar | Tahun | Frekuensi | Kecepatan Maksimal (teoritis) |
|---|---|---|---|
| 802.11a | 1999 | 5 GHz | 54 Mbps |
| 802.11b | 1999 | 2,4 GHz | 11 Mbps |
| 802.11g | 2003 | 2,4 GHz | 54 Mbps |
| 802.11n | — | 2,4/5 GHz | ~108 Mbps, dikenal dengan teknologi MIMO |

Pemilihan standar biasanya mempertimbangkan kebutuhan kecepatan transfer, jangkauan sinyal (termasuk kemampuan menembus tembok), dan jumlah user yang akan mengakses.

### 2. Istilah-Istilah WLAN

- **Wi-Fi** — nama dagang untuk produk yang mengikuti spesifikasi 802.11.
- **SSID (Service Set Identifier)** — nama identifikasi suatu jaringan wireless. Perangkat dianggap satu jaringan jika menggunakan SSID yang sama.
- **Channel** — jalur frekuensi spesifik dalam pita frekuensi WLAN. Agar bisa saling berkomunikasi, perangkat harus menggunakan channel yang sama.
- **MIMO (Multiple Input Multiple Output)** — teknologi yang meningkatkan throughput, reliabilitas, dan jumlah client yang bisa terkoneksi bersamaan.
- **Throughput** — kecepatan dan kemampuan aktual suatu jaringan dalam mengirim/menerima data.
- **HotSpot** — area yang menyediakan layanan akses internet berbasis wireless.
- **Enkripsi** — metode mengkodekan data agar tidak bisa dibaca pihak lain tanpa proses dekripsi (contoh: WEP, WPA).

### 3. Topologi WLAN

- **Mode Ad-Hoc** — perangkat terhubung langsung satu sama lain (peer-to-peer) tanpa memerlukan Access Point. Cocok untuk jaringan kecil yang tidak perlu terhubung ke jaringan kabel (wired LAN).
- **Mode Infrastruktur** — perangkat terhubung melalui Access Point sebagai central node. Digunakan untuk jaringan yang lebih besar dan kompleks, terutama jika WLAN perlu dihubungkan ke wired LAN.

### 4. Mengenal Security WLAN

- **WEP (Wired Equivalent Privacy)** — mekanisme enkripsi paling awal (akhir 1990-an), menggunakan enkripsi 64-bit (40-bit key + 24-bit initialization vector). Tergolong lemah dan mudah dibobol.
- **WEP2** — versi lanjutan WEP dengan enkripsi 128-bit, membuat serangan brute force butuh waktu lebih lama untuk berhasil dibanding WEP biasa.
- **WPA (Wi-Fi Protected Access)** — menggunakan enkripsi TKIP (Temporal Key Integrity Protocol) dengan algoritma RC4, serta protokol 802.1X. WPA mengatasi kelemahan WEP dengan menyediakan distribusi kunci per-paket. Panjang kunci antara 8-63 karakter.
- **MAC Address Filtering** — membatasi perangkat yang boleh terhubung ke Access Point berdasarkan alamat MAC.

### 5. Ancaman Wireless LAN

- **Pencurian Identitas** — MAC Address sebenarnya bukan mekanisme keamanan yang kuat, karena MAC Address bisa dipalsukan (spoofing) sehingga penyerang bisa menyamar sebagai perangkat yang sah.
- **Man-in-the-Middle (MITM)** — penyerang menyisipkan perangkatnya sendiri di antara komunikasi client dan Access Point, sehingga bisa menyadap atau memanipulasi data yang lewat tanpa disadari kedua pihak.
- **Denial of Service (DoS)** — serangan yang menyebabkan downtime pada jaringan; pada WLAN, serangan ini bisa datang dari segala arah karena sifat medianya yang broadcast melalui udara.
- **Network Injection** — teknik menyisipkan paket ke jaringan atau ke Access Point untuk menguasai keseluruhan jaringan, terutama jika AP terhubung ke jaringan yang tidak terfilter dengan baik (memanfaatkan protokol seperti OSPF, RIP, atau spanning tree).

### 6. Anatomi Hacking WLAN

Proses peretasan WLAN umumnya melalui 3 tahap besar:

1. **War Driving** — kegiatan mencari SSID aktif di suatu area. Informasi yang dikumpulkan mencakup MAC Address, SSID, channel, kekuatan sinyal, vendor, jenis enkripsi, hingga IP Address/subnet target.
2. **Anatomy Hacking** — tahapan sistematis untuk menembus sistem: **Footprinting** (mengumpulkan info awal target) → **Scanning** (memindai celah lebih detail) → **Gaining Access** (mendapatkan akses, misal lewat brute force) → **Escalating Privilege** (menaikkan hak akses) → **Covering Track** (menghapus jejak) → **Creating Backdoors** (menanam akses tersembunyi untuk kembali) → **DoS** (jika tujuan akhirnya melumpuhkan, bukan mencuri data).
3. **Forensic System** — proses investigasi setelahnya: mengidentifikasi, meneliti, dan menyimpulkan apa yang terjadi pada sistem secara analitis (biasanya dilakukan pihak korban/investigator, bukan penyerang).

### 7. Implementasi Serangan WLAN

Contoh praktik nyata yang biasa dilakukan penyerang, dari awal hingga eksploitasi:
- **Pengintaian jarak jauh** — menggunakan kartu jaringan wireless dengan antena tambahan untuk menangkap sinyal dari luar ruangan tanpa perlu dekat secara fisik.
- **Menyembunyikan identitas penyerang** — menggunakan firewall untuk melindungi diri dari deteksi balik oleh IDS (Intrusion Detection System) milik target.
- **Pengumpulan informasi jaringan** — memakai tools seperti NetStumbler untuk mendapatkan IP Address, access point, dan server DHCP target.
- **Sniffing lalu lintas data** — menangkap paket yang melintas di udara memakai protocol analyzer untuk mendapatkan MAC/IP Address yang valid, serta mengintip data dari protokol yang tidak terenkripsi (Telnet, POP, HTTP) untuk mencuri username/password.
- **MAC Spoofing** — memalsukan MAC Address (misal dengan tool SMAC) untuk melewati MAC Filtering dan menangkap lebih banyak paket data.
- **Koneksi & eksplorasi pasif** — menyambungkan diri ke WLAN target, memeriksa apakah mendapat IP secara diam-diam, lalu memindai kelemahan sistem/jaringan untuk memperluas akses ke bagian jaringan lain.

**Tools yang umum dipakai:** Kismet (war-driving & sniffing), Airsnort (cracking WEP), Wireshark/Ethereal (analisis paket), Airjack (MITM & DoS), FakeAP (membuat AP palsu), WEPCrack (cracking WEP).

### 8. Bagaimana Mengamankan WLAN?

- **Ubah password & IP default** Access Point — kredensial bawaan pabrik sangat mudah ditebak/dicari di internet.
- **Aktifkan enkripsi kuat**, gunakan WPA dengan Pre-Shared Key (WPA-PSK) dan password yang aman.
- **Matikan broadcast SSID** — agar jaringan tidak mudah terdeteksi lewat proses War Driving.
- **Ganti nama SSID default** — hindari nama yang mudah ditebak atau mengidentifikasi pemilik/lokasi.
- **Aktifkan MAC Address Filtering** — menambah lapisan pembatasan akses, meski bisa di-spoof.
- **Nonaktifkan DHCP, gunakan IP Static** — mempersulit penyerang mendapat alamat IP otomatis saat mencoba masuk ke jaringan.
- **Tambahkan security ekstra** — misal Captive Portal, atau firmware tambahan pada Access Point.
- **Monitoring Access Point via client** — memantau aktivitas AP secara berkala untuk mendeteksi anomali.

---

### Tugas: Topologi WLAN dengan Hidden SSID

**Soal tugas:** *"Buat topologi jaringan nirkabel sederhana untuk mengonfigurasi router dan menyembunyikan SSID. Lalu hubungkan sebuah laptop ke jaringan tersembunyi."*

Karena tugas ini butuh **router** sebagai pengendali konfigurasi, topologi yang dipakai adalah **Mode Infrastruktur** — router bertindak sebagai central node (Access Point), dan laptop menjadi client yang terhubung ke sana.

```
[Internet/ISP] --- [Router/Access Point] ~~~ (wireless) ~~~ [Laptop]
```

**Langkah konfigurasi (umum, tampilan bisa beda tiap merk router):**
1. Sambungkan laptop ke router (via kabel LAN atau WiFi default terlebih dahulu).
2. Buka browser, akses IP default router (umumnya `192.168.1.1` atau `192.168.0.1`).
3. Login ke halaman admin (cek label di bodi router untuk username/password default).
4. Masuk ke menu **Wireless Settings**.
5. Ubah nama SSID sesuai keinginan, aktifkan enkripsi WPA-PSK, dan set password WiFi.
6. Cari opsi **"Enable SSID Broadcast"**, lalu **nonaktifkan** (atau centang "Hide SSID").
7. Simpan pengaturan; router biasanya restart otomatis.

**Menghubungkan laptop ke jaringan tersembunyi:**
Karena SSID tidak muncul di daftar WiFi otomatis, koneksi harus dilakukan manual — buka pengaturan WiFi laptop, pilih opsi **"Connect to a hidden network"**, masukkan **nama SSID persis**, pilih jenis keamanan (WPA2-Personal), lalu masukkan password.

**Tujuan menyembunyikan SSID:** mengurangi visibilitas jaringan dari proses War Driving — jaringan tidak muncul di daftar WiFi umum sehingga tidak mudah jadi target awam yang sekadar iseng melakukan scanning.

**Catatan penting:** hidden SSID **bukan metode keamanan yang kuat berdiri sendiri** — tools seperti Kismet tetap bisa mendeteksi keberadaan jaringan lewat paket probe request/response yang tetap terpancar meski SSID tidak di-broadcast. Karena itu, praktiknya selalu dikombinasikan dengan enkripsi WPA-PSK dan MAC Filtering.

---

## 6. (Kisi-kisi berikutnya — menyusul)

