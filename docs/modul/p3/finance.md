# Frontend — Finance

Referensi source of truth backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p3/finance.md

## Tujuan UI
Menyediakan alur operator/employee untuk finance tanpa menggandakan aturan bisnis atau otorisasi backend. API backend menentukan field, state, validasi dan akses.

## Route dan halaman
- /app/finance: ringkasan/list dengan pencarian, filter dan cursor pagination sesuai endpoint backend.
- /app/finance/new: form create hanya bila tersedia izin action.
- /app/finance/:id: detail, status lifecycle, riwayat perubahan dan action yang diizinkan.
- /app/finance/:id/edit: hanya untuk data mutable; If-Match/ETag saat simpan.
- /app/finance/admin: policy/configuration jika relevan, terpisah dari halaman employee.

## API yang dikonsumsi
- POST /api/v1/finance/expense-claims
- GET /api/v1/finance/expense-claims/{id}
- POST /api/v1/finance/expense-claims/{id}/submit
- POST /api/v1/finance/expense-claims/{id}/approve
- GET /api/v1/finance/budgets/{id}/utilization
Typed API client mengikuti kontrak backend; tidak memanggil database atau IdP admin API langsung dari browser. Use cursor, abort request saat filter berubah, dan request ID untuk error. Submit command idempotent memakai key yang sama saat retry; update mengirim If-Match.

## Komponen dan pola interaksi
DataTable/filter toolbar, detail panel/page, controlled form, status badge berlabel, approval/action confirmation, timeline bila API menyediakan history. Jangan membuat nilai/threshold/policy sendiri. Masking mengikuti respons server. Untuk private role domain (HR/payroll), gunakan halaman terpisah dengan no-store dan jangan cache persisten.

## State UX wajib
Loading; populated; empty dengan CTA aman; field validation; API/network error + retry; 401 login ulang; 403 forbidden; 404 unavailable; 409 state conflict; 412 stale version; 429 retry-after. Jangan menganggap hide button = security.

## Acceptance dan skenario test UI
- FIN-01 total lines=claim.
- FIN-02 closed cost center ditolak.
- FIN-03 submit budget reservation atomik.
- FIN-04 maker-checker/SOD.
- FIN-05 reject releases reservation.
- FIN-06 retry submit/approve idempotent.
- Keyboard dapat mengoperasikan tabel/form/dialog; focus kembali setelah dialog; layout usable mobile.
- Direct route tanpa izin menghasilkan 403/redirect UX yang tepat, tidak menampilkan cached sensitive data.
- API error tidak mencetak token, PII, payload atau stack trace ke console.

## TDD component/E2E
Mock sesuai OpenAPI fixture; uji render states, submit success dan error, no duplicate submit, stale version recovery, permission-limited direct route, keyboard navigation dan viewport sempit. E2E data sintetis; hindari production account.
