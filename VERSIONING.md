# Versioning and Release Management

## Project

Arista Optical Discovery for IXP Manager

Maintainer: Randy Epstein (randy@communityix.org)
Organization: Community IX (https://communityix.org)

Repository:
https://github.com/repstein2/ixpmanager-optical-discovery

## Versioning

This project uses Semantic Versioning.

MAJOR.MINOR.PATCH

Project versions are independent of IXP Manager versions.

MAJOR:
Breaking changes or incompatible architectural changes.

MINOR:
Backward-compatible functionality and enhancements.

PATCH:
Backward-compatible bug fixes and maintenance.

Pre-release identifiers:
rc.1, rc.2, rc.3, etc.

## Initial Release Plan

v0.9.0-rc.1:
Original validated five-file community candidate.

v0.9.0-rc.2:
Security improvements and additional regression tests.

v1.0.0:
First approved public stable release.

Future versions will be assigned based on actual changes.

## Git Branches

main:
Stable approved code.

feature/*:
New development.

fix/*:
Bug fixes.

release/*:
Release preparation when needed.

## Release Requirements

Every release must include:

- Version identification.
- Changelog updates.
- Compatibility documentation.
- Installation and rollback instructions.
- Passing regression tests.
- Clean patch applicability verification.
- Confidentiality and secret scanning.
- SHA-256 release checksums.
- Maintainer approval.

## Production Deployment

GitHub publication does not trigger production deployment.

FL-IX, CIX-ATL, and CIX-NoVA deployments must be
individually validated before changes are enabled.

Production code synchronization must be verified
using file checksums.

## Release Integrity

Published release tags must not be moved or reused.

Corrections require a new release version.

Release artifacts must match their published checksums.

## Security

Never publish:

- SNMP credentials.
- Environment files.
- SSH keys.
- Customer or member information.
- Internal management addresses.
- Production database exports.
- Confidential operational logs.

Synthetic test fixtures should be used whenever possible.

## Upstream Contributions

Contributions to IXP Manager should preserve upstream
licensing and copyright notices.

The independent GitHub repository may track releases
separately from upstream IXP Manager acceptance.

## Publication Approval

No public release, GitHub publication, or upstream
submission without explicit maintainer approval.
