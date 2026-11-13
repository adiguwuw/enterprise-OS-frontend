# Urutan Implementasi Frontend

1. Bootstrap WSL, Vite React TS, shadcn/ui, tokens, router, env, lint/typecheck/test.
2. Typed API wrapper + error model + OIDC login/callback/logout dan unauthenticated shell.
3. Authenticated app shell, responsive nav, accessible primitives, empty/error/loading pages.
4. Organization tree/search, employee directory/detail, profile masking.
5. HR employee list/create/detail/lifecycle dengan server permission dan optimistic concurrency.
6. Admin role/scope assignment + audit reader; test negative direct URL.
7. Phase 2–5 satu modul demi satu modul mengikuti masing-masing docs/modul spec dan backend API.

Definition of Ready: API schema/security/scope jelas, data classification dan UX state ditulis, mock valid. Definition of Done: test IDs lulus, responsive keyboard UX, no token/PII persistence/logs, API errors safe, docs updated, build berhasil di WSL.
