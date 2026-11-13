# EnterpriseOS Frontend — Blueprint Final

React/TypeScript UI terpisah dari Go API repository: https://github.com/adiguwuw/enterprise-OS-backend. Status repo saat ini dokumentasi/scaffold. Data organisasi/pegawai fiktif; referensi Telkom hanya konteks publik, bukan struktur internal.

## Review
1. Keputusan dan PRD backend.
2. Dokumen frontend ini: route/design system, auth, API boundary.
3. Spesifikasi fitur per modul di folder docs/modul.
4. Matriks skenario frontend dan roadmap.

## Frontend module blueprints
- Phase 1 — [Organization Service](modul/p1/organization-service.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p1/organization-service.md
- Phase 1 — [IAM Service](modul/p1/iam-service.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p1/iam-service.md
- Phase 1 — [Authentication & SSO](modul/p1/authentication-sso.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p1/authentication-sso.md
- Phase 1 — [RBAC & ABAC](modul/p1/rbac-abac.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p1/rbac-abac.md
- Phase 1 — [Company Structure](modul/p1/company-structure.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p1/company-structure.md
- Phase 1 — [Employee Directory](modul/p1/employee-directory.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p1/employee-directory.md
- Phase 2 — [Employee Management](modul/p2/employee-management.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p2/employee-management.md
- Phase 2 — [Attendance](modul/p2/attendance.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p2/attendance.md
- Phase 2 — [Leave Management](modul/p2/leave-management.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p2/leave-management.md
- Phase 2 — [Payroll](modul/p2/payroll.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p2/payroll.md
- Phase 2 — [Performance Management](modul/p2/performance-management.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p2/performance-management.md
- Phase 3 — [Finance](modul/p3/finance.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p3/finance.md
- Phase 3 — [Accounting](modul/p3/accounting.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p3/accounting.md
- Phase 3 — [Procurement](modul/p3/procurement.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p3/procurement.md
- Phase 3 — [Asset Management](modul/p3/asset-management.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p3/asset-management.md
- Phase 4 — [CRM](modul/p4/crm.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p4/crm.md
- Phase 4 — [Project Management](modul/p4/project-management.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p4/project-management.md
- Phase 4 — [Document Management](modul/p4/document-management.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p4/document-management.md
- Phase 4 — [Collaboration](modul/p4/collaboration.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p4/collaboration.md
- Phase 5 — [RabbitMQ](modul/p5/rabbitmq.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p5/rabbitmq.md
- Phase 5 — [Event-driven Architecture](modul/p5/event-driven-architecture.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p5/event-driven-architecture.md
- Phase 5 — [Audit & Compliance](modul/p5/audit-compliance.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p5/audit-compliance.md
- Phase 5 — [Monitoring](modul/p5/monitoring.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p5/monitoring.md
- Phase 5 — [Distributed Tracing](modul/p5/distributed-tracing.md) · kontrak backend: https://github.com/adiguwuw/enterprise-OS-backend/blob/main/docs/modul/p5/distributed-tracing.md

API backend adalah source of truth untuk ERD, permission, endpoint dan bisnis. UI hanya presentasi dan UX validation; semua action diperiksa kembali oleh API.
