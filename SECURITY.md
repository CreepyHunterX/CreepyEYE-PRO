# Security & Responsible Use Policy

**CreepyEYE PRO** is intended for **ethical OSINT purposes only**. By using this tool, you agree to
the following.

## Purpose

* Use CreepyEYE PRO **only for legal and ethical purposes**
* Do **not** use it for hacking, phishing, stalking, or violating other people's privacy
* Suitable for learning, research, authorised testing, and auditing your own accounts

## Data handling

* CreepyEYE PRO does **not store your API keys** on CreepyCORE servers — keys are saved locally in
  `settings/api/api_keys.env` on your machine
* Keep that file private. If it is ever shared or leaked, **rotate all third-party API keys
  immediately**
* You are responsible for the data you input (emails, IPs, usernames, domains, phone numbers) and
  for having a lawful basis to process it (GDPR and equivalents)
* Do **not** transmit other people's personal information to third parties without a lawful basis
* Comply with each third-party API and data source's terms of service

## Responsibility

* The developer is **not responsible** for any illegal use of the tool
* The tool is provided "as-is" without guarantees for full API correctness or completeness

## Reporting a vulnerability

* Security issues: **security@creepycore.com** — please report privately and **do not exploit**
* Everything else (licence, activation, devices, bugs): **support@creepycore.com**
* Do not attack or exploit vulnerabilities in the connected third-party services

## Operator hardening

When running CreepyEYE PRO on a shared or production machine:

| Control | Recommendation |
|---------|----------------|
| Official signed build | Use the installer from your CreepyCORE **License** page and verify its SHA-256 against `SHA256SUMS.txt`. Packaged builds enable production hardening automatically. |
| `CREEPYEYE_PRODUCTION=1` | Enable production hardening when you run from source |
| Activation cache | `~/.creepyeye_pro/` is restricted to your user (`0600` on Unix, `icacls` on Windows) — keep it that way |
| Integrity recovery | If the app enters its protective locked state, recover with a signed recovery token issued by CreepyCORE support |
| Local Web API | Stays on `127.0.0.1`; in production it requires `Authorization: Bearer <CREEPYEYE_WEB_API_TOKEN>` |

## SpiderFoot integration (TLS)

CreepyEYE PRO starts SpiderFoot locally (`127.0.0.1`) and talks to its web UI over HTTP on loopback.
Upstream SpiderFoot modules (GPL, shipped unmodified) may call external sites with TLS verification
disabled for legacy `.onion` or misconfigured targets — **CreepyEYE does not patch vendor source**.

| Risk | Mitigation |
|------|------------|
| MITM on the **localhost** SpiderFoot API | Low: traffic stays on loopback. Do not expose the SpiderFoot port (`5001`) beyond the host. |
| MITM on **SpiderFoot → internet** fetches | Inherited from upstream: run on trusted networks and keep the bundled SpiderFoot at its shipped version |

If other people share your machine, firewall the SpiderFoot listen port after enabling integrations.

## Activation file (`activation.json`)

* **Never share or commit** `activation.json` — it contains a live activation token
* If it was ever shared, committed, or copied elsewhere: **revoke that device** in
  CreepyCORE → **Devices**, delete the local file, and re-activate from a fresh key
* Losing access to a device you no longer control? Revoke it in the Device Hub — the slot is freed
  for a new activation

## Licence compliance

* CreepyEYE PRO is licensed under the proprietary **End User License Agreement (EULA)**, shown in the
  **License** section of CreepyCORE above the download button
* Optional integrations (SpiderFoot, Sherlock, ExifTool) and Python dependencies carry **their own
  licences** — see EULA §8 and the upstream projects' terms
* Use third-party APIs according to their terms of service
* Up to **3 devices** per key; reverse engineering the binaries is prohibited (EULA §2), except where
  the law expressly allows it

---

← Back to the [CreepyEYE PRO documentation](README.md) ·
[creepycore.com](https://creepycore.com) · [support@creepycore.com](mailto:support@creepycore.com)
