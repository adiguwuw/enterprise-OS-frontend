# Frontend — RabbitMQ

Referensi source of truth backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p5/rabbitmq.md

## Tujuan UI
Menyediakan alur operator/employee untuk rabbitmq tanpa menggandakan aturan bisnis atau otorisasi backend. API backend menentukan field, state, validasi dan akses.

## Route dan halaman
- /app/rabbitmq: ringkasan/list dengan pencarian, filter dan cursor pagination sesuai endpoint backend.
- /app/rabbitmq/new: form create hanya bila tersedia izin action.
- /app/rabbitmq/:id: detail, status lifecycle, riwayat perubahan dan action yang diizinkan.
- /app/rabbitmq/:id/edit: hanya untuk data mutable; If-Match/ETag saat simpan.
- /app/rabbitmq/admin: policy/configuration jika relevan, terpisah dari halaman employee.

## API yang dikonsumsi
- GET /internal/messaging/health
- GET /internal/messaging/consumers
- POST /internal/messaging/dead-letters/{id}/replay
- POST /internal/messaging/dead-letters/{id}/discard
Typed API client mengikuti kontrak backend; tidak memanggil database atau IdP admin API langsung dari browser. Use cursor, abort request saat filter berubah, dan request ID untuk error. Submit command idempotent memakai key yang sama saat retry; update mengirim If-Match.

## Komponen dan pola interaksi
DataTable/filter toolbar, detail panel/page, controlled form, status badge berlabel, approval/action confirmation, timeline bila API menyediakan history. Jangan membuat nilai/threshold/policy sendiri. Masking mengikuti respons server. Untuk private role domain (HR/payroll), gunakan halaman terpisah dengan no-store dan jangan cache persisten.

## State UX wajib
Loading; populated; empty dengan CTA aman; field validation; API/network error + retry; 401 login ulang; 403 forbidden; 404 unavailable; 409 state conflict; 412 stale version; 429 retry-after. Jangan menganggap hide button = security.

## Acceptance dan skenario test UI
- MQ-01 broker down leaves outbox pending.
- MQ-02 ack only after transaction commit.
- MQ-03 bounded retry then DLQ.
- MQ-04 replay idempotent+audited.
- MQ-05 poison event quarantined.
- MQ-06 credentials/TLS never logged.
- Keyboard dapat mengoperasikan tabel/form/dialog; focus kembali setelah dialog; layout usable mobile.
- Direct route tanpa izin menghasilkan 403/redirect UX yang tepat, tidak menampilkan cached sensitive data.
- API error tidak mencetak token, PII, payload atau stack trace ke console.

## TDD component/E2E
Mock sesuai OpenAPI fixture; uji render states, submit success dan error, no duplicate submit, stale version recovery, permission-limited direct route, keyboard navigation dan viewport sempit. E2E data sintetis; hindari production account.
