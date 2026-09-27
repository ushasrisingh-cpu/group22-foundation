# ADR 005 Layered Security Scanning

**Status:** Accepted

## Context and problem

No single scanner covers source secrets, infrastructure policy, Kubernetes manifests, container packages, and code quality.

## Decision

Use blocking Gitleaks, Checkov, and Trivy checks in CI. Run Maven tests as a
quality gate. Run SonarCloud analysis when the repository `SONAR_TOKEN` is
available, and retain the Quality Gate result as reviewed delivery evidence.
Document every Checkov skip with a specific rationale.

## Alternatives considered

- One all-purpose commercial scanner
- Advisory-only scans that never fail CI
- Manual scanning before release

## Consequences and trade-offs

Layered tools improve coverage but increase CI duration and maintenance. False
positives require documented review. SonarCloud analysis depends on its
repository secret, while Snyk and ZAP remain future improvements. Whether the
SonarCloud Quality Gate is a required merge check is configured in GitHub, not
in this repository file.

## Security implications

The enforced gates prevent secret leaks, unsafe infrastructure changes, and fixable high or critical image vulnerabilities from passing unnoticed.

## Cost implications

The selected open-source tools and GitHub Actions usage avoid additional platform subscriptions for the capstone.

## Rationale

The combination covers the implemented delivery path and produces reproducible evidence without overstating unconfigured controls.
