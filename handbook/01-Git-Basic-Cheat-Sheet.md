# Git Basic — Cheat Sheet & Fast Practical

> Catatan ringkas untuk mengingat ulang workflow Git dari awal sampai push ke GitHub.

---

## 📖 Konsep Dasar

```text
Working Directory
        │
        │ git add
        ▼
Staging Area
        │
        │ git commit
        ▼
Local Repository
        │
        │ git push
        ▼
GitHub / Remote Repository
```

### Intinya

| Area | Fungsi |
|---|---|
| Working Directory | Tempat file sedang diedit |
| Staging Area | Tempat memilih file/perubahan yang akan masuk commit |
| Local Repository | Riwayat commit di komputer |
| Remote Repository | Repository online di GitHub |

---

## ⚡ Cheat Sheet Command

| Command | Fungsi | Contoh |
|---|---|---|
| `git --version` | Cek versi Git | `git --version` |
| `gh --version` | Cek versi GitHub CLI | `gh --version` |
| `git init` | Membuat folder menjadi repo Git | `git init` |
| `git status` | Melihat status perubahan | `git status` |
| `git diff` | Melihat detail perubahan sebelum commit | `git diff` |
| `git add .` | Stage semua perubahan | `git add .` |
| `git add <file>` | Stage file tertentu | `git add README.md` |
| `git commit -m` | Simpan perubahan ke repo lokal | `git commit -m "Update README"` |
| `git log --oneline` | Lihat riwayat commit singkat | `git log --oneline` |
| `git remote -v` | Lihat remote yang terhubung | `git remote -v` |
| `git remote add origin <url>` | Hubungkan repo lokal ke GitHub | `git remote add origin https://github.com/user/repo.git` |
| `git remote set-url origin <url>` | Ubah URL remote | `git remote set-url origin https://github.com/user/repo.git` |
| `git push -u origin main` | Push pertama + set upstream | `git push -u origin main` |
| `git push` | Push berikutnya | `git push` |
| `git pull` | Ambil update dari GitHub | `git pull` |
| `gh auth login` | Login GitHub CLI | `gh auth login` |
| `gh auth status` | Cek status login GitHub CLI | `gh auth status` |
| `gh repo create` | Membuat repository GitHub dari terminal | `gh repo create git-playground --public` |
| `gh repo view --web` | Buka repo di browser | `gh repo view --web` |

---

# 🚀 Fast Practical

Targetnya bukan hafal command, tapi paham workflow yang akan dipakai sehari-hari.

---

## Praktik 1 — Membuat Project

Buat folder:

```bash
mkdir git-playground
cd git-playground
```

Inisialisasi Git:

```bash
git init
```

Cek status:

```bash
git status
```

Output kira-kira:

```text
On branch main

No commits yet

nothing to commit
```

✅ Sampai sini folder biasa sudah berubah menjadi Git Repository.

---

## Praktik 2 — Buat File

```bash
echo "# Git Playground" > README.md
```

Cek lagi:

```bash
git status
```

Output:

```text
Untracked files:
README.md
```

**Untracked** = Git tahu ada file baru, tapi belum mulai melacaknya.

---

## Praktik 3 — Masukkan ke Staging

```bash
git add README.md
```

Cek:

```bash
git status
```

Output:

```text
Changes to be committed:
README.md
```

✅ File sudah masuk Staging Area dan siap di-commit.

---

## Praktik 4 — Commit Pertama

```bash
git commit -m "Initial commit"
```

Lihat riwayat:

```bash
git log --oneline
```

Misalnya:

```text
f3a92ab Initial commit
```

🎉 Selamat! Kamu sudah membuat commit pertama.

---

## Praktik 5 — Edit File

Edit `README.md`.

Misalnya isi menjadi:

```md
# Git Playground

Belajar Git bersama ChatGPT.
```

Lalu cek status:

```bash
git status
```

Output kira-kira:

```text
modified: README.md
```

Lihat apa yang berubah:

```bash
git diff
```

`git diff` adalah command yang sering dipakai sebelum commit untuk memastikan perubahan sudah benar.

---

## Praktik 6 — Commit Kedua

Stage perubahan:

```bash
git add .
```

Commit:

```bash
git commit -m "Update README"
```

Lihat history:

```bash
git log --oneline
```

Output kira-kira:

```text
4bc12f Update README
f3a92ab Initial commit
```

✅ Sekarang repo lokal sudah punya dua commit.

---

## Praktik 7 — Hubungkan ke GitHub

Buat repository baru tanpa membuka browser:

```bash
gh repo create git-playground --public
```

Nanti GitHub CLI akan bertanya beberapa hal.

Pilih:

```text
✓ Push an existing local repository
✓ Remote = origin
✓ Push now
```

Cek remote:

```bash
git remote -v
```

Output kira-kira:

```text
origin  https://github.com/username/git-playground.git (fetch)
origin  https://github.com/username/git-playground.git (push)
```

✅ Repo lokal sudah terhubung ke GitHub.

---

## Praktik 8 — Jika Remote Belum Terhubung

Kalau `git remote -v` kosong, tambahkan remote secara manual:

```bash
git remote add origin https://github.com/username/git-playground.git
```

Cek lagi:

```bash
git remote -v
```

Lalu push pertama:

```bash
git push -u origin main
```

`-u` adalah singkatan dari `--set-upstream`.

Artinya Git mengingat bahwa branch `main` lokal terhubung ke `origin/main`, sehingga push berikutnya cukup:

```bash
git push
```

---

## Praktik 9 — Workflow Harian

Setiap selesai coding:

```bash
git status
```

↓

```bash
git diff
```

↓

```bash
git add .
```

↓

```bash
git commit -m "Deskripsi perubahan"
```

↓

```bash
git push
```

---

## Workflow yang Akan Sering Dipakai

```text
Mulai kerja
    │
    ▼
Edit file
    │
    ▼
git status
    │
    ▼
git diff
    │
    ▼
git add .
    │
    ▼
git commit -m "Pesan commit"
    │
    ▼
git push
```

---

# 📚 Istilah Penting

| Istilah | Arti |
|---|---|
| Git | Version control untuk mencatat perubahan file |
| GitHub | Tempat menyimpan repository Git secara online |
| GitHub CLI (`gh`) | Tool untuk mengakses GitHub dari terminal |
| Repository / Repo | Folder project yang dilacak Git |
| Working Directory | Area file yang sedang diedit |
| Staging Area | Area memilih perubahan sebelum commit |
| Commit | Snapshot perubahan |
| Local Repository | Riwayat commit di komputer |
| Remote Repository | Repository online seperti GitHub |
| origin | Nama alias untuk remote GitHub |
| main | Branch utama |
| HEAD | Posisi commit yang sedang aktif |
| upstream | Hubungan branch lokal dengan branch remote |
| Untracked | File baru yang belum dilacak Git |
| Modified | File yang sudah berubah |
| Staged | Perubahan sudah siap di-commit |
| Push | Kirim commit lokal ke GitHub |
| Pull | Ambil update dari GitHub ke lokal |

---

# 🧪 Error Umum

## 1. Repository not found

Penyebab umum:

- Salah URL remote
- Typo nama repository
- Login GitHub CLI ke akun yang berbeda
- Repository belum dibuat

Cek dengan:

```bash
git remote -v
gh auth status
```

Ubah remote jika URL salah:

```bash
git remote set-url origin https://github.com/username/repo.git
```

---

## 2. `gh: command not found`

Penyebab:

- GitHub CLI belum terinstall
- Terminal belum di-restart setelah install

Cek:

```bash
gh --version
```

Solusi:

- Tutup terminal
- Buka terminal baru
- Coba lagi

---

## 3. `fatal: not a git repository`

Penyebab:

- Command Git dijalankan di folder yang bukan repository Git

Solusi:

```bash
pwd
cd nama-folder-project
git status
```

---

# 💡 Best Practice

- Jalankan `git status` sebelum `git add`.
- Jalankan `git diff` sebelum `git commit`.
- Gunakan pesan commit yang jelas.
- Jangan langsung `git add .` kalau AI mengubah banyak file dan belum kamu review.
- Gunakan `git remote -v` kalau ada masalah push.
- Gunakan `git push -u origin main` hanya untuk push pertama.
- Setelah upstream tersimpan, cukup gunakan `git push`.

---

# 🎯 Mini Challenge

Coba lakukan sendiri tanpa melihat catatan:

1. Buat folder `git-playground`.
2. Jalankan `git init`.
3. Buat `README.md`.
4. Commit pertama.
5. Edit `README.md`.
6. Commit kedua.
7. Tampilkan `git log --oneline`.
8. Buat repo GitHub dengan `gh repo create`.
9. Cek `git remote -v`.
10. Push ke GitHub.

Kalau berhasil, berarti kamu sudah menguasai workflow dasar Git yang paling sering dipakai sehari-hari.

---

# ➡️ Next Level

Topik berikutnya:

```text
Git Branch & Merge
```

Branch penting karena nanti saat memakai AI coding seperti Cursor atau Antigravity, kamu bisa meminta AI bekerja di branch terpisah agar `main` tetap aman.
