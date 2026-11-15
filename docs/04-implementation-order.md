# Urutan Implementasi Frontend

1. Bootstrap WSL, Vite React TS, shadcn/ui, tokens, router, env, lockfile, lint/typecheck/test.
2. Typed API wrapper + error model + OIDC login/callback/logout.
3. Authenticated shell, responsive nav, accessible primitives, loading/empty/error/forbidden pages.
4. Organization, directory, employee lifecycle with masks and scopes.
5. IAM admin, grants and audit reader; negative direct-route tests.
6. Phase 2 attendance: Dashboard Admin policy (default demo: Asia/Jakarta, shift weekdays 09:00–17:00, break 12:00–13:00, grace 15m, radius 150m, accuracy 100m, capture age 60s, photo 30d, metadata 365d; bounded editing, verified CIDR, role separation, versi effective-dated + audit) → remote request and reason → manager decision/reason → attendance policy/location states → camera/GPS capture only on explicit punch → direct signed storage upload + confirm → punch receipt/history → scoped manager evidence review → adjustment exception UX.
7. Leave/performance/payroll sandbox then Phase 3-5 only when backend contracts are accepted.

## Attendance implementation guardrails
Never upload image bytes through Vercel/API; never persist signed URLs or coordinates in URL/localStorage/analytics. Show location/kecamatan from backend, not browser IP geolocation. No background tracking or face recognition. Include permission denied, inaccurate GPS, wrong office network, pending approval, signed URL expiry, storage quota and failure states.

Definition of Ready: backend OpenAPI, policy, data privacy and error states reviewed. Done: contract tests, accessibility/responsive states, no token/PII/evidence leakage, actual commands recorded and docs updated.
