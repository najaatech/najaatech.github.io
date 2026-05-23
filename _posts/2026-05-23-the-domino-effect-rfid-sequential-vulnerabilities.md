---
layout: post
title: "The Domino Effect: Single-Factor RFID Authentication and Sequential Card IDs"
categories: cybersecurity physical security rfid pentest education
author: Anas Najaa
---

![The Domino Effect: RFID Sequential Vulnerabilities](/assets/images/2026-05-rfid-domino-effect-cover.png)

# Physical security is cybersecurity

True security is holistic. While a great deal of time goes into securing servers, optimizing web applications, and hardening digital infrastructure, none of that matters if an unauthorized individual can simply walk through the front door of your data center.

During a recent physical penetration test of a client's campus, the objective was to evaluate the resilience of their physical access control systems (PACS). The campus was secured using [ZKTeco BioFace D1](https://www.zkteco.me/product-details/bioface-d1) terminals, multi-biometric readers supporting face, fingerprint, RFID card, and password authentication.

During the assessment, using standard hardware research tools like the [Flipper Zero](https://flipperzero.one/) (running [Momentum firmware](https://github.com/Next-Flip/Momentum-Firmware)) and [Proxmark3](https://github.com/RfidResearchGroup/proxmark3), we uncovered two compounding vulnerabilities: the access control system relied entirely on the card ID as a single factor, with no PIN, biometric, or any secondary verification and on top of that, the RFID badge numbers were completely sequential. Either problem alone is serious. Together, they made the system trivially exploitable.

---

# The anatomy of an access badge

To understand the vulnerability, we first need to look at how the BioFace D1 handles RFID authentication. Like most access control terminals in the region, the client had it configured to accept legacy 125 kHz proximity cards via the Wiegand interface, the path of least resistance during a campus-wide rollout. These cards, such as standard EM4100 or legacy HID proxies, communicate with no cryptographic handshake.

When a student or faculty member taps their card, the badge simply powers up via the reader's magnetic field and broadcasts its unique identifier (UID) in plain text. What the Proxmark3 or Flipper Zero captures is a raw 5-byte hexadecimal string, for example:

```
8E 00 00 27 10
8E 00 00 27 11
```

The reader decodes the card's identifier and outputs it over the Wiegand interface to the access control panel. In the examples above, both cards share the same Facility Code (`8E` = 142 in decimal) and differ only in their last byte. That one-byte increment is all it takes to move from one user's identity to the next.

---

# The discovery: the problem with predictability

When the client ordered their access cards, the manufacturer printed and encoded them sequentially to avoid duplicates. A box might contain cards with a Facility Code of `142` and Card Numbers running from `10000` to `15000`.

During our audit, the red team acquired a single valid student card simulating a dropped or temporarily unattended ID. By reading that one card, we immediately extracted the Facility Code and the current numerical range of active cards. Because the system administrators mapped these cards sequentially to users in the database without randomizing the internal IDs, they inadvertently mapped out their entire organization's physical security structure for us.

---

# How we exploited the sequential flaw

Armed with knowledge of the sequential structure, we demonstrated two critical attack vectors.

## 1. Silent brute forcing and enumeration

We didn't need to steal any additional badges. Using a Flipper Zero, we wrote a simple script to emulate a badge, increment the Card Number by 1, and present it to the reader.

```
Emulate ID 10001... Access Denied.
Emulate ID 10002... Access Granted. Door opens.
```

Because the client's legacy system lacked rate-limiting or physical intrusion detection at the door reader level, an attacker could silently brute-force access into restricted areas without triggering any backend alarms.

## 2. Privilege escalation via hierarchy mapping

Sequential numbering often mirrors organizational timelines. In this client's case, card numbers `10000` to `14000` belonged to the student body, while the earliest batch (`00001` to `00500`) had been assigned to faculty, maintenance staff, and IT administrators.

---

# One device, every door: the uniform deployment problem

What amplified the damage in this case wasn't just the sequential numbering, it was the deployment decision that preceded it. The client had installed the [BioFace D1](https://www.zkteco.me/product-details/bioface-d1) as the single access control terminal across **every door on campus**: the main entrance gate, classrooms, staff offices, the IT room, the server room, the archive and we are not making this up, even the bathrooms. Every reader shared the same Facility Code and drew cards from the same sequential pool.

This means that once we had a working emulation of any card in the range, the Flipper Zero in our pocket was effectively a **master key to the entire campus**. There was no door it could not open.

This is a textbook violation of the **principle of least privilege access** applied to physical space. In network security, we segment infrastructure into zones for example a guest Wi-Fi network has no path to the internal VLAN; a developer workstation cannot reach production databases directly. The same logic must apply to physical access:

- A student badge should open lecture halls and common areas, nothing else.
- A maintenance badge should access utility rooms and corridors, not server racks.
- An IT administrator badge should be the only credential that opens the server room, and even then, paired with a second factor.

By using a single device model with a single shared Facility Code across all security zones, the client created what is known in security architecture as a **flat access control model**, the physical equivalent of putting every system on the same network segment with no firewall between them. One compromised credential cascades into total access. This is the "domino effect" in the title: you knock over one card, and every door in the building falls with it.

The BioFace D1 is a capable piece of hardware. It supports face and fingerprint authentication precisely to prevent this kind of attack. The failure here was not the device, it was how it was deployed.

---

# The underlying issue: single-factor authentication and no cryptography

It is worth being precise about what actually went wrong here, because "sequential IDs" is only half the story.

The deeper flaw is that the system asked one question is that *do you have a card with this ID?* and nothing else. No PIN. No biometric match. No challenge-response. If you can present the right number, the door opens. It does not matter whether you are the person the card was issued to.

This is **single-factor physical authentication**, and it is insecure regardless of whether the IDs are sequential or random. If the IDs had been randomized, an attacker who physically cloned a single card would still have unrestricted access to every door that card is authorized for. Sequential numbering simply removes the need to clone anything when enumeration alone is sufficient.

The second layer is the absence of cryptography. Legacy 125 kHz RFID technology transmits its payload in plain text with no mutual authentication. If the cards had used a protocol requiring a cryptographic challenge-response such as MIFARE DESFire or HID SEOS emulation would not be possible without the secret key, even if the IDs were known. Cryptography would have broken the attack at the hardware level; a second factor would have broken it at the access policy level. The client had neither.

---

# Remediation: securing the perimeter

If you manage physical access control for your organization, these are the steps worth prioritizing:

**1. Upgrade the hardware stack**

Transition away from unencrypted 125 kHz proximity cards. Implement high-frequency (13.56 MHz) smart cards that support modern cryptography, such as [MIFARE DESFire EV3](https://www.nxp.com/products/rfid-nfc/mifare-hf/mifare-desfire:MC_53450) or [HID iCLASS SEOS](https://www.hidglobal.com/products/cards-and-credentials/iclass-seos). These cards require cryptographic challenge-response authentication before revealing any actionable data.

**2. Randomize UIDs in the database**

If an immediate hardware upgrade isn't feasible and you are stuck with legacy Wiegand systems, never assign card numbers sequentially. Map random, non-contiguous badge IDs to user accounts in the backend access control database.

**3. Implement anomaly detection**

Access control software should act like a web firewall. If a single door reader registers dozens of "Access Denied" events from sequential badge numbers within a few minutes, an alert must be triggered and security personnel dispatched.

**4. Enforce multi-factor authentication (MFA)**

For server rooms, financial offices, or executive suites, a badge tap should not be enough. Require a badge plus a PIN code or biometric verification.

---

# Conclusion

The same principles that protect web applications and cloud deployments must be applied to physical doors: layered authentication, encryption, and anomaly detection. Sequential IDs made this particular attack faster, but the system was broken before the first card was ever enumerated because it never asked for more than one thing to prove who you are. A card ID on its own is not an identity. It is a number, and numbers can be guessed, cloned, or emulated. That has to be the starting assumption when designing any access control system.

---

*References: [Flipper Zero](https://flipperzero.one/); [Momentum Firmware](https://github.com/Next-Flip/Momentum-Firmware); [Proxmark3](https://github.com/RfidResearchGroup/proxmark3); [ZKTeco BioFace D1](https://www.zkteco.me/product-details/bioface-d1); [MIFARE DESFire EV3 — NXP](https://www.nxp.com/products/rfid-nfc/mifare-hf/mifare-desfire:MC_53450); [HID iCLASS SEOS](https://www.hidglobal.com/products/cards-and-credentials/iclass-seos); [26-bit Wiegand format — Wikipedia](https://en.wikipedia.org/wiki/Wiegand_interface)*