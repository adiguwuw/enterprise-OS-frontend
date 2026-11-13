# Route Map dan Design System

## App shell
- /login, /auth/callback, /logout
- /app/dashboard
- /app/organization, /app/organization/units/:id
- /app/directory, /app/directory/:employeeId, /app/me
- /app/admin/access (grant, roles, policies), /app/admin/audit
- /app/hr/employees, /app/hr/employees/:id
- /app/<module> routes hanya dibuka bertahap sesuai fase.

## Navigation
Sidebar per domain dan disaring oleh capability endpoint untuk UX. Breadcrumb, page title, primary action, search/filter, data table, detail sheet/page, pagination, confirmation untuk destructive/state-changing actions. Jangan menyimpulkan user tidak punya akses hanya dari capability cache.

## Design system
shadcn/ui + Tailwind tokens. Semantic color tokens; status color selalu dilengkapi label/icon. Responsive sidebar collapsible, table-to-card pada layar sempit. Form label/hint/error; dialog fokus terperangkap; toast tidak menjadi satu-satunya status kritis. Loading skeleton, empty state dengan tindakan aman, error dengan retry/request ID, 403/404, stale/conflict (412) state.

## Aksesibilitas
Keyboard-only flow, focus visible, semantic headings, accessible name, aria-describedby untuk error, contrast AA target, reduced motion, tabel dapat dibaca screen reader. Jangan gunakan warna saja untuk status. Uji zoom dan viewport sempit.

## UX privacy
Masking mengikuti payload server. Hindari PII di URL, analytics, console. Jangan tampilkan data stale sebagai status berhasil. Payslip/private fields tidak pernah masuk dashboard umum.
