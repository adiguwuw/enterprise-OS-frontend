# Frontend — Attendance

Backend source of truth: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p2/attendance.md

## Tujuan dan aktor
Employee mengajukan WFH/WFA dan punch dengan foto + lokasi. Manager memutus request dan meninjau evidence dalam scope. HR melihat konfigurasi dan exception sesuai izin. Frontend tidak membuat keputusan IP, radius, approval atau authz.

## Routes
- /app/attendance — policy hari ini, riwayat dan receipt punch.
- /app/attendance/punch — wizard check-in/out.
- /app/attendance/remote-work/new dan /app/attendance/remote-work — request dan status.
- /app/manager/attendance/requests — approval queue scoped.
- /app/manager/attendance/team — attendance review scoped.
- /app/attendance/adjustments — correction flow bila granted.

## API
POST /api/v1/attendance/remote-work-requests; GET /attendance/remote-work-requests/me; GET /attendance/remote-work-requests/pending; POST /attendance/remote-work-requests/{id}/decision; POST /attendance/evidence-upload-intents; POST /attendance/evidence-upload-intents/{id}/confirm; POST /attendance/punches; GET /attendance/me; GET /attendance/team; GET /attendance/punches/{id}/evidence-url; adjustment endpoints. Typed client mengikuti OpenAPI, abort stale queries, request ID error display, idempotency key stable saat retry.

## Employee flow
1. Pilih WFH/WFA, periode, label area dan alasan wajib; submit.
2. Tampilkan status dan alasan keputusan atasan. Remote punch aktif hanya bila request approved mencakup tanggal lokal.
3. Pada klik punch, minta izin kamera/GPS; bukan saat membuka halaman. Preview/retake/cancel. Tampilkan GPS accuracy/time, work mode dan instruksi lokasi.
4. Minta upload intent backend, unggah file langsung ke private Supabase dengan signed URL/headers, confirm upload, lalu kirim punch metadata. Jangan kirim byte foto melalui API/Vercel.
5. Tampilkan receipt hanya setelah API sukses. Retry expired URL dengan intent baru dan idempotency key punch yang sama; storage quota error bukan sukses.

## WFO vs remote presentation
WFO: backend memvalidasi trusted request network dan mengembalikan configured WorkLocation/kecamatan + match state. Frontend tidak membaca SSID atau menyatakan sendiri IP publik. Remote: tampilkan request approved, area label dan hasil GPS policy dari server. Jangan melakukan reverse lookup IP untuk kecamatan.

## Evidence privacy
Private signed read URL hanya diminta setelah backend authz, gunakan dalam memori sesaat dan jangan cache/persist/log/analytics. Hapus object URL preview setelah selesai. Hanya synthetic photos. No face recognition, background tracking, geolocation outside punch.

## UI/test scenarios
FA-01 alasan remote wajib; FA-02 manager keputusan wajib alasan; FA-03 self-approval/API 403; FA-04 capture permission hanya setelah klik; FA-05 preview retake; FA-06 GPS denied/stale/accuracy rendah; FA-07 WFO mismatch and server location; FA-08 remote pending/rejected blocks punch; FA-09 signed direct upload + confirm; FA-10 signed expiry retry; FA-11 storage quota prevents success; FA-12 scoped evidence URL and no persistent caching; FA-13 manager scope/masking; FA-14 keyboard/mobile/accessibility; FA-15 no sensitive console/telemetry. Add backend ATT-01–18 coverage in E2E contract.
