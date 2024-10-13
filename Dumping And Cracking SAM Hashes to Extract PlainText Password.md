**Nama: Dhani Medianto Saputra** 

**Nim : 09011282126067 Keamanan Jaringan Komputer** 

**### Dumping And Cracking SAM Hashes to Extract PlainText Password** 

Security Account Manager (SAM) adalah basis data di sistem operasi Windows yang menyimpan informasi akun pengguna dan deskriptor keamanannya. File ini menyimpan kata sandi pengguna dalam bentuk hash (LM dan NTLM). Karena proses hashing bersifat satu arah, ini memberikan tingkat keamanan dalam penyimpanan kata sandi.Dalam konteks peretasan, penyerang biasanya akan mengekstrak hash kata sandi setelah berhasil mengakses komputer target. Hash ini memungkinkan mereka untuk melakukan berbagai serangan, seperti peretasan kata sandi, menggunakan hash untuk mengakses sistem lain, menganalisis kata sandi, dan mengidentifikasi pola untuk memecahkan kata sandi lain dalam lingkungan yang sama.Untuk dapat mengekstrak isi file SAM, diperlukan hak akses administrator. Menilai kekuatan kata sandi  adalah  langkah  penting  dalam  penilaian  keamanan.  Proses  ini  dimulai  dengan mengekstrak hash SAM dan kemudian menggunakan metode dekripsi untuk mendapatkan kata sandi dalam bentuk teks biasa. 

Tujuan dari dumping dan cracking ini adalah untuk membantu mempelajari cara: 

- Mengetahui cara mengunakan alat pwdump7 untuk mengekstrak hash kata sandi 
- Mengetahui cara mengunakan alat Ophcrack untuk memecahkan kata sandi dan mendapatkan teks biasa 
1. Pertama, kita mencari tahu User ID dengan username menggunakan cmd administrator mode. 
   ![image](https://github.com/user-attachments/assets/2596bd4b-8648-411a-9037-5aac73ca1554)


2. Kemudian ketik code wmic useraccount get name,sid yang memiliki fungsi menampilkan daftar semua akun pengguna yang ada di sistem beserta SID-nya masing-masing. 
   ![image](https://github.com/user-attachments/assets/1d369594-6022-40f8-84c1-c295264b8cdf)


3. Kemudian mendownload dan mengekstrak file pwdump dan ophcrack
   
   ![image](https://github.com/user-attachments/assets/f262c3b0-d639-4fab-b42c-2e6f729c50d2)


4. Setelah itu buka dan copy lokasi file pwdump dan klik enter untuk masuk ke directory pwdump- master , kemudian ketik PwDump7.exe untuk mendapatkan dan menampilkan password hashes dan userID. 
   ![image](https://github.com/user-attachments/assets/1d0543c3-4015-4a4e-9379-88e4791aef2a)
   ![image](https://github.com/user-attachments/assets/dab4a17a-3713-47ab-b610-0d3cd3bacd47)


5. Kemudian untuk memindahkan dan men-copy semua data hasil dari PwDump7.exe ke hashes.txt menggunakan command PwDump7.exe > c:\hashes.txt 
   ![image](https://github.com/user-attachments/assets/ce60b378-a40c-4d2b-9407-743d497204de)


6. Berikut ini adalah isi file dari hashes.txt. 

   ![image](https://github.com/user-attachments/assets/d2c6bad3-c2e1-4453-9f18-9bbfe3e26c55)


7. Selanjutnya mengisi semua username yang kosong sesuai dengan username pengguna pada step 2 kemudian save file hashes.txt 
   ![image](https://github.com/user-attachments/assets/b527ac13-40d2-4d5e-aa65-0bc607a27f43)


8. Selanjutnya buka oph crack kemudian pilih load PWDUMP file dan pilih file hashes.txt sebelumnya. 
   ![image](https://github.com/user-attachments/assets/2aa17833-c244-441d-9301-84da00022001)

   ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.009.jpeg)

9. File Hashes tersebut akan tampil dengan lm hash dan nt hash sesuai username user. 
   ![image](https://github.com/user-attachments/assets/da5837d5-6fa6-4881-bd9b-dd0337256302)

![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.010.png)

10. Kemudia klik table dan pada table selection pilih vista free kemudian klik install, kemudian pilih table vista free yang sudah di download sebelumnya . ( table vista free bisa di download menggunakan link :[ https://ophcrack.sourceforge.io/tables.php)](https://ophcrack.sourceforge.io/tables.php) 
      ![image](https://github.com/user-attachments/assets/aa06a678-caed-4e3b-986b-1f515e9574a3)
   ![image](https://github.com/user-attachments/assets/3eb490ed-8b42-4ca2-9f37-eeffd08448cb)

    ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.011.png)

    ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.012.png)

11. Setelah table tambil kemudian klik icon crack disamping icon untuk mulai memecahkan kata sandi. Ophcrack akan membutuhkan waktu beberapa menit untuk memecahkan kata sandi. Tunggu hingga proses pemecahan kata sandi selesai. 
   ![image](https://github.com/user-attachments/assets/b19ce97a-cb27-497d-a67f-ba1575e501f4)

    ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.013.png)

12. Setelah  selesai  maka  password  akan  tampil,  Jika  hasilnya  menunjukkan  not  found  maka kemungkinan besar karena windows 10 terbaru secara default tidak lagi menyimpan password di hash  LM  karena  kurang  aman  atau  bisa  juga  karena  beberapa  akun  (seperti  "Guest"  atau "DefaultAccount") mungkin tidak memiliki password atau sedang tidak aktif, sehingga Ophcrack tidak menemukan apa-apa. 
      ![image](https://github.com/user-attachments/assets/78dcbdf5-c596-43db-987b-41c1b9a41677)

    ![](Aspose.Words.c82e2afb-549f-4539-8010-5d824846e90b.014.jpeg)
