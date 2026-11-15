# Route Map dan Design System

## App shell
- /login, /auth/callback, /logout
- /app/dashboard
- /app/organization, /app/organization/units/:id
- /app/directory, /app/directory/:employeeId, /app/me
- /app/admin/access, /app/admin/audit
- /app/hr/employees, /app/hr/employees/:id
- /app/attendance, /app/attendance/punch, /app/attendance/history
- /app/attendance/remote-work, /app/attendance/remote-work/new
- /app/manager/attendance/requests, /app/manager/attendance/team
Routes tampil sesuai capability untuk UX; backend tetap otoritatif.

## Attendance journeys
Employee memeriksa mode dan policy → mengajukan WFH/WFA dengan tanggal/lokasi/alasan → melihat pending/approved/rejected + alasan manager → pada hari kerja memilih check-in/out → memberi izin kamera/GPS sekali untuk aksi → preview foto, accuracy dan location label → upload langsung ke private storage → konfirmasi punch → melihat receipt/status. WFO memperlihatkan lokasi kantor/kecamatan hasil konfigurasi dan status jaringan tervalidasi; WFH/WFA memperlihatkan request yang disetujui. Manager melihat request/team dalam scope, memberi keputusan dengan alasan, membuka bukti melalui izin sementara.

UI harus menjelaskan permission denied, GPS accuracy tidak memenuhi batas, jaringan kantor tidak cocok, request remote belum approved, file tidak valid, storage gagal/kuota penuh dan koreksi manual. Jangan memalsukan GPS/IP, menyimpulkan lokasi dari IP geolocation, melacak latar belakang, atau mengenali wajah.

## Design system dan aksesibilitas
shadcn/ui + Tailwind semantic tokens. Status selalu label/icon selain warna. Responsive sidebar/table, accessible labels/errors/focus, keyboard flow, contrast target AA, reduced motion. Loading, empty, API error + request ID, 401, 403, 404, 409/412, timeout/quota states. Jangan menampilkan data sensitif pada URL atau cache persistent. Foto/koordinat hanya tampil pada view berizin dan tidak masuk analytics/console.


## Dashboard Admin presensi
Tambahkan halaman /app/admin/attendance/policies dan /app/admin/attendance/policies/:id/history untuk Admin berizin. Form mengelola radius GPS, accuracy maksimum, shift/timezone, kalender, retensi evidence, aturan exception, WorkLocation dan CIDR kantor. Tampilkan policy aktif, periode efektif, draft/pending approval, alasan dan ringkasan before/after. Versi historis read-only; perubahan membuat versi baru. Tampilkan action approval terpisah bila maker-checker aktif. Enforcement tetap di backend.

### Nilai yang ditampilkan pada dashboard
Default seed demo: Asia/Jakarta; Senin–Jumat, shift 09:00–17:00, break 12:00–13:00; grace 15 menit; GPS radius 150 m; accuracy maksimum 100 m; usia GPS maksimum 60 detik; retensi foto 30 hari; metadata 365 hari. Tampilkan bounds server (radius 25–500 m, accuracy 10–200 m, usia GPS 30–300 detik, retensi foto 1–90 hari, metadata 30–3650 hari) dan pesan bahwa nilai di luar rentang ditolak. CIDR default kosong/nonaktif sampai admin memasukkan dan memverifikasi egress kantor. UI tidak boleh mengaktifkan WFO sendiri.
