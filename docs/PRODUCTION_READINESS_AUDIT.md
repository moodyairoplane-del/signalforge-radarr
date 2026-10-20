# SignalForge Radar — Production Readiness Audit

Audit date: 2026-10-20  
Repository reviewed: `moodyairoplane-del/signalforge-radarr`  
Current entry point: `index.html`

## Verified from the current source

- The app is a single static HTML document with inline CSS and JavaScript.
- The JavaScript contains eight illustrative prospect records. They are explicitly fictional/sample records, not live leads.
- Search filters those local records by company, sector, type, and signal text.
- Type and status dropdowns filter the same local array.
- Selecting a row shows a local detail panel with rationale, next research action, evidence note, and illustrative fit score.
- Navigation buttons scroll between sections / change the workspace labels; they do not load separate data sources.
- The research-brief modal builds a text brief from the chosen goal, market, and list size. The copy button uses the browser clipboard API with a fallback.
- There is no observed `fetch()` data request, API client, database integration, persistent storage, authentication, user account, billing, or membership implementation in this file.

## Feature status

| Feature | Current status | Production requirement |
|---|---|---|
| Responsive workspace UI | Present in static HTML/CSS | Test on real mobile and desktop browsers |
| Prospect search | Works on local sample array by code inspection | Add tests; search real server-side records once backend exists |
| Type/status filters | Works on local sample array by code inspection | Add combined-filter and empty-state tests |
| Prospect detail inspection | Local details only | Store evidence URLs, checked dates, verification state, and provenance per record |
| Business Signals | Example/illustrative content | Connect to permitted, reliable sources and show source/date for each signal |
| Fit score | Illustrative numeric score | Define documented scoring rules; do not present as validated prediction |
| Research brief | Generates a prompt/template | Add real research job execution only after a source/provider is chosen |
| Copy brief | Clipboard API plus fallback in code | Test in deployed HTTPS browser and report copy failures accurately |
| Login / signup / password reset | Not implemented | Add authentication provider, secure session handling, and account flows |
| User dashboard / saved searches | Not implemented | Add backend persistence and per-user access controls |
| Membership / subscription | Not implemented | Define plans and permissions; add payment provider only after owner selects one |
| Admin / client test access | Not implemented | Role-based authorization, test account, and safe demo dataset |
| Live data ingestion | Not implemented | Select data providers, comply with terms/rate limits, validate records, schedule refresh |
| Data storage / audit trail | Not implemented | Database schema, migrations, provenance, last-checked timestamps, retention policy |
| Monitoring / error reporting | Not implemented | Server logs, health checks, and visible failure states |
| Automated tests / CI | Not observed in this single-file app | Add unit and end-to-end checks plus deployment verification |

## Recommended implementation sequence

1. **Truthful demo baseline:** preserve clear sample/not-live labels; remove any production claim that is not backed by a real source and timestamp.
2. **Quality and accessibility:** cover search/filter combinations, selected-row state, keyboard/modal behavior, clipboard failure, small screens, and browser console errors with tests.
3. **Backend foundation:** choose a stack and create server-side APIs and a database. Keep secrets on the server; never put provider keys in browser JavaScript.
4. **Real-data connector:** select an allowed provider/source, normalize records, store source URLs and publication/check dates, deduplicate, and distinguish verified from unverified signals.
5. **Authentication and workspace:** sign-up, login, reset, user-specific saved searches and briefs, authorization checks.
6. **Client testing and memberships:** controlled test accounts, role/plan permissions, usage limits, and payment integration only if required.
7. **Production validation:** verify build/deployment, live API responses, error states, data provenance, security boundaries, mobile behavior, and a clean smoke-test report.

## Release gate

Do not advertise live prospect discovery, verified leads, automated research, subscriptions, or secure accounts until each corresponding production implementation has been tested on the deployed site. A working local filter over sample records is not evidence of live data access.
