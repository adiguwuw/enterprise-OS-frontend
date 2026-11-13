# Frontend — Procurement

Referensi source of truth backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p3/procurement.md

## Tujuan UI
Menyediakan alur operator/employee untuk procurement tanpa menggandakan aturan bisnis atau otorisasi backend. API backend menentukan field, state, validasi dan akses.

## Route dan halaman
- /app/procurement: ringkasan/list dengan pencarian, filter dan cursor pagination sesuai endpoint backend.
- /app/procurement/new: form create hanya bila tersedia izin action.
- /app/procurement/:id: detail, status lifecycle, riwayat perubahan dan action yang diizinkan.
- /app/procurement/:id/edit: hanya untuk data mutable; If-Match/ETag saat simpan.
- /app/procurement/admin: policy/configuration jika relevan, terpisah dari halaman employee.

## API yang dikonsumsi
- POST /api/v1/procurement/requisitions
- POST /api/v1/procurement/requisitions/{id}/submit
- POST /api/v1/procurement/requisitions/{id}/quotes
- POST /api/v1/procurement/purchase-orders
- POST /api/v1/procurement/purchase-orders/{id}/receipts
Typed API client mengikuti kontrak backend; tidak memanggil database atau IdP admin API langsung dari browser. Use cursor, abort request saat filter berubah, dan request ID untuk error. Submit command idempotent memakai key yang sama saat retry; update mengirim If-Match.

## Komponen dan pola interaksi
DataTable/filter toolbar, detail panel/page, controlled form, status badge berlabel, approval/action confirmation, timeline bila API menyediakan history. Jangan membuat nilai/threshold/policy sendiri. Masking mengikuti respons server. Untuk private role domain (HR/payroll), gunakan halaman terpisah dengan no-store dan jangan cache persisten.

## State UX wajib
Loading; populated; empty dengan CTA aman; field validation; API/network error + retry; 401 login ulang; 403 forbidden; 404 unavailable; 409 state conflict; 412 stale version; 429 retry-after. Jangan menganggap hide button = security.

## Acceptance dan skenario test UI
- PROC-01 quantity positive/quote valid.
- PROC-02 requester tak approve sendiri.
- PROC-03 PO dari requisition approved dan total valid.
- PROC-04 supplier/PO unique.
- PROC-05 receipt tidak melebihi qty PO.
- PROC-06 partial receipt mencegah cancel sembarang.
- Keyboard dapat mengoperasikan tabel/form/dialog; focus kembali setelah dialog; layout usable mobile.
- Direct route tanpa izin menghasilkan 403/redirect UX yang tepat, tidak menampilkan cached sensitive data.
- API error tidak mencetak token, PII, payload atau stack trace ke console.

## TDD component/E2E
Mock sesuai OpenAPI fixture; uji render states, submit success dan error, no duplicate submit, stale version recovery, permission-limited direct route, keyboard navigation dan viewport sempit. E2E data sintetis; hindari production account.
