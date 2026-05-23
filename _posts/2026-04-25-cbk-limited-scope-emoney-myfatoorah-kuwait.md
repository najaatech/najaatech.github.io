---
layout: post
title: "Kuwait's New E-Money Crackdown: What MyFatoorah's Circular Means for Your Business"
categories: fintech payments kuwait regulation cbk ecommerce
author: Anas Najaa
---

![Kuwait's New E-Money Crackdown: CBK Limited-Scope E-Money and MyFatoorah](/assets/images/2026-04-cbk-limited-scope-emoney-myfatoorah-kuwait-cover.png)

# What Happened?

On April 16, 2026, the [Central Bank of Kuwait (CBK)](https://www.cbk.gov.kw/en) issued a circular tightening the rules around **limited-scope electronic money services** (_خدمات النقود الإلكترونية ذات النطاق المحدود_). The core requirement is straightforward but consequential: **no entity may operate such a service without first obtaining a no-objection certificate (NOC) from the CBK**.

Shortly after, [MyFatoorah](https://www.myfatoorah.com) — one of the most widely used payment gateways in Kuwait — issued a notice to all its merchants, requiring them to either confirm compliance or apply for the required certificate by **April 30, 2026**. Merchants who miss that deadline risk having their accounts restricted until their status is regularised.

I use MyFatoorah at [Najaa Technologies](https://najaa.org) alongside other Kuwait-based payment providers including [uPayments](https://www.upayments.com) and [Tap Payments](https://www.tap.company). The notice landed in my inbox like everyone else's, which is what prompted me to write this up.

---

# What Exactly Are "Limited-Scope Electronic Money Services"?

The CBK circular defines the activity precisely: it applies when **a single entity issues electronic monetary value** — stored as a digital wallet balance, credits, or loyalty points — that can be used **inside Kuwait** to pay for goods or services from **a specific group of contracted merchants on the same platform**.

The key distinguishing features:

| Factor | Limited-Scope E-Money | Ordinary Payment |
|---|---|---|
| Value stored per end-user? | Yes (wallet / credits) | No (card charged at checkout) |
| Multiple external merchants on the platform? | Yes | Typically no |
| Jurisdiction | Kuwait only | Any |

Concrete examples that would **fall under** the regulation:
- A marketplace app where sellers are independent merchants and buyers top up a wallet balance to pay them.
- A loyalty or rewards platform where points are issued by one operator and redeemed across many partner merchants.

Examples that would **not apply**:
- A single-merchant online store that only accepts payments for its own products.
- A SaaS platform that bills its own subscription — there is no third-party merchant network.

---

# What MyFatoorah Is Asking Merchants to Do

MyFatoorah's notice breaks down the obligation into three scenarios:

1. **You believe you operate such a service** → Contact MyFatoorah immediately via [supportkuwait@myfatoorah.com](mailto:supportkuwait@myfatoorah.com) and provide an up-to-date, valid NOC from CBK.

2. **You have an NOC but it is expired** → You must renew it and submit a fresh copy to MyFatoorah before the deadline.

3. **You do not have an NOC at all** → You must apply to the CBK by **April 30, 2026** at the latest. MyFatoorah offered to guide merchants through the online portal process on request.

If you are **unsure whether the regulation applies to you**, MyFatoorah explicitly recommends reaching out to them first, before going to the CBK, so they can point you in the right direction.

---

# Documents Required to Apply for the NOC

If you do need to apply, the CBK requires the following documents when submitting your registration request:

- Company memorandum and articles of association
- Company by-laws
- A commercial registration certificate issued **no more than 3 months** before the date of application
- Ownership structure showing any partner holding more than 5% of the company
- A list of names and IDs of executive management and board members
- Audited annual financial statements; if the company has been operating for fewer than 3 financial years, statements covering the period since commencement of operations

---

# Why This Matters for the Local Fintech Ecosystem

Kuwait has been steadily modernising its payments infrastructure. The CBK's discount rate currently sits at 3.5% and the central bank has made fintech oversight a stated priority — as recently as April 1, 2026, it [launched a cybersecurity leaders programme](https://www.cbk.gov.kw/en/cbk-news/announcements-and-press-releases/press-releases/2026/04/202604010800-cbk-launches-the-first-edition-of-the-advanced-cybersecurity-leaders-program) aimed at the financial sector. The CBK also maintains a dedicated [e-Payment Services supervision page](https://www.cbk.gov.kw/en/supervision/e-payment-services) and an Innovation Hub ("Wolooj") for regulated experimentation.

This circular fits a global pattern: regulators everywhere are closing the gap between traditional payment institutions and the newer generation of wallet-based platforms. The European Union did this with its revised Payment Services Directive (PSD2); the UK did it through the FCA's e-money regulations; and Gulf regulators — including Saudi Arabia's SAMA and Bahrain's CBB — have been moving in the same direction for several years.

The short deadline (two weeks from the circular's issue date) is deliberately tight. It signals that the CBK is not just establishing a framework — it is enforcing one that was arguably already implied by existing e-money legislation.

---

# Practical Takeaway

If you are building or operating a multi-merchant platform in Kuwait that involves stored value for end users, assume this applies to you and act now. The April 30 deadline leaves very little room for deliberation. Even if your business ultimately does not fall under the definition, a quick email to MyFatoorah costs nothing and removes any ambiguity.

For developers integrating MyFatoorah or building marketplace payment flows in Kuwait: this is a timely reminder that payment regulation is a first-class concern, not an afterthought. Architecture decisions around wallets, escrow, and multi-party settlements carry regulatory weight — factor that in from day one.

---

*References: MyFatoorah merchant announcement (April 2026); [Central Bank of Kuwait](https://www.cbk.gov.kw/en); [CBK e-Payment Services Supervision](https://www.cbk.gov.kw/en/supervision/e-payment-services); [MyFatoorah Payment Solutions](https://www.myfatoorah.com)*
