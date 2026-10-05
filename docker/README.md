# Docker + WSL2 — Personal Cheatsheet

## 1. Environment

Setup yang digunakan:

```text
Windows
└── WSL2
    └── Ubuntu
        └── Docker Engine
```

Tidak menggunakan Docker Desktop.

Komponen yang terpasang:

- WSL2
- Ubuntu 26.04 LTS
- Docker Engine
- Docker CLI
- Docker Compose
- Docker Buildx
- containerd

Docker dapat digunakan tanpa `sudo`.

---

## 2. Masuk dan Keluar WSL

### Masuk dari PowerShell

```powershell
wsl
```

atau:

```powershell
wsl -d Ubuntu
```

### Keluar dari Ubuntu

```bash
exit
```

atau:

```text
Ctrl + D
```

### Menghentikan seluruh WSL

Dijalankan dari PowerShell:

```powershell
wsl --shutdown
```

> `exit` hanya keluar dari terminal.
> `wsl --shutdown` menghentikan seluruh instance WSL.

---

# 3. Docker Basic

## Cek versi Docker

```bash
docker --version
```

## Cek informasi Docker

```bash
docker info
```

## Cek Docker yang sedang berjalan

```bash
docker ps
```

## Cek semua container

```bash
docker ps -a
```

Perbedaan:

```text
docker ps
    ↓
container yang sedang Running

docker ps -a
    ↓
semua container
Running + Stopped
```

---

# 4. Image

## Melihat image

```bash
docker images
```

## Download image

```bash
docker pull <image>
```

Contoh:

```bash
docker pull nginx
```

## Menghapus image

```bash
docker rmi <image>
```

Contoh:

```bash
docker rmi nginx
```

---

# 5. Container

## Menjalankan container

```bash
docker run <image>
```

Contoh:

```bash
docker run nginx
```

## Menjalankan container di background

```bash
docker run -d <image>
```

Contoh:

```bash
docker run -d nginx
```

`-d` = detached mode.

## Memberikan nama container

```bash
docker run -d --name <nama> <image>
```

Contoh:

```bash
docker run -d --name web nginx
```

---

# 6. Port

Format:

```bash
docker run -d -p <PORT_HOST>:<PORT_CONTAINER> <image>
```

Contoh:

```bash
docker run -d -p 8080:80 nginx
```

Artinya:

```text
localhost:8080
       ↓
Docker container port 80
```

Akses dari browser:

```text
http://localhost:8080
```

---

# 7. Melihat Container

## Container yang sedang berjalan

```bash
docker ps
```

## Semua container

```bash
docker ps -a
```

## Melihat log

```bash
docker logs <container>
```

Contoh:

```bash
docker logs web
```

## Melihat log secara realtime

```bash
docker logs -f <container>
```

Keluar dengan:

```text
Ctrl + C
```

## Melihat detail container

```bash
docker inspect <container>
```

---

# 8. Menjalankan Perintah di Container

```bash
docker exec -it <container> <command>
```

Contoh:

```bash
docker exec -it web bash
```

Kalau image tidak memiliki `bash`, coba:

```bash
docker exec -it web sh
```

Keluar dari shell container:

```bash
exit
```

---

# 9. Stop dan Start Container

## Stop

```bash
docker stop <container>
```

## Start kembali

```bash
docker start <container>
```

## Restart

```bash
docker restart <container>
```

## Hapus container

```bash
docker rm <container>
```

Container harus berhenti terlebih dahulu.

Jika ingin langsung force remove:

```bash
docker rm -f <container>
```

---

# 10. Resource Monitoring

## Melihat penggunaan CPU dan RAM

```bash
docker stats
```

Menampilkan resource container secara realtime.

Keluar:

```text
Ctrl + C
```

---

# 11. Docker Compose

## Melihat versi

```bash
docker compose version
```

## Menjalankan Compose

Di folder yang memiliki `compose.yaml` atau `docker-compose.yml`:

```bash
docker compose up
```

## Menjalankan di background

```bash
docker compose up -d
```

## Menghentikan service

```bash
docker compose down
```

## Melihat container Compose

```bash
docker compose ps
```

## Melihat log

```bash
docker compose logs
```

Realtime:

```bash
docker compose logs -f
```

---

# 12. Dockerfile

Contoh sederhana:

```dockerfile
FROM node:22

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "run", "dev"]
```

## Build image

```bash
docker build -t <nama-image> .
```

Contoh:

```bash
docker build -t my-app .
```

## Jalankan hasil build

```bash
docker run -p 3000:3000 my-app
```

---

# 13. Volume

Volume digunakan untuk menyimpan data agar tidak hilang ketika container dihapus.

## Melihat volume

```bash
docker volume ls
```

## Membuat volume

```bash
docker volume create <nama-volume>
```

## Menggunakan volume

```bash
docker run -v <nama-volume>:/data <image>
```

---

# 14. Network

## Melihat network

```bash
docker network ls
```

## Membuat network

```bash
docker network create <nama-network>
```

## Menjalankan container menggunakan network

```bash
docker run -d \
  --network <nama-network> \
  --name <nama-container> \
  <image>
```

Container dalam network yang sama dapat berkomunikasi menggunakan nama container.

---

# 15. Membersihkan Docker

## Menghapus container yang berhenti

```bash
docker container prune
```

## Menghapus image yang tidak digunakan

```bash
docker image prune
```

## Membersihkan resource yang tidak digunakan

```bash
docker system prune
```

> Hati-hati dengan perintah `prune`. Periksa terlebih dahulu apa yang akan dihapus.

---

# 16. Alur Belajar Docker

Urutan yang disarankan:

```text
Docker Concept
      ↓
Image
      ↓
Container
      ↓
Port
      ↓
Volume
      ↓
Network
      ↓
Dockerfile
      ↓
Docker Compose
      ↓
Multi-container Application
      ↓
Docker + CI/CD
      ↓
Docker + Cloud
```

---

# 17. Command yang Paling Sering Dipakai

Kalau lupa semuanya, ingat dulu command berikut:

```bash
docker ps
docker ps -a

docker images

docker run
docker stop
docker start
docker restart
docker rm

docker logs
docker exec

docker build

docker compose up
docker compose down
docker compose ps

docker stats
```

---

# 18. Mental Model

Jangan menganggap:

```text
Docker = Virtual Machine
```

Lebih tepat:

```text
Docker Image
     ↓
Container
     ↓
Process/Application
```

Image adalah template.

Container adalah instance yang dijalankan dari image.

Contoh:

```text
nginx image
     ↓
┌─────────────┐
│ nginx       │
│ container   │
└─────────────┘
```

Satu image dapat digunakan untuk membuat banyak container.

---

# 19. Environment Saat Ini

Informasi setup:

```text
OS Host       : Windows
Virtualization: WSL2
Linux         : Ubuntu 26.04 LTS
Docker Engine : 29.8.2
Docker Compose: 5.6.0
Buildx        : 0.37.1
Architecture  : amd64
```

Docker dijalankan langsung di Ubuntu WSL2 tanpa Docker Desktop.
