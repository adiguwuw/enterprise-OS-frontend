# Frontend SRS/TDD dan Test Strategy

## Functional expectations
OIDC login/logout; route guards UX; organization tree; directory visibility; employee admin; access/audit; attendance remote request, manager decision, WFO/WFH/WFA punch, evidence upload, history and scoped review. Backend API adalah source of truth untuk role, location/IP match, approval, GPS policy dan status.

## UI state
Loading, populated, empty, validation, API error/retry/request ID, unauthenticated, forbidden, out-of-scope, stale conflict, offline/timeout, camera denied, GPS denied/stale/low accuracy, network mismatch, unapproved remote work, upload/confirm failure, storage quota reached. Jangan kehilangan draft alasan saat retry aman.

## Test IDs
F-01 unauthenticated redirect; F-02 OIDC state/nonce error; F-03 permission nav; F-04 forbidden direct URL; F-05 cursor search; F-06 masked field; F-07 422 maps to form; F-08 409/412 recovery; F-09 stable idempotency key retry; F-10 logout clears memory; F-11 dialog keyboard; F-12 mobile 375px; F-13 no PII/token console; F-14 API outage; F-15 no sensitive URL/storage.
- FA-01 request WFH/WFA requires mode, dates and reason.
- FA-02 manager queue respects scope; approve/reject requires reason and pending status.
- FA-03 self-approval unavailable; API 403 rendered safely.
- FA-04 punch asks camera/GPS only after explicit click and states purpose.
- FA-05 preview allows retake/cancel before upload; no face recognition.
- FA-06 GPS accuracy/location time shown; invalid/stale result gives recovery instructions.
- FA-07 WFO shows server matched location/kecamatan only after API response; no client IP claims.
- FA-08 remote punch disabled without approved request covering date.
- FA-09 upload uses signed direct-to-storage URL, correct headers, then confirm; no photo POST to API.
- FA-10 expired signed URL retries by requesting a new intent without duplicate punch.
- FA-11 quota/storage failure never shows successful punch; preserves safe draft and offers manual procedure.
- FA-12 evidence view requires authorization, no persistent signed URL/cache.
- FA-13 team page filters and masks by backend response; no data from outside scope.
- FA-14 keyboard/screenreader; no camera/GPS prompt on page load.
- FA-15 error telemetry excludes image, coordinates, reasons and signed URL.

Test with synthetic fixtures and mocked browser media/location; no real employee evidence. Merge gate follows lockfile and actual available format/lint/typecheck/test/build commands.


## Test Dashboard Admin presensi
- FA-16 admin mengisi policy dengan reason/effective date dan melihat validasi server.
- FA-17 non-admin atau admin di luar scope tidak dapat membaca/mengubah policy.
- FA-18 riwayat menunjukkan versi, actor, alasan dan before/after; versi lama read-only.
- FA-19 maker-checker aktif: creator tidak dapat menyetujui versi sendiri.
- FA-20 overlap/stale If-Match/validation failure tidak mengubah policy yang ditampilkan sebagai aktif; draft aman tetap tersedia.
- FA-21 UI tidak menghitung ulang histori punch setelah policy berubah; detail menunjukkan policy version yang dipakai.
- FA-22 seed dashboard menunjukkan nilai demo dan bounds; nilai out-of-bounds ditolak backend dan UI memetakan error.
- FA-23 office CIDR belum terverifikasi tampil nonaktif; WFO tidak ditandai siap sampai API menyatakan verified.
- FA-24 role menu sesuai matriks: policy admin tidak otomatis membuka evidence; Platform/IAM Admin tidak otomatis membuka data HR; direct URL tetap 403.
