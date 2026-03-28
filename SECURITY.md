# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability, please report it responsibly:

- **Email**: [TODO: add security contact email]
- **Do not** open a public GitHub issue for security vulnerabilities

We will acknowledge receipt within 48 hours and aim to provide a fix within 7 days for critical issues.

## Scope

OpenShelf is a client-side web application. The primary security concerns are:
- XSS via imported JSON configs
- CDN integrity for Three.js dependency
- Data privacy (all data stays in browser, nothing sent to servers)
