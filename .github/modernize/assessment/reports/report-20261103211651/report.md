# PhotoAlbum

## Assessment Status and Limitations

- **Core assessment:** AppCAT 1.0.1127 produced 8 issue types and 28 incidents across 2 projects in Restricted privacy mode. It emitted `Error: Msbuild was not found.` for both projects on Linux; coverage may be incomplete and should be verified in a supported build environment.
- **.NET 10 upgrade assessment: blocked.** Target `net10.0` was requested, but the required MCP tools (`get_state`, `get_scenarios`, `initialize_scenario`, `generate_dotnet_upgrade_assessment`) are unavailable. No upgrade assessment was generated; this is not a successful compatibility assessment.
- **Security:** 119 dependency coordinates queried successfully; 6 raw advisories found. The **high** threshold includes 4 advisories and excludes 2 medium advisories. Six sequential CWE reviews assessed 59 rules: 3 FOUND, 56 NOT_FOUND.
- Dependency matches do not establish application exploitability. CWE-259 and CWE-798 describe the same SQL provisioning credential pattern; CWE-778 records missing failed-login audit logging, not an independently exploitable vulnerability. No credentials are reproduced and no application remediation was performed.
- Static review only; no live deployment, fuzzing or runtime exploit testing. CWE review excludes tests, generated code and vendored implementations; the core assessment includes both application and test projects. NOT_FOUND does not guarantee absence.
- [Assessment status](assessment-status.json), [security report](security/security-assessment.md), [raw CVE results](security/cve-assessment-result.json), and [dependency scan coverage](security/coverage-summary.json).

## Summary

| Metric | Value |
|--------|-------|
| Total Issues | 15 |
| Mandatory Blockers | 5 |
| Potential Issues | 5 |

## Component Information

| Property | Value |
|----------|-------|
| Language | C# |
| Frameworks | net9.0 |
| Build tools | MSBuild |

## Cloud Readiness Issues

| Issue Name | Criticality | Story Points | Occurrences |
|------------|-------------|--------------|-------------|
| Windows authentication detected | Mandatory | 3 | [1](#Windows_authentication_detected) |
| Local or network IO operations detected | Potential | 3 | [18](#Local_or_network_IO_operations_detected) |
| Local application configuration detected | Potential | 1 | [3](#Local_application_configuration_detected) |
| SQL database connection detected | Potential | 3 | [1](#SQL_database_connection_detected) |
| Connection string is detected | Potential | 3 | [1](#Connection_string_is_detected) |
| Hardcoded sensitive data detected | Optional | 3 | [2](#Hardcoded_sensitive_data_detected) |
| Static content detected | Optional | 3 | [1](#Static_content_detected) |
| Connection strings without configuration builders detected | Optional | 3 | [1](#Connection_strings_without_configuration_builders_detected) |

### Issue Details

<details id="Windows_authentication_detected">
<summary><b>Windows authentication detected</b> — affected files</summary>

- `PhotoAlbum/Web.config`

</details>

<details id="Local_or_network_IO_operations_detected">
<summary><b>Local or network IO operations detected</b> — affected files</summary>

- `PhotoAlbum/Program.cs (line 41)`
- `PhotoAlbum/Program.cs (line 39)`
- `PhotoAlbum/Pages/PhotoFile.cshtml.cs (line 60)`
- `PhotoAlbum/Pages/PhotoFile.cshtml.cs (line 66)`
- `PhotoAlbum/Pages/PhotoFile.cshtml.cs (line 58)`
- `PhotoAlbum/Services/PhotoService.cs (line 149)`
- `PhotoAlbum/Services/PhotoService.cs (line 200)`
- `PhotoAlbum/Services/PhotoService.cs (line 243)`
- `PhotoAlbum/Services/PhotoService.cs (line 147)`
- `PhotoAlbum/Services/PhotoService.cs (line 198)`
- `PhotoAlbum/Services/PhotoService.cs (line 241)`
- `PhotoAlbum/Services/PhotoService.cs (line 157)`
- `PhotoAlbum.Tests/Unit/Services/PhotoServiceTests.cs (line 30)`
- `PhotoAlbum.Tests/Unit/Services/PhotoServiceTests.cs (line 209)`
- `PhotoAlbum.Tests/Unit/Services/PhotoServiceTests.cs (line 123)`
- `PhotoAlbum.Tests/Unit/Services/PhotoServiceTests.cs (line 31)`
- `PhotoAlbum.Tests/Unit/Services/PhotoServiceTests.cs (line 248)`
- `PhotoAlbum.Tests/Unit/Services/PhotoServiceTests.cs (line 246)`

</details>

<details id="Local_application_configuration_detected">
<summary><b>Local application configuration detected</b> — affected files</summary>

- `PhotoAlbum/appsettings.json`
- `PhotoAlbum/appsettings.json`
- `PhotoAlbum/appsettings.json`

</details>

<details id="SQL_database_connection_detected">
<summary><b>SQL database connection detected</b> — affected files</summary>

- `PhotoAlbum/Web.config`

</details>

<details id="Connection_string_is_detected">
<summary><b>Connection string is detected</b> — affected files</summary>

- `PhotoAlbum/appsettings.json`

</details>

<details id="Hardcoded_sensitive_data_detected">
<summary><b>Hardcoded sensitive data detected</b> — affected files</summary>

- `PhotoAlbum/Pages/Login.cshtml.cs (line 55)`
- `PhotoAlbum/Pages/Login.cshtml.cs (line 42)`

</details>

<details id="Static_content_detected">
<summary><b>Static content detected</b> — affected files</summary>

- `PhotoAlbum/PhotoAlbum.csproj`

</details>

<details id="Connection_strings_without_configuration_builders_detected">
<summary><b>Connection strings without configuration builders detected</b> — affected files</summary>

- `PhotoAlbum/Web.config`

</details>

## Security Issues

> **Note:** These issues were generated by AI and may contain inaccuracies or incomplete information. Please review carefully.

| Issue Name | Criticality | Story Points | Files |
|------------|-------------|--------------|-------|
| CVE-2026-106110: ImageSharp: TIFF CCITT T4 encoder can write past its compressed output buffer | Mandatory | 1 | [1](#CVE-2026-106110_ImageSharp_TIFF_CCITT_T4_encoder_can_write_past_its_compressed_output_buffer) |
| CVE-2026-106113: ImageSharp: HistogramEqualization uses an unvalidated luminance as an unchecked histogram index | Mandatory | 1 | [1](#CVE-2026-106113_ImageSharp_HistogramEqualization_uses_an_unvalidated_luminance_as_an_unchecked_histogram_index) |
| CVE-2026-106115: ImageSharp: TIFF CCITT T6 encoder writes beyond an undersized output buffer | Mandatory | 1 | [1](#CVE-2026-106115_ImageSharp_TIFF_CCITT_T6_encoder_writes_beyond_an_undersized_output_buffer) |
| CVE-2026-106118: ImageSharp: Tiled fax TIFF: tile buffer sized by TileWidth but fax decompressor writes scanlines of ImageWidth — heap OOB write | Mandatory | 1 | [1](#CVE-2026-106118_ImageSharp_Tiled_fax_TIFF_tile_buffer_sized_by_TileWidth_but_fax_decompressor_writes_scanlines_of_ImageWidth_heap_OOB_write) |
| CWE-778: Insufficient Logging | Potential | 3 | [2](#CWE-778_Insufficient_Logging) |
| CWE-259: Use of Hard-coded Password | Optional | 5 | [2](#CWE-259_Use_of_Hard-coded_Password) |
| CWE-798: Use of Hard-coded Credentials | Optional | 5 | [2](#CWE-798_Use_of_Hard-coded_Credentials) |

### Security Issue Details

<details id="CVE-2026-106110_ImageSharp_TIFF_CCITT_T4_encoder_can_write_past_its_compressed_output_buffer">
<summary><b>CVE-2026-106110: ImageSharp: TIFF CCITT T4 encoder can write past its compressed output buffer</b> — affected files</summary>

- `PhotoAlbum/PhotoAlbum.csproj:16`

</details>

<details id="CVE-2026-106113_ImageSharp_HistogramEqualization_uses_an_unvalidated_luminance_as_an_unchecked_histogram_index">
<summary><b>CVE-2026-106113: ImageSharp: HistogramEqualization uses an unvalidated luminance as an unchecked histogram index</b> — affected files</summary>

- `PhotoAlbum/PhotoAlbum.csproj:16`

</details>

<details id="CVE-2026-106115_ImageSharp_TIFF_CCITT_T6_encoder_writes_beyond_an_undersized_output_buffer">
<summary><b>CVE-2026-106115: ImageSharp: TIFF CCITT T6 encoder writes beyond an undersized output buffer</b> — affected files</summary>

- `PhotoAlbum/PhotoAlbum.csproj:16`

</details>

<details id="CVE-2026-106118_ImageSharp_Tiled_fax_TIFF_tile_buffer_sized_by_TileWidth_but_fax_decompressor_writes_scanlines_of_ImageWidth_heap_OOB_write">
<summary><b>CVE-2026-106118: ImageSharp: Tiled fax TIFF: tile buffer sized by TileWidth but fax decompressor writes scanlines of ImageWidth — heap OOB write</b> — affected files</summary>

- `PhotoAlbum/PhotoAlbum.csproj:16`

</details>

<details id="CWE-778_Insufficient_Logging">
<summary><b>CWE-778: Insufficient Logging</b> — affected files</summary>

- `PhotoAlbum/Pages/Login.cshtml.cs:40-58`
- `PhotoAlbum/appsettings.json:16-20`

</details>

<details id="CWE-259_Use_of_Hard-coded_Password">
<summary><b>CWE-259: Use of Hard-coded Password</b> — affected files</summary>

- `infra/main.bicep:59`
- `infra/main.bicep:65-68`

</details>

<details id="CWE-798_Use_of_Hard-coded_Credentials">
<summary><b>CWE-798: Use of Hard-coded Credentials</b> — affected files</summary>

- `infra/main.bicep:59`
- `infra/main.bicep:65-68`

</details>

---

## Codebase Insights

> **Note:** These documents are generated by AI and may contain inaccuracies or incomplete information. Please review carefully.

> **Codebase Insights aren't available yet.**
>
> These documents are generated when assessment runs with **Full analysis** coverage. Re-run the assessment and set `analysisCoverage: full` to enable them.

[Share feedback](https://aka.ms/ghcp-appmod/feedback)
