# Security Scan Report

## 1. Project Details

- Project: Jenkins Docker Demo
- Repository: https://github.com/nisha-subramaniyan/jenkins-docker-demo
- CI/CD tools: Jenkins, Docker, GitHub Actions
- Security scanner: Trivy
- Scan date: [Enter date]
- Image scanned: jenkins-docker-demo:security

## 2. Objective

The objective of this assessment is to identify vulnerabilities in the Docker image, review the container configuration, and recommend security improvements.

## 3. Scan Summary

- Critical vulnerabilities: [Actual count]
- High vulnerabilities: [Actual count]
- Medium vulnerabilities: [Actual count]
- Low vulnerabilities: [Actual count]
- Unfixed vulnerabilities: [Actual count, if available]

## 4. Findings

| Finding / CVE | Severity | Affected package | Recommended remediation |
|---|---|---|---|
| [Actual CVE or finding] | [Severity] | [Package] | [Specific fix] |

Add one row for each relevant finding. If no findings are returned for the selected severity levels, state that explicitly.

## 5. Linux and Docker Hardening

Checks performed:
- Reviewed Linux package updates.
- Checked user and file permissions.
- Reviewed listening ports and running services.
- Inspected the Dockerfile for root execution.
- Checked for hardcoded secrets and unnecessary build-context files.

Results: [Record the actual findings.]

## 6. Remediation and Retesting

For each confirmed issue:
1. Record the original finding.
2. Apply the appropriate fix.
3. Rebuild the Docker image.
4. Rerun the scan.
5. Record whether the issue was resolved.

## 7. Conclusion

The assessment identified the security issues documented above and proposed corresponding remediation steps. The final security status is based on the scan output and the verification performed after remediation.
