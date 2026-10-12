# Installation and Rollback

## Requirements

- IXP Manager v7.3.1.
- Supported Arista Ethernet switch.
- Working SNMP management connectivity.
- ENTITY-MIB access.
- Appropriate filesystem and database backups.

Other IXP Manager versions have not been validated.

## Before Installation

Review COMPATIBILITY.md and TESTING.md.

Back up the IXP Manager installation, including:

- Modified application files.
- Custom templates and skins.
- Environment configuration.
- Database and switch-port inventory.

Do not publish backups or production configuration.

## Installation

The patch is provided at:

patches/optical-discovery-v2.patch

From the IXP Manager installation directory:

    git apply --check /path/to/optical-discovery-v2.patch

If the check fails, stop and investigate.
Do not force the patch onto modified application files.

After successful validation:

    git apply /path/to/optical-discovery-v2.patch

Verify PHP syntax for the modified and added files.

## Configuration

Discovery is disabled by default.

Enable it through the IXP Manager environment:

    IXPM_OPTICS_ENABLED=true
    IXPM_OPTICS_SWITCH_IDS=1

Replace 1 with the actual IXP Manager switch ID.

Multiple switch IDs may be configured:

    IXPM_OPTICS_SWITCH_IDS=1,2,3

Switch IDs are installation-specific.

The legacy single-switch setting is also recognized:

    IXPM_OPTICS_SWITCH_ID=1

When the switch ID list is populated, it takes precedence.

## Initial Validation

Enable one Arista switch initially.

Run a non-saving SNMP poll using the supported
IXP Manager switch polling command.

Review the discovered optical classifications.

Then perform a normal poll and compare the resulting
switch-port inventory against the pre-install baseline.

Verify:

- Interface count and identities.
- Interface names and indexes.
- Interface speeds.
- Newly populated media classifications.
- Absence of unexpected changes.

Expand the allowlist gradually after validation.

## Rollback

Disable discovery first:

    IXPM_OPTICS_ENABLED=false

Restore the original application files from the
pre-installation backup or reverse the patch only
after verifying that no unrelated modifications
would be overwritten.

For an otherwise clean patched checkout:

    git apply --reverse --check /path/to/optical-discovery-v2.patch

If the reverse check passes:

    git apply --reverse /path/to/optical-discovery-v2.patch

Do not use destructive Git reset commands against
an installation containing local customizations.

Disabling or reversing the code does not automatically
restore media values previously written to the database.

Use a verified database backup or controlled restoration
procedure if database-level rollback is required.

## Operational Notes

Discovery uses IXP Manager's existing SNMP polling.

No switch configuration changes are required by the
patch itself, assuming ENTITY-MIB is already accessible.

IPv6-only SNMP management has not been validated.

See COMPATIBILITY.md for additional limitations.
