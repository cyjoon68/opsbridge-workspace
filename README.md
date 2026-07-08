# OpsBridge Workspace

Public portfolio workspace for a Frontend / Product Engineer application.

## Repository topology

- Organization workspace: `https://github.com/opsbridge-labs/opsbridge-workspace`
- Personal mirror: `https://github.com/cyjoon68/opsbridge-workspace`
- App submodule: `https://github.com/opsbridge-labs/opsbridge-fe`
- API submodule: `https://github.com/opsbridge-labs/opsbridge-be`
- Default branch: `develop`
- `main` branch is retained.

## Implementation scope

- FE: React, TypeScript, `ky`, TanStack Query, D3, jQuery/Ajax compatibility, Playwright smoke test.
- BE: Python Flask RESTful API, MVC, PostgreSQL, SQLAlchemy 2.0 Async Mode, pytest, OpenAPI, k6.
- demo-backend conversion: auth/user/phone/token ideas converted to REST. GraphQL is not used.

## Local commands

```bash
git submodule update --init --recursive
cd opsbridge-fe && npm install && npm run build
cd ../opsbridge-be && python -m venv .venv && . .venv/bin/activate && pip install -r requirements.txt && pytest
```

## Screenshot

![OpsBridge dashboard](docs/screenshots/dashboard.png)

## API example

```http
POST /api/auth/login
POST /api/auth/refresh
GET /api/dashboard
PATCH /api/events/{event_id}/status
```

## ERD

```mermaid
erDiagram
  admin_users ||--o{ refresh_tokens : owns
  admin_users ||--o{ change_requests : creates
  change_requests ||--o{ approvals : receives
  change_requests ||--o{ audit_logs : writes
```

## Verification

- `npm install && npm run build`: passed
- `npm audit --audit-level=critical`: passed, 0 vulnerabilities
- `npm run test:e2e`: passed, 1 Playwright smoke test
- `pip install -r requirements.txt && pytest`: passed, 2 tests
- Screenshot captured with Playwright
