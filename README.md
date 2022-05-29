# P2_Probstat_E_5025201011
Repository untuk pengerjaan Praktikum 2 mata kuliah Probabilitas dan Statistik 2022.

</br>

## Identitas
| Nama                      | NRP        |
|---------------------------|------------|
| Nur Muhammad Ainul Yaqin  | 5025201011 |

</br>

## Soal 1
Seorang peneliti melakukan penelitian mengenai pengaruh aktivitas 𝐴 terhadap kadar saturasi oksigen pada manusia. Peneliti tersebut mengambil sampel sebanyak 9 responden. Pertama, sebelum melakukan aktivitas 𝐴, peneliti mencatat kadar saturasi oksigen dari 9 responden tersebut. Kemudian, 9 responden tersebut diminta melakukan aktivitas 𝐴. Setelah 15 menit, peneliti tersebut mencatat kembali kadar saturasi oksigen dari 9 responden tersebut. Berikut data dari 9 responden mengenai kadar saturasi oksigen sebelum dan sesudah melakukan aktivitas 𝐴.

| Responden   | X        | Y        |
|-------------|----------|----------|
| 1 | 78 | 100 |
| 2 | 75 | 95 |
| 3 | 67 | 70 |
| 4 | 77 | 90 |
| 5 | 70 | 90 |
| 6 | 72 | 90 |
| 7 | 78 | 89 |
| 8 | 74 | 90 |
| 9 | 77 | 100 |

Berdasarkan data pada tabel diatas, diketahui kadar saturasi oksigen dari responden ke-3 ketika belum melakukan aktivitas 𝐴 sebanyak 67, dan setelah melakukan aktivitas 𝐴 sebanyak 70.

### Poin A
> Carilah standar deviasi dari data selisih pasangan pengamatan tabel di atas.

*Pertama*, memasukkan data yang telah ada ke dalam variabel sesuai pengelompokannya.

```R
before <- c(78, 75, 67, 77, 70, 72, 78, 74, 77)
after <- c(100, 95, 70, 90, 90, 90, 89, 90, 100)
```

*Kedua*, mencari selisih dari antar data dengan index yang sama. Kemudian, dilakukan pencarian rata-rata dari selisih-selisih tersebut untuk digunakan dalam mencari nilai standar deviasinya.

```R
difference <- after - before
difference
mean(difference)
sd(difference)
```

![1a](https://user-images.githubusercontent.com/64957624/170872905-64b82bf7-6ab2-401b-ab02-de37f1ac7c9e.png)

</br>

### Poin B
>Carilah nilai t (p-value).

Solusi dilakukan dengan menggunakan fungsi `t.test()` sebagai berikut dengan parameter masukan data yaitu data kelompok yang telah dikelompokkan pada poin sebelumnya.

```R
t.test(after, before, paired = TRUE)
```

![1b](https://user-images.githubusercontent.com/64957624/170873083-01d171c1-702b-457f-a396-60fe649119ec.png)

</br>

### Poin C
>Tentukanlah apakah terdapat pengaruh yang signifikan secara statistika dalam hal kadar saturasi oksigen , sebelum dan sesudah melakukan aktivitas 𝐴 jika diketahui tingkat signifikansi 𝛼 = 5% serta H0 : “tidak ada pengaruh yang signifikan secara statistika dalam hal kadar saturasi oksigen , sebelum dan sesudah melakukan aktivitas 𝐴”

Berdasarkan hasil dari poin sebelumnya, diketahui bahwa nilai probabilitas dari uji 𝑡 (p-value) adalah 6.003e-05 atau 0.00006003. Karena nilai probabilitas tersebut lebih kecil dibandingkan tingkat signifikansi 𝛼 = 0.05, maka **hipotesis nol ditolak dan hipotesis alternatif diterima.** 

Hal ini berarti terdapat pengaruh yang signifikan secara statistika dalam hal kadar saturasi oksigen, sebelum dan sesudah melakukan aktivitas 𝐴 pada tingkat signifikansi 5%.


</br>

## Soal 2
Diketahui bahwa mobil dikemudikan rata-rata lebih dari 20.000 kilometer per tahun. Untuk menguji klaim ini, 100 pemilik mobil yang dipilih secara acak diminta untuk mencatat jarak yang mereka tempuh. Jika sampel acak menunjukkan rata-rata 23.500 kilometer dan standar deviasi 3900 kilometer. (Kerjakan menggunakan 2 library seperti referensi pada modul).
### Poin A
>Apakah Anda setuju dengan klaim tersebut?

Setuju, karena dengan rata-rata 23.5000 dari sampel acak dengan standar deviasi 3900 kilometer, maka sangatlah mungkin klaim tersebut valid. Hal itu karena grafik dari persebaran data distribusi normal yang dihasilkan akan lebih pekat di daerah lebih dari 20.000 kilometer dengan asumsi nilai tengah grafik tersebut adalah rata-rata dari sampel acak yang didapatkan.

Selanjutnya, digunakan sebuah package library BSDA untuk membuat solusi permasalahannya.

```R
install.packages("BSDA")
library(BSDA)
```

</br>

### Poin B
>Jelaskan maksud dari output yang dihasilkan!

Fungsi yang digunakan adalah fungsi `tsum.test()` dengan parameter-parameter yang disebutkan pada poin sebelumnya. Hasilnya adalah sebagai berikut.

```R
tsum.test(mean.x = 23500, s.x = 3900, n.x = 100)
```

![2b](https://user-images.githubusercontent.com/64957624/170874039-90e7a435-fe58-42f8-820c-28981119fb07.png)

Hal tersebut berarti, 

</br>

### Poin C
>Buatlah kesimpulan berdasarkan P-Value yang dihasilkan!

Karena nilai probabilitas tersebut lebih kecil dibandingkan tingkat signifikansi 𝛼 = 0.05, maka **hipotesis nol diterima dan hipotesis alternatif ditolak.** Sehingga, kesimpulan yang didapatkan yaitu bahwa mobil dikemudikan rata-rata lebih dari 20.000 kilometer per tahun.

</br>

## Soal 3
Diketahui perusahaan memiliki seorang data analyst ingin memecahkan permasalahan pengambilan keputusan dalam perusahaan tersebut. Selanjutnya didapatkanlah data berikut dari perusahaan saham tersebut.

| Nama Kota/Atribut   | Bandung        | Bali       |
|-------------|----------|----------|
| Jumlah Saham              | 19 | 27 |
| Sampel Mean               | 3.64 | 2.79 |
| Sampel Standar Deviasi    | 1.67 | 1.32 |

Dari data diatas berilah keputusan serta kesimpulan yang didapatkan dari hasil
diatas. Asumsikan nilai variancenya sama, apakah ada perbedaan pada
rata-ratanya (α= 0.05)? Buatlah:

### Poin A
>H0 dan H1

Berdasarkan deskripsi dan data yang terlampir, maka dapat disusun hipotesis H0 dan H1 sebagai berikut.
- H0 ← μ1 = μ2 (rata-rata saham di Bandung sama dengan di Bali)
- H1 ← μ1 ≠ μ2 (rata-rata saham di Bandung tidak sama dengan di Bali)

</br>

### Poin B
>Hitung sampel statistik

Solusi dilakukan dengan menggunakan fungsi `tsum.test()` dengan parameter sesuai dengan data pada tabel terlampir. Fungsi tersebut menghasilkan nilai dari sampel statistik.

```R
tsum.test(mean.x=3.64, s.x = 1.67, n.x = 19, 
          mean.y =2.79 , s.y = 1.32, n.y = 27, 
          alternative = "greater", var.equal = TRUE)
```

![3b](https://user-images.githubusercontent.com/64957624/170874938-94512ecc-99e2-41e2-9f9e-9175000cc61d.png)

</br>

### Poin C
>Lakukan uji statistik (df =2)

Digunakan sebuah package library Mosaic untuk membuat solusi permasalahannya.

```R
install.packages("mosaic")
library(mosaic)
```

Selanjutnya, digunakan fungsi `plotDist()` untuk mendapatkan gambaran atau visualisasi dari statistik dengan derajat bebas sebesar 2.

```R
plotDist(dist = 't', df = 2, col = "blue")
```

![3c](https://user-images.githubusercontent.com/64957624/170875180-ac54354b-7b25-44f9-a6d8-bfe1f22cd1f5.png)

</br>

### Poin D
>Nilai Kritikal

Digunakan fungsi `qchisq()` dengan nilai `df` sesuai dengan yang telah terlampir untuk mendapatkan nilai kritikal.

```R
qchisq(p = 0.05, df = 2, lower.tail = FALSE)
```

![3d](https://user-images.githubusercontent.com/64957624/170875348-aed39047-c1f4-4bd4-b4b8-9b65ec999e8d.png)

</br>

### Poin E
>Keputusan

Teori keputusan adalah teori formal pengambilan keputusan di bawah ketidakpastian. Aksinya adalah `({a}\_{a∈A})` dengan kemungkinan konsekuensinya adalah `({c}_{c∈C})` (tergantung pada keadaan dan tindakan).

Maka keputusan dapat diperoleh dengan fungsi `t.test`

</br>

### Poin F
>Kesimpulan

Kesimpulan yang didapatkan yaitu perbedaan rata-rata yang terjadi tidak ada jika dilihat dari uji statistik.

Namun, akan ada (meski tidak signifikan) jika dipengaruhi oleh nilai kritikal.

</br>

## Soal 4



</br>

## Soal 5