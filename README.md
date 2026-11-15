# EnterpriseOS Frontend

Antarmuka React + TypeScript untuk portofolio EnterpriseOS. Seluruh organisasi, pegawai, kebijakan, lokasi, dan bukti demo bersifat fiktif. Telkom Indonesia hanya menjadi referensi terbuka untuk kategori kapabilitas organisasi; proyek ini tidak berafiliasi dan tidak mengklaim memakai informasi internal.

## Blueprint
Lihat `docs/README.md` untuk route, design system, aksesibilitas, kontrak API, test, dan perjalanan tiap modul. Sumber kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/tree/main/docs

## Stack dan WSL
React + TypeScript + Vite + shadcn/ui. Jalankan Node dan package manager dari checkout WSL/Linux, ikuti lockfile yang ada, dan jangan mencampur `node_modules` Windows dengan WSL.

## Bukti presensi
Kamera dan GPS diminta hanya saat pegawai menekan tombol presensi. WFO divalidasi backend memakai IP egress publik kantor yang dikonfigurasi dan dipetakan ke WorkLocation; WFH/WFA memerlukan persetujuan atasan dengan alasan. Setiap punch membutuhkan foto dan bukti GPS. Browser mengunggah foto langsung ke private bucket Supabase Storage Free memakai signed URL singkat dari backend; foto tidak dikirim melalui Vercel/API. Tampilkan kegagalan izin, upload, dan kuota secara jelas. Tidak ada pelacakan latar belakang atau pengenalan wajah. Gunakan bukti sintetis.

## Deployment gratis
Demo memakai Vercel Hobby, Neon Free, provider OIDC free yang dipilih, dan Supabase Storage Free. Kuota dan syarat dapat berubah. Jangan memakai plan berbayar, kartu, domain berbayar atau fallback berbayar. Demo hosted boleh dihentikan sementara ketika kuota habis.
