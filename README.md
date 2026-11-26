# AS9929 VPS Guide: Is China Unicom Premium Worth It, What Does SixtyNet Cost, and Which Plan Fits? (Full Plan Table, Port and Refund Limits)

AS9929 is worth paying for when a meaningful share of your users connect through China Unicom and you care about how the connection behaves between 20:00 and 23:00 Beijing time. SixtyNet’s cheapest publicly priced AS9929 VPS is **LAX-STARTER at US$200 per year** (list US$240), which works out to about US$16.67 per month on annual billing for 2 cores, 2GB RAM, 40GB NVMe and 5TB of traffic. Most readers should start there. The residential-IP plans are a different product with a hard restriction: **ports 80 and 443 are not opened**, so they are a poor fit for a website even though they carry the same AS9929 label.

> **Quick pick:** SixtyNet LAX-STARTER, US$200/year (list US$240), 2 cores / 2GB RAM / 40GB NVMe / 5TB traffic, AS9929 premium network and DDoS protection. It is the lowest-priced standard AS9929 plan on SixtyNet’s page and the one that fits a small site, API or proxy for Unicom users. 👉 [See SixtyNet’s current AS9929 VPS pricing](https://sixtynet.net/aff.php?aff=39)

## SixtyNet’s AS9929 plans and prices

SixtyNet’s VPS page separates two lines that look similar but are not interchangeable. The standard LAX plans are the ones with public annual pricing and no residential-IP port restriction. The residential-IP plans are aimed at US residential IP use cases and carry access restrictions that matter more than the CPU count.

| Plan | vCPU / RAM / NVMe | Network / traffic | Price (USD) | Order |
| --- | --- | --- | --- | --- |
| LAX-STARTER | 2 cores / 2GB / 40GB | 2Gbps premium, 5TB, DDoS protection | **$200/yr** (list $240; ≈$16.67/mo) | [ Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-MICRO | 4 cores / 4GB / 80GB | 4Gbps premium, 10TB, DDoS protection | **$400/yr** (list $480; ≈$33.33/mo) | [ Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-MEDIUM | 8 cores / 8GB / 160GB | 10Gbps premium, 20TB, DDoS protection | **$800/yr** (list $960; ≈$66.67/mo) | [ Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-LARGE | 8 cores / 16GB / 320GB | 10Gbps premium, 40TB, DDoS protection | **$1,600/yr** (list $1,920; ≈$133.33/mo) | [ Order](https://sixtynet.net/aff.php?aff=39) |
| Residential 2C | 2 cores / 2GB / 40GB | 2Gbps premium, 5TB, residential IP, no 80/443 | From $35/mo (launch coverage) | [ Order](https://sixtynet.net/aff.php?aff=39) |
| Residential 4C | 4 cores / 4GB / 80GB | 4Gbps premium, 10TB, residential IP, no 80/443 | From $55/mo (launch coverage) | [ Order](https://sixtynet.net/aff.php?aff=39) |
| Residential 8C | 8 cores / 8GB / 160GB | 10Gbps premium, 20TB, residential IP | Not shown | [ Order](https://sixtynet.net/aff.php?aff=39) |
| Residential 16C | 16 cores / 16GB / 320GB | 10Gbps premium, 40TB, residential IP | Not shown | [ Order](https://sixtynet.net/aff.php?aff=39) |
| 4C storage variant (unnamed) | 4 cores / 4GB / 300GB + 200GB RAID10 | 10Gbps premium, 10TB, DDoS protection | Not shown | [ Order](https://sixtynet.net/aff.php?aff=39) |

The four LAX plans are listed with annual prices. The monthly figures above are arithmetic, not a separate monthly billing option shown on the page. The annual discount is consistent at 17%, which saves US$40/year on LAX-STARTER, US$80/year on LAX-MICRO, US$160/year on LAX-MEDIUM and US$320/year on LAX-LARGE. The page does not show whether the discounted annual rate repeats on renewal, so that is one thing to confirm before paying.

The residential configurations are a murkier purchase. The official page lists the 2-core and 4-core plans with “Residential IP” and a notice that ports 80 and 443 are not opened. It does not show a public monthly price for those tiers in the listing; the US$35 and US$55 figures come from launch coverage, not from a price printed next to the plan. The 8-core and 16-core residential tiers also appear without a public price. Treat those as quote-first products until checkout or support confirms the number.

There is also a separate Los Angeles China Unicom-Premium BGP listing at **US$2,500/year** (list US$3,000). That is not a VPS decision: it includes a 100Mbps base network commit, 3x burst rate, 95th-percentile billing, a free BGP session and limited BGP technical support. If you need a committed bandwidth or BGP setup rather than a virtual machine, that is the relevant listing.

## What AS9929 actually changes

AS9929 is China Unicom’s premium international backbone, formally the China Unicom Global VIP Network and often shortened to CUG. It sits above AS4837, the cheaper commercial path that carries most ordinary Unicom consumer traffic. The practical difference shows up at peak hours. On a well-peered Hong Kong or Tokyo route, AS9929 typically sits in the 30–80ms range to mainland China with low packet loss; AS4837 is more likely to congest when Beijing time hits 20:00–23:00. For SSH, RDP, VoIP, APIs and anything with interactive users, lower jitter matters more than a single low ping number.

The route is the product in this category. CPU and RAM are commodity parts; a 2-core AS9929 VPS and a 2-core AS4837 VPS can feel completely different at 21:00 Beijing time. That is why a plan like LAX-STARTER at US$200/year can be reasonable while a cheaper non-optimized VPS is not a substitute for the same workload.

SixtyNet’s page advertises AS9929 for the China-facing network. It does not claim a combined CN2 GIA (AS4809) plus AS9929 plus CMIN2 (AS58807) profile. If your audience includes China Telecom and China Mobile users as well as Unicom users, ask SixtyNet for a test IP or looking-glass before ordering. A good AS9929 node often pairs with CN2 GIA for Telecom and CMIN2 for Mobile, but that is a provider-by-provider detail, not something the AS9929 label guarantees.

## The two specs that matter more than CPU: outbound bandwidth and post-quota speed

SixtyNet’s page lists a “2Gbps”, “4Gbps” or “10Gbps” premium network, but it does not separate inbound from outbound bandwidth. That distinction is not cosmetic. Tudcloud’s Seattle AS9929 plan, for example, is explicit: 2Gbps in and 200Mbps out. Spartan Host’s Seattle AS9929-CMIN2 plans list 10Gb/s in and 200Mb/s to 1Gb/s out, depending on the plan. In both cases, the big number is the inbound port, while the China-optimized outbound path is much smaller.

Ask SixtyNet support what the outbound cap is on the plan you are buying. A 10Gbps port sounds generous until you find out that the China-optimized direction is capped at a few hundred megabits, or that the “premium network” figure is a port speed rather than a guaranteed commit. This is especially important for video, backups, large downloads and anything that pushes sustained traffic toward mainland China.

Post-quota behavior is the other spec that rarely makes it into the headline. Spartan Host throttles to **1Mb/s** after the traffic allocation is used. Tudcloud’s cheaper Seattle AS4837 plan throttles to **5Mbps** after its 1TB allowance. Those are both “service continues” policies, but 1Mb/s is barely usable for a control panel, let alone a website. SixtyNet’s page does not state a post-quota speed. Do not assume “5TB traffic” means unlimited usable bandwidth after 5TB. Ask what happens when the allowance runs out, and get the answer before you pay.

## The residential IP catch: no ports 80 or 443

The residential-IP plans are not a cheaper way to run a website. SixtyNet’s own notice says residential IP products do not open ports 80 and 443 because of IP risk-control rules. The AS9929 residential listings also say access is restricted unless you configure whitelisted IPs or port forwarding, and that the service rejects external probes and scans.

> SixtyNet’s residential-IP listings do not open ports 80 and 443. Access is restricted unless configured; only whitelisted or port-forwarded devices can connect.

That restriction makes sense for the intended use case: a US residential IP for account management, streaming checks, regional app access or a private remote environment. It is the wrong product for a public website, a public API or anything that needs standard web ports. If you want to host a site on SixtyNet, the standard LAX line is the one to compare. The standard LAX plans do not carry the residential-IP port notice.

There is a second financial catch. The page states that refunds for the AS9929 residential-IP product are valid only as website balance. That is different from a cash refund to your original payment method. If you are testing a residential IP for a specific platform, assume the money stays inside SixtyNet if you cancel.

## Refunds, stock and network failures

SixtyNet’s refund policy is narrow enough to matter. A full refund is available within **3 days of invoice creation**, after deducting handling fees, and only if the used transfer quota does not exceed **5GB**. Refunds do not restore promo-code usage counts. Requests are rejected after the 3-day window, for instances that have been transferred, or where the original payment channel cannot accept the refund. Shut the instance down before starting a refund so it does not burn through the 5GB allowance while the request is processed.

That 3-day/5GB window is workable for a quick connectivity test, but it is not a long trial. If you need two weeks to judge peak-hour performance, you are outside the full-refund window. Test the route immediately with a real workload, not just a ping.

Stock is the other reason not to wait. Spartan Host’s Seattle AS9929-CMIN2 page currently shows all eight configurations at **0 available**. A third-party tracker recorded the 16GB plan at **US$96/month**, sold out, with only one restock in 90 days (1 November 2026). That is a useful market signal: premium AS9929 capacity is not sitting on a shelf. SixtyNet’s page does not display inventory counts, so availability is confirmed at checkout. If a plan you can use is in stock at a price you accept, waiting for a better restock is a gamble.

AS9929 also does not make a provider immune to carrier-side problems. Spartan Host reported two China Unicom network failures in a row: one starting 9 November 2026 at 22:35 Asia/Shanghai, affecting AS4837 and AS9929 toward China Telecom with elevated latency and packet loss, and a renewed incident on 10 November 2026 at 19:00 Asia/Shanghai on the same paths. The first incident included temporary alternate routes, and AS4837 congestion cleared before AS9929 fully recovered. The second was still ongoing when reported. The failures were path-level, not a full Seattle datacenter outage.

That is the realistic picture. AS9929 is less congested than AS4837 in normal conditions; it is not a private line. When a carrier interconnect segment has a problem, the VPS provider can switch routes, but it cannot make the carrier problem disappear. Ask any AS9929 provider three questions before ordering: do they publish a status page, do they have alternate routes, and what credit or compensation applies when a China path degrades?

## How SixtyNet compares on the AS9929 shelf

SixtyNet’s strongest argument is price for a standard AS9929 VPS with public annual pricing. LAX-STARTER at US$200/year is cheaper per year than most residential-IP options and includes DDoS protection. Its weakness is that the page leaves out details that matter: outbound cap, post-quota speed, renewal rate and stock count.

| Provider | Verified AS9929 entry point | What to watch |
| --- | --- | --- |
| SixtyNet | LAX-STARTER, US$200/yr, 2C/2GB/40GB, 5TB, DDoS | Residential plans block 80/443; outbound and post-quota speed not stated |
| Tudcloud | US$8/mo, 1 vCPU/1GB/20GB, 1TB, 2Gbps in / 200Mbps out | Cheapest entry; 200Mbps outbound and 24-hour VPS refund window |
| Spartan Host | 4GB to 32GB configs listed, all eight currently 0 available; 16GB tracked at US$96/mo | 1Mb/s after traffic allowance; recent Unicom path incidents |
| DMIT | Pro, EB and T1 profiles; AS9929 in Pro, best-effort in EB, absent from T1 | Tier logic is clear; pricing changes and promos make comparison unstable |

Tudcloud is the low-cost test option if you want to see whether AS9929 helps your workload before committing to an annual plan. Spartan Host is for larger configurations, but availability is poor and the post-quota throttle is brutal. DMIT is the provider to study if you want a formal Pro/EB/T1 split and a three-carrier design, but its plan pricing is not consistent across public write-ups, so verify on its own site rather than trusting a comparison table.

SixtyNet sits between those extremes. It is not the absolute cheapest entry point, and it is not the most transparent network page. It is a reasonable annual prepay for a standard LAX AS9929 VPS if you confirm the missing specs, and it is one of the few options that also sells a US residential IP on the same AS9929 network.

## FAQ

**Is AS9929 better than CN2 GIA?**
They serve different carriers. CN2 GIA (AS4809) is China Telecom’s premium route; AS9929 is China Unicom’s. If your users are mostly on Unicom, AS9929 is the more relevant route. If they are on Telecom, CN2 GIA matters more. A mixed audience is best served by a provider that combines CN2 GIA, AS9929 and CMIN2. SixtyNet advertises AS9929, so ask for a test IP if Telecom and Mobile users are part of the plan.

**Do I need AS9929 if my users are not in China?**
No. You are paying for a China-facing route. For a US or Europe-only audience, a standard Tier 1 VPS is cheaper and just as fast for those users.

**What happens after I use the 5TB or 10TB traffic allowance?**
SixtyNet’s page does not state a post-quota speed. Other providers show how wide the range can be: Spartan Host throttles to 1Mb/s, while Tudcloud’s AS4837 plan throttles to 5Mbps. Ask SixtyNet support directly. Do not assume the instance stays usable at full speed.

**Can I get a refund?**
Yes, within 3 days of invoice creation, with used transfer under 5GB, after handling fees. Refunds do not restore promo-code usage. Residential-IP AS9929 plans refund only to website balance. Shut the instance down before requesting a refund.

**Can I host a website on the residential-IP plan?**
No. Ports 80 and 443 are not opened on the residential-IP products. Use the standard LAX line for a website or public API.

## Which SixtyNet plan to pick

- **Small site, API or proxy for Unicom users:** LAX-STARTER at US$200/year. 2 cores and 2GB RAM are enough for a lightweight workload, and 5TB is generous for the price.
- **More concurrent work and 10TB traffic:** LAX-MICRO at US$400/year. The doubled cores, RAM and traffic are worth the extra US$200/year if you expect real users.
- **8 cores and 20TB:** LAX-MEDIUM at US$800/year. This is the first plan that feels like a small production box rather than a test bed.
- **16GB RAM and 40TB:** LAX-LARGE at US$1,600/year. Only buy this if you already know you need the memory and traffic.
- **US residential IP, no public website:** the 2-core or 4-core residential plan. Confirm the price, the whitelist setup and the no-80/443 restriction before checkout.
- **BGP or committed bandwidth:** the separate US$2,500/year Los Angeles China Unicom-Premium BGP listing, not a VPS plan.

Before you pay, confirm two things with SixtyNet: whether the discounted annual rate recurs on renewal or reverts to the list price, and what the outbound cap and post-quota speed are on your chosen plan. Those two answers decide whether the annual price is a bargain or a one-term discount.

If LAX-STARTER fits your workload, 👉 [start with SixtyNet’s US$200/year AS9929 plan](https://sixtynet.net/aff.php?aff=39) and test the route during Beijing peak hours inside the 3-day refund window.
