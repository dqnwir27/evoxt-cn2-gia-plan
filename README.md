# China Optimized VPS: Is CN2 GIA Worth Paying For, Does Direct 163 Peering Count, and Which Evoxt Plan Do You Actually Need? (Full Plan Table + Yearly Cost Math)

Every "China optimized VPS" on the market is one of four China Telecom tiers wearing a marketing label, and the gap between the cheapest tier and the best one is wider than the gap between any two plans from the same provider. Evoxt's lineup runs from $2.99 to $95.99 a month on identical billing terms across the board. What decides whether your SSH session survives 9pm is the network and location you deploy into, not the core count you paid for.

Below: how to tell the four tiers apart, why a 200 Mbps premium line beats a 1 Gbps generic port during peak hours, which Evoxt plan clears the bar for actual work, and what five competitors charge for comparable routing.

> **Quick pick:** VM-1 at $5.99/month (1 core, 2 GB RAM, 20 GB disk, 500 GB transfer) is the cheapest Evoxt plan that can hold a real site or a proxy shared by more than one person. VM-0.5 at $2.99 ships with 5 GB of disk, which is a tunnel and little else. Add $0.96 and VM-1.5 at $6.95 doubles your cores, the best value in the list. 👉 [See the full Evoxt plan list and current pricing](https://bit.ly/EvoXt)

## Every Evoxt plan, with price and billing cycle

Evoxt prices by resource, not by network. The same plan name costs the same whether you deploy in Kuala Lumpur or Frankfurt, so the table below is also a menu of network choices.

| Plan | vCPU / RAM | Storage | Transfer / mo | Price (USD / mo) | Order |
| --- | --- | --- | --- | --- | --- |
| VM-0.5 | 1 core, up to 6.0 GHz / 512 MB | 5 GB | 250 GB | $2.99 | [Deploy](https://bit.ly/EvoXt) |
| VM-0.75 | 1 core / 1 GB | 10 GB | 250 GB | $4.99 | [Deploy](https://bit.ly/EvoXt) |
| VM-1 | 1 core / 2 GB | 20 GB | 500 GB | $5.99 | [Deploy](https://bit.ly/EvoXt) |
| VM-1.5 | 2 cores / 2 GB | 20 GB | 500 GB | $6.95 | [Deploy](https://bit.ly/EvoXt) |
| VM-2 | 2 cores / 4 GB | 30 GB | 1 TB | $11.99 | [Deploy](https://bit.ly/EvoXt) |
| VM-3 | 4 cores / 4 GB | 30 GB | 1 TB | $14.99 | [Deploy](https://bit.ly/EvoXt) |
| VM-4 | 4 cores / 8 GB | 60 GB | 2 TB | $23.99 | [Deploy](https://bit.ly/EvoXt) |
| VM-6 | 8 cores / 8 GB | 60 GB | 2 TB | $29.99 | [Deploy](https://bit.ly/EvoXt) |
| VM-8 | 8 cores / 16 GB | 80 GB | 3 TB | $47.99 | [Deploy](https://bit.ly/EvoXt) |
| VM-12 | 16 cores / 16 GB | 80 GB | 3 TB | $60.95 | [Deploy](https://bit.ly/EvoXt) |
| VM-16 | 16 cores / 32 GB | 100 GB | 5 TB | $95.99 | [Deploy](https://bit.ly/EvoXt) |

Every plan includes a weekly offsite backup at no extra charge, root access, a browser VNC console, firewall rules managed from the control panel, VM cloning, IP reassignment and floating IPs, and OS templates that include Windows RDP alongside the usual Linux images. Billing runs from monthly up to three years, and you can top up account credit and let it settle future invoices. Individual resources can be added to a running VM without moving to a different plan.

Two things the table does not tell you. Port speed isn't listed on Evoxt's own pricing page, though third-party test tables of this lineup list 1 Gbps on every plan. Transfer allowances are as published on the pricing page; check the figure on the deploy screen before you commit, since that is the number your monthly usage is measured against.

## What "optimized" actually means: four tiers, one label

China Telecom's international capacity comes in four grades, and every provider selling to Chinese users is buying one of them.

**AS4134 (ChinaNet, "163")** is the cheap default. Huge capacity, and it fills up every evening when residential traffic peaks. Most cloud providers route China-bound traffic here without mentioning it.

**CN2 GT (AS4809 Global Transit)** was built to escape that congestion. For years now it has performed about as badly as the plain 163 route at peak while still costing the provider more, so you pay extra for the label rather than the experience.

**CN2 GIA (AS4809 Global Internet Access)** is the premium grade. Transit pricing has reached $120 per megabit in some markets, which is why a full 1 Gbps commit could theoretically produce a six-figure monthly bill. It is the tier that holds steady for video calls, interactive SSH and game traffic.

**CTGNet (AS23764)** is the newest premium option and performs close to CN2 GIA at similar pricing.

The only question worth asking a sales page is which of those four it is actually buying. Plenty of budget "China optimized" plans are repackaged 163 with a new sticker on the box.

## Direct peering to 163 is not the same as fixing it

SoftShellWeb builds its China pitch on direct peering with China Telecom's 163 backbone in San Jose. That is a real thing and it does help: cutting third-party transit hops removes places where packets queue, and it removes the unpredictable Tier-1 detours that make generic US hosting so inconsistent after dark.

It does not add capacity to the 163 backbone itself. Fewer hops to a congested network still lands you on a congested network. When a provider's entire China story is "we peer with 163," you are buying a shorter path to the same evening slowdown. The same page also notes its 1 Gbps uplink is a shared port on the host node, which is honest and worth remembering when you compare it against a plan advertising a dedicated-looking gigabit.

## Three carriers, three different premium routes

CN2 GIA solves the Telecom half of the problem and nothing else. Unicom's premium return path is AS9929. Mobile's premium international line is CMIN2, which runs on AS58807. A plan labelled only "CN2 GIA" is optimized for Telecom users; if your own connection is Unicom or Mobile, or a meaningful share of your visitors are, you are paying premium money to travel the standard path.

Providers do not always name the Unicom leg the same way. BandwagonHost describes its Los Angeles DC9 line as CN2 GIA plus CMIN2 plus China Unicom Premium on AS10099, while ZgoCloud labels its Unicom leg AS9929 and never mentions 10099. Those are different numbers, and neither vendor documents how they relate, so treat the labels as separate claims rather than one route with two names.

When a provider claims three-network optimization, ask which route each carrier returns over: Telecom to CN2 GIA or CTGNet, Unicom to 9929, Mobile to CMIN2. If the answer is a single line item, the claim is a single-carrier claim.

## Port speed is not bandwidth, and 200 Mbps can beat 1 Gbps

Two numbers get confused constantly. A 1 Gbps, 2.5 Gbps or 10 Gbps figure in a plan table is a port speed, the ceiling your VM can burst to on the host node. What you can actually push toward China at 9pm is a different number entirely. Premium CN2 GIA capacity is finite, and the typical allocation per VM is around 200 Mbps on a fair-use basis, not a gigabit. Neither figure is dishonest; they answer different questions.

That is also why a 200 Mbps premium plan can feel quicker than a 1 Gbps generic one for interactive work. Packet loss and jitter set the pace during peak hours, not the port ceiling. A gigabit port that drops 20% of packets under load is slower in practice than a 200 Mbps line that doesn't.

There is one more hard limit worth knowing before you buy premium routing. CN2 GIA capacity is scarce and providers do not tolerate attacks on it; when a VM gets hit, the usual response is nullrouting the IP until the traffic stops. If you need always-on DDoS filtering, the cheaper ChinaNet path is the better-suited tool.

## Location buys more latency than plan size does

Rough numbers for a good premium route: Hong Kong to southern China often runs under 30 ms, Tokyo to the east coast under 50 ms, and Los Angeles around 130–160 ms. Asia-based plans usually pay for that proximity with a 100 Mbps fair-use cap and a higher price per gigabyte. Los Angeles gives you more transfer for the money at three to five times the round trip.

Choose by workload. Interactive work such as SSH, RDP or a real-time dashboard feels noticeably better from Hong Kong. Bulk transfer, CDN origins and anything serving users on the US side belong in Los Angeles.

This is where Evoxt's structure matters more than its spec sheet. Its pricing page sells single-core clock speed and low prices, and it makes no China route claim at all; the plan table is identical across locations. The China-relevant option is the optimized network in Kuala Lumpur. A third-party route test of that line reported Telecom returning over CN2 GIA (AS4809), Unicom over AS9929, and Mobile over a direct CMI connection, with a 1 Gbps port across the plans. The same test identified a 4th-gen EPYC Genoa with a 4.2 GHz boost on that hardware, a useful check against the "up to 6.0 GHz+" headline: the clock you get depends on the node you land on.

Frankfurt is a different product in practice. The same reviewer's test of a Frankfurt VM-0.5 measured 243 ms to Tokyo and 160 ms to Singapore, with the Unicom return running over AS4837 into Germany. Fine for European traffic, wrong tool for Chinese users.

## The real cost, normalized to a year

Published prices mix monthly, quarterly and annual billing, which makes cross-provider comparison meaningless until you convert them.

| Reference | Published price | Per year |
| --- | --- | --- |
| Evoxt VM-0.5 | $2.99 / mo | $35.88 |
| Evoxt VM-1 | $5.99 / mo | $71.88 |
| Evoxt VM-1.5 | $6.95 / mo | $83.40 |
| BandwagonHost EC-1GB | $49.99 / quarter | ≈ $199.96 |
| ZgoCloud LA Optimised Starter | $116 / yr | ≈ $9.67 / mo |
| HostDare CKVM1 | $55.99 / yr | ≈ $4.67 / mo |
| Incognion MECO-VPS-1 | €19.99 / mo | ≈ €239.88 |

Evoxt bills up to three years in advance, but its pricing page publishes no term discount, so do not assume a multi-year prepay is cheaper until the cart shows you one. For a China-facing deployment, paying monthly for the first cycle is the cheaper mistake: routing is the one thing you cannot evaluate from a spec table, and a month costs you $5.99 instead of three years of regret.

👉 [Start on VM-1 at $5.99/month and verify the route before prepaying](https://bit.ly/EvoXt)

## How the competition compares on routing

These are published prices and route claims, nothing else. All five charge more per unit of CPU than Evoxt and all five are selling routing rather than hardware.

| Provider | Route claim | Entry price | Main limitation |
| --- | --- | --- | --- |
| BandwagonHost | CN2 GIA + CTGNet; LA DC9 adds CMIN2 (AS58807) and China Unicom Premium (AS10099); Hong Kong, Osaka, Tokyo, Singapore on the Ultra line | EC-1GB at $49.99/quarter (≈ $200/yr) | The most expensive per gigabyte here; CN2 GIA is not DDoS-tolerant and attacked IPs get nullrouted |
| ZgoCloud | CN2 GIA + AS9929 + CMIN2 on LA Optimised; 9929 + CMIN2 only on the cheaper LA AMD line | $116/yr (≈ $9.67/mo) | Premium plans allocate 200 Mbps; its Asia locations cap at 100 Mbps fair use |
| HostDare | CN2 GIA + CU + CM in Los Angeles | CKVM1 at $55.99/yr (≈ $4.67/mo) | Entry plans capped at 50 Mbps uplink; HDD storage; 3-day refund window with conditions, and 20% bandwidth use can void it |
| SoftShellWeb | Direct China Telecom 163 peering in San Jose | $5/mo | 163 is the congested tier; the 1 Gbps is a shared port |
| Incognion | Claims direct Telecom (CN2), Unicom (AS4837/AS9929) and Mobile routing; no KYC, crypto payments | €19.99/mo | Priced in euros, so the entry cost lands well above the US-focused options |

Read that table as a price ladder for routing quality. HostDare is the cheapest way onto a genuine CN2 GIA return path with an annual commitment and a hard 50 Mbps ceiling. ZgoCloud charges roughly double for a tri-network line at 200 Mbps. BandwagonHost charges the most and gives you the most locations, migration between them, and a 30-day refund window. SoftShellWeb is the budget bandwidth play and the weakest China routing claim of the five.

## Who should not buy premium routing at all

A single personal tunnel moving a few hundred gigabytes a month does not need tri-network optimization. You will not notice the difference between 9929 and plain 163 on a Telegram proxy at 11pm, and you will pay two to four times as much for the privilege.

Anyone who needs protection against sustained attacks should stay off CN2 GIA entirely. Scarce premium capacity gets nullrouted rather than defended.

And if your users are all inside one city in southern China and 25 ms versus 140 ms changes whether your product works, no amount of tuning a US-based VM gets you there. You need the box in Hong Kong, and you should budget accordingly.

## FAQ

**Is "China optimized" the same as CN2 GIA?**
No. The label covers four Telecom tiers, and direct peering with the 163 backbone is routinely sold as optimization. Ask which tier, and confirm the answer names an ASN.

**Why would a 200 Mbps plan beat a 1 Gbps one?**
Because 1 Gbps is the port ceiling on the host, while 200 Mbps is the premium capacity allocated to your VM. During peak hours, loss and jitter on the international segment decide your real throughput, and the premium line has less of both.

**Is Hong Kong always faster than Los Angeles?**
Lower latency, yes: often sub-30 ms versus 130–160 ms. Faster for bulk transfer, usually no. Asian locations typically cap at 100 Mbps fair use and cost more per gigabyte.

**Can I test the route before committing?**
Deploy monthly, then run a traceroute from your own connection during peak evening hours, and check which ASN each carrier's return path lands on. That one test tells you more than any plan table.

**Does Evoxt's cheapest plan work as a website host?**
VM-0.5 gives you 512 MB of RAM and 5 GB of disk. That is a proxy or a single static page. A real site with a database starts at VM-1, and VM-1.5 is the better buy once you want a second core.

## Before you order

Match the plan to the job. A personal tunnel with light traffic: VM-0.5 at $2.99, monthly billing, no prepay. A small site or a proxy several people share: VM-1 at $5.99, or VM-1.5 at $6.95 for the extra core. Docker, a database and a couple of services: VM-2 at $11.99 or VM-3 at $14.99. Anything above that is capacity you should only buy after measuring.

Three things to confirm on the order screen: which location and network you selected, since that decides your China latency far more than the plan does; the actual transfer allowance attached to the plan; and the refund terms for your location, because prepaying three years is only sensible after a monthly cycle has proven the route on your own line.

👉 [Check Evoxt's current plans, pick a location, and deploy in a few minutes](https://bit.ly/EvoXt)
