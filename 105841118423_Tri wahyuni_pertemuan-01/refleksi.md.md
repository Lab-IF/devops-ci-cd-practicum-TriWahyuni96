# 📋 Laporan Praktikum Pertemuan 01
## DevOps Culture & Principles

---

## 👤 Identitas Mahasiswa

| Item | Keterangan |
|------|------------|
| **Nama** | Tri Wahyuni |
| **NIM** | 105841118423 |
| **Kelas** | 5A |
| **Tanggal** | 2026-02-25 |

---

## 📚 Pemahaman DevOps

### Apa itu DevOps?

DevOps merupakan sebuah paradigma baru dalam dunia teknologi informasi yang mengintegrasikan aspek budaya, praktik kerja, dan pemanfaatan alat otomatisasi untuk menjembatani kesenjangan yang selama ini terjadi antara tim pengembang aplikasi (Development) dan tim operasional infrastruktur (Operations). Secara filosofis, metodologi ini bertujuan untuk menciptakan siklus hidup pengembangan perangkat lunak yang jauh lebih cepat, efisien, dan memiliki tingkat keandalan yang tinggi dibandingkan dengan model tradisional yang bersifat kaku dan terpisah. Dalam praktikum yang sedang kamu jalani, pemahaman ini dimulai dengan penguasaan alat dasar seperti Git untuk manajemen versi dan Docker sebagai fondasi teknologi kontainerisasi yang memungkinkan aplikasi berjalan secara konsisten di lingkungan mana pun.

Inti dari efektivitas DevOps terletak pada penerapan sistem Continuous Integration dan Continuous Delivery (CI/CD) yang memungkinkan setiap perubahan kode diuji secara otomatis dan segera diintegrasikan ke dalam repositori utama, seperti GitHub Classroom yang kamu gunakan. Selain itu, konsep Infrastructure as Code (IaC) menjadi pilar penting di mana konfigurasi server dan jaringan tidak lagi dikelola secara manual, melainkan melalui file teks seperti YAML, yang memastikan proses penyebaran aplikasi dapat diulang dengan hasil yang identik dan minim risiko kesalahan manusia.

Dengan mengadopsi budaya DevOps, organisasi tidak hanya memperoleh kecepatan dalam merilis fitur baru ke tangan pengguna, tetapi juga meningkatkan stabilitas sistem melalui pemantauan dan pengujian otomatis yang berkelanjutan. Penggunaan ekstensi pada editor seperti Visual Studio Code termasuk Docker, GitLens, dan Dev Containers membantu kamu sebagai mahasiswa informatika untuk mengelola kode dan infrastruktur secara terpadu dalam satu lingkungan kerja. Pada akhirnya, DevOps adalah tentang kolaborasi yang erat untuk memberikan nilai maksimal bagi pengguna akhir dengan meminimalkan hambatan teknis yang biasanya muncul saat transisi dari tahap penulisan kode menuju tahap produksi yang stabil.

### Mengapa DevOps Penting?

Penerapan DevOps menjadi krusial dalam industri perangkat lunak modern karena ia mampu mentransformasi cara organisasi memberikan nilai kepada pengguna melalui integrasi budaya dan teknologi otomatisasi. Di tengah persaingan pasar yang sangat ketat, metodologi ini memungkinkan perusahaan untuk mencapai kecepatan rilis yang luar biasa, sehingga fitur-fitur baru atau perbaikan bug dapat diluncurkan secara berkelanjutan tanpa harus menunggu siklus pengembangan yang panjang seperti pada model tradisional. Dengan memanfaatkan alat-alat yang sedang kamu siapkan dalam praktikum ini, seperti Git untuk kolaborasi kode dan Docker untuk konsistensi lingkungan, risiko terjadinya kegagalan sistem akibat perbedaan konfigurasi antar komputer dapat diminimalisir secara signifikan.

Selain faktor kecepatan, DevOps sangat penting untuk menjaga kualitas dan keandalan aplikasi melalui praktik pengujian otomatis yang terintegrasi dalam alur CI/CD. Hal ini memastikan bahwa setiap perubahan yang dilakukan oleh pengembang telah melalui verifikasi standar sebelum digabungkan ke repositori utama, seperti yang sedang kamu lakukan pada tugas di GitHub Classroom. Dengan adanya kolaborasi yang erat antara tim pengembang dan operasional, hambatan komunikasi dapat dihilangkan, yang pada akhirnya meningkatkan efisiensi biaya dan memungkinkan sistem untuk diskalakan dengan mudah sesuai pertumbuhan pengguna. Bagi kamu sebagai mahasiswa Informatika, menguasai ekosistem ini mulai dari penggunaan terminal hingga ekstensi VS Code seperti YAML dan Dev Containers adalah investasi besar untuk memahami standar kerja profesional di industri teknologi saat ini.

### Contoh Perusahaan yang Menerapkan DevOps

Netflix: Sebagai salah satu pionir DevOps, Netflix membangun alat otomatisasi yang sangat kuat untuk mengelola ribuan microservices mereka. Mereka menggunakan pendekatan "Chaos Engineering" untuk menguji ketahanan sistem secara otomatis, yang memungkinkan mereka merilis fitur baru ribuan kali setiap hari tanpa membuat layanan streaming mereka mati.

Amazon: Perusahaan ini berpindah dari arsitektur monolitik ke microservices dan mengadopsi budaya DevOps yang sangat disiplin. Hasilnya, Amazon mampu melakukan deployment kode rata-rata setiap 11,7 detik sekali, yang merupakan tingkat kecepatan dan skala yang sangat sulit dicapai tanpa otomatisasi CI/CD yang matang.

Etsy: Perusahaan e-commerce ini sering dijadikan contoh transformasi DevOps yang sukses dari budaya yang penuh konflik antara tim pengembang dan operasional menjadi budaya kolaborasi. Dengan alat bantu seperti yang kamu gunakan (Git dan Docker), mereka meningkatkan frekuensi rilis dari dua kali sebulan menjadi puluhan kali sehari.

Google: Melalui penerapan Site Reliability Engineering (SRE)—yang merupakan implementasi spesifik dari filosofi DevOps—Google mampu mengelola layanan skala global seperti Search dan YouTube dengan ketersediaan (uptime) yang sangat tinggi meskipun terus melakukan pembaruan kode secara masif.

---

## 🎯 Pemahaman Prinsip CALMS

1. Culture (Budaya)
Fokus utama DevOps adalah manusia, bukan sekadar alat. Prinsip ini menekankan perlunya kolaborasi, kepercayaan, dan tanggung jawab bersama antara tim pengembang (Dev) dan operasional (Ops).
Contoh Penerapan: Mengadakan rapat harian bersama (sync meeting) antara tim pengembang dan tim infrastruktur untuk membahas kendala teknis secara transparan, alih-alih saling menyalahkan saat terjadi error pada sistem.

2. Automation (Otomatisasi)
Prinsip ini bertujuan untuk menghilangkan tugas manual yang berulang dan rawan kesalahan dengan menggunakan teknologi. Ini mencakup seluruh alur kerja mulai dari pengujian hingga peluncuran aplikasi.
Contoh Penerapan: Menggunakan alat seperti Git dan Docker (yang sudah kamu instal) untuk membangun jalur CI/CD otomatis. Jadi, setiap kali kamu melakukan git push, sistem secara otomatis menjalankan pengujian dan membungkus aplikasi ke dalam kontainer Docker.

3. Lean (Ramping)
Terinspirasi dari manufaktur Toyota, prinsip Lean dalam DevOps berfokus pada penghapusan pemborosan dan penyampaian nilai secepat mungkin kepada pengguna melalui iterasi kecil.
Contoh Penerapan: Merilis pembaruan fitur dalam potongan kode yang kecil secara berkala (misalnya seminggu sekali), daripada mengumpulkan banyak fitur besar yang dirilis setiap enam bulan sekali yang berisiko tinggi menyebabkan kegagalan sistem.

4. Measurement (Pengukuran)
Organisasi harus mengukur segala sesuatu untuk memahami performa sistem dan efektivitas proses. Tanpa data, sulit untuk mengetahui bagian mana yang perlu ditingkatkan.
Contoh Penerapan: Menggunakan fitur pemantauan (monitoring) di Docker Desktop atau alat eksternal untuk melacak berapa lama waktu yang dibutuhkan dari penulisan kode hingga aplikasi aktif di server (Cycle Time) atau seberapa sering terjadi kegagalan saat rilis.

5. Sharing (Berbagi)
Berbagi pengetahuan, alat, dan tanggung jawab sangat penting untuk meruntuhkan batasan antar tim. Keberhasilan atau kegagalan harus dipelajari bersama agar seluruh organisasi menjadi lebih pintar.
Contoh Penerapan: Melakukan sesi "Post-Mortem" setelah terjadi gangguan sistem, di mana tim berbagi apa yang salah dan bagaimana cara mencegahnya di masa depan tanpa mencari siapa yang bersalah.

---

## 🔧 Setup Development Environment

### Versi Software

| Software | Versi |
|----------|-------|
| Git | git Version 2.53.0 |
| Docker | Docker version 29.0.1 |

### Konfigurasi Git

```
user.name = Tri Wahyuni
user.email = 105841118423@student.unismuh.ac.id
```

### VS Code Extensions

1. Docker
2. GitLens
3. YAML
4. Remote - Containers

### GitHub Account

- Username: TriWahyuni96

---

## 📸 Screenshots

| No | Screenshot | Keterangan |
|----|------------|------------|
| 1 | ![Git Version](screenshots/01-git-version.png) | Output git --version |
| 2 | ![Git Config](screenshots/02-git-config.png) | Output git config --list |
| 3 | ![Docker Version](screenshots/03-docker-version.png) | Output docker --version |
| 4 | ![Docker Hello World](screenshots/04-docker-hello-world.png) | Output docker run hello-world |
| 5 | ![VS Code](screenshots/05-vscode-extensions.png) | VS Code dengan extensions |

---

## 💭 Refleksi Pribadi

### Harapan dari Praktikum Ini

Harapan utama dari praktikum DevOps ini adalah agar saya tidak hanya sekadar mahir menggunakan alat teknis seperti Git, Docker, atau VS Code, tetapi juga mampu menginternalisasi filosofi CALMS dalam setiap proses pengembangan perangkat lunak yang saya lakukan. Melalui tugas-tugas di GitHub Classroom ini, diharapkan saya dapat membangun kemandirian dalam mengelola lingkungan kerja yang konsisten, sehingga masalah perbedaan konfigurasi antar komputer tidak lagi menjadi hambatan. Selain itu, praktikum ini bertujuan membentuk mentalitas otomatisasi, di mana saya terbiasa menggunakan skrip dan file konfigurasi untuk mempercepat pekerjaan rutin dan meminimalisir kesalahan manual.

### Skill yang Ingin Dikuasai

Di akhir semester ini, saya memiliki target utama untuk menguasai keterampilan teknis yang mendalam dalam membangun alur kerja otomatisasi menggunakan prinsip CI/CD. Saya ingin mahir dalam mengintegrasikan berbagai alat yang sudah saya instal, seperti Git untuk kolaborasi kode dan Docker untuk standardisasi lingkungan pengembangan, sehingga saya bisa memastikan aplikasi yang saya bangun dapat berjalan dengan stabil di server mana pun tanpa kendala konfigurasi. Selain itu, saya ingin menguasai penulisan file konfigurasi YAML yang efisien untuk mengatur infrastruktur secara otomatis melalui kode, sebuah kemampuan yang sangat dibutuhkan dalam standar industri software saat ini.

### Tantangan yang Dihadapi

Satu tantangan yang sangat sering terjadi adalah ketidaksesuaian versi atau dependensi antar perangkat lunak, misalnya ketika versi Docker yang saya gunakan membutuhkan pembaruan kernel WSL yang lebih baru pada sistem operasi Windows saya agar bisa berjalan optimal. Hal ini menuntut saya untuk selalu waspada terhadap pembaruan sistem dan memastikan semua komponen pendukung berada pada versi yang kompatibel. Selain itu, memahami perbedaan alur perintah antara berbagai terminal seperti Command Prompt, PowerShell, atau Git Bash juga menjadi tantangan tersendiri bagi saya, karena perintah yang sama terkadang membutuhkan penyesuaian sintaksis di lingkungan yang berbeda.

---

## ✅ Checklist

- [x] Git terinstall dan terkonfigurasi dengan benar
- [x] Docker dapat menjalankan container hello-world
- [x] VS Code terinstall dengan semua extensions yang diminta
- [x] Laporan ditulis dengan bahasa yang baik dan benar
- [x] Semua screenshot jelas dan terbaca

---

*Laporan ini dibuat pada Rabu, 25 Februari 2026*
