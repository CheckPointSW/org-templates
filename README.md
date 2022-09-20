# Secure Code Workflow Template
Use this template to monitor, classify and protect your code, assets, and infrastructure for exposed API keys, tokens, credentials, vulnerable open-source packages, and high-risk security misconfigurations in a simple way, without noise.

## GitHub Integration
 
The following instructions would help you to perform a fast and simple integration to your GitHub repo workflow actions using [GitHub Actions](https://docs.github.com/en/actions).
 
### Add To Repo
 
Add this job to your workflow yml file under .github/workflows/

```
name: Secure Code Analysis

on:
  - push
  - pull_request

jobs:
  code-analysis:
    uses: CheckPointSW/secure-code-workflow/.github/workflows/code-analysis.yml@main
    secrets: inherit
```

### Configuration
 
SourceGuard action must receive:
 
- `SG_CLIENT_ID` - Infinity Portal account identification
- `SG_SECRET_KEY` - Secret key for access
 
To generate these parameters, refer to https://portal.checkpoint.com/dashboard/sourceguard#/config/install (select your required Tenant) > GENERATE TOKEN
 
Spectral action must receive:
- `SPECTRAL_DSN` - You'll need to provide Spectral dsn.  [GitHub secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets).

To retrieve  `SPECTRAL_DSN` parameter, refer to https://app.spectralops.io/sources

Now, create these keys: 
- Organization Scope
  https://github.com/organizations/OrganizationName/settings/secrets/actions
- Repo Scope
  https://github.com/AccountName/RepoName/settings/secrets/actions

See more about [GitHub secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets).

## References
- [What is Developer Security?](https://www.checkpoint.com/cyber-hub/cloud-security/what-is-developer-security/)
- [Shift Left: Check Point Security Solution for DevOps](https://www.checkpoint.com/cloudguard/devsecops/)
