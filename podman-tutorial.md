# Tutorial Dasar Menggunakan Podman

Podman adalah container engine yang kompatibel dengan Open Container Initiative (OCI), standar terbuka untuk format gambar (image) dan runtime container. Ia menyediakan antarmuka baris perintah (Command Line Interface atau CLI) yang hampir identik dengan Docker, memungkinkan pengguna untuk dengan mudah mencari, menarik, membangun, dan menjalankan container.

## 1. Instalasi Podman

### Linux (Fedora, CentOS, RHEL)

```bash
sudo dnf install podman -y
```

### Ubuntu/Debian

```bash
sudo apt update
sudo apt install podman -y
```

### MacOS

```bash
brew install podman
```

### Windows

Podman tersedia melalui **WSL2** atau instalasi via MSI. Lihat dokumentasi resmi:  
[https://podman.io/getting-started/installation](https://podman.io/getting-started/installation)

---

## 2. Mengecek Versi

```bash
podman --version
```

---

## 3. Menjalankan Container Pertama

```bash
podman run --rm -it docker.io/library/alpine sh
```

- `--rm` → Menghapus container setelah keluar.
- `-it` → Mode interaktif dengan terminal.

---

## 4. Menarik Image

```bash
podman pull docker.io/library/nginx
```

---

## 5. Menjalankan Container di Background

```bash
podman run -d -p 8080:80 nginx
```

- `-d` → Detached mode (jalan di background).
- `-p` → Mapping port host ke container.

---

## 6. Melihat Daftar Container

```bash
podman ps
```

Gunakan `podman ps -a` untuk melihat container yang sudah berhenti.

---

## 7. Menghentikan & Menghapus Container

```bash
podman stop <container_id>
podman rm <container_id>
```

---

## 8. Menghapus Image

```bash
podman rmi nginx
```

---

## 9. Mode Rootless

Secara default, Podman mendukung mode **rootless**, memungkinkan user biasa menjalankan container tanpa hak akses root:

```bash
podman info | grep rootless
```

---

## 10. Perbedaan Utama Podman & Docker

- **Daemonless**: Tidak ada `dockerd` seperti di Docker.
- **Rootless**: Bisa berjalan tanpa root.
- **Pod Concept**: Podman memiliki konsep pod seperti di Kubernetes.
- **CLI Mirip Docker**: Banyak perintah sama persis dengan Docker.

---
