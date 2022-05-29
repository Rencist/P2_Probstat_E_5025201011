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

Hal tersebut berarti dengan interval kepercayaan 95%, rata-rata jarak tempuh mobil per tahun berada di antara 22.726,16 km dan 24.273,84 km. 

Dengan interval kepercayaan 95% dan dari 100 responden, dapat dibuktikan bahwa rata-rata jarak tempuh mobil per thn lebih dari 20.000 km karena nilai p-value kurang dari tingkat signifikansi 𝛼 = 0.05.

</br>

### Poin C
>Buatlah kesimpulan berdasarkan P-Value yang dihasilkan!

Karena nilai probabilitas tersebut lebih kecil dibandingkan tingkat signifikansi 𝛼 = 0.05, maka **hipotesis nol ditolak dan hipotesis alternatif diterima.** Sehingga, kesimpulan yang didapatkan yaitu bahwa mobil dikemudikan rata-rata lebih dari 20.000 kilometer per tahun.

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
Seorang Peneliti sedang meneliti spesies dari kucing di ITS. Dalam penelitiannya ia mengumpulkan data tiga spesies kucing yaitu kucing oren, kucing hitam dan kucing putih dengan panjangnya masing-masing.

Jika diketahui dataset pada **https://intip.in/datasetprobstat1** dan H0 adalah tidak ada perbedaan panjang antara ketiga spesies atau rata-rata panjangnya sama, maka kerjakan atau carilah:

### Poin A
>Buatlah masing masing jenis spesies menjadi 3 subjek "Grup" (grup 1, grup 2, dan grup 3). Lalu gambarkan plot kuantil normal untuk setiap kelompok dan lihat apakah ada outlier utama dalam homogenitas varians.

*Pertama*, memasukkan data dari dataset yang disediakan.

```R
dataoneway <- read.table("data_soal_4.txt", h = T)
attach(dataoneway)
names(dataoneway)
```

*Kedua*, melakukan grouping sesuai dengan label yang telah ditentukan sekaligus melakukan pengecekan value dalam grup yang dihasilkan.

```R
dataoneway$Group <- as.factor(dataoneway$Group)
dataoneway$Group = factor(dataoneway$Group, labels = c("Kucing Oren", "Kucing Hitam", "Kucing Putih"))

class(dataoneway$Group)
```

![4a](https://user-images.githubusercontent.com/64957624/170876621-adbbe23b-8282-4b73-b250-0b2549d31da5.png)

*Ketiga*, membagi tiap valuer menjadi 3 bagian sesuai dengan label grup yang telah dibuat.

```R
Group1 <- subset(dataoneway, Group == "Kucing Oren")
Group2 <- subset(dataoneway, Group == "Kucing Hitam")
Group3 <- subset(dataoneway, Group == "Kucing Putih")
```

*Keempat*, menggambar plot kuantil normal untuk setiap grup untuk melihat distribusi data dan outlier utama dalam homogenitas varians pada masing-masing grup.

```R
qqnorm(Group1$Length)
qqline(Group1$Length)
```

![4aa](https://user-images.githubusercontent.com/64957624/170876859-83e10e7b-54fd-47d4-807c-c2955967235a.png)

```R
qqnorm(Group2$Length)
qqline(Group2$Length)
```

![4ab](https://user-images.githubusercontent.com/64957624/170876874-b58ec0b6-9eab-4bae-a387-5c71d11b0ca7.png)

```R
qqnorm(Group3$Length)
qqline(Group3$Length)
```

![4ac](https://user-images.githubusercontent.com/64957624/170876886-fc9252ff-bc4e-4b70-b4f3-f0d2797fde58.png)

</br>

### Poin B
>Carilah atau periksalah homogeneity of variances-nya. Berapa nilai p yang didapatkan? Apa hipotesis dan kesimpulan yang dapat diambil?

Untuk mendapatkan homogeneity of variances, digunakan sebuah fungsi yaitu fungsi `bartlett.test()` dengan parameter dari data yang telah dimasukkan sebelumnya.

```R
bartlett.test(Length ~ Group, data = dataoneway)
```

![4b](https://user-images.githubusercontent.com/64957624/170877622-efc5728f-e53a-4de0-a085-1acb8f00c21c.png)

Dari hasil uji fungsi `bartlett.test()` didapatkan p-value sebesar 0.8054 yang lebih dari nilai 𝛼 = 0.05 sehingga asumsi kesamaan varians terpenuhi.

</br>

### Poin C
>Untuk uji ANOVA (satu arah), buatlah model linier dengan panjang versus grup dan beri nama model tersebut model 1.

Untuk membuat uji anova dan model liniernya, digunakan fungsi yaitu fungsi `lm()` dan `anova()` dengan parameter dari data yang telah dimasukkan sebelumnya.

```R
model1 = lm(Length ~ Group, data = dataoneway)
anova(model1)
```

![4c](https://user-images.githubusercontent.com/64957624/170877742-5c0f86d2-2707-46be-bedf-a0905bbcbaa1.png)


</br>

### Poin D
>Dari hasil poin C, berapakah nilai p? Apa yang dapat Anda simpulkan dari H0?

Berdasarkan hasil yang didapatkan pada poin sebelumnya, pada taraf uji 5% didapatkan nilai p-value sebesar 0.0013. Maka, terdapat perbedaan panjang kucing yang signifikan berdasarkan grupnya.

</br>

### Poin E
>Verifikasilah jawaban model 1 dengan Post-hoc test Tukey HSD, dari nilai p yang didapatkan apakah satu jenis kucing lebih panjang dari yang lain? Jelaskan.

Untuk verifikasi jawaban model 1 sebelumnya, digunakan sebuah fungsi yaitu fungsi `TukeyHSD()` dengan parameter model 1 dari AOV sebelumnya.

```R
TukeyHSD(aov(model1))
```

![4e](https://user-images.githubusercontent.com/64957624/170877879-582c1df7-377f-48e4-baff-c4917c02ed51.png)

Dari hasil uji Tukey, dapat dilihat kombinasi dari kelompok mana yang secara signifikan berbeda. Jika menggunakan 𝛼 = 5%, **perbedaan panjang kucing yang signifikan adalah grup 2 (Kucing Hitam) terhadap grup 1 (Kucing Oren) dan grup 3 (Kucing Putih)**.

</br>

### Poin F
>Visualisasikan data dengan ggplot2

Digunakan fungsi `ggplot()` untuk melakukan visualisasi data.

```R
install.packages("ggplot2")
library("ggplot2")

ggplot(dataoneway, aes(x = Group, y = Length)) + geom_boxplot(fill = "grey80", colour = "black") + scale_x_discrete() + xlab("Treatment Group") + ylab("Length (cm)")
```

![4f](https://user-images.githubusercontent.com/64957624/170877905-19ffda5c-13a4-4b05-be5a-513121fa36a5.png)

</br>

## Soal 5
Data yang digunakan merupakan hasil eksperimen yang dilakukan untuk mengetahui pengaruh suhu operasi (100˚C, 125˚C, dan 150˚C) dan tiga jenis kaca pelat muka (A, B dan C) pada keluaran cahaya tabung osiloskop. Percobaan dilakukan sebanyak 27 kali dan didapatkan [**data hasil eksperimen berikut**](https://drive.google.com/file/d/1aLUOdw_LVJq6VQrQEkuQhZ8FW43FemTJ/view). Dengan data tersebut:

### Poin A
>Buatlah plot sederhana untuk visualisasi data

```R
install.packages("multcompView")
library(readr)
library(ggplot2)
library(multcompView)
library(dplyr)
```


```R
GTL <- read_csv("data_soal_5.csv")
head(GTL)
```

![5aa](https://user-images.githubusercontent.com/64957624/170877976-eaac5491-e4b5-4062-be1e-9dc1b3631d45.png)

```R
str(GTL)
```

![5ab](https://user-images.githubusercontent.com/64957624/170878012-15dc056c-343e-4ff0-9af1-64fed63f0024.png)

```R
qplot(x = Temp, y = Light, geom = "point", data = GTL) + facet_grid(.~Glass, labeller = label_both)
```

![5ac](https://user-images.githubusercontent.com/64957624/170878035-dcf7884a-d6aa-4715-960e-71505362bb3b.png)

</br>

### Poin B
>Lakukan uji ANOVA dua arah

```R
GTL$Glass <- as.factor(GTL$Glass)
GTL$Temp_Factor <- as.factor(GTL$Temp)
str(GTL)
```

![5ba](https://user-images.githubusercontent.com/64957624/170878099-b8777847-dd91-4454-9ff0-08c8de4be64f.png)

```R
anova <- aov(Light ~ Glass*Temp_Factor, data = GTL)
summary(anova)
```

![5bb](https://user-images.githubusercontent.com/64957624/170878125-c178eb3e-04b3-40ff-8b62-5b95674dfd8f.png)



</br>

### Poin C
>Tampilkan tabel dengan mean dan standar deviasi keluaran cahaya untuk setiap perlakuan (kombinasi kaca pelat muka dan suhu operasi)

```R
data_summary <- group_by(GTL, Glass, Temp) %>%
  summarise(mean = mean(Light), sd = sd(Light)) %>%
  arrange(desc(mean))
print(data_summary)
```

![5c](https://user-images.githubusercontent.com/64957624/170878143-acdb24f5-fc7b-4e25-ba60-0e915f7f3612.png)

</br>

### Poin D
>Lakukan uji Tukey

```R
tukey <- TukeyHSD(anova)
print(tukey)
```

![5da](https://user-images.githubusercontent.com/64957624/170878200-7053be86-1ae8-4743-a908-204d63a34635.png)

![5db](https://user-images.githubusercontent.com/64957624/170878210-18182cfa-69e8-4633-ba58-512fb93b46f6.png)

</br>

### Poin E
Buatlah plot sederhana untuk visualisasi data
>Gunakan compact letter display untuk menunjukkan perbedaan signifikan antara uji Anova dan uji Tukey

```R
tukey.cld <- multcompLetters4(anova, tukey)
print(tukey.cld)
```

![5ea](https://user-images.githubusercontent.com/64957624/170878296-3c210e50-74ac-4440-a7bf-c65357d884fd.png)

```R
cld <- as.data.frame.list(tukey.cld$`Glass:Temp_Factor`)
data_summary$Tukey <- cld$Letters
print(data_summary)
```

![5eb](https://user-images.githubusercontent.com/64957624/170878313-838a1d73-743a-4f29-a168-628e14ebf188.png)

</br>
