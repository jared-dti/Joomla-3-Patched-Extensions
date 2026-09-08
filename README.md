# Joomla 3 Patched Regular Labs Extensions

Security-maintenance builds for the supplied Joomla 3 / PHP 7.4 Regular Labs extension packages.

## Download

For the complete handoff, download `Joomla-3-Patched-Extensions-j3sec1-complete.zip` from the repository root. Installable Joomla packages are also available individually in `installers/`.

## Contents

- `installers/` — five Joomla package ZIPs ready for first-site testing
- `source/` — complete patched installer source for each extension
- `tests/` — static policy and Sourcerer adversarial tests
- `docs/README-FIRST.md` — installation order and functional acceptance tests
- `docs/SECURITY-CHANGES.md` — patch and CVE mapping
- `docs/VALIDATION-REPORT.md` — completed validation and its boundaries
- `docs/SHA256SUMS.txt` — SHA-256 hashes for the five Joomla installers

## Retained functionality

- Advanced Module Manager: module assignments
- Modules Anywhere: embedding published, visitor-authorized modules, including form modules
- Cache Cleaner: Joomla cache and Cloudflare purge
- ReReplacer: ordinary text and regular-expression replacement, with PHP/XML execution disabled
- Sourcerer: stored article code with Super User provenance and explicitly allowlisted Custom HTML modules

Read `docs/README-FIRST.md` before installing. These packages close the reviewed extension paths but do not remove persistence from a site that was already compromised.

Build identifier: `j3sec1`  
Build date: 8 September 2026

