# Authentication dan API Consumption

## OIDC
Authorization Code + PKCE via Auth0 Free hosted atau Keycloak local. Validate state, nonce, PKCE, issuer, audience, expiry. Callback hanya route sementara; hapus query code dari history setelah exchange. Jangan menaruh token dalam URL/log. Pilih session in-memory dan refresh policy dari OIDC SDK; jangan localStorage. Evaluasi BFF/cookie dan CSRF sebelum implementasi hosted; catat keputusan final di ADR bila kemampuan Vercel functions membatasi.

## Client boundary
Satu typed client per domain dengan base URL dari env; fetch wrapper memaksa timeout/abort, request ID, content type, safe retry hanya pada GET/idempotent command. Tangani 401 logout/refresh sekali, 403 unauthorized screen, 404 not found, 409 conflict, 412 reload/reconcile, 422 field errors, 429 retry-after, 5xx correlation ID. Jangan expose detail server.

## Data fetching
Server pagination cursor; debounce search; cancel stale requests; jangan simpan data sensitif di persistent cache. Cache key menyertakan principal/scope/version dan dibersihkan saat logout/role changes. Do not infer permission from menu visibility; 403 normal flow.

## Forms
Client validation untuk feedback saja; server authority. Idempotency key untuk submission yang aman retry; disable duplicate click; handle uncertain network state by retry with same key. If-Match/ETag saat update. Confirm irreversible transitions and require reason where API spec requires.

## Environment
VITE_API_BASE_URL non-secret; OIDC public client ID only; secrets/provider credentials hanya server env dan tidak masuk bundle. .env.example placeholder non-secret.
