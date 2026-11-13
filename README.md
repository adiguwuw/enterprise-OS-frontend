# EnterpriseOS Frontend

Frontend React + TypeScript untuk proyek portofolio EnterpriseOS. Semua perusahaan, pegawai, transaksi, dan data contoh adalah simulasi. Proyek ini tidak berafiliasi dengan Telkom dan tidak memakai data internal/rahasia Telkom.

## Blueprint final
Lihat `docs/README.md` untuk arsitektur frontend, route, design system, kontrak backend yang dikonsumsi, aksesibilitas, dan skenario uji per modul.

## Lingkungan kerja
Pengembangan dilakukan dari WSL/Linux shell. UI menggunakan React, TypeScript dan shadcn/ui. Gunakan Node package manager yang tercatat di repo dan jangan mencampur dependency Windows/WSL.

## API
Panggilan HTTP melalui API Gateway. Kontrak otoritatif berada di [EnterpriseOS Backend](https://github.com/adiguwuw/enterprise-OS-backend/tree/main/docs).

## Biaya
Frontend di-deploy di Vercel Hobby dengan subdomain gratis. Jangan membeli domain, menambahkan service berbayar, memasang metode pembayaran, atau meng-upgrade plan. Saat kuota tercapai, demo boleh pause.

## Status
Repository ini memuat blueprint dan scaffold dokumentasi. Implementasi UI dilakukan bertahap sesuai acceptance criteria dan kontrak API.
