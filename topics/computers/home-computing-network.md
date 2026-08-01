# Home Network — Broadband, Router & Wi-Fi Coverage

Related files: `home-computing-overview.md` (device inventory), `home-computing-upgrade-plan.md` (backup/NAS strategy, machine upgrade reasoning).

## Current Setup

- **ISP**: Community Fibre — 2.5 Gbps symmetric, £25/month, first 12 months free, fixed price for the contract term. Own FTTP network (new cable installed).
- **Router**: Linksys SPNM60-CF (Wi-Fi 7, Velop Cognitive Mesh, dual-band, mesh-expandable).
- **Legacy hardware**: old Sagemcom FAST 5364-3.TB (ex-TalkTalk router) intended for repurposing as a downstairs Wi-Fi access point; Apple Time Capsule (5th-gen "tall" model) being phased out of network duty — see below.

## Broadband — Comparison & Decision

Started as a simple TalkTalk Fibre 150→500 upgrade question, expanded into a full market comparison once the bundled router for the 500 Mbps tier (TalkTalk Wi-Fi Hub 3) turned out to be Wi-Fi 5, no mesh — no real improvement on the existing Sagemcom for downstairs coverage.

**Options compared** (24-month total cost):

| Option | Total (24mo) | Avg/month | Speed | Symmetric? | Price fixed? |
|---|---|---|---|---|---|
| TalkTalk Fibre 150 (new contract) | £648 | £27.00 | 150 Mbps | No | No |
| TalkTalk Fibre 500 (upgrade) | £792 | £33.00 | 500 Mbps | No | No |
| Rise Fibre 900 Mbps | £740 | £30.83 | 900 Mbps | Yes | No — 3 scheduled rises |
| Community Fibre 1 Gbps (leaflet) | £525 | £21.88 | 1000 Mbps | Yes | Yes |
| Community Fibre 2.5 Gbps (phone offer) | £486–558 | £20.25–£23.25 | 2500 Mbps | Yes | Unconfirmed at the time |
| Community Fibre 1 Gbps (later offer, 12mo free) | £276 | £11.50 | 1000 Mbps | Yes | Yes, confirmed in writing |

Notes on specific options:

- **Rise Fibre** was uswitch's top-ranked result, but this was later found to be a **sponsored placement**, not a genuine best-value ranking. Likely runs over the existing Openreach line (no new cable needed). Well-reviewed (Trustpilot 4.5/5), genuinely symmetric, but not price-fixed.
- **Community Fibre** required a new independent FTTP cable install (not reusing Openreach), and offer terms shifted several times across leaflet vs phone quotes — always worth getting the final terms confirmed in writing before signing, which is what settled the price-fixing question.

**Decision**: Community Fibre. Final agreed deal was **2.5 Gbps, £25/month, first 12 months free, fixed price** — a better tier than the cheapest quoted option, at a comparable low cost. Installed and working well (~1200 Mbps measured on iPhone 17 Pro).

**Symmetric upload** was a deciding factor beyond price — relevant to NAS/cloud backup uploads, Xbox Remote Play, and potential future Minecraft server hosting (see `household-computing-upgrade-history.md` for the backup reasoning this fed into).

**Declined**: Community Fibre's "Premium WiFi" mesh add-on (confirmed a paid extra, not included). The repurposed Sagemcom access point (see below) was judged to achieve a similar practical outcome for free. Also relevant: a same-SSID setup was tested previously across two access points and found to cause "sticky client" behaviour (devices won't roam to the closer access point) — so the household is sticking with separate SSIDs rather than paying for proper mesh roaming.

## Router: Linksys SPNM60-CF

Wi-Fi 7, dual-band, part of the Velop Cognitive Mesh family (expandable with further mesh nodes if ever needed). Independent user reports flagged some real quirks: a flaky web admin interface, no companion app, and a long-standing "ghost SSID" bug reported across several Linksys mesh generations. Independent testing (Rtings) suggests no Wi-Fi 7 router currently delivers its full marketed potential — an industry-wide immaturity, not specific to this unit. Early real-world result: ~1200 Mbps measured on iPhone 17 Pro.

## Downstairs Wi-Fi Coverage & the Time Capsule

**Background**: the Apple Time Capsule (5th-gen "tall" model, connected via Ethernet to the main router) has been providing downstairs Wi-Fi coverage and doubling as a Time Machine backup target (excluding the Photos library).

**Diagnosed throughput problem**: the Xbox, wired directly into the Time Capsule, measured only ~95 Mbps, versus Grandad's laptop (wired directly into the main router) getting close to full package speed. Since the Time Capsule was running in **bridge mode** (no routing/NAT overhead to explain a slowdown), this pointed toward a cable or port fault rather than general processing slowness — never conclusively isolated with a cable-swap test before the household switched ISP and router entirely, so it's now moot in practice but worth remembering as a diagnostic approach (test a known-good device at both ends of a suspect link) if similar symptoms turn up elsewhere.

**Software end-of-life**: macOS 27 (successor to Tahoe) will drop AFP protocol support entirely, which Time Capsule relies on for network Time Machine backups. This only becomes an active problem once a Mac capable of running macOS 27 joins the household — none of the current fleet can run it, so this was a dormant, not urgent, risk at the time.

**Decision**: retire the Time Capsule from network duty. Repurpose the old Sagemcom (surplus once the new Community Fibre router arrived) as a bridge-mode Wi-Fi access point in the same downstairs spot — a stronger radio (4×4 antennas) than the Time Capsule's older 3-stream 802.11ac, at zero cost. This uses the existing Ethernet run already in place to that location.

## Open Items

- **Sagemcom repurposing as downstairs access point** — planned, not yet confirmed done.
- **Xbox Remote Play** — NAT type showing "Moderate" instead of "Open" on the new router. Troubleshooting steps given: try UPnP first; if that doesn't work, manual port forwarding with a DHCP reservation or static IP for the Xbox (ports: UDP 88, 500, 3074, 3544, 4500; TCP 53, 80, 3074); check for double NAT on the Community Fibre ONT if neither resolves it. Not yet confirmed resolved.
- **Time Capsule** — final fate undecided (recycle vs keep as a supplementary Time Machine target for as long as it still works). See `home-computing-upgrade-plan.md` for the NAS plan that will eventually replace its backup role entirely.
