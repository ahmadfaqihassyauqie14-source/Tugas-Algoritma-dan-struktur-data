# Tugas 2 Algoritma dan Struktur Data

**Nama :** Ahmad Faqih

**Kelas :** 3B

**Nim :** 1251170138

**Mata Kuliah :** Algoritma dan Struktur Data

**Dosen Pengampu :** Al Muhdi Karim, M.Hum

# A. ANALISIS KOMPONEN

## Studi Kasus

Studi kasus yang digunakan adalah **Sistem Transaksi & Validasi Toko Buku Modern**.

Algoritma ini digunakan untuk menghitung total pembayaran pelanggan berdasarkan status member, jumlah buku yang dibeli, dan total belanja awal.

## 1. Variabel dan Tipe Data

| Variabel | Tipe Data | Keterangan |
|---|---|---|
| `is_member` | Boolean | Menentukan apakah pelanggan member atau bukan |
| `jumlah_buku` | Integer | Menyimpan jumlah buku yang dibeli |
| `total_awal` | Real/Float | Menyimpan total belanja sebelum diskon |
| `diskon_persen` | Real/Float | Menyimpan persentase diskon |
| `nominal_diskon` | Real/Float | Menyimpan jumlah uang yang didapat dari diskon |
| `total_bayar` | Real/Float | Menyimpan total yang harus dibayar setelah diskon |

## 2. Struktur Kontrol yang Digunakan

### a. Sequence

Sequence digunakan saat langkah program dijalankan secara berurutan.

Contohnya mulai dari memasukkan data, mengecek data, menghitung diskon, sampai menampilkan hasil akhir.

### b. Iteration

Iteration digunakan untuk melakukan validasi input.

Kalau `total_awal < 0` atau `jumlah_buku < 1`, maka sistem akan meminta pengguna memasukkan data lagi sampai datanya benar.

Perulangan yang digunakan adalah **WHILE**.

### c. Selection

Selection digunakan untuk menentukan besar diskon berdasarkan status member, total belanja, dan jumlah buku.

Struktur yang digunakan adalah **IF - THEN - ELSE** dan terdapat kondisi IF di dalam kondisi lainnya.

---

# B. PENYUSUNAN PSEUDOCODE

## Program Sistem Transaksi Toko Buku
```
DEKLARASI:

    is_member : Boolean
    jumlah_buku : Integer
    total_awal : Real
    diskon_persen : Real
    nominal_diskon : Real
    total_bayar : Real

ALGORITMA:

    INPUT(is_member)
    INPUT(jumlah_buku)
    INPUT(total_awal)

    WHILE total_awal < 0 OR jumlah_buku < 1 DO
    OUTPUT("Input tidak valid, silakan masukkan ulang")

    INPUT(is_member)
    INPUT(jumlah_buku)
    INPUT(total_awal)
    ENDWHILE

    diskon_persen ← 0

    IF is_member = TRUE

    THEN
    diskon_persen ← 10

    IF total_awal >= 200000 AND jumlah_buku >= 3 THEN
    diskon_persen ← 15
    ENDIF

    ELSE
    IF total_awal >= 300000 THEN
    diskon_persen ← 5

    ELSE
    diskon_persen ← 0
    ENDIF

    ENDIF

    nominal_diskon ← total_awal * diskon_persen / 100

    total_bayar ← total_awal - nominal_diskon

    OUTPUT(nominal_diskon)
    OUTPUT(total_bayar)

END PROGRAM
```

## sedikit penjelasan 

Menurut saya alur algoritma ini cukup sederhana. Pertama pengguna memasukkan data seperti status member, jumlah buku, dan total belanja.
setelah itu data dicek terlebih dahulu. Kalau total belanja masih negatif atau jumlah bukunya kurang dari 1, maka data dianggap salah dan pengguna diminta memasukkan ulang.
Kalau datanya sudah benar, sistem lanjut menentukan diskon. Untuk member, diskon awalnya 10%. Tapi kalau total belanja minimal Rp200.000 dan jumlah buku minimal 3, diskonnya jadi 15%.
Sedangkan untuk bukan member, kalau total belanja minimal Rp300.000 maka mendapat diskon 5%. Kalau kurang dari itu tidak mendapat diskon sama sekali.
Setelah persentase diskon didapat, sistem menghitung nominal diskon dan total yang harus dibayar.

---

# C. UJI LOGIKA / TRACE TABLE

## Kasus A

**Input:**

* `is_member = True`
* `total_awal = 250000`
* `jumlah_buku = 4`

Karena pelanggan adalah member, pelanggan mendapat diskon dasar 10%.

Kemudian dicek lagi apakah total belanja minimal Rp200.000 dan jumlah buku minimal 3.

Karena kedua kondisi terpenuhi, diskon menjadi 15%.

Perhitungan:

```text
nominal_diskon = 250000 × 15 / 100
               = 37500

total_bayar = 250000 - 37500
            = 212500
```

### Trace Table Kasus A

| Langkah | Kondisi / Proses | Nilai |
|---|---|---|
| 1 | Input `is_member` | True |
| 2 | Input `total_awal` | 250000 |
| 3 | Input `jumlah_buku` | 4 |
| 4 | Validasi input | Valid |
| 5 | Cek member | True |
| 6 | Diskon awal | 10% |
| 7 | Cek total >= 200000 | True |
| 8 | Cek jumlah buku >= 3 | True |
| 9 | Diskon akhir | 15% |
| 10 | Nominal diskon | Rp37.500 |
| 11 | Total bayar | Rp212.500 |

**Hasil akhir:** pelanggan mendapat diskon **Rp37.500** dan harus membayar **Rp212.500**.

---

## Kasus B

**Input:**

* `is_member = False`
* `total_awal = 350000`
* `jumlah_buku = 2`

Karena pelanggan bukan member, sistem mengecek apakah total belanja minimal Rp300.000.

Total belanja Rp350.000, jadi pelanggan mendapat diskon 5%.

Perhitungan:

```text
nominal_diskon = 350000 × 5 / 100
               = 17500

total_bayar = 350000 - 17500
            = 332500
```

### Trace Table Kasus B

| Langkah | Kondisi / Proses | Nilai |
|---|---|---|
| 1 | Input `is_member` | False |
| 2 | Input `total_awal` | 350000 |
| 3 | Input `jumlah_buku` | 2 |
| 4 | Validasi input | Valid |
| 5 | Cek member | False |
| 6 | Cek total >= 300000 | True |
| 7 | Diskon | 5% |
| 8 | Nominal diskon | Rp17.500 |
| 9 | Total bayar | Rp332.500 |

**Hasil akhir:** pelanggan mendapat diskon **Rp17.500** dan harus membayar **Rp332.500**.

---

## Kasus C

**Input awal:**

* `is_member = False`
* `total_awal = -50000`
* `jumlah_buku = 1`

Pada input awal, `total_awal` bernilai -Rp50.000.

Karena total belanja kurang dari 0, input dianggap tidak valid. Sistem kemudian meminta pengguna memasukkan ulang data.

Input diperbaiki menjadi:

* `is_member = False`
* `total_awal = 100000`
* `jumlah_buku = 1`

Karena pelanggan bukan member dan total belanja kurang dari Rp300.000, maka tidak mendapatkan diskon.

Perhitungan:

```text
nominal_diskon = 100000 × 0 / 100
               = 0

total_bayar = 100000 - 0
            = 100000
```

### Trace Table Kasus C

| Langkah | Kondisi / Proses | Nilai |
|---|---|---|
| 1 | Input `is_member` | False |
| 2 | Input `total_awal` | -50000 |
| 3 | Input `jumlah_buku` | 1 |
| 4 | Cek `total_awal < 0` | True |
| 5 | Status input | Tidak valid |
| 6 | Input diulang | Ya |
| 7 | `total_awal` setelah diperbaiki | 100000 |
| 8 | `jumlah_buku` | 1 |
| 9 | Validasi input | Valid |
| 10 | Cek member | False |
| 11 | Cek total >= 300000 | False |
| 12 | Diskon | 0% |
| 13 | Nominal diskon | Rp0 |
| 14 | Total bayar | Rp100.000 |

**Hasil akhir:** pelanggan tidak mendapat diskon dan harus membayar **Rp100.000**.

---

