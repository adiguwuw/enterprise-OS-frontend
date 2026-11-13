# Frontend SRS/TDD dan Test Strategy

## Functional expectations
Login/logout; route guards UX; shell/menu; org tree; directory search/detail/visibility; employee admin lifecycle; access admin; audit reader; fase lanjutan mengikuti modul. Responsif, Bahasa Indonesia, permission-aware nav tetapi API tetap otoritatif.

## State model wajib per screen
Loading/skeleton, success populated, empty, validation error, API error + retry/request ID, unauthenticated, forbidden, not found/out-of-scope, stale version conflict, offline/timeout, partial result bila API memang mendukung.

## Test layers
- Unit: format date/currency, policy-aware visibility helpers, form validation, error mapping.
- Component: keyboard interaction, form errors, table pagination, dialogs/focus, loading/error/empty.
- Contract: typed API schema matches OpenAPI examples; mocked response fixture generated/maintained against backend contract.
- E2E: login test IdP, Phase 1 journeys, positive and negative access; screenshot not sole assertion.
- Accessibility: automated checks plus keyboard manual walkthrough; color contrast/labels.

## Test IDs
F-01 unauthenticated route redirect; F-02 OIDC state/nonce failure displays safe error; F-03 role-limited nav; F-04 direct URL forbidden still shows 403; F-05 search debounce/cancel/cursor; F-06 masked private field; F-07 form server 422 maps field; F-08 409/412 asks refresh without losing draft where safe; F-09 repeated submit uses same idempotency key; F-10 logout clears state/cache; F-11 keyboard dialog focus/escape; F-12 viewport 375px; F-13 no token/PII console logs; F-14 API down displays retry/correlation ID; F-15 no private data in URL/storage.

Merge gate: format, lint, typecheck, unit/component/E2E for touched features, build; record actual command and outcome. Respect repo package lock.
