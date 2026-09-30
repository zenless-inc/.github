# Security Policy

## Supported versions

Zenless is in early development. Security fixes go into the **latest release** of each app. Please update before
reporting, since the issue may already be fixed.

| Version | Supported |
|---|---|
| 0.1.x (latest) | ✅ |
| Older | ❌ |

## Reporting a vulnerability

**Please do not open a public issue for security problems.**

Report them privately through GitHub:

1. Open the affected repository, e.g. [zenless-download-manager](https://github.com/zenless-inc/zenless-download-manager).
2. Go to **Security → Report a vulnerability**.
3. Describe the problem, the affected version, and how to reproduce it. A proof of concept helps a lot.

We aim to acknowledge reports within **3 days** and to ship a fix or mitigation for confirmed issues as soon as we can.
We'll keep you updated, and credit you in the release notes unless you'd rather stay anonymous.

## Scope

These are especially interesting to us:

- **The local integration API** (`127.0.0.1:6812` / `6813`): anything that lets a web page, another user or a remote
  host trigger downloads, read state or control the apps, such as origin-check bypasses or DNS rebinding.
- **Browser extensions:** leaking cookies or browsing data, or letting web pages drive the extension.
- **The installer:** writing outside its own install folder, path traversal in payloads, or anything that could
  be abused for privilege escalation.
- **Download handling:** file names or server responses that write outside the chosen folder.

Out of scope: bugs that need an already-compromised machine or admin rights, and the unsigned-binary SmartScreen warning.
