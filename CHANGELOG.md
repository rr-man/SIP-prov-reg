# Changelog — SIP Provisioning & Registration Training Suite

All notable changes to this project are documented here.
Versioning: **MAJOR.MINOR.PATCH** — MINOR for new sections/features, PATCH for fixes, swaps, and small text changes.

---

## sip-flow-interactive.html

### v1.10.0 — Flow step content enrichment (current)
- Added DHCP Option 66 explanation to the "DHCP server responds" step
- Added config file contents breakdown (credentials, SBC address, codecs, feature keys, firmware pointers) to the "Provisioning server responds" step
- Added what REGISTER accomplishes (binds extension to the phone's IP:port for inbound call routing) to the "REGISTER sent" step
- Added explicit "401 is a challenge, not an error" framing to the "401 Unauthorized" step
- Added SIP ALG explanation (what it is, why moving off 5060 bypasses it) to the "REGISTER sent" failure note
- Corrected the "Provisioning server responds" failure note: MAC.boot 404 is normal fallback behavior; MAC.cfg 404 is the real problem (previously flagged all 404s as problems)

### v1.9.0 — Troubleshooting sub-tabs and content
- Added two sub-tabs under Troubleshooting ("Dig deeper"): Reading the provisioning log / What sip.listen_port does — color-coded violet/amber, NAT card stays always visible above
- Added "Where to find it" steps to the provisioning log panel (PBX > Reports > Auto Provisioning > search MAC)
- Added Yealink-only warning callout to the sip.listen_port panel (parameter is Yealink syntax; other vendors use their own)

### v1.8.0 — Reading the provisioning log
- New Troubleshooting card: Yealink boot request sequence (.boot 401→404 normal, .cfg 401→200 goal), status-code reference table, digest auth tie-in to the SIP handshake
- Embedded provisioning log screenshot with MAC addresses pixelated (device-name column and URL filenames), 256-color optimized
- Repositioned card directly below "Resolving NAT issues"

### v1.7.0 — Layer tab visibility
- "Jump to layer" sub-tabs upgraded from underline style to bordered buttons in a tray with label
- Full color coding: layer-colored border/text at rest, tinted hover, solid fill with white text when active

### v1.6.0 — sip.listen_port explainer
- New Troubleshooting section: "What sip.listen_port actually does" — definition, phone→NAT→SBC diagram ("this side changes / this side doesn't"), SIP ALG and port-collision explanations, quick rules box, provisioning-vs-registration tie-in
- Diagram's phone port live-syncs with the port picker selection
- Self-contained SVG arrow marker (no dependency on hidden Flow tab defs)

### v1.5.0 — YMCS remote reboot
- Added steps 4–5 to NAT resolution: log in to YMCS (linked), Device Management > MAC search > Diagnose > Reboot
- Embedded YMCS screenshot with lightbox; generalized lightbox to handle multiple images with per-image download filenames
- v1.5.1: replaced YMCS screenshot with MAC-redacted version (privacy)

### v1.4.0 — Branding
- COEO logo embedded in header (base64, 118px)
- Footer credit: "Created by Ron Mangune" with LinkedIn icon linked to profile

### v1.3.0 — Three-part phone diagram & default port
- "What's happening on the phone" rebuilt as three separate cards (DHCP / Provisioning / Registration), each with its own client↔server round-trip animation; registration card keeps PBX-behind-SBC, NAT tag, and four-message handshake pacing
- Default port changed to 5060 (the problem state); picking any port chip updates the line to the fix; hint text updated

### v1.2.0 — Image preview lightbox
- Screenshot click opens full-screen preview with dark overlay, Download button, Close/Escape/click-outside dismiss
- Deduplicated base64 (was stored twice in anchor + img)

### v1.1.0 — Tab structure & NAT troubleshooting
- Primary tabs: Flow / Troubleshooting
- Layer selector moved into Flow tab as sub-tabs (hidden on Troubleshooting)
- NAT resolution card: UAD Auto Provisioning Template steps, interactive port picker (20 ports) correlated to a live sip.listen_port line, copy-to-clipboard, embedded UAD template screenshot

### v1.0.0 — Initial release
- Interactive 8-step flow tracker (DHCP → provisioning → registration) with per-step protocol, explanation, and failure notes
- Layer legend with synced highlighting across tracker and diagram
- Animated bidirectional handshake dots; registration line paced to the four-message REGISTER handshake
- SBC/PBX architectural separation with L1 plain-language notes

---

## sip-l1-exam.html

### v1.0.0 — Initial release
- 15-question multiple-choice exam covering DHCP (2), provisioning (2), registration (4), troubleshooting (7)
- Layer-tagged questions, sticky progress bar, submit gating until all answered
- Scoring with 12/15 (80%) pass threshold, per-layer breakdown, per-question explanations, retake
- Correct answers balanced across A–D positions (4/4/4/3)
- COEO branding and footer credit consistent with the flow tool

## sip-l1-exam-answer-key.html

### v1.0.0 — Initial release
- Grader copy: all correct answers highlighted on load, answer letter + explanation under each question
- Amber "Answer key" badge, do-not-distribute banner, interaction disabled
