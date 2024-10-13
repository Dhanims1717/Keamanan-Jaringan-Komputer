**Nama: Dhani Medianto Saputra** 

**Nim : 09011282126067 Keamanan Jaringan Komputer** 

**Dumping And Cracking SAM Hashes to Extract PlainText Password** 

Security Account Manager (SAM) adalah basis data di sistem operasi Windows yang menyimpan informasi akun pengguna dan deskriptor keamanannya. File ini menyimpan kata sandi pengguna dalam bentuk hash (LM dan NTLM). Karena proses hashing bersifat satu arah, ini memberikan tingkat keamanan dalam penyimpanan kata sandi.Dalam konteks peretasan, penyerang biasanya akan mengekstrak hash kata sandi setelah berhasil mengakses komputer target. Hash ini memungkinkan mereka untuk melakukan berbagai serangan, seperti peretasan kata sandi, menggunakan hash untuk mengakses sistem lain, menganalisis kata sandi, dan mengidentifikasi pola untuk memecahkan kata sandi lain dalam lingkungan yang sama.Untuk dapat mengekstrak isi file SAM, diperlukan hak akses administrator. Menilai kekuatan kata sandi  adalah  langkah  penting  dalam  penilaian  keamanan.  Proses  ini  dimulai  dengan mengekstrak hash SAM dan kemudian menggunakan metode dekripsi untuk mendapatkan kata sandi dalam bentuk teks biasa. 

Tujuan dari dumping dan cracking ini adalah untuk membantu mempelajari cara: 

- Mengetahui cara mengunakan alat pwdump7 untuk mengekstrak hash kata sandi 
- Mengetahui cara mengunakan alat Ophcrack untuk memecahkan kata sandi dan mendapatkan teks biasa 
1. Pertama, kita mencari tahu User ID dengan username menggunakan cmd administrator mode. 

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.001.png)

2. Kemudian ketik code wmic useraccount get name,sid yang memiliki fungsi menampilkan daftar semua akun pengguna yang ada di sistem beserta SID-nya masing-masing. 

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.002.png)

3. Kemudian mendownload dan mengekstrak file pwdump dan ophcrack 

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.003.png)

4. Setelah itu buka dan copy lokasi file pwdump dan klik enter untuk masuk ke directory pwdump- master , kemudian ketik PwDump7.exe untuk mendapatkan dan menampilkan password hashes dan userID. 

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.004.png)

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.005.png)

5. Kemudian untuk memindahkan dan men-copy semua data hasil dari PwDump7.exe ke hashes.txt menggunakan command PwDump7.exe > c:\hashes.txt 

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.006.png)

6. Berikut ini adalah isi file dari hashes.txt. 

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.007.png)

7. Selanjutnya mengisi semua username yang kosong sesuai dengan username pengguna pada step 2 kemudian save file hashes.txt 

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.008.png)

8. Selanjutnya buka oph crack kemudian pilih load PWDUMP file dan pilih file hashes.txt sebelumnya. 

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.009.jpeg)

9. File Hashes tersebut akan tampil dengan lm hash dan nt hash sesuai username user. 

![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.010.png)

10. Kemudia klik table dan pada table selection pilih vista free kemudian klik install, kemudian pilih table vista free yang sudah di download sebelumnya . ( table vista free bisa di download menggunakan link :[ https://ophcrack.sourceforge.io/tables.php)](https://ophcrack.sourceforge.io/tables.php) 

    ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.011.png)

    ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.012.png)

11. Setelah table tambil kemudian klik icon crack disamping icon untuk mulai memecahkan kata sandi. Ophcrack akan membutuhkan waktu beberapa menit untuk memecahkan kata sandi. Tunggu hingga proses pemecahan kata sandi selesai. 

    ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.013.png)

12. Setelah  selesai  maka  password  akan  tampil,  Jika  hasilnya  menunjukkan  not  found  maka kemungkinan besar karena windows 10 terbaru secara default tidak lagi menyimpan password di hash  LM  karena  kurang  aman  atau  bisa  juga  karena  beberapa  akun  (seperti  "Guest"  atau "DefaultAccount") mungkin tidak memiliki password atau sedang tidak aktif, sehingga Ophcrack tidak menemukan apa-apa. 

    ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.014.jpeg)
