# Security Assessment Report

**Generated:** 2026-11-03T21:28:06.696339+00:00

Minimum CVE severity: **high**. All six raw dependency advisories are preserved; two medium advisories are excluded from this merged report. Dependency presence does not establish application exploitability.

## Summary

| Metric | Count |
|--------|-------|
| TotalFindings | 7 |
| CveCount | 4 |
| CweCount | 3 |
| TotalRulesAssessed | 59 |
| RulesPassed | 56 |

### By Severity

| Severity | Count |
|----------|-------|
| mandatory | 4 |
| optional | 2 |
| potential | 1 |

## CVE Findings (Dependency Vulnerabilities)

### CVE-2026-106110: ImageSharp: TIFF CCITT T4 encoder can write past its compressed output buffer
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** PhotoAlbum/PhotoAlbum.csproj:16

[CVE-2026-106110](https://github.com/advisories/GHSA-j9gm-c75j-xc9q): ImageSharp: TIFF CCITT T4 encoder can write past its compressed output buffer

Severity: HIGH

Affected dependencies:
  - SixLabors.ImageSharp:3.1.11 (declared at PhotoAlbum/PhotoAlbum.csproj:16; transitive in PhotoAlbum.Tests/PhotoAlbum.Tests.csproj; resolved inventory: PhotoAlbum.Tests/obj/project.assets.json (not an explicit project declaration)); affected range: >= 2.0.0, < 3.2.0

Recommended fix:
  - Upgrade SixLabors.ImageSharp to 3.2.0 or later within the applicable supported release line.

Dependency inventory match only; application-level exploitability was not tested. Patched-version recommendations use structured GitHub advisory metadata; verify current vendor guidance before upgrading.

### CVE-2026-106113: ImageSharp: HistogramEqualization uses an unvalidated luminance as an unchecked histogram index
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** PhotoAlbum/PhotoAlbum.csproj:16

[CVE-2026-106113](https://github.com/advisories/GHSA-j3p4-wp97-rph4): ImageSharp: HistogramEqualization uses an unvalidated luminance as an unchecked histogram index

Severity: HIGH

Affected dependencies:
  - SixLabors.ImageSharp:3.1.11 (declared at PhotoAlbum/PhotoAlbum.csproj:16; transitive in PhotoAlbum.Tests/PhotoAlbum.Tests.csproj; resolved inventory: PhotoAlbum.Tests/obj/project.assets.json (not an explicit project declaration)); affected range: >= 2.0.0, < 3.2.0

Recommended fix:
  - Upgrade SixLabors.ImageSharp to 3.2.0 or later within the applicable supported release line.

Dependency inventory match only; application-level exploitability was not tested. Patched-version recommendations use structured GitHub advisory metadata; verify current vendor guidance before upgrading.

### CVE-2026-106115: ImageSharp: TIFF CCITT T6 encoder writes beyond an undersized output buffer
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** PhotoAlbum/PhotoAlbum.csproj:16

[CVE-2026-106115](https://github.com/advisories/GHSA-jjfr-hcj7-qf5w): ImageSharp: TIFF CCITT T6 encoder writes beyond an undersized output buffer

Severity: HIGH

Affected dependencies:
  - SixLabors.ImageSharp:3.1.11 (declared at PhotoAlbum/PhotoAlbum.csproj:16; transitive in PhotoAlbum.Tests/PhotoAlbum.Tests.csproj; resolved inventory: PhotoAlbum.Tests/obj/project.assets.json (not an explicit project declaration)); affected range: >= 2.1.0, < 3.2.0

Recommended fix:
  - Upgrade SixLabors.ImageSharp to 3.2.0 or later within the applicable supported release line.

Dependency inventory match only; application-level exploitability was not tested. Patched-version recommendations use structured GitHub advisory metadata; verify current vendor guidance before upgrading.

### CVE-2026-106118: ImageSharp: Tiled fax TIFF: tile buffer sized by TileWidth but fax decompressor writes scanlines of ImageWidth — heap OOB write
- **Category:** CVE
- **Severity:** mandatory
- **Story Points:** 1
- **Files:** PhotoAlbum/PhotoAlbum.csproj:16

[CVE-2026-106118](https://github.com/advisories/GHSA-v76p-62qx-wwq2): ImageSharp: Tiled fax TIFF: tile buffer sized by TileWidth but fax decompressor writes scanlines of ImageWidth — heap OOB write

Severity: HIGH

Affected dependencies:
  - SixLabors.ImageSharp:3.1.11 (declared at PhotoAlbum/PhotoAlbum.csproj:16; transitive in PhotoAlbum.Tests/PhotoAlbum.Tests.csproj; resolved inventory: PhotoAlbum.Tests/obj/project.assets.json (not an explicit project declaration)); affected range: >= 3.0.0, < 3.2.0

Recommended fix:
  - Upgrade SixLabors.ImageSharp to 3.2.0 or later within the applicable supported release line.

Dependency inventory match only; application-level exploitability was not tested. Patched-version recommendations use structured GitHub advisory metadata; verify current vendor guidance before upgrading.

## CWE Findings (Code-Level Vulnerabilities)

### CWE-259: Use of Hard-coded Password
- **Category:** Credentials & Secrets
- **Severity:** optional
- **Story Points:** 5
- **Files:** infra/main.bicep:59, infra/main.bicep:65-68

SQL provisioning derives the administrator password from a source-defined literal template and deterministic uniqueString(resource-group ID, environment name). The resulting credential is reproducible from deployment metadata and source rather than secret random input; the credential value is intentionally not reproduced.

### CWE-778: Insufficient Logging
- **Category:** Credentials & Secrets
- **Severity:** potential
- **Story Points:** 3
- **Files:** PhotoAlbum/Pages/Login.cshtml.cs:40-58, PhotoAlbum/appsettings.json:16-20

LoginModel.OnPostAsync returns failed authentication results without recording an application security event; the model has no logger or audit integration. Default application configuration suppresses ASP.NET Core informational messages. This is a confirmed logging weakness, not an independently exploitable vulnerability; external monitoring and deployed logging overrides were not verified.

### CWE-798: Use of Hard-coded Credentials
- **Category:** Credentials & Secrets
- **Severity:** optional
- **Story Points:** 5
- **Files:** infra/main.bicep:59, infra/main.bicep:65-68

SQL administrator provisioning consumes a credential constructed from a code-defined literal template and deterministic deployment identifiers. A reader of the source with resource-group and environment metadata can reconstruct it. Credential values are withheld.

## Scope and limitations

All six CWE categories were assessed sequentially against first-party production sources and applicable deployment configuration. Tests, generated code and vendored implementations were excluded. NOT_FOUND means no confirmed pattern was identified, not proof of absence. No live deployment, fuzzing or runtime exploit testing was performed. The two credential CWE entries describe the same SQL provisioning pattern; insufficient login logging is a weakness, not an independently exploitable vulnerability. No application remediation was performed.
