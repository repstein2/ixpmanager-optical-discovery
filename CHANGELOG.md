# Changelog

## v1.0.0 - Initial Public Release

Developed by Randy Epstein (randy@communityix.org)
and Community IX (https://communityix.org).

### Added

- Arista ENTITY-MIB optical media discovery.
- Integration with IXP Manager SNMP switch polling.
- Per-switch feature enablement.
- Exact interface and immediate-parent matching.
- Recognition of Arista AMP-ZR amplifier modules.
- Unknown and conflicting media safeguards.
- Discovery failure handling.
- Synthetic parser and discovery regression tests.

### Validation

- IXP Manager v7.3.1.
- 28 Arista switches across three Community IX exchanges.
- 204 media classification changes.
- Zero unexpected interface inventory changes.
- 21 synthetic regression tests passed.
- Sanitized SNMP exception handling.
- Added interface-mapping regression coverage.
- Added synthetic exception confidentiality testing.
- Independent clean-install patch verification.
- Gitleaks scan completed with zero findings.

### Limitations

See COMPATIBILITY.md for tested platforms,
management protocol limitations, and future capabilities.

### Release Status

Initial public release of Arista Optical Discovery for IXP Manager.
