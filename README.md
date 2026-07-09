# SIP Provisioning & Registration Training Suite

Interactive training tools for COEO L1/NOC support teams covering the full phone boot-to-registered lifecycle: DHCP, provisioning, SIP registration, and the NAT troubleshooting playbook.

**Current versions:** flow tool `v1.10.0` · exam `v1.0.0` · answer key `v1.0.0`

---

## Files

| File | Purpose | Audience |
|---|---|---|
| `sip-flow-interactive.html` | Interactive flow tool: 8-step boot-to-registered tracker, three-part phone diagram with animated handshakes, and a Troubleshooting tab (NAT resolution, provisioning log reading, sip.listen_port explainer) | Whole team |
| `sip-l1-exam.html` | 15-question exam with scoring, 80% pass threshold, per-layer breakdown, and per-question feedback | L1 techs |
| `sip-l1-exam-answer-key.html` | Grader copy with all answers highlighted — **do not publish with the exam** | Trainers only |
| `CHANGELOG.md` | Version history for every alteration | Maintainers |

## Architecture

Follows the standard COEO internal-tool pattern:

- **Single self-contained HTML file** per tool — vanilla JS, no build step, no runtime dependencies (Google Fonts is the only external call)
- **All images embedded as base64** (COEO logo, PBX/YMCS/provisioning-log screenshots), quantized to 256-color PNG to keep file size down
- **Screenshots redacted** — MAC addresses pixelated in both device names and URL filenames before embedding
- Deployable to **GitHub Pages** and embeddable in **Confluence via iframe**

## Deployment

1. Commit the HTML files to the repo (keep `sip-l1-exam-answer-key.html` out of any page linked to the team, or in a separate private location)
2. GitHub Pages serves them at `https://<org>.github.io/<repo>/sip-flow-interactive.html`
3. Embed in Confluence with an iframe macro pointing at the Pages URL

## Content covered

- **DHCP:** boot sequence, Option 66/67/43, what the lease delivers
- **Provisioning:** config file contents, MAC-based requests, HTTP/TFTP delivery, reading the provisioning log (.boot vs .cfg, which 404s matter), PBX log location (Reports > Auto Provisioning)
- **Registration:** the four-message digest auth handshake (REGISTER → 401 → REGISTER → 200 OK), what REGISTER binds, SBC vs PBX roles, Expires/refresh
- **Troubleshooting:** NAT resolution via `sip.listen_port` (Yealink-only), SIP ALG, port collisions, UAD Auto Provisioning Template, YMCS remote reboot, layer-based symptom diagnosis

## Versioning

`MAJOR.MINOR.PATCH` per file, stamped in two places:

- HTML comment on line 2 of each file
- Visible `vX.Y.Z` badge in the footer

**MINOR** = new section or feature · **PATCH** = fix, content swap, or small text change. Every alteration gets an entry in `CHANGELOG.md`.

## Maintenance notes

- The exam's questions live in the `QUESTIONS` array in `sip-l1-exam.html`; the answer key is generated from the same file — regenerate the key after any exam edit so they stay in sync
- The flow tool's step content lives in the `FLOW` array; troubleshooting cards are plain HTML sections
- Exam answers are visible in page source — treat it as a self-check/training exam, not a proctored one
- `sip.listen_port` guidance is Yealink-specific; the tool says so explicitly

---

Created by [Ron Mangune](https://www.linkedin.com/in/ronmangune/) · COEO AI Enablement
