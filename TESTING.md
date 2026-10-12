# Testing and Validation

## Project

Arista Optical Discovery v2 for IXP Manager

Developed by Randy Epstein (randy@communityix.org)
and Community IX (https://communityix.org).

## Production Validation

Optical Discovery v2 was deployed and tested across
three Community IX Internet exchanges.

| Exchange | Switches | Media Changes | Unexpected Changes |
|----------|----------|---------------|--------------------|
| FL-IX    | 14       | 98            | 0                  |
| CIX-NoVA | 2        | 0             | 0                  |
| CIX-ATL  | 12       | 106           | 0                  |
| Total    | 28       | 204           | 0                  |

Baseline comparisons checked:

- Switch-port inventory counts and identities.
- Interface indexes.
- Interface names.
- Interface speeds.
- Optical media classifications.

The production deployments used IXP Manager v7.3.1.

The five-file community patch excludes an unused
resolver present in the six-file production version.

The community patch was independently applied to a
clean IXP Manager v7.3.1 checkout and verified.

## Synthetic Regression Tests

The public package contains three dependency-free tests:

- tests/test-parser.php
- tests/test-discovery.php
- tests/test-interface-mapping.php

Parser tests: 6 passed.

Discovery and security tests: 5 passed.

Interface-mapping tests: 10 passed.

Total: 21 passed, 0 failed.

Interface-mapping tests exercise a copy of the
production matching algorithm rather than invoking
Switcher::snmpPollSwitchPorts() directly.

The security regression test verifies that fabricated
sensitive exception text is not returned by discovery.

These tests use synthetic data and do not connect
to switches, databases, or production services.

## Running the Tests

Apply the community patch to a compatible IXP Manager
v7.3.1 checkout.

Set IXPM_SOURCE_DIR to that checkout.

Example:

    IXPM_SOURCE_DIR=/path/to/ixp-manager \
      php tests/test-parser.php

    IXPM_SOURCE_DIR=/path/to/ixp-manager \
      php tests/test-discovery.php

Run the standalone interface-mapping test:

    php tests/test-interface-mapping.php

This test exercises a copy of the matching algorithm,
not the live Switcher integration.

No PHPUnit installation is required for these tests.

## Clean Installation Verification

The five-file patch was applied successfully to an
independent clean IXP Manager v7.3.1 worktree.

All five resulting files matched the release candidate.

All five PHP files passed syntax validation.

## Security Screening

The community patch was scanned using Gitleaks v8.30.1.

No potential secrets were reported in the final
isolated patch scan.

Automated scanning cannot guarantee the absence
of all confidential information.

## Known Testing Limitations

- Physical transceiver removal was not hardware-tested.
- IPv6-only SNMP management was not validated.
- OSFP hardware was not validated.
- 800G and 1.6T hardware was not validated.
- Not every Arista EOS version was tested.
- Synthetic tests do not cover every database update path.
- Future DWDM wavelength/frequency discovery is not
  implemented in this release.

## Community Testing

Additional testing by IXP operators is encouraged,
especially on different Arista platforms, EOS versions,
optical modules, and breakout configurations.

Please report reproducible issues without including
production credentials or confidential network data.
