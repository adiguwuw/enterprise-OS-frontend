# Aturan Codex — EnterpriseOS Frontend

Bahasa UI/dokumentasi Indonesia. Kerjakan semua project command dari WSL/Linux root checkout; jangan campur Windows Node dengan WSL filesystem. Baca README.md dan docs/README.md, route map, design system, API contract backend dan spesifikasi modul sebelum coding.

Stack final React + TypeScript + Vite + shadcn/ui. Gunakan komponen accessible, typed API client, feature folder. Frontend bukan enforcement security: jangan anggap hidden button sebagai authz; backend menentukan akses. Jangan menyimpan token di localStorage; pakai pola OIDC PKCE yang aman (prefer BFF/cookie bila deploy mampu, atau library OIDC yang mendukung in-memory session dan state/nonce/PKCE; catat trade-off). Jangan log payload/token/PII. Jangan tambahkan paid UI/API providers atau dependency tanpa kebutuhan/ADR.

Satu task per perubahan. Update route map, API consumption, loading/empty/error/unauthorized states dan skenario test. Jalankan package manager yang terkunci package-lock/pnpm-lock dari WSL, lint/typecheck/test/build yang benar-benar tersedia; jangan klaim test tanpa hasil. Data fixture wajib fiktif. Jangan memasang custom domain berbayar atau layanan berbayar.
