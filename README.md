# Joomla 3 Patched Regular Labs Extensions

Joomla 3 / PHP 7.4 security-maintenance builds for the five supplied Regular Labs extensions.

## Download

Download `regularlabs-j3-security-maintenance-j3sec2-bundle.zip` from the repository root. It contains:

- five directly installable Joomla 3 package ZIPs in `installers/`
- the complete Joomla-3-only patched package source in `source/`
- security and adversarial tests in `tests/`
- installation instructions, security changes, validation results, and hashes in `docs/`

Read `docs/README-FIRST.md` inside the bundle before installing.

## Retained functionality

- Advanced Module Manager: module assignments
- Modules Anywhere: embedding published, visitor-authorized modules, including form modules
- Cache Cleaner: Joomla cache and Cloudflare purge
- ReReplacer: ordinary text and regular-expression replacement, with PHP/XML execution disabled
- Sourcerer: stored article code with Super User provenance and explicitly allowlisted Custom HTML modules

## Validation summary

- 1,415 PHP files passed PHP 7.4.33 syntax checks
- 49 XML manifests passed parsing
- 78 static security assertions passed
- 11 Sourcerer adversarial request-origin tests passed
- every installer passed byte-for-byte ZIP round-trip verification
- zero non-Joomla-3 payload entries

Bundle SHA-256: `1e11ec88615d732a236b42c8873bc6c613eaf14ee57f9e6f42bf42c29769ccdc`

These packages close the reviewed extension paths but do not remove persistence from a site that was already compromised.

Build identifier: `j3sec2`  
Build date: 8 September 2026
