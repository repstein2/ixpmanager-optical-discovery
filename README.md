# Arista Optical Discovery v2 for IXP Manager

Automatic optical media discovery for Arista Ethernet switches
using ENTITY-MIB, integrated with IXP Manager's existing SNMP
switch polling functionality.

## Authors and Contributors

**Randy Epstein** - randy@communityix.org

**Community IX** - https://communityix.org

GitHub: https://github.com/repstein2

Developed and production-tested by Randy Epstein and Community IX.

## Overview

Optical Discovery v2 supplements IXP Manager's existing MAU-MIB
media classification using Arista ENTITY-MIB descriptions.

The implementation preserves existing valid MAU classifications
and uses ENTITY-MIB information when the MAU classification is
empty or unrecognized.

Discovery is optional, disabled by default, and restricted to
explicitly configured Arista switches.

## Features

- Automatic optical media identification via ENTITY-MIB.
- Support for Arista Ethernet interface descriptions.
- Recognition of tested 10G, 40G, 100G and 400G media.
- Nested physical interface and breakout-aware matching.
- Recognition of Arista AMP-ZR optical amplifier modules.
- Rejection of unknown and conflicting media descriptions.
- Preservation of existing valid MAU classifications.
- Graceful handling of ENTITY-MIB discovery failures.
- Per-switch enablement through environment configuration.

## Compatibility

Developed and tested against IXP Manager v7.3.1.

Production validation was performed across 28 Arista switches
operated by Community IX at three Internet exchanges.

The deployment populated 204 previously empty media
classifications without unexpected interface inventory changes
in the recorded baseline comparisons.

See COMPATIBILITY.md for tested capabilities and limitations.

## Installation

See INSTALL.md for installation, configuration, verification,
and rollback instructions.

The patch is located at:

patches/optical-discovery-v2.patch

## Testing

Synthetic regression tests are provided under tests/.

These tests do not require production credentials, a database,
or physical Arista hardware.

See TESTING.md for instructions and validation results.

## Known Limitations

- IPv6-only SNMP management has not been validated.
- IPv4-managed switches with IPv4, IPv6, or dual-stack peering
  are compatible with the tested design.
- OSFP hardware has not been validated.
- Future 800G and 1.6T media recognition depends on platform
  ENTITY-MIB reporting and requires additional testing.
- Physical transceiver removal has not been hardware-tested.
- DWDM frequency, wavelength, and channel discovery are not
  implemented in this release.
- Support currently targets Arista ENTITY-MIB descriptions.

## Future Development

See ROADMAP.md for proposed enhancements, including:

- Fixed and tunable DWDM wavelength/frequency discovery.
- Tunable 10G, 100G, 400G, 800G and future optical modules.
- Coherent and non-coherent optical technologies.
- OSFP and CMIS-based transceiver discovery.
- Optical amplifier monitoring.
- Digital optical monitoring and optical health information.
- Additional vendor support.

These are proposed enhancements, not guaranteed features.

## License

GNU General Public License version 2.0.

This project builds upon IXP Manager and preserves applicable
upstream licensing and copyright requirements.

## Upstream Contribution

This project is intended for contribution to the IXP Manager
open-source community.

The independent project repository is maintained
under Randy Epstein's personal GitHub account:

https://github.com/repstein2/ixpmanager-optical-discovery
