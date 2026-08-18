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

## Issues

- **Sagemcom repurposing as downstairs access point/switch** — confirmed plan (see below); not yet physically completed.
- **Xbox Remote Play** — RESOLVED. Root cause was a stuck Remote Play service on the Xbox itself, not network configuration. Fix: hard reboot of the console. NAT now reliably shows Open. Worth trying an Xbox hard reboot first if Remote Play issues recur before troubleshooting the network.
- **Downstairs Ethernet run** — diagnosed as faulty (see below), not yet physically fixed/replaced.

## Downstairs Wi-Fi Coverage & the Time Capsule

**Revised decision (supersedes earlier "retire Time Capsule" plan):** the Time Capsule will continue in network duty until it dies, repositioned as a Gigabit switch in the boys' room rather than downstairs.

**Diagnosed throughput problem — RESOLVED (root cause identified):** the ~95 Mbps downstairs speed was caused by a faulty downstairs Ethernet run, not the Time Capsule. Confirmed by testing the Time Capsule upstairs on a known-good cable (achieved Gigabit) versus testing directly into the TV on the downstairs run (100 Mbps). The downstairs cable is a ~20m flat Cat6 (Amazon UK B088R96D6T) — 20m is well within Gigabit spec (~100m max), so the fault is very likely a damaged pair, bad termination, or a kink/crush point, most likely where it's clipped to the wall, rather than cable length. Not yet proven; needs inspection/retest with the cable unclipped, and replacement if the loose cable still negotiates 100 Mbps. A round Cat6/Cat6a replacement (no need for Cat7/8) is preferred if a new run is needed; estimated cost ~£15–20.

**Revised topology:**
- **Boys' room**: Linksys SPNM60-CF → Time Capsule (Wi-Fi off, used purely as a Gigabit switch) → Xbox Series X + boys' MacBook Air (via Plugable UD-3900 USB-3 adapter) + Farrah's MacBook Pro (via Thunderbolt-to-Gigabit adapter). All three wired devices are 1Gbps-capped regardless of switch, so no capacity loss versus wiring directly into the CF router. Time Capsule's proximity also gives Time Machine backup a direct Ethernet path to the Macs.
- **Downstairs**: Linksys SPNM60-CF → Sagemcom FAST 5364-3.TB (bridge mode, DHCP/routing disabled, used as AP/switch) → Xbox Series X + TV + downstairs Wi-Fi. Sagemcom's 4×4 802.11ac radio is stronger than the Time Capsule's 3-stream 802.11ac, so it's the better downstairs Wi-Fi choice regardless of the switch/AP role.
- **Linksys SPNM60-CF** remains sole router/DHCP/NAT for the whole household. Confirmed via Linksys's own spec page: all three LAN ports are 2.5Gbps-capable (not just WAN) — relevant if any future device needs above-1Gbps wired, since neither legacy device can deliver that.

**Rejected alternative — second SPNM60-CF mesh node:** considered as a way to bypass the damaged downstairs cable via wireless backhaul instead of fixing it, but rejected — a replacement cable (~£15–20) is far cheaper than another mesh node, and wired backhaul avoids wireless-backhaul capacity/consistency loss. Remains a possible future upgrade if better whole-house Wi-Fi roaming is independently wanted, separate from the cable-fault fix.

**Software end-of-life (unchanged):** macOS 27 will drop AFP protocol support, which Time Capsule relies on for network Time Machine backups. Still a dormant risk — no current household Mac can run macOS 27 yet.
