# Optical Discovery Development Roadmap

Developed by Randy Epstein (randy@communityix.org)
and Community IX (https://communityix.org).

This roadmap describes potential future enhancements
to Optical Discovery for IXP Manager.

These are development targets, not functionality
guaranteed by the current release.

## Phase 1: DWDM Wavelength and Frequency Discovery

Target capabilities:

- Configured optical frequency.
- Operational optical frequency.
- Wavelength in nanometers.
- ITU-T channel identification.
- Channel spacing and tuning range.
- Fixed versus tunable optical modules.
- Detection of configuration/operational mismatches.

Support should include fixed and tunable DWDM optics
at 10G, 100G, 400G, 800G, and future speeds.

Tunability and coherent transmission are independent
characteristics and must be identified separately.

Do not universally infer wavelengths from model numbers.
Some vendor-specific model suffixes identify channels,
but actual operational values should be queried.

## Phase 2: Optical Module Inventory

Target capabilities:

- Manufacturer and vendor information.
- Model and part number.
- Serial number.
- Hardware and firmware revisions.
- Form factor identification.
- QSFP28, QSFP-DD, OSFP, and future modules.
- Physical-to-logical breakout relationships.

Future support may use ENTITY-MIB, vendor-specific MIBs,
CMIS, and other applicable management interfaces.

## Phase 3: Optical Monitoring

Target capabilities:

- Transmit optical power.
- Receive optical power.
- Module temperature.
- Supply voltage.
- Laser bias current.
- Optical alarm and warning thresholds.
- Historical measurements and trending.

Potential integration with IXP Manager monitoring
and visualization interfaces.

## Phase 4: Coherent Optics and Amplifiers

Target capabilities:

- Coherent module operational status.
- Configured and operational optical frequency.
- Optical amplifier identification.
- Amplifier gain.
- Optical input/output power.
- Line-system monitoring where supported.

Arista AMP-ZR identification is supported in v2.
Amplifier telemetry is not currently implemented.

## Phase 5: Platform and Vendor Expansion

Potential enhancements:

- OSFP hardware validation.
- 800G and 1.6T platform testing.
- IPv6-only SNMP management validation.
- Additional Arista EOS/platform combinations.
- Multi-vendor optical discovery.
- Expanded breakout interface handling.
- Community-contributed hardware test fixtures.

Support depends on actual management interfaces,
vendor reporting formats, and hardware validation.

## Design Principles

Future enhancements should preserve:

- Optional feature enablement.
- Existing valid media classifications.
- Safe failure behavior.
- Compatibility with normal IXP Manager polling.
- Separation of physical media and logical interfaces.
- Clear distinction between tested and proposed features.
- No hardcoded organization-specific infrastructure.

## Community Contributions

Hardware testing, feature suggestions, and code
contributions from IXP operators are welcome.

Project maintainer:
Randy Epstein - randy@communityix.org

Community IX:
https://communityix.org
