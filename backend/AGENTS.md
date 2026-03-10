# Backend Agent Instructions

## Scope
Applies to backend services and backend-supporting files under this directory.

## Backend principles
- Follow current service architecture and established Spring patterns.
- Prefer constructor injection.
- Keep controller, service, repository, and integration responsibilities separate.
- Preserve backward compatibility for public APIs unless change is explicitly requested.
- Favor explicit validation and predictable error responses.

## API expectations
- Validate request inputs clearly and early.
- Keep DTOs separate from persistence models unless the codebase already intentionally combines them.
- For API changes, note:
  - request/response impact
  - consumer impact
  - versioning or backward compatibility
  - validation changes
  - documentation/test updates

## Data and persistence
- Avoid query changes without checking indexes, filters, and expected data volume.
- Do not introduce N+1 behavior.
- Call out migration needs clearly.
- Treat audit and compliance-related fields carefully.

## Logging and observability
- Use existing logging style.
- Do not log secrets or sensitive payloads.
- Add enough logs/metrics to support troubleshooting without creating noise.

## Testing
- Prefer unit tests for business logic and integration tests where data or framework behavior matters.
- Reuse existing test fixtures and conventions.
- If mocking is already overused in the codebase, avoid making it worse.

## Performance
- Flag potentially expensive loops, remote calls, and serialization-heavy flows.
- Mention caching, batching, retries, and timeout concerns when relevant.

## Security
- Treat auth, entitlement, input validation, file handling, and external integrations as high-risk areas.
- For security-sensitive code, slow down and explain reasoning before changing logic.