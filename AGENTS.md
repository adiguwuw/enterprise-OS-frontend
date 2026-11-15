# Aturan Codex — EnterpriseOS Frontend

Bahasa UI/dokumentasi Indonesia. Jalankan command dari WSL/Linux root checkout dan ikuti lockfile. Baca README/docs index, route/design system, backend OpenAPI, privacy dan spesifikasi modul sebelum coding.

Stack React + TypeScript + Vite + shadcn/ui. Frontend hanya UX; backend adalah otoritas akses dan policy. Jangan simpan access/refresh token di localStorage atau log token/PII. Gunakan OIDC PKCE sesuai keputusan auth frontend; jangan menciptakan secret di browser.

Untuk attendance, minta kamera/GPS hanya saat aksi punch dan jelaskan tujuan. Foto upload langsung ke private Supabase bucket melalui signed URL backend yang singkat; jangan proxy bytes melalui Vercel. Jangan simpan signed URL permanen, koordinat di URL/localStorage/analytics, melakukan background tracking, atau face recognition. WFO kecamatan ditampilkan dari location config backend; jangan geolocate IP dari frontend. WFH/WFA memperlihatkan status persetujuan dan alasan.

Satu task per perubahan. Implementasikan state loading/empty/error/unauthorized/offline/quota-full dan aksesibilitas keyboard. Uji mocked contract sesuai OpenAPI; laporkan command yang benar-benar dijalankan. Semua fixture organisasi, akun, foto dan koordinat sintetis.
