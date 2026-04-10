# Security Policy

## Reporting Security Issues

**Please do not report security vulnerabilities through public GitHub issues.**

Instead, please use GitHub's private vulnerability reporting:

1. Go to https://github.com/GeiserX/runtipi-appstore/security/advisories
2. Click "Report a vulnerability"
3. Fill out the form with details

We will respond within **48 hours** and work with you to understand and address the issue.

### What to Include

- Type of issue (e.g., insecure defaults, container escape, credential exposure)
- Full paths of affected source files
- Step-by-step instructions to reproduce
- Proof-of-concept or exploit code (if possible)
- Impact assessment and potential attack scenarios

### Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |

Only the latest version receives security updates. We recommend always running the latest version.

## Security Best Practices for Users

1. **Review app configurations** - Audit docker-compose files before deploying
2. **Use strong passwords** - For all application credentials
3. **Keep images updated** - Regularly pull latest container images
4. **Restrict network access** - Use Runtipi's built-in network isolation
5. **Never expose management ports** - Keep admin interfaces behind authentication

## Contact

For security questions that aren't vulnerabilities, contact: security@geiser.cloud
