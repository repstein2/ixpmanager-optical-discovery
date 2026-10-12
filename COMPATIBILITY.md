# Compatibility and Known Limitations

## Supported Software

- IXP Manager v7.3.1: production validated.
- PHP 8.4: tested in the development environment.
- Other IXP Manager versions: not validated.

## Supported Switch Vendors

Optical Discovery v2 currently supports Arista switches
using ENTITY-MIB physical descriptions.

Other vendors are not supported by this implementation.

## Production Validation

The implementation was validated by Community IX across:

- FL-IX: 14 Arista switches.
- CIX-ATL: 12 Arista switches.
- CIX-NoVA: 2 Arista switches.

Total: 28 switches.

The recorded baseline comparisons identified 204 media
classification changes and zero unexpected changes to
interface inventories, indexes, names, or speeds.

## Tested Media Types

Production observations included:

- 10GBASE-LR, ER, and ZR.
- 40GBASE-PLR4 and PSM4.
- 100GBASE-LR and LR4.
- 400GBASE-AR8, SR8, FR4, LR4, and ZR.
- Arista AMP-ZR optical amplifier modules.

Recognition depends on the media descriptions returned
by the switch through ENTITY-MIB.

## Interface Mapping

The implementation attempts an exact interface match
first, followed by its immediate parent interface.

This supports tested Arista interface naming patterns,
including Ethernet interfaces with breakout suffixes.

It does not guarantee correct behavior for arbitrary
multi-level breakout hierarchies.

## IPv4 and IPv6

Optical media discovery is independent of the IP
protocols carried over the Ethernet interface.

The following configurations are compatible with
the tested design:

- IPv4 SNMP management with IPv4 peering.
- IPv4 SNMP management with IPv6 peering.
- IPv4 SNMP management with dual-stack peering.

IPv6-only SNMP management has not been validated.
Support must not be assumed without additional testing.

## OSFP and Future Speeds

The parser is not inherently restricted to QSFP-DD.

However, OSFP hardware has not been validated.

800G and 1.6T discovery is not guaranteed. Support
depends on switch platform capabilities, ENTITY-MIB
reporting, vendor description formats, and testing.

## Optical Amplifiers

Arista QSFP-AMP-ZR modules were successfully identified
as AMP-ZR in production.

Amplifier gain, optical input/output power, and
operational telemetry are not implemented.

## Transceiver Removal and Replacement

Synthetic tests cover parsing and discovery responses.

Physical transceiver removal and replacement have
not been validated through hardware testing.

Successful empty ENTITY-MIB discovery must not be
confused with an SNMP discovery failure.

## DWDM Wavelength Discovery

This release identifies optical media classifications.

It does not discover:

- Configured or operational optical frequency.
- Wavelength in nanometers.
- ITU channel or channel spacing.
- Tunability or supported tuning range.

These capabilities are targeted for future development.

## Operational Safeguards

- Disabled by default.
- Explicit per-switch enablement.
- Arista vendor eligibility check.
- Existing valid MAU classifications preserved.
- Unknown media classifications ignored.
- Discovery failures handled without aborting
  the normal switch polling process.

## Limitations of Validation

Testing does not guarantee compatibility with every
Arista EOS version, platform, transceiver, or breakout
configuration.

Operators should test against their own equipment
before enabling discovery broadly.
