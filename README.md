# Joomla 3 Patched Extensions

Joomla 3 / PHP 7.4 security-maintenance builds for extensions from separate vendors. The Regular Labs products are distributed together; jDownloads is distributed independently.

## Download

### Regular Labs

Download `regularlabs-j3-security-maintenance-j3sec2-bundle.zip`. It contains the five patched Regular Labs extensions, source, tests, documentation, and hashes.

### jDownloads

Download the directly installable standalone package:

`com_jdownloads_3.2.69.1-j3sec1_J3.zip`

This is a patched build of jDownloads 3.2.69 for Joomla 3 and PHP 7.4. It is not bundled with the Regular Labs products.

The standalone installer contains:

- the complete jDownloads component installation payload
- Joomla 3-only compatibility guards
- the jDownloads security backports described below

## Retained functionality

- Advanced Module Manager: module assignments
- Modules Anywhere: embedding published, visitor-authorized modules, including form modules
- Cache Cleaner: Joomla cache and Cloudflare purge
- ReReplacer: ordinary text and regular-expression replacement, with PHP/XML execution disabled
- Sourcerer: stored article code with Super User provenance and explicitly allowlisted Custom HTML modules
- jDownloads: existing public download/catalog functionality and administrator-managed uploads; every frontend upload/create/edit/delete route is disabled

## Validation summary

- jDownloads installer: 1,260 files passed byte-for-byte ZIP/source verification
- jDownloads PHP files passed PHP 7.4.33 syntax checks
- jDownloads XML files passed parsing
- 83 jDownloads security assertions passed
- restore-parser dynamic tests accepted the valid legacy backup and rejected executable PHP
- Regular Labs j3sec2 validation remains documented inside its separate bundle

jDownloads SHA-256: `867c82b9e28d33df32f89cbce0e95e2ec286737cf3379f0bc0b5f935756a71a8`

Regular Labs bundle SHA-256: `1e11ec88615d732a236b42c8873bc6c613eaf14ee57f9e6f42bf42c29769ccdc`

These packages close the reviewed extension paths but do not remove persistence from a site that was already compromised.

Build identifiers: Regular Labs `j3sec2`; jDownloads `j3sec1`  
Build date: 9 September 2026
