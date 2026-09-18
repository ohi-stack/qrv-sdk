# QR-V™ Production SDK Build Contract

**Tracking:** qrv-sdk#1  
**API dependency:** ohi-stack/qrv-api#16

## Objective

Ship the canonical TypeScript/JavaScript integration layer for QR-V so organizations and approved software agents do not reimplement protocol status, error, authentication, retry, and idempotency behavior.

## Required client separation

### QRVPublicClient

No secret required.

Required capabilities:

- verify a QRVID
- retrieve publicly permitted record data
- retrieve service status
- generate canonical verification URL

### QRVIssuerClient

Server-side scoped credential required.

Required capabilities:

- create record
- retrieve record
- list/search records
- revoke record
- retrieve audit history
- retrieve issuer profile
- service-account/API credential operations when API contract is available

Privileged methods must never encourage embedding credentials in browser bundles.

## Type contract

SDK types should be generated from or validated against the normative OpenAPI contract where practical.

Verification must use a discriminated union that preserves deterministic QR-V states.

Network or server failures must remain distinguishable from `NOT_FOUND`.

## Transport requirements

- request ID propagation
- idempotency key support
- timeout and AbortSignal support
- bounded retries only when safe
- rate-limit metadata
- pagination helpers
- credential redaction in errors/logs
- package/version user-agent

## Webhook helpers

Provide server-side utilities for:

- signature verification
- timestamp tolerance
- event parsing
- replay protection examples

## Required examples

- public verify CLI
- issuer lifecycle in Node/TypeScript
- Next.js server/BFF example
- bounded-concurrency batch verification
- webhook consumer
- service-account/agent integration
- server-side WordPress/WooCommerce REST bridge guidance

## Acceptance coverage

Tests must cover:

- VERIFIED
- REVOKED
- EXPIRED
- NOT_FOUND
- malformed identifier
- unavailable/timeout/5xx
- 401/403
- rate limiting
- idempotency
- pagination
- secret redaction
- webhook signature success/failure/replay
- OpenAPI contract drift

## Release quality

Require lint, typecheck, tests, build, semantic versioning, changelog, supported Node matrix, and no real secrets in fixtures.
