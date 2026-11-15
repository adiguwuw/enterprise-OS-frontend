# EnterpriseOS Frontend

React + TypeScript portfolio UI for EnterpriseOS. All organizations, employees, policies, locations and demo evidence are fictional. Telkom Indonesia is only a public reference for organizational capability categories; no affiliation or confidential information is claimed.

## Blueprint
See docs/README.md for routes, design system, accessibility, API contracts, tests and module journeys. Backend source of truth: https://github.com/adiguwuw/enterprise-OS-backend/tree/main/docs

## Stack and WSL
React + TypeScript + Vite + shadcn/ui; run Node/package manager from WSL/Linux checkout and follow the committed lockfile. Do not mix Windows and WSL node_modules.

## Attendance evidence
Camera and GPS are requested only when the employee initiates a punch. WFO uses backend-validated office public egress IP mapped to configured WorkLocation; WFH/WFA requires an approved manager request with reasons. Each punch requires photo and GPS evidence. Browser uploads directly to a private Supabase Storage Free bucket using a short-lived server-issued signed URL; never send photo bytes through Vercel/API. Handle permission denial, upload failure and quota exhaustion clearly; no background location or face recognition. Use synthetic evidence only.

## Free deployment
Vercel Hobby frontend/API demo, Neon Free PostgreSQL, selected free OIDC, Supabase Storage Free. Quotas and terms can change. No paid plan, card, custom paid domain or silent paid fallback. Hosted demo may pause at quota.
