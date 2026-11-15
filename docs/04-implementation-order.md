# Urutan Implementasi Frontend

1. Bootstrap WSL, Vite React TS, shadcn/ui, tokens, router, env, lockfile, lint/typecheck/test.
2. Typed API wrapper + error model + OIDC login/callback/logout.
3. Authenticated shell, responsive nav, accessible primitives, loading/empty/error/forbidden pages.
4. Organization, directory, employee lifecycle with masks and scopes.
5. IAM admin, grants and audit reader; negative direct-route tests.
6. Phase 2 attendance: Dashboard Admin policy (radius/accuracy/shift/timezone/calendar/retention/exception, versi effective-dated + audit) → remote request and reason → manager decision/reason → attendance policy/location states → camera/GPS capture only on explicit punch → direct signed storage upload + confirm → punch receipt/history → scoped manager evidence review → adjustment exception UX.
7. Leave/performance/payroll sandbox then Phase 3-5 only when backend contracts are accepted.

## Attendance implementation guardrails
Never upload image bytes through Vercel/API; never persist signed URLs or coordinates in URL/localStorage/analytics. Show location/kecamatan from backend, not browser IP geolocation. No background tracking or face recognition. Include permission denied, inaccurate GPS, wrong office network, pending approval, signed URL expiry, storage quota and failure states.

Definition of Ready: backend OpenAPI, policy, data privacy and error states reviewed. Done: contract tests, accessibility/responsive states, no token/PII/evidence leakage, actual commands recorded and docs updated.
