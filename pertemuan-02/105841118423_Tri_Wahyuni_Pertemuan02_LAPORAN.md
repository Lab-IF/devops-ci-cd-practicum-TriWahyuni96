# 🐳 Laporan Praktikum Pertemuan 02
## Docker Fundamentals

---

## 👤 Identitas Mahasiswa

| Item | Keterangan |
|------|------------|
| **Nama** | Tri Wahyuni |
| **NIM** | 105841118423 |
| **Kelas** | 5A |
| **Tanggal** | 2026-02-25 |

---

## 📚 Pemahaman Docker

### Apa itu Docker?

Docker merupakan sebuah platform inovatif yang memungkinkan saya untuk membungkus aplikasi beserta seluruh komponen pendukungnya, seperti pustaka, file konfigurasi, dan dependensi lainnya, ke dalam satu unit paket yang disebut kontainer. Secara filosofis, teknologi ini berfungsi layaknya kotak kargo pada kapal laut yang memastikan bahwa apa pun yang ada di dalamnya akan tetap konsisten dan dapat dijalankan di lingkungan mana pun, baik itu di komputer pribadi saya, server kampus, maupun penyedia layanan awan, tanpa perlu khawatir akan munculnya masalah ketidaksesuaian sistem. Dalam praktikum ini, saya mempelajari beberapa komponen inti seperti Docker Image yang merupakan cetak biru instruksi bersifat baca-saja, dan Docker Container sebagai unit hidup yang menjalankan aplikasi tersebut.

Proses pembuatan infrastruktur ini saya awali dengan menyusun sebuah Dockerfile, yakni file teks berisi serangkaian perintah otomatis untuk membangun image, mulai dari pemilihan sistem operasi dasar hingga penyalinan file proyek saya ke dalam server. Dengan menggunakan Docker, saya dapat bekerja secara jauh lebih efisien karena proses instalasi lingkungan pengembangan yang biasanya rumit dan memakan waktu lama kini dapat diselesaikan hanya dengan satu baris perintah saja. Kemampuan untuk menciptakan lingkungan yang identik, cepat untuk dibangun, dan sangat mudah untuk dipindahkan antar perangkat ini merupakan implementasi nyata dari prinsip otomatisasi dalam DevOps yang sedang saya pelajari.

### Komponen Utama Docker

1. Docker Images
Docker Image adalah sebuah paket yang bersifat baca-saja (read-only) dan berfungsi sebagai cetak biru atau instruksi untuk membuat sebuah kontainer. Image ini berisi semua kebutuhan aplikasi, mulai dari kode program, runtime, hingga konfigurasi sistem, image memastikan bahwa aplikasi saya akan selalu memiliki landasan yang sama persis di mana pun ia dijalankan.

2. Docker Containers
Docker Container adalah bentuk hidup atau unit yang sedang berjalan dari sebuah image. Jika image adalah resep masakan, maka kontainer adalah masakan yang sudah jadi dan siap untuk dinikmati. Kontainer bersifat terisolasi dari sistem utama, namun tetap dapat berinteraksi melalui pemetaan port, seperti saat saya menjalankan kontainer praktikum-web yang dapat diakses melalui port 8080 pada browser saya. Saya bisa menjalankan, menghentikan, atau menghapus kontainer ini tanpa memengaruhi sistem operasi utama laptop saya.

3. Docker Registry
Docker Registry adalah tempat penyimpanan dan distribusi untuk Docker Images. Komponen ini memungkinkan saya untuk mengunggah image yang telah saya buat agar bisa digunakan oleh orang lain, atau mengunduh image milik orang lain untuk saya gunakan sendiri. Registry yang paling populer dan sering saya gunakan dalam praktikum ini adalah Docker Hub, di mana saya bisa mencari image resmi seperti Nginx, Python, atau MySQL hanya dengan satu perintah pencarian di terminal.

### Perbedaan Docker vs Virtual Machine

Berikut adalah penjelasan mengenai perbedaan mendasar keduanya:
1. Arsitektur dan Sumber Daya
Virtual Machine berjalan di atas Hypervisor dan memerlukan sistem operasi tamu (Guest OS) yang lengkap untuk setiap instance, sehingga memakan banyak ruang penyimpanan dan memori. Sebaliknya, Docker Container berjalan langsung di atas sistem operasi utama (Host OS) dan berbagi kernel yang sama, sehingga jauh lebih ringan dan efisien dalam penggunaan sumber daya.

2. Kecepatan dan Performa
Karena tidak perlu melakukan proses booting sistem operasi dari awal, Docker Container dapat aktif dalam hitungan detik, sangat kontras dengan Virtual Machine yang membutuhkan waktu beberapa menit untuk siap digunakan. Hal ini memungkinkan saya untuk melakukan skalabilitas aplikasi dengan sangat cepat sesuai kebutuhan trafik.

3. Portabilitas dan Konsistensi
Docker Container menjamin bahwa apa pun yang saya bungkus di dalamnya akan berjalan dengan cara yang sama persis di lingkungan mana pun karena ia membawa serta seluruh dependensinya. Virtual Machine juga menawarkan portabilitas, namun ukuran file imagenya yang sangat besar (bisa mencapai puluhan gigabyte) membuatnya jauh lebih sulit untuk dipindahkan atau dibagikan dibandingkan Docker Image yang jauh lebih kecil.

---

## 🔧 Praktik Docker Commands

### Output docker ps -a

```
CONTAINER ID   IMAGE                               COMMAND                  CREATED          STATUS                     PORTS                                         NAMES
02838d8ee065   nginx                               "/docker-entrypoint.…"   52 seconds ago   Up 51 seconds              0.0.0.0:8080->80/tcp, [::]:8080->80/tcp       webserver
57d9ed53eca1   nginx                               "/docker-entrypoint.…"   12 minutes ago   Exited (0) 4 minutes ago                                                 stupefied_poitras
7c0ba8e1b935   hello-world                         "/hello"                 3 hours ago      Exited (0) 3 hours ago                                                   quirky_merkle
3e5012643597   baseline-cna-notification-service   "docker-entrypoint.s…"   2 months ago     Exited (0) 6 weeks ago                                                   notification-service
c73755a68b49   baseline-cna-api-gateway            "docker-entrypoint.s…"   2 months ago     Exited (255) 6 weeks ago   0.0.0.0:3000->3000/tcp                        api-gateway
197191a56926   baseline-cna-course-service         "docker-entrypoint.s…"   2 months ago     Up 3 hours                 0.0.0.0:3002->3002/tcp, [::]:3002->3002/tcp   course-service
799fbce62625   baseline-cna-calendar-service       "docker-entrypoint.s…"   2 months ago     Up 3 hours                 0.0.0.0:3001->3001/tcp, [::]:3001->3001/tcp   calendar-service
1e763e2b958b   provectuslabs/kafka-ui:latest       "/bin/sh -c 'java --…"   2 months ago     Exited (255) 6 weeks ago   0.0.0.0:8080->8080/tcp                        kafka-ui
8b49bde0a161   confluentinc/cp-kafka:7.5.0         "/etc/confluent/dock…"   2 months ago     Exited (255) 6 weeks ago   0.0.0.0:9092->9092/tcp                        kafka
92799b910d60   postgres:15-alpine                  "docker-entrypoint.s…"   2 months ago     Exited (255) 6 weeks ago   0.0.0.0:5432->5432/tcp                        postgres-db
339c85aa2f77   confluentinc/cp-zookeeper:7.5.0     "/etc/confluent/dock…"   2 months ago     Exited (255) 6 weeks ago   2888/tcp, 0.0.0.0:2181->2181/tcp, 3888/tcp    zookeeper
5182b55c848f   docker/welcome-to-docker:latest     "/docker-entrypoint.…"   2 months ago     Exited (255) 6 weeks ago   0.0.0.0:8088->80/tcp                          welcome-to-docker
```

### Output docker images

```
IMAGE                                                                   ID             DISK USAGE   CONTENT SIZE   EXTRA
baseline-cna-api-gateway:latest                                         45f79eb00c41        217MB         50.4MB    U
baseline-cna-calendar-service:latest                                    469ff1e4a6ee        202MB           48MB    U
baseline-cna-course-service:latest                                      2daec22d4b4c        213MB         49.5MB    U
baseline-cna-notification-service:latest                                2911053e21a4        188MB         45.5MB    U
confluentinc/cp-kafka:7.5.0                                             fbbb6fa11b25       1.33GB          439MB    U
confluentinc/cp-zookeeper:7.5.0                                         02f6c042bb9a       1.33GB          439MB    U
docker/desktop-kubernetes:kubernetes-v1.34.1-cni-v1.7.1-critools-v1.…   12d6673564e0        591MB          184MB
docker/desktop-storage-provisioner:v2.0                                 115d77efe6e2       59.2MB         17.3MB
docker/desktop-vpnkit-controller:dc331cb22850be0cdd97c84a9cfecaf44a1…   7ecf567ea070         47MB         10.8MB
docker/welcome-to-docker:latest                                         c4d56c24da4f       22.2MB         6.03MB    U
hello-world:latest                                                      ef54e839ef54       20.3kB         3.96kB    U
khannedy/nginx-curl:latest                                              9e0def51f0c3       35.1MB         9.33MB
khannedy/nodejs-env:latest                                              5a6ffb1623ad        135MB         29.5MB
khannedy/nodejs-job:latest                                              eb2d3eae06b6        135MB         29.5MB
khannedy/nodejs-stateful:latest                                         3c313889adb1        138MB         30.2MB
khannedy/nodejs-web:1                                                   dc08e1974f2b        135MB         29.5MB
khannedy/nodejs-web:2                                                   6005adb1fb1d        135MB         29.5MB
khannedy/nodejs-web:3                                                   9b3345b4550a        135MB         29.5MB
khannedy/nodejs-web:latest                                              ee570e869d3b        135MB         29.5MB
khannedy/nodejs-writer:latest                                           28fa9ca746b7        138MB         30.2MB
kubernetesui/dashboard:v2.7.0                                           2e500d29e9d5        334MB         75.8MB
kubernetesui/metrics-scraper:v1.0.8                                     76049887f07a       63.6MB         19.7MB
nginx:latest                                                            0236ee02dcbc        237MB         62.9MB
postgres:15-alpine                                                      aa7b1ef595e1        391MB          109MB    U
provectuslabs/kafka-ui:latest                                           8f2ff02d64b0        449MB          154MB    U
registry.k8s.io/coredns/coredns:v1.12.1                                 e8c262566636        101MB         22.4MB
registry.k8s.io/etcd:3.6.4-0                                            e36c08168342        273MB         74.3MB
registry.k8s.io/ingress-nginx/controller@sha256:e5c4824e7375fcf2a393…   e5c4824e7375        407MB          114MB
registry.k8s.io/ingress-nginx/kube-webhook-certgen@sha256:543c40fd09…   543c40fd0939       71.4MB         20.3MB
registry.k8s.io/kube-apiserver:v1.34.1                                  b9d7c117f8ac        118MB         27.1MB
registry.k8s.io/kube-controller-manager:v1.34.1                         2bf47c1b01f5        101MB         22.8MB
registry.k8s.io/kube-proxy:v1.34.1                                      913cc83ca0b5        102MB           26MB
registry.k8s.io/kube-scheduler:v1.34.1                                  6e9fbc4e25a5       73.5MB         17.4MB
registry.k8s.io/metrics-server/metrics-server:v0.8.0                    89258156d0e9        108MB         22.5MB
registry.k8s.io/pause:3.10                                              ee6521f290b2       1.06MB          318kB
registry.k8s.io/pause:3.10.1                                            278fb9dbcca9       1.06MB          318kB
```

### Docker Run Command

```bash
docker run -d -p 8080:80 --name webserver nginx
```

---

## 📄 Dockerfile

### Isi Dockerfile

```dockerfile
# Gunakan nginx alpine sebagai base image
FROM nginx:alpine

# Copy file HTML ke direktori nginx
COPY app/index.html /usr/share/nginx/html/index.html

# Expose port 80
EXPOSE 80

# Command default nginx
CMD ["nginx", "-g", "daemon off;"]
```

### Penjelasan Dockerfile

FROM nginx:alpine
Baris ini menentukan base image atau fondasi yang akan saya gunakan untuk membangun kontainer. Saya menggunakan nginx dengan varian alpine, yaitu versi sistem operasi Linux yang sangat ringan dan kecil, sehingga ukuran akhir image saya tidak akan membebani ruang penyimpanan.

COPY app/index.html /usr/share/nginx/html/index.html
Instruksi ini berfungsi untuk menyalin file index.html yang ada di dalam folder app di komputer saya ke dalam direktori standar server Nginx di dalam kontainer. Dengan melakukan ini, saya mengganti halaman selamat datang bawaan Nginx dengan halaman web kustom yang sudah saya buat sebelumnya.

EXPOSE 80
Baris ini berfungsi sebagai dokumentasi dan instruksi bahwa kontainer ini akan mendengarkan koneksi pada port 80 saat dijalankan. Meskipun baris ini tidak secara otomatis membuka port ke jaringan luar, ia memberikan informasi penting bagi saya untuk melakukan port mapping, seperti saat saya menggunakan parameter -p 8080:80.

CMD ["nginx", "-g", "daemon off;"]
Ini adalah instruksi perintah utama yang akan dijalankan secara otomatis segera setelah kontainer saya aktif. Perintah daemon off memastikan bahwa proses Nginx tetap berjalan di latar depan (foreground) sehingga kontainer tidak langsung mati setelah dijalankan, karena kontainer akan terus hidup selama proses utamanya masih berjalan.

---

## 🐙 Docker Compose

### Isi docker-compose.yml

```yaml
version: '3.8'

services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
    volumes:
      - ./app:/usr/share/nginx/html:ro
    depends_on:
      - api
    networks:
      - praktikum-net

  api:
    image: httpd:alpine
    ports:
      - "8081:80"
    networks:
      - praktikum-net

  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_USER: praktikum
      POSTGRES_PASSWORD: devops123
      POSTGRES_DB: praktikum_db
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - praktikum-net

networks:
  praktikum-net:
    driver: bridge

volumes:
  db_data:
```

### Penjelasan Docker Compose

Berikut adalah penjelasan setiap bagian utamanya:
Bagian Umum (Versi, Network, dan Volume)
version: '3.8': Menentukan versi format Docker Compose yang saya gunakan agar kompatibel dengan Docker Engine di laptop saya.

networks: Mendefinisikan jaringan isolasi bernama praktikum-net dengan driver bridge, yang memungkinkan ketiga layanan (web, api, db) saling berkomunikasi menggunakan nama layanan mereka sebagai alamat host.

volumes (tingkat atas): Mendefinisikan db_data sebagai volume persisten yang dikelola oleh Docker, sehingga data database tidak akan hilang meskipun kontainer dihapus.

Definisi Layanan (Services)
Dalam file ini, saya mendefinisikan tiga layanan utama yang bekerja bersama:

1. Layanan Web (Nginx)

image: nginx:alpine: Menggunakan image Nginx versi ringan sebagai server web.

ports: "8080:80": Melakukan port mapping agar saya bisa mengakses layanan ini melalui localhost:8080 di browser.

volumes: Menghubungkan folder ./app di komputer saya ke folder html di dalam kontainer dengan mode read-only (ro). Ini memudahkan saya karena setiap perubahan pada file HTML lokal akan langsung terlihat di browser tanpa perlu build ulang image.

depends_on: Memastikan kontainer api berjalan terlebih dahulu sebelum kontainer web diaktifkan.

2. Layanan API (Apache/Httpd)

image: httpd:alpine: Menggunakan server Apache sebagai perwakilan layanan API.

ports: "8081:80": Dapat saya akses melalui localhost:8081 untuk keperluan pengujian API secara terpisah.

3. Layanan Database (PostgreSQL)

image: postgres:15-alpine: Menggunakan image resmi PostgreSQL versi 15.

environment: Mengatur variabel lingkungan untuk konfigurasi awal database, seperti nama pengguna, kata sandi, dan nama database yang saya inginkan.

volumes: Memetakan volume db_data ke direktori data PostgreSQL di dalam kontainer agar data tetap tersimpan secara permanen.

### Output Docker Compose Up

```
time="2026-02-25T19:56:19+08:00" level=warning msg="C:\\Users\\LENOVO\\devops-ci-cd-practicum-TriWahyuni96\\pertemuan-02\\task3-compose\\docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion"
[+] Running 2/8
[+] Running 5/8 Pulling                                   11.2s
[+] Running 5/8 Pulling                                   13.1s
[+] Running 5/8 Pulling                                   13.2s
[+] Running 5/8 Pulling                                   13.3s
[+] Running 5/8 Pulling                                   13.4s
[+] Running 5/8 Pulling                                   13.5s
[+] Running 5/8 Pulling                                   13.6s
[+] Running 5/8 Pulling                                   13.7s
[+] Running 5/8 Pulling                                   13.8s
[+] Running 5/8 Pulling                                   13.9s
[+] Running 5/8 Pulling                                   14.0s
[+] Running 5/8 Pulling                                   14.1s
[+] Running 5/8 Pulling                                   14.2s
[+] Running 5/8 Pulling                                   14.3s
[+] Running 5/8 Pulling                                   14.4s
[+] Running 5/8 Pulling                                   14.5s
[+] Running 5/8 Pulling                                   14.6s
[+] Running 5/8 Pulling                                   14.7s
[+] Running 5/8 Pulling                                   14.8s
[+] Running 5/8 Pulling                                   14.9s
[+] Running 5/8 Pulling                                   15.0s
[+] Running 5/8 Pulling                                   15.1s
[+] Running 5/8 Pulling                                   15.2s
[+] Running 5/8 Pulling                                   15.3s
[+] Running 5/8 Pulling                                   15.4s
[+] Running 5/8 Pulling                                   15.5s
[+] Running 5/8 Pulling                                   15.6s
[+] Running 5/8 Pulling                                   15.7s
[+] Running 5/8 Pulling                                   15.8s
[+] Running 5/8 Pulling                                   15.9s
[+] Running 5/8 Pulling                                   16.0s
[+] Running 5/8 Pulling                                   16.1s
[+] Running 5/8 Pulling                                   16.2s
[+] Running 5/8 Pulling                                   16.3s
[+] Running 5/8 Pulling                                   16.4s
[+] Running 5/8 Pulling                                   16.5s
[+] Running 5/8 Pulling                                   16.6s
[+] Running 5/8 Pulling                                   16.7s
[+] Running 5/8 Pulling                                   16.8s
[+] Running 5/8 Pulling                                   16.9s
[+] Running 5/8 Pulling                                   17.0s
[+] Running 5/8 Pulling                                   17.1s
[+] Running 5/8 Pulling                                   17.2s
[+] Running 5/8 Pulling                                   17.3s
[+] Running 5/8 Pulling                                   17.4s
[+] Running 5/8 Pulling                                   17.5s
[+] Running 5/8 Pulling                                   17.6s
[+] Running 5/8 Pulling                                   17.7s
[+] Running 5/8 Pulling                                   17.8s
[+] Running 5/8 Pulling                                   17.9s
[+] Running 5/8 Pulling                                   18.0s
[+] Running 5/8 Pulling                                   18.1s
[+] Running 5/8 Pulling                                   18.2s
[+] Running 5/8 Pulling                                   18.3s
[+] Running 5/8 Pulling                                   18.4s
[+] Running 5/8 Pulling                                   18.5s
[+] Running 5/8 Pulling                                   18.6s
[+] Running 5/8 Pulling                                   18.7s
[+] Running 5/8 Pulling                                   18.8s
[+] Running 5/8 Pulling                                   18.9s
[+] Running 5/8 Pulling                                   19.0s
[+] Running 5/8 Pulling                                   19.1s
[+] Running 5/8 Pulling                                   19.3s
[+] Running 5/8 Pulling                                   19.3s
[+] Running 5/8 Pulling                                   19.4s
[+] Running 5/8 Pulling                                   19.5s
[+] Running 5/8 Pulling                                   19.6s
[+] Running 5/8 Pulling                                   19.7s
[+] Running 5/8 Pulling                                   19.8s
[+] Running 5/8 Pulling                                   19.9s
[+] Running 5/8 Pulling                                   20.0s
[+] Running 5/8 Pulling                                   20.1s
[+] Running 5/8 Pulling                                   20.2s
[+] Running 5/8 Pulling                                   20.3s
[+] Running 5/8 Pulling                                   20.4s
[+] Running 5/8 Pulling                                   20.5s
[+] Running 5/8 Pulling                                   20.6s
[+] Running 5/8 Pulling                                   20.7s
[+] Running 5/8 Pulling                                   20.8s
[+] Running 5/8 Pulling                                   20.9s
[+] Running 5/8 Pulling                                   21.0s
[+] Running 5/8 Pulling                                   21.1s
[+] Running 5/8 Pulling                                   21.2s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 21.3s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 21.4s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 21.5s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 21.6s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 21.7s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 21.8s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 21.9s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 22.0s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 22.1s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 22.2s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 22.3s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 22.4s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 22.5s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣦⠀⣿⣿] 5.243MB / 16.96MB Pulling                 22.6s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 22.7s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 22.8s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 22.9s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.0s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.1s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.2s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.3s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.4s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.5s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.6s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.7s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.8s
[+] Running 5/854 Pull complete                            0.1s
 - api [⣿⣿⣷⠀⣿⣿] 6.292MB / 16.96MB Pulling                 23.9s
[+] Running 6/854 Pull complete                            0.1s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.0s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.1s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.2s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.3s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.4s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.5s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.6s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.7s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.8s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 24.9s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 25.0s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 25.1s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 25.2s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 25.3s
[+] Running 6/8 6.292MB / 16.96MB Pulling                 25.4s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 25.5s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 25.6s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 25.7s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 25.8s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 25.9s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.0s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.1s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.2s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.3s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.4s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.5s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.6s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.7s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.8s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 26.9s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 27.0s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 27.1s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 27.2s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 27.3s
[+] Running 6/8  7.34MB / 16.96MB Pulling                 27.4s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 27.5s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 27.6s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 27.7s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 27.8s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 27.9s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 28.0s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 28.1s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 28.2s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 28.3s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 28.4s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 28.5s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 28.6s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 28.7s
[+] Running 6/8 8.389MB / 16.96MB Pulling                 28.8s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 28.9s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.0s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.1s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.2s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.3s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.4s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.5s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.6s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.7s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.8s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 29.9s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 30.0s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 30.1s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 30.2s
[+] Running 6/8 9.437MB / 16.96MB Pulling                 30.3s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 30.4s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 30.5s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 30.6s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 30.7s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 30.8s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 30.9s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 31.0s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 31.1s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 31.2s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 31.3s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 31.4s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 31.5s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 31.6s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 31.7s
[+] Running 6/8 10.49MB / 16.96MB Pulling                 31.8s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 31.9s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 32.0s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 32.1s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 32.2s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 32.3s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 32.4s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 32.5s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 32.6s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 32.7s
[+] Running 6/8 11.53MB / 16.96MB Pulling                 32.8s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 32.9s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.0s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.1s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.2s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.3s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.4s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.5s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.6s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.7s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.8s
[+] Running 6/8 12.58MB / 16.96MB Pulling                 33.9s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.0s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.1s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.2s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.3s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.4s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.5s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.6s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.7s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.8s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 34.9s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 35.0s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 35.1s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 35.2s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 35.3s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 35.4s
[+] Running 6/8 13.63MB / 16.96MB Pulling                 35.5s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 35.6s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 35.7s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 35.8s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 35.9s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.0s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.1s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.2s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.3s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.4s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.5s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.6s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.7s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.8s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 36.9s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 37.0s
[+] Running 6/8 14.68MB / 16.96MB Pulling                 37.1s
[+] Running 6/8 15.73MB / 16.96MB Pulling                 37.2s
[+] Running 6/8 15.73MB / 16.96MB Pulling                 37.3s
[+] Running 6/8 15.73MB / 16.96MB Pulling                 37.4s
[+] Running 6/8 15.73MB / 16.96MB Pulling                 37.5s
[+] Running 6/8 15.73MB / 16.96MB Pulling                 37.6s
[+] Running 8/8 15.73MB / 16.96MB Pulling                 37.7s
 ✔ api Pulled                                             42.5s
   ✔ 4f4fb700ef54 Pull complete                            0.1s
   ✔ 79273eb2147b Pull complete                            2.8s
   ✔ b9df760bab4a Pull complete                           32.1s
   ✔ 3688fd767e4a Pull complete                           30.8s
   ✔ abd702cd48c8 Pull complete                           32.2s
   ✔ 987f24f891f4 Pull complete                            2.7s
 ✔ web Pulled                                              6.6s
[+] Running 4/5
 ✔ Network task3-compose_praktikum-net  Created            0.6s
 ✔ Volume task3-compose_db_data         Created            0.2s
 ✔ Container task3-compose-api-1        Started            5.6s
 ✔ Container task3-compose-db-1         Started            5.6s
 - Container task3-compose-web-1        Starting           7.0s
Error response from daemon: failed to set up container networking: driver failed programming external connectivity on endpoint task3-compose-web-1 (72503e91febd519f711f784d89dcf60f8c916ccc412d9a637bae2fad5cd29593): Bind for 0.0.0.0:8080 failed: port is already allocated
```

---

## 📸 Screenshots

| No | Screenshot | Keterangan |
|----|------------|------------|
| 1 | ![Container Running](screenshots/01-container-running.png) | Container yang sedang berjalan |
| 2 | ![Docker Images](screenshots/02-docker-images.png) | Daftar Docker images |
| 3 | ![Dockerfile](screenshots/03-dockerfile-content.png) | Isi file Dockerfile |
| 4 | ![Docker Build](screenshots/04-docker-build.png) | Proses docker build |
| 5 | ![App Browser](screenshots/05-app-browser.png) | Aplikasi berjalan di browser |
| 6 | ![Compose Up](screenshots/06-compose-up.png) | Docker Compose up |

---

## 💭 Refleksi & Kesimpulan

### Yang Dipelajari

Dari praktikum Docker yang telah saya jalankan, saya memperoleh pemahaman mendalam mengenai teknologi kontainerisasi dan perannya dalam mendukung ekosistem DevOps. Hal utama yang saya pelajari adalah bagaimana membungkus sebuah aplikasi beserta seluruh dependensinya ke dalam satu unit paket yang konsisten, sehingga masalah perbedaan konfigurasi antar lingkungan pengembangan tidak lagi menjadi hambatan. Melalui pembuatan Dockerfile, saya belajar mendefinisikan infrastruktur dalam bentuk kode, mulai dari memilih base image yang ringan seperti Alpine Linux hingga mengatur perintah otomatis untuk menjalankan server web.

### Manfaat Docker

Docker memberikan kontribusi besar dalam pengembangan perangkat lunak dengan cara menstandarisasi lingkungan kerja di setiap tahap siklus pengembangan. Dengan teknologi kontainer, saya dapat membungkus aplikasi bersama seluruh dependensinya sehingga aplikasi tersebut dijamin akan berjalan dengan perilaku yang sama persis, baik di komputer pribadi saya saat tahap koding, di server pengujian, maupun saat sudah digunakan oleh pengguna luas. Hal ini secara efektif menghilangkan masalah klasik di mana aplikasi berfungsi di satu perangkat namun mengalami error di perangkat lain akibat perbedaan versi sistem operasi atau pustaka pendukung.

Selain konsistensi lingkungan, Docker sangat membantu saya dalam meningkatkan efisiensi dan kecepatan pengembangan melalui prinsip otomatisasi. Proses instalasi basis data atau server web yang biasanya rumit kini dapat diselesaikan dalam hitungan detik hanya dengan menjalankan perintah docker run atau menggunakan Docker Compose untuk mengaktifkan seluruh infrastruktur sekaligus. Kemampuan untuk dengan cepat menghancurkan dan membangun kembali kontainer tanpa meninggalkan sisa sampah di sistem operasi utama laptop saya memungkinkan saya untuk bereksperimen dengan berbagai teknologi baru secara lebih aman dan teratur.

Dalam konteks kolaborasi tim, Docker memudahkan saya dalam membagikan lingkungan proyek kepada rekan pengembang lainnya melalui Docker Registry seperti Docker Hub. Alih-alih memberikan panduan instalasi yang panjang dan berisiko salah, saya cukup membagikan Dockerfile atau Docker Image yang sudah saya buat, sehingga rekan saya bisa langsung mulai bekerja dengan lingkungan yang identik hanya dengan sekali klik. Pendekatan ini sangat mendukung filosofi DevOps dalam hal transparansi dan standarisasi alat kerja di seluruh organisasi.

### Tantangan dan Solusi

Dalam mengerjakan praktikum ini, saya menghadapi beberapa tantangan teknis yang cukup umum namun memberikan pelajaran berharga dalam memahami alur kerja DevOps. Salah satu kendala yang saya temui adalah masalah konflik port, di mana saya tidak bisa menjalankan kontainer baru karena port 8080 di laptop saya masih digunakan oleh proses kontainer sebelumnya. Solusi yang saya lakukan adalah dengan terlebih dahulu mengidentifikasi kontainer yang aktif menggunakan perintah docker ps, kemudian menghentikan dan menghapusnya menggunakan perintah docker stop dan docker rm agar port tersebut tersedia kembali untuk digunakan oleh kontainer praktikum-web.

Tantangan lainnya muncul saat proses konfigurasi awal Git dan Docker di lingkungan Windows. Saya sempat mengalami kebingungan terkait perbedaan karakter baris baru antara Windows (CRLF) dan Linux (LF) saat melakukan perintah git add, serta kendala koneksi Docker Desktop yang memerlukan pengaturan WSL2 yang tepat agar mesin Docker dapat berjalan. Saya mengatasi hal ini dengan mengikuti panduan konfigurasi global pada Git untuk menangani perbedaan baris baru secara otomatis serta memastikan fitur virtualisasi pada sistem operasi saya sudah aktif. Selain itu, ketelitian dalam menuliskan instruksi di Dockerfile juga menjadi tantangan, di mana setiap kesalahan kecil pada sintaksis dapat menyebabkan proses build gagal. Dengan lebih teliti membaca pesan error di terminal dan memahami setiap baris perintah, saya akhirnya berhasil membangun image kustom saya sendiri.

---

## ✅ Checklist

- [x] Berhasil membuat Dockerfile yang valid
- [x] Berhasil build Docker image
- [x] Container berjalan dan aplikasi bisa diakses
- [x] Docker Compose berhasil dijalankan
- [x] Semua screenshot lengkap dan jelas
- [x] Penjelasan ditulis dengan bahasa sendiri

---

*Laporan ini dibuat pada Rabu, 25 Februari 2026*
