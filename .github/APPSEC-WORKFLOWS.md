# Double Commander - GitHub AppSec Workflows

This package is designed for the `master` branch of `lukasz-schab/doublecmd`.

## Account-free toolset

The package intentionally contains only tools that do not require creating an external vendor account, purchasing a license, or configuring external API keys/tokens.

Enabled workflows:

- CodeQL: C/C++, Python, GitHub Actions
- Dependency Review
- Gitleaks
- zizmor
- OpenSSF Scorecard
- Pascal Semgrep Generic security hotspots
- Syft SBOM + Grype
- OSV-Scanner full and PR differential scans
- Trivy filesystem, misconfiguration, secret and license scanning
- Flawfinder
- DevSkim

The only credentials used by these workflows are GitHub-provided runtime credentials such as `github.token` where required by GitHub itself. No SonarQube Cloud, Snyk, Fortify, or other external service account is required.

## Removed integrations

The following integrations are intentionally not included because they require an external account, token, subscription, or service configuration:

- SonarQube Cloud / SonarCloud
- Snyk
- Fortify / Fortify SSC / ScanCentral

## Recommended required checks after baseline cleanup

Good candidates for blocking checks:

- CodeQL (c-cpp)
- CodeQL (python)
- CodeQL (actions)
- Dependency Review
- Gitleaks
- zizmor
- OSV-Scanner PR Diff

Initially advisory/non-blocking:

- Pascal Security Hotspots
- OpenSSF Scorecard
- Trivy
- Flawfinder
- DevSkim
- Syft/Grype full-repository baseline scans until existing findings are triaged

## Security design notes

- External GitHub Actions are pinned to full commit SHA where a verified SHA was available.
- Vendor actions that publish immutable releases but for which a verified full SHA was not established in this package remain pinned to an explicit release tag.
- No workflow uses `pull_request_target`.
- The package does not require external vendor secrets or API tokens.
- SBOM and vulnerability discovery are separated: Syft inventories components, while Grype and OSV provide independent vulnerability intelligence.
- Pascal Semgrep rules are security heuristics, not semantic/interprocedural SAST. Findings require validation before assigning CVSS.
- DevSkim and Flawfinder are additional heuristic signals and should not be treated as authoritative vulnerability confirmation.

## First-run recommendation

Commit this package in a dedicated branch first. Let all workflows run once, establish a baseline, then promote only low-noise checks into the repository ruleset.
