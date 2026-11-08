# Affordable cloud servers: what $3.48–$4 a month really buys, when a $79 bare-metal box is the better deal, and the traffic and IP rules that decide the bill

Entry-level cloud servers cluster between $3.48 and $4 a month for the smallest size worth running. Cloudzy's 1 GB plan is $3.48, half of a $6.95 list price. Kamatera starts at $4. UpCloud's Starter tier is €3 for 1 GB with 10 GB of storage. SpinServers doesn't compete at that end of the market: its KVM VPS line starts at 2 vCPU with 4 TB of monthly transfer, and its bare metal starts at $79 a month.

Three things move the bill further than core count does: the traffic allowance and how overage is handled, whether an IPv4 address is included or billed separately, and whether a server you powered off still gets charged. Those rules differ sharply between providers, and they matter more on a cheap plan than on an expensive one, because a $3.50 surcharge is a 100% increase on a $3.48 base.

Below: the full SpinServers line-up with the specifications it publishes, the billing mechanics at four competitors, and a straight answer on which of these you should actually buy.

> **Quick pick:** A $3–$5 VPS for a blog, a bot, a staging box or a small API should come from Cloudzy, Kamatera or UpCloud, not from SpinServers. If your project pushes 4 TB or more of transfer a month, needs a dedicated IPv4 plus IPv6, RAID-10 SSD storage, and root on hardware that isn't shared, price out the SpinServers KVM line first. 👉 [See the current KVM VPS configurations](https://bit.ly/Spinservers)

## The SpinServers cloud line: six KVM configurations, 4 TB to 20 TB of transfer

SpinServers sells two things. The KVM VPS line is the cloud product, and it's built around bandwidth rather than around the lowest possible monthly number. Six configurations are listed:

| Plan | vCPU / RAM | RAID-10 SSD | Monthly transfer | Price | Order |
| --- | --- | --- | --- | --- | --- |
| Simple Application Server, 2 vCPU | 2 / 2 GB DDR4 | 40 GB | 4 TB | On order page | [Check price](https://bit.ly/Spinservers) |
| Simple Application Server, 6 vCPU | 6 / 8 GB DDR4 | 120 GB | 8 TB | On order page | [Check price](https://bit.ly/Spinservers) |
| Simple Application Server, 8 vCPU | 8 / 8 GB DDR4 | 160 GB | 10 TB | On order page | [Check price](https://bit.ly/Spinservers) |
| KVM 12 vCPU | 12 / 12 GB DDR4 | 160 GB | 10 TB | On order page | [Check price](https://bit.ly/Spinservers) |
| Simple Application Server, Xeon 16 vCPU | 16 / 16 GB DDR4 | 320 GB | 15 TB | On order page | [Check price](https://bit.ly/Spinservers) |
| Advanced Application Server, Xeon 32 vCPU | 32 / 32 GB | 500 GB SSD | 20 TB | On order page | [Check price](https://bit.ly/Spinservers) |

Every one of those plans ships with the same base specification:

- 1 Gbps network port
- 1 IPv4 and 1 IPv6 address
- RAID-10 SSD storage
- Port 25 closed by default

That last item deserves a spot in the table rather than a footnote. SpinServers blocks SMTP port 25 on all VPS by default to limit IP abuse, and opening it requires a support ticket with a justification. The company reserves the right to refuse. If you're planning to run a mail server, a cold-email setup or anything that hands off to an SMTP relay over port 25, budget time for that ticket and assume a no.

SpinServers lists the hardware for each configuration without a fixed published monthly rate on the plan page, so I've left the price column honest rather than filling it with a number I can't verify. The figure you pay depends on what the order page quotes for your configuration. 👉 [Get the current configured price](https://bit.ly/Spinservers)

## The bare-metal side starts at $79 a month, which is where the value argument gets interesting

SpinServers' main business is single-tenant hardware. The published configuration pricing has looked like this in review listings current to autumn 2026:

| Configuration | CPU / RAM | Storage | Bandwidth | Listed price | Order |
| --- | --- | --- | --- | --- | --- |
| Entry | Intel Xeon E3-1280 v5, 4 cores / 32 GB | 1 TB NVMe | 30 TB on 2×10 Gbps | $79/mo | [Check availability](https://bit.ly/Spinservers) |
| Starter | Intel E5-1280 v5 / 32 GB DDR4 | 1 TB M.2 NVMe | 10 TB on 10 Gbps | $99/mo | [Check availability](https://bit.ly/Spinservers) |
| Growth | Dual Intel E5-2630L v3 / 256 GB DDR4 | 2×1.6 TB SSD RAID-1 | 20 TB on 10 Gbps | $149/mo | [Check availability](https://bit.ly/Spinservers) |
| High Performance | Quad Intel E5-4640 v2 / 768 GB DDR3 | 8×2 TB SSD RAID-10 | 40 TB on 10 Gbps | $679/mo | [Check availability](https://bit.ly/Spinservers) |

Two caveats before anyone treats those as a price list. SpinServers prices by location, hardware and availability, so the same class of machine can quote differently depending on what's in stock in Dallas or San Jose. And the $79 entry configuration carries 30 TB of transfer on dual 10 Gbps ports, which is more bandwidth than most small teams will use in a year.

The feature set around the hardware is standard for bare metal and worth checking against your own stack: instant provisioning, automated install of Linux, Windows or ESXi, IPMI or iKVM remote management, VPC networking with private Layer 2 connectivity, and a DDoS-protected multihomed network. PCI-compliant facilities are advertised, but managed PCI compliance work and scanning sit with you rather than with SpinServers.

## What actually decides the monthly bill

### The headline price and the renewal price are two different numbers

Cloudzy's $3.48 is 50% off a $6.95 list price. The same discount shows up on the annual option: prepay 12 months, pay the half-price rate, and the plan doesn't auto-renew, so you get an invoice before renewal instead of a silent charge. From month 13 the plan costs $6.95. A "cheap" VPS at $3.48 is really a $6.95 VPS with a first-term discount, and any yearly cost comparison that uses the discounted figure for years two and three is wrong by roughly double.

### A powered-off server is not always a free server

- **Hetzner** bills every cloud server from the moment creation finishes until you delete it, regardless of power state, because resources stay allocated so boots are fast.
- **Kamatera** charges hourly servers according to whether they're powered on or off, and stops charging once you terminate.
- **UpCloud** bills Starter and Premium plans 24/7/365 until deletion. Its Cloud Native plans bill only while powered on, though storage and IP addresses keep billing because they stay allocated.
- **Cloudzy** bills hourly, monthly or annually with no commitment term.

For a temporary project that sits idle for three weeks, those four rules produce four different invoices. Hetzner's model is the one that surprises people.

### IPv4 is a line item, not an afterthought

UpCloud includes IPv4 on Starter plans; an extra public IPv4 or a floating IP costs €3.47 a month. Cloudzy includes IPv4 and IPv6 and charges $2.50 a month for a floating IP. Hetzner's listed cloud prices include IPv4. SpinServers gives every KVM VPS one IPv4 and one IPv6. On a $4 plan, a $3.47 IPv4 charge is most of the plan again, so confirm what's bundled before comparing two headline prices.

### Traffic is where the models diverge most

Cloudzy includes a transfer quota and says it notifies customers about overage rather than throttling the connection. UpCloud charges €0.00 per GiB in both directions, public and private. Kamatera's unmetered hosting package includes up to 5,000 GB a month and bills the excess, and the company says about 90% of its customers stay under 2,000 GB. Kamatera also applies a rule that catches people out: when inbound traffic exceeds 33% of total traffic (a 2:1 outbound-to-inbound ratio), you're billed for the entire traffic volume rather than the excess. Backup-heavy or mirror-heavy workloads can flip that switch without any change in monthly volume.

## How the $3–$4 tier compares

| Provider | Entry price | What that buys | The catch |
| --- | --- | --- | --- |
| Cloudzy | $3.48/mo (from $6.95) | 1 GB DDR5, 1 vCPU at 4.2 GHz+, 25 GB NVMe, 1 TB transfer, 40 Gbps | Discount is first-term; 14-day money-back |
| UpCloud | €3/mo | 1 GB, 1 core, 10 GB storage, 250 Mbit/s, IPv4 included, 99.99% SLA | Previous-gen AMD CPUs; pricing changes on November 16 |
| Kamatera | $4/mo | Configurable server, 99.9% SLA, 30-day trial worth up to $100 on one server | 5,000 GB cap; inbound above 33% bills all traffic |
| Hetzner | Not quoted in the cost-optimized listing reviewed | Older-generation Ampere, Intel and AMD hardware | Limited stock, several models unavailable; billed while powered off |

Two notes on that table. UpCloud's pricing page states that changes to cloud server plans and block storage take effect on November 16, so the €3 figure is the October price and is about to move. Hetzner's cost-optimized page explains its model (proven older hardware, lower prices, limited server quantities) but the listing reviewed carried no numeric figures, and multiple models including cax11, cax31, cax41 and cx53 showed as currently unavailable. Hetzner also states that its own price-performance comparison, based on sparecores.com benchmark data, puts it ahead of competitors, which is the company's claim rather than an independent finding.

The pattern across the cheap tier: lower prices come from older silicon and constrained supply. UpCloud says outright that Starter plans use previous-generation AMD CPUs. Hetzner says the same about its cost-optimized line. Neither is a defect, but neither is a current-generation EPYC at $3 either.

## Where SpinServers is the wrong buy

Be clear about the trade you're making. SpinServers is not the cheap option for a single small project, and four situations should send you elsewhere:

- **You need a $3–$5 server.** The entry tier above does that job, and SpinServers' smallest KVM plan carries 4 TB of transfer you'd be paying for and not using.
- **You need a contractual uptime number near the top of the range.** UpCloud offers 99.999% SLA on Premium plans; Kamatera offers 99.9%.
- **Your bill is dominated by outbound transfer.** UpCloud charges nothing per GiB in either direction, which beats any allowance once you're past a few terabytes.
- **You want to try before committing.** Kamatera runs a 30-day trial worth up to $100 on a single server, UpCloud offers a 30-day trial, and Cloudzy has a 14-day money-back window. SpinServers doesn't publish an equivalent trial on the pages reviewed.

There's also the mail constraint. If port 25 is central to your workload, the default block turns a five-minute deploy into a support negotiation.

## Two things to confirm before you pay

**The refund position.** Review coverage of the dedicated line states that month-to-month services generally carry no refund policy. Combined with the location-dependent pricing, that makes the first invoice the commitment. If you're unsure whether a configuration fits, start with the smallest KVM plan that covers your transfer needs rather than the largest one you can justify. 👉 [Review the current terms on the order page](https://bit.ly/Spinservers)

**Renewal and term.** Confirm whether the price you're quoted is the recurring rate or an introductory one, and confirm what happens at renewal. On a $3.48 plan this is the difference between $42 and $83 a year.

## Which one to buy

Match the decision to the constraint that's actually binding for you:

- **Cost is the constraint, workload is small:** Cloudzy at $3.48, or Kamatera at $4 if you want a trial before paying. Expect Cloudzy's rate to revert to $6.95 after the first term.
- **Egress volume is the constraint:** UpCloud, where transfer costs €0.00/GiB, with the caveat that the price list changes on November 16.
- **Transfer plus dedicated IPs plus root on non-shared hardware:** the SpinServers KVM line, where 4 TB starts at the bottom of the range and 1 IPv4 plus 1 IPv6 come standard.
- **You need the whole machine:** SpinServers bare metal from $79 a month, with 10 Gbps options and IPMI access, in Dallas or San Jose.

For most readers arriving from a search for affordable cloud servers, the honest answer is that SpinServers isn't the cheapest and isn't trying to be. It's the option that stops charging you for bandwidth you'd otherwise meter. 👉 [Start with the KVM VPS line if bandwidth is your bottleneck](https://bit.ly/Spinservers)
