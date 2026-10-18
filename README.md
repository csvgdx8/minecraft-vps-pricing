# minecraft vps hosting: Real Prices, RAM Sizing Rules, and the Right Vultr Plan for Vanilla, Modded, and Cross-Play Servers

Search for minecraft vps hosting and you'll get two different products back: game-specific hosts with a Minecraft control panel, and general cloud VPSs where you run the server yourself. This piece is about the second kind — renting a plain virtual server, putting your own Minecraft instance on it, and paying for actual hardware instead of player slots.

The short answer before the details: Minecraft's main game loop runs on a single thread, so single-core CPU speed sets your TPS ceiling before RAM ever becomes the bottleneck. A 2 GB server at $12/month comfortably runs vanilla for 5–10 players, Paper servers with plugins want 4 GB, and serious modpacks want 8–16 GB. Vultr, the provider covered below, sells that class of machine from $6/month with hourly billing and a $250 trial credit for new accounts — you can have a world running this evening for almost nothing.

> **Quick picks if you're in a hurry**
> - Small vanilla world, 5–10 friends: Cloud Compute **High Performance, 2 GB — $12/mo**
> - Paper server with plugins, 10–20 players: **High Performance, 4 GB — $24/mo**
> - Modded pack (FTB, ATM, Create-heavy): **High Performance, 8 GB — $48/mo**
> - Test or staging world: deploy any plan, destroy it when done — hourly billing means you only pay for the hours the machine exists
>
> New Vultr accounts get **$250 in trial credit, valid for 30 days**. Vultr doesn't advertise a money-back window the way game hosts do; the trial credit is its version of try-before-you-buy. 👉 [Check current Cloud Compute prices](https://www.vultr.com/pricing/?ref=7268283)

## What "Minecraft VPS hosting" actually gets you

A VPS gives you an empty Linux box with full root access: you install Java, drop in a server jar, manage the firewall, and handle your own backups. A Minecraft-specific host gives you a web panel with one-click modpack installers instead. Both are valid, and the difference matters more than most comparison posts admit.

The VPS route pays off in three situations. You want full control over the software stack — any mod loader, any plugin, custom JVM flags, no waiting for a host to whitelist something. You want to run other things on the same machine, like a Discord bot, a web map, or a voice server, on one bill. Or you simply want raw hardware per dollar and don't mind a terminal.

It's the wrong tool if you've never touched a command line and have no interest in starting. Editing a systemd unit to update your modpack gets old fast. For a hands-off experience, a panel host is the honest answer — several of them are compared further down, with real prices.

One more expectation to set: Vultr's support covers the virtual machine, not your modpack. When something breaks at 11 PM, you're reading logs yourself or asking a community.

## Vultr's Cloud Compute plans and prices for Minecraft

Vultr sells one product family that matters here: Cloud Compute, in three shared-vCPU variants plus a dedicated-core line. Regular Performance runs on Intel cores with SSD storage, High Performance on AMD EPYC with NVMe, and High Frequency on Intel with NVMe. There's no Minecraft markup and no player-slot pricing — the player count is whatever your hardware and view distance tolerate.

Here's the full current lineup in the sizes that matter for a Minecraft server:

| Plan | vCPUs | Storage | Transfer | Monthly price | Deploy |
| --- | --- | --- | --- | --- | --- |
| Regular Performance – 1 GB | 1 | 25 GB SSD | 1 TB | $5 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| Regular Performance – 2 GB | 1 | 55 GB SSD | 2 TB | $10 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| Regular Performance – 4 GB | 2 | 80 GB SSD | 3 TB | $20 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| Regular Performance – 8 GB | 2 | 160 GB SSD | 4 TB | $40 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| Regular Performance – 16 GB | 4 | 320 GB SSD | 5 TB | $80 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| High Performance – 0.5 GB | 1 | 10 GB NVMe | 0.5 TB | $2.50 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-performance) |
| High Performance – 1 GB | 1 | 25 GB NVMe | 1 TB | $6 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-performance) |
| High Performance – 2 GB | 2 | 55 GB NVMe | 2 TB | $12 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-performance) |
| High Performance – 4 GB | 2 | 80 GB NVMe | 3 TB | $24 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-performance) |
| High Performance – 8 GB | 4 | 160 GB NVMe | 4 TB | $48 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-performance) |
| High Performance – 16 GB | 6 | 320 GB NVMe | 5 TB | $96 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-performance) |
| High Performance – 32 GB | 8 | 640 GB NVMe | 6 TB | $192 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-performance) |
| High Frequency – 1 GB | 1 | 32 GB NVMe | 1 TB | $6 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-frequency) |
| High Frequency – 2 GB | 2 | 64 GB NVMe | 2 TB | $12 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-frequency) |
| High Frequency – 4 GB | 2 | 128 GB NVMe | 3 TB | $24 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-frequency) |
| High Frequency – 8 GB | 4 | 256 GB NVMe | 4 TB | $48 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-frequency) |
| Optimized (dedicated core) – 4 GB | 1 dedicated | 25 GB NVMe | 2 TB | $28 | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |
| Optimized (dedicated cores) – 8 GB | 2 dedicated | 50 GB NVMe | 3 TB | $56 | [ Deploy](https://www.vultr.com/pricing/?ref=7268283) |

A few things the table doesn't show:

- **Billing is hourly, capped at the monthly rate.** A $12 server costs about a cent an hour. Destroy the instance and billing stops. No contract, no cancellation call.
- **Transfer is a monthly allowance** per instance, sized to the plan. Exceeding it triggers overage billing, though a normal Minecraft server won't get close.
- **Automatic backups add 20% to the instance price.** On the $12 plan that's $14.40 total. Cheap insurance for a world someone spent 200 hours on, but it's a line item most people forget to budget.
- Larger Regular and High Performance sizes exist up to 64 GB, plus General Purpose and Storage Optimized flavors. None of them change the math for servers under 16 GB.

Now the detail worth understanding before you click anything: the three main lines share physical cores with other tenants on the host node. The Optimized line rents you cores nobody else can touch, starting at $28/month. Since Minecraft's tick processing happens on one thread, a noisy neighbor on a shared host node is what turns "fine at noon" into "TPS death spiral at 8 PM" — the classic creeper-farm-next-door problem. For a friends server, shared vCPUs are genuinely fine. For a busy public server, dedicated cores are the upgrade that matters. 👉 [Compare the High Performance plans](https://www.vultr.com/products/cloud-compute/?ref=7268283#high-performance)

## How much RAM a Minecraft server actually needs

Ram requirements scale with mod count more than player count, so sizing rules work better as a table than a formula:

| Your server | RAM to allocate | Vultr fit (High Performance) |
| --- | --- | --- |
| Vanilla survival, 2–5 friends | 1–2 GB | 2 GB, $12/mo |
| Vanilla, 5–10 players, default view distance | 2 GB | 2 GB, $12/mo |
| Paper/Spigot SMP with plugins, 10–20 players | 3–4 GB | 4 GB, $24/mo |
| Light modpack (50–100 mods), small group | 4–6 GB | 4 GB, $24/mo |
| Heavy modpack (FTB, ATM, Create-heavy), 10–20 players | 8–16 GB | 8 GB, $48/mo — or 16 GB at $96/mo |

Three rules that make these numbers work in practice. First, give the Java heap about 75% of the VPS's RAM and leave the rest for the OS — a 4 GB machine wants roughly `-Xmx3G`. Second, use Aikar's G1GC flags rather than defaults; they smooth out tick times noticeably on any hardware. Third, view distance and entity counts matter more than raw player numbers — dropping view-distance from 10 to 8 buys you more headroom than 2 GB of RAM in many cases. Heavily modded packs roughly halve the player capacity of any given size.

## Vultr vs. specialized Minecraft hosts, honestly compared

Specialized hosts win on convenience and price per GB; Vultr wins on flexibility, locations, and pricing that doesn't change after month one. Here are the verified numbers side by side:

| Provider | Cheapest relevant plan | What you get | Refund / trial |
| --- | --- | --- | --- |
| Vultr | $6/mo — 1 GB High Performance (EPYC, NVMe) | Full root, hourly billing, 32 data center locations, free DDoS protection, no MC panel | None advertised; $250 trial credit for 30 days |
| Gravel Host | $1.80/mo — 2 GB Budget (Ryzen 5, panel) | MC panel, one-click modpacks, 2.2 Tbps DDoS on every plan; dedicated Ryzen 9 7950X cores reserved for Ultimate tier | 72 hours |
| Cloudzy | $7.47/mo — 2 GB EPYC VPS (promo) | Full root EPYC VPS, NVMe storage | 14 days |
| OliveVPS | $7.99/mo — 4 GB with Minecraft preinstalled | itzg/minecraft-server container preinstalled, daily snapshots, Docker-based updates | 7 days |

The pricing detail most comparisons skip: promotional rates. Cloudzy's $7.47 is a 50% discount off a $14.95 list price — once the promo ends, you're paying more monthly than Vultr's flat $12 for a comparable 2 GB machine. Compare list prices when you do the math, because first-term discounts are how this industry markets.

Where Gravel Host genuinely beats the general VPS route: a friends server at $1.80 is cheaper than anything here, the panel handles modpacks without a terminal, and 2.2 Tbps of DDoS filtering on every tier is serious capacity for a public server. Where Vultr beats it: the $250 trial credit, hourly billing for disposable test worlds, roughly twice the location count, and the freedom to run other services on the same box. Pick based on which of those you actually need. 👉 [See Vultr's plans and data center locations](https://www.vultr.com/pricing/?ref=7268283)

## Setting up a Minecraft server on a Vultr VPS

The whole process is copy-paste work; the deploy itself takes a minute or two. Current Minecraft requires Java 21 or newer, and Ubuntu 24.04 LTS makes that a one-liner.

1. **Create an account** and add a payment method (card or PayPal). The $250 credit applies automatically to new signups and covers everything you deploy for 30 days.
2. **Deploy an instance:** Products → Cloud Compute → High Performance, pick a size, choose Ubuntu 24.04 LTS, and select the location closest to your players. Vultr has data centers in New Jersey, Atlanta, Chicago, Dallas, Los Angeles, Seattle, Toronto, São Paulo, London, Frankfurt, Amsterdam, Stockholm, Tel Aviv, Mumbai, Singapore, Tokyo, Seoul, Sydney, and more.
3. **Install Java:** `apt update && apt install openjdk-21-jre-headless`.
4. **Set up the server:** create a non-root user, drop the latest Paper jar into its home folder, accept the EULA, and run it under systemd with the heap set to ~75% of RAM plus Aikar's G1GC flags. On a 4 GB plan that core line looks like `java -Xms3G -Xmx3G -XX:+UseG1GC -jar paper.jar nogui`. Shortcut: Vultr's Marketplace has a one-click Minecraft server app that handles this stage for you.
5. **Open the firewall:** port 25565 TCP for Java players. Vultr's firewall is free and configured from the control panel, or use `ufw`. Add 19132 UDP if you'll bridge Bedrock clients with Geyser.
6. **Back up the world:** either enable Vultr's automatic backups (+20% of the instance price) or rsync the world folder on a cron job. Do one of these before installing big mods, not after the first griefing incident.
7. **Optional — a domain:** point an A record at your VPS IP. Using a non-standard port? Add an SRV record (`_minecraft._tcp`) so players can connect without typing a port number.

For Bedrock cross-play, Geyser runs as a Paper plugin and lets Switch, Xbox, and mobile players join the same Java world — no second server needed. 👉 [Deploy a Vultr instance and follow the steps above](https://www.vultr.com/products/cloud-compute/?ref=7268283)

## DDoS, uptime, and the risks of going public

Vultr includes DDoS protection with its cloud compute instances at no extra cost, and its published uptime SLA is 100%, with outages compensated as account credit. For a friends server or a mid-size community, that's plenty.

Go public with a real player base and the picture changes. Public Minecraft servers are common DDoS targets, especially during community disputes, and general-purpose protection isn't tuned for game traffic the way dedicated anti-DDoS networks are. Two upgrades exist at that point: a specialized host with multi-terabit mitigation (Gravel Host's 2.2 Tbps across all plans is the standout number), or a TCPShield-style proxy in front of your Vultr server, which costs nothing to try and handles the worst of it.

## Minecraft VPS hosting FAQ

**How many players fit on the cheapest plans?** The $6 1 GB plan is a minimal setup — think 1–3 friends with reduced view distance. The 2 GB plan at $12 runs vanilla for roughly 5–10 players. A Paper server with a dozen plugins should move up to 4 GB ($24), and 200-mod packs cut any of these numbers roughly in half.

**Can I run Java and Bedrock on the same Vultr server?** Yes. Geyser runs as a Paper plugin and bridges Bedrock clients into a Java world with no second machine. You can also run Mojang's official Bedrock dedicated server on Linux, listening on UDP port 19132.

**Can I upgrade if the server grows?** Yes — moving to a bigger plan is a control-panel change. Vultr doesn't support shrinking an instance back down, so start one tier above current need rather than buying 16 GB "just in case."

**Do I get a Minecraft control panel?** No. You get root SSH and a dedicated IPv4. The Marketplace one-click app covers the initial install, but day-to-day management is file access and console commands. If you want scheduled modpack installers and a game-aware panel, that's specifically what the specialized hosts charge for.

**What happens when the 30-day trial credit runs out?** Your instances keep running and start billing hourly at list price. Destroy what you don't need before day 30; there's no contract to cancel. Unused credit doesn't roll over.

## Which Vultr plan to pick before you deploy

Match the plan to the world, not to aspirations:

- Vanilla with friends → **High Performance 2 GB, $12/mo**, and you're done
- Paper SMP with plugins, 10–20 players → **4 GB, $24/mo**
- Modpack server → **8 GB, $48/mo**; if peak-hour TPS dips, the **2-core dedicated plan at $56/mo** is the fix
- Public network with a proxy → two 8 GB instances instead of one oversized box
- Test or staging world → any plan, hourly billing, destroy it when the test ends

And if you truly never want to see a terminal, skip all of this and use a panel-based Minecraft host — that's a legitimate answer, not a failure.

Before you click deploy, confirm three things: the region closest to most of your players, whether the world matters enough to pay for the backups toggle, and that your heap is set to about 75% of RAM. Everything else is reversible.

👉 [Open a Vultr account with the $250 trial credit and get your world online tonight](https://bit.ly/VulTR)
