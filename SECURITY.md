# Security Policy

This repository exists to keep sites running the abandoned **OneTone** and **OneTone Pro**
WordPress themes on a patched, safer build. Security reports are therefore the most
valuable contribution you can make here.

## Supported versions

| Theme | Version | Status |
| --- | --- | --- |
| OneTone | `4.0.0` | ✅ Supported — patches land here |
| OneTone Pro | `3.0.0` | ✅ Supported — patches land here |
| OneTone (MageeWP upstream) | `≤ 3.0.6` | ❌ Unmaintained — upgrade to `4.0.0` |
| OneTone Pro (MageeWP upstream) | `≤ 2.7.7` | ❌ Unmaintained — upgrade to `3.0.0` |

Only the builds published in this repository receive fixes. The original MageeWP releases
are no longer maintained by their author, and the free theme is no longer listed in the
WordPress.org theme directory.

## Reporting a vulnerability

**Please do not open a public issue for an unpatched vulnerability.**

Report it privately using either channel:

1. **GitHub Security Advisories** — use the
   [Report a vulnerability](https://github.com/SurefireStudios/onetone-wordpress-theme/security/advisories/new)
   form on this repository. This is the preferred route.
2. **Email** — contact [Surefire Studios](https://www.surefirestudios.io) through the
   contact details on our site, with `OneTone security` in the subject line.

Please include, where you can:

- The affected theme and version (`onetone` 4.0.0 or `onetone-pro` 3.0.0)
- The file and, if known, the line or function involved
- Steps to reproduce, ideally with a minimal proof of concept
- The privilege level required (unauthenticated, subscriber, editor, admin)
- Your assessment of the impact

### What to expect

- We aim to acknowledge a report within **7 days**.
- We will confirm the issue and share a rough remediation timeline.
- Once a fix ships, we will credit you in the release notes unless you prefer otherwise.

## Scope

**In scope** — anything shipped inside `onetone-patched.zip` or `onetone-pro-patched.zip`:
theme PHP, JavaScript, bundled libraries, and the theme options handling.

**Out of scope:**

- Vulnerabilities in WordPress core, WooCommerce, or any third-party plugin
- The *OneTone Companion* plugin, which is published separately by MageeWP
- Issues that require an already-compromised administrator account
- Findings against the original MageeWP builds that are already fixed here

## Hardening advice for site owners

Whichever build you run, these reduce your exposure:

- Keep WordPress core, plugins and PHP up to date
- Take a full backup before replacing any theme
- Restrict administrator accounts and enable two-factor authentication
- Put a web application firewall in front of the site
- Remove the theme entirely if the site no longer needs it — an inactive theme is still
  reachable on disk
