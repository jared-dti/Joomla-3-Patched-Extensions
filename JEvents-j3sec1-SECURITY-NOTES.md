# JEvents 3.6.82.3-j3sec1 security notes

This package is an independent Joomla 3 / PHP 7.4 maintenance build. It is not part of the Regular Labs bundle or the jDownloads package.

## Research result

The supplied outer package is labelled 3.6.82.2, but its core component is 3.6.82.1. That distinction matters: CVE-2025-49467 is an unauthenticated SQL injection in JEvents date-range listing actions affecting releases through 3.6.82 and again 3.6.83 through 3.6.87. The published fixed branches are 3.6.82.1 and 3.6.88 or later.

- Belgian CCB advisory: https://ccb.belgium.be/advisories/warning-critical-sql-injection-jevents-patch-immediately
- Joomla Vulnerable Extensions List: https://extensions.joomla.org/vulnerable-extensions/vulnerable/jevents-3-6-87-sql-injection/
- CVE record: https://app.opencve.io/cve/CVE-2025-49467

The audited date-range query implementation in the supplied 3.6.82.1 component matches the corresponding implementation in the supplied 3.6.102 reference. Inputs are converted to date components and query dates are quoted before SQL construction. This patch retains that hotfix and adds request-size/date-window controls in front of the JSON range endpoints.

Two older issue classes were also checked:

- CVE-2015-7340 (`evid` SQL injection) predates this code. Current event IDs and calendar IDs are converted to integers before use: https://nvd.nist.gov/vuln/detail/CVE-2015-7340
- Academic testing previously found a reflected search XSS and an `ics_id` SQL injection in older JEvents builds. In this base, search output is HTML-escaped and `ics_id` is integer-cast. The paper is available at https://informatik.rub.de/veroeffentlichungenbkp/nds/veroeffentlichungen/2021/pdfs/2021_Over_100_Bugs_in_a_Row__Security_Analysis_of_the_Top_Rated_Joomla_Extensions.pdf

No credible public report of a mass compromise campaign specifically targeting 3.6.82.1 was found during this review. That is not evidence that exploitation is impossible; the known critical vulnerability is unauthenticated and automatable in affected builds.

## j3sec1 changes

- Exact installer guards: Joomla 3.x and PHP 7.4.x only.
- Removed the vendor update server so this maintenance build is not silently replaced by an incompatible branch.
- Removed standalone Joomla 4 CSS/LESS assets and Joomla 4 installer behavior.
- Public event/calendar detail views and exports remain available.
- All core frontend create, edit, save, publish, delete, repeat-edit and calendar-import controller routes return HTTP 403.
- Frontend permission helpers return false for authoring operations, removing ordinary add/edit controls and blocking the conflict-check save simulation.
- Administrator event management remains enabled.
- Administrator mutation tasks require a valid Joomla request token, closing inconsistent legacy CSRF coverage.
- Event descriptions, extra information and translated event fields use Joomla's Safe HTML filter unless the existing `allowraw` administrator option is deliberately enabled.
- Public aggregate calendar pages are restricted to the current year minus two through the current year plus five, further narrowed by existing JEvents earliest/latest-year settings.
- Invalid, impossible and out-of-window aggregate dates return HTTP 404 instead of resolving to duplicate calendar pages.
- Aggregate date pages send `X-Robots-Tag: noindex, follow` and equivalent HTML metadata. Event detail pages remain indexable.
- Public JSON ranges must be valid ISO dates, remain inside the public year window, and span no more than 370 days.
- Fixed two legacy input-access typos encountered in administrator calendar/event paths.

The public year window affects browsing/navigation only. It does not restrict dates administrators can create, edit or import.

## Validation

- 590 PHP files linted with PHP 7.4.33: 0 failures
- 69 XML files parsed: 0 failures
- 17 nested ZIP packages opened successfully
- 0 unsafe absolute or parent-traversal archive paths
- 0 standalone `j4.css` / `j4.less` payloads
- Outer package SHA-256: `3910ab5aa966b3d5a33c85a1086667ebf33348d0ec3989db68c6ebf6592b76a5`

This package closes the reviewed extension paths. It does not remove persistence, malicious users, scheduled tasks, altered templates, web shells or stolen credentials from a site that was already compromised.
