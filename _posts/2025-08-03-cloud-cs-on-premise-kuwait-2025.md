---
layout: post
title: "Revisiting the age old question, cloud hosting vs on-premise in Kuwait in 2025"
categories: cloud saas startup tech industry business hosting kuwait cost strategic
author: Anas Najaa
---

![saas tech startup]({{site.cdn_url}}/blog/2025/08/6cd4df39-96c9-4585-8e3d-0acc301b0b34.jpg)

# Intro

This morning, after I had my morning espresso and cleaned my small office in Hawally, I revised my balance sheet and my annual performance. I just finished reading [Farsighted](https://www.amazon.com/Farsighted-Make-Decisions-That-Matter/dp/1594488215), a book that describes the kind of deliberate planing that goes into long term strategic decisions. After all, it is not easy running a business as a solo founder. 
As a budding software startup, for the past 3 years DigitalOcean’s cloud servers have powered my web apps without a hitch. But this morning I had a tempting idea to cut costs: what if I brought everything in-house and ran it on hardware parked right here in my office? After all I'm already paying for rent, internet access, static IP and electricity + cooling (included in the rent).

Join me as I walk through every twist and turn of my cost-comparison journey—using real local prices, my own DigitalOcean real cost, and equipment you can actually buy in Kuwait. By the end, you’ll see how I arrived at the numbers and what made my decision the this time almost final at least for the next five year. 

As usual, the only constant is change, and this idea will respawn again in my head after a while and another reassessment need to be made. Until that time comes, lets start the breakdown.


# Money speaks: Time Value, Inflation, and Discount Rate

I started by reminding myself of one of the most important financial concepts I studied back in my MBA, Time Value of money. [Kuwait’s inflation](https://data.worldbank.org/indicator/FP.CPI.TOTL.ZG?locations=KW) is hovering around 2.3%. In simple terms, money spent next year will cost more in real terms than money spent today. 
To capture both this inflation and local economic risks, I chose an 4% discount rate for my five-year forecast as set by [CBK](https://www.cbk.gov.kw/en/cbk-news/announcements-and-press-releases/press-releases/2024/09/202409181900-cbk-cuts-discount-rate-by-25-basis-points-to-400). From here on, every future expense would be viewed through that lens.

# On premise costs real Local Prices
I've been a loyal customer for [PC Kuwait](https://pckuwait.com/) for the past 10 years. They are trust worthy and reliant. I checked their website and found the following server:
- [Dell PowerEdge T150](https://pckuwait.com/product/dell-t150-poweredge-tower-server-xeon-e-2314-16gb-ram-2tb-hdd/) (Xeon E-2314, 16 GB RAM, 2 TB HDD): 350 KWD

Add to it a simple UPS to ensure uptime:
- [LightWave 3 KVA](https://pckuwait.com/product/lightwave-3kva-online-ups/) UPS: 180 KWD 

And extra SSD storage:
- [Samsung 2 TB 9100](https://pckuwait.com/product/samsung-2tb-9100-pro-heatsink-nvme-m-2-ssd-pcie-5-0-x4-14700mb-s/) NVMe SSD : 112 KWD

Total up-front capital expense: 642 KWD

## What about the physical location for the server?
I used a portion of my monthly office rent for the server space, so let us say around 100 KWD/month to cover electricity, physical security, cooling, and room: 1,200 KWD per year.

## Internet access to get the server online
I've already subscribed to Internet & Static IP from Zain. The cost breakdown is as follows:
- Unlimited 5G plan: 20 KWD/month
- Static IP: 3 KWD/month

Total monthly cost: (20 + 3) × 12 = 276 KWD per year

## Other Security considerations for local hosting
Running on-premises means I’m responsible for:
- Physical security: locked cabinet, CCTV, access logs
- Network security: firewalls, intrusion detection
- Data protection: encrypted disks, off-site backups

A rough estimate would be 150 KWD/year for tools and backup storage.

## The hidden cost of going local, my time valued at opportunity cost
The local setup is not going to deploy itself magically after all. Someone needs to plan the setup, find a good and preferably free software to manage the server such as [Proxmox](https://www.proxmox.com/en/) and to help with deploying websites and services such as [Coolify](https://github.com/coollabsio/coolify).

So modestly speaking, I’ll spend about 1–2 hours per day managing all of this show. Valuing my time at 10 KWD/hour and averaging 1.5 hours/day:

1.5 h/day × 10 KWD/h × 365 days ≈ 5,475 KWD per year

This represents the opportunity cost of my attention and effort, a cost often overlooked by many.

## On-Premises cost Over Five Years
I laid out each year’s cash flows:

- Depreciation of hardware, UPS & SSD: 642 KWD / 5 = 128.4 KWD
- Rent (electricity & space): 1,200 KWD
- Internet & IP: 276 KWD
- Security & backups: 150 KWD
- Administrator’s time (my time): 5,475 KWD

That sums to 7,229.4 KWD per year, plus the initial 642 KWD.

### Present Value Calculation Using 4% Discount Rate

#### Formula

PV = 642 + Σ (7,229.4 / 1.04^t) for t = 1 to 5

#### Year over year calculations:

Year 1:  
7,229.4 / 1.04^1 = 7,229.4 / 1.04 = **6,949.42**

Year 2:  
7,229.4 / 1.04^2 = 7,229.4 / 1.0816 = **6,679.25**

Year 3:  
7,229.4 / 1.04^3 = 7,229.4 / 1.124864 = **6,418.51**

Year 4:  
7,229.4 / 1.04^4 = 7,229.4 / 1.169858 = **6,166.84**

Year 5:  
7,229.4 / 1.04^5 = 7,229.4 / 1.216653 = **5,923.88**

#### Total Discounted Future Cash Flows:

6,949.42 + 6,679.25 + 6,418.51 + 6,166.84 + 5,923.88 = **32,137.90**

#### Add Initial Cash Flow:

642 + 32,137.90 = **32,779.90**

#### Final Present Value of those cash flows:

**PV = 32,779.90**

# Cloud cost with DigitalOcean
If I go to DigitalOcean and select a droplet (VPS), with specs close to the PowerEdge server I picked from PC Kuwait, my bill will amount to 70 KWD/month. The specs are:
- 16 GB RAM
- 8 Intel-core CPUs
- 1480 GB NVMe SSD

Total cost per year: 840 KWD

Note: You might argue that the server specs don't exactly match the one picked from the local supplier, but those specs are as close I can get. There will be inaccuracies here and there but in the grand scheme of things, they will not matter that much as you have to take into account that cloud host is handling cooling, power, redundancy, and security for me.

## Cloud Over Five Years

With 1000 KWD per year (actually it is 840, I just pushed it to 1000 KWD to account for discrepancies in specs and to include my opportunity cost of managing the infrastructure and assuming a modest 5% annual price rise, all again discounted each year at 4%.

### Present Value Calculation for Growing Cash Flows (4% Discount Rate, 5% Growth)

#### Formula:

PV = Σ (1,000 × 1.05^(t−1) / 1.04^t) for t = 1 to 5

#### Step-by-Step Calculations:

Year 1:  
1,000 × 1.05^(1−1) / 1.04^1 = 1,000 × 1 / 1.04 = **961.54**

Year 2:  
1,000 × 1.05^(2−1) / 1.04^2 = 1,050 / 1.0816 = **970.92**

Year 3:  
1,000 × 1.05^(3−1) / 1.04^3 = 1,102.50 / 1.124864 = **980.22**

Year 4:  
1,000 × 1.05^(4−1) / 1.04^4 = 1,157.63 / 1.169858 = **989.46**

Year 5:  
1,000 × 1.05^(5−1) / 1.04^5 = 1,215.51 / 1.216653 = **998.63**

#### Total Discounted Cash Flows:

961.54 + 970.92 + 980.22 + 989.46 + 998.63 = **4,900.77**

#### Final Present Value of those cash flows:

**PV = 4,900.77**


# Reality, what the Numbers Say

- On-Premises: ~32,700 KWD over five years (PV)
- Cloud (DigitalOcean): ~5,000 KWD over five years (PV)

Even accounting for my time and extra security steps, the cloud remains roughly **six times** cheaper and spares me the nitty-gritty of keeping the racks humming. Attention and stress cost that I'd happily pay a hefty amount for at any day.

## So, will On-Prem ever Make Sense for startups?
For a startup, I don't think so, at least not anytime soon. This research is hardly thorough, but for you as a founder please feel free to add as many factors as you see fit to enhance the formula and come up with your own valuation. 

Don't forget that my choice of cloud, DigitalOcean, is considered one of the more expensive cloud providers out there. In the end,I rather spend my time building features instead of troubleshooting hardware.

Plug in your own inputs—prices, hours, discount rate—and let the data guide your decision. Steven Johnson said it best in his [book](https://www.amazon.com/Farsighted-Make-Decisions-That-Matter/dp/1594488215):
> “Great decisions are not made by people who see the future clearly.  
> They’re made by people who can map it, imagine it, and include a wider circle of insight —  
> people who embrace complexity, uncertainty, and long-term consequences.”  
> — *Steven Johnson, Farsighted*

# Appendices 

## On-Premises: Capital & Operational Expenses

**Initial Capital Expenditure (CAPEX)**

| Item                           | Cost (KWD) | Details                                      |
|--------------------------------|------------|----------------------------------------------|
| Dell PowerEdge T150 Server     | 350        | Xeon E-2314, 16 GB RAM, 2 TB HDD             |
| LightWave 3 KVA Online UPS     | 180        | Online UPS with battery backup               |
| Samsung 2 TB 9100 Pro NVMe SSD | 112        | PCIe 5.0, up to 14 700 MB/s                  |
| **Total CAPEX**                | **642**    |                                              |

**Annual Operating Expenses (OPEX)**

| Category                     | Annual Cost (KWD) | Notes                                           |
|------------------------------|-------------------|-------------------------------------------------|
| Depreciation                 | 128.4             | Straight-line over 5 years (642 KWD/5)          |
| Rent (Electricity & Space)   | 1,200             | 100 KWD per month                               |
| Internet & Static IP         | 276               | Zain unlimited 5G + static IP                   |
| Security & Backups           | 150               | Physical security, firewalls, off-site backups  |
| Opportunity Cost of CEO Time | 5,475             | 1.5 h/day × 10 KWD/h × 365 days                 |
| **Total Annual OPEX**        | **1,229.4**       |                                                 |


## Cloud Hosting: Predictable, Managed Services

| Category                      | Annual Cost (KWD) | Notes                                                          |
|-------------------------------|-------------------|----------------------------------------------------------------|
| Cloud Service Subscription    | 840               | 70 KWD/month for 16 GB RAM, 8 vCPUs, 1.48 TB SSD, 9 TB transfer |
| Price Escalation Assumption   | +5% p.a.          | Reflects inflation and vendor pricing trends                   |

**Value-Added Features of Cloud**  
1. **DDoS Protection & Network Security**: DigitalOcean’s managed security suite includes always-on DDoS mitigation, automated firewalls, and secure VPC isolation ([DigitalOcean Security](https://www.digitalocean.com/security)).  
2. **Redundancy & Uptime SLA**: 99.99% uptime commitments with geo-distributed backups.  
3. **Managed Patching & Updates**: OS and hypervisor patches applied automatically.  
4. **Operational Simplicity**: No hardware procurement, maintenance, or staff overhead.


# References
- [Dell PowerEdge T150 Server (PC Kuwait)](https://pckuwait.com/product/dell-t150-poweredge-tower-server-xeon-e-2314-16gb-ram-2tb-hdd/)
- [LightWave 3 KVA Online UPS (PC Kuwait)](https://pckuwait.com/product/lightwave-3kva-online-ups/)
- [Samsung 2 TB 9100 Pro NVMe SSD (PC Kuwait)](https://pckuwait.com/product/samsung-2tb-9100-pro-heatsink-nvme-m-2-ssd-pcie-5-0-x4-14700mb-s/)
- [DigitalOcean Security (DDoS protection, firewalls, etc.)](https://www.digitalocean.com/security)
- [Farsighted](https://www.amazon.com/Farsighted-Make-Decisions-That-Matter/dp/1594488215)
- [Kuwait’s inflation](https://data.worldbank.org/indicator/FP.CPI.TOTL.ZG?locations=KW)
- [CBK Discount Rate](https://www.cbk.gov.kw/en/cbk-news/announcements-and-press-releases/press-releases/2024/09/202409181900-cbk-cuts-discount-rate-by-25-basis-points-to-400)
