# Household Computing — Upgrade Decisions & Reasoning

Covers a single extended planning conversation, June–July 2026. Companion file: `household-computing-overview.md` for current-state summary.

## Origin

Started as a question about Nate's Minecraft lag on his MacBook Air (11", A1465, Intel integrated graphics). Ruled out software fixes — tried Lunar client, then vanilla + OptiFine (best result), then Sodium (didn't work well — modern rendering paths are poorly supported on old Intel Mac GPU drivers, especially since Apple deprecated OpenGL). Concluded the integrated GPU is a genuine hardware ceiling (~40–50 FPS), not fixable in software.

## Monitor: KTC H27T6

- Bought at a discount (£104, reduced from £140). 27", 2K@200Hz (210Hz overclocked), Fast IPS, HDR400.
- Considered and rejected the "should we get 4K/8K instead" question — at 27" and normal desk viewing distance, 1440p is the current sweet spot for gaming; 4K/8K deliver diminishing or imperceptible returns on a screen this size while costing much more GPU headroom.
- For the MacBook Air bridging period: decided **not** to buy a new Mini DisplayPort cable, and to keep using the existing Mini DP→HDMI adapter instead — the MacBook Air can't exceed 1080p60 regardless of cable used, and any Mini DP cable would be made obsolete once a different machine (different port type) eventually drives the monitor.
- Monitor will run at full native spec once Nate's Christmas gaming PC arrives.

## Mac mini — explored at length, ultimately dropped from the plan

Considered as Nate's birthday gift and as a potential household "hub" machine (shared backup host, more powerful shared machine). Reasons for dropping it:

1. **Budget tightened mid-conversation** once the household's full picture came into view (multiple ageing machines needing attention, not just Nate's).
2. **Pricing moved against it**: Apple discontinued the £599 16GB/256GB base config in May 2026, raising the new base to £799 (16GB/512GB). A hoped-for ~£509 refurbished unit never appeared; a refurbished 16GB/256GB unit later did appear, but at £679 (priced off the new £799 baseline, not the old discontinued one).
3. **WWDC 2026 (8–12 June) confirmed no new Mac mini** — M5 Mac mini pushed to an expected Oct/Nov 2026 launch (TSMC silicon supply constraints), removing any "wait a few weeks" rationale.
4. **Farrah's situation changed the equation** (see below) — freed up budget but also removed one of the mini's intended roles.
5. **Cheaper alternative emerged**: hand Matt's 2019 MBP down to Zach once Matt buys his own new machine, and build Nate a proper (upgradeable) gaming PC at Christmas instead. Solves both boys' situations without the Mac mini spend.

## Farrah — MacBook Neo considered, declined

- Explored the MacBook Neo (£599, A18 Pro chip) to replace her 2013 MBP. Surprisingly strong single-core and even Minecraft performance for the price, but real constraints: 8GB RAM with no upgrade option, no Thunderbolt, one USB-C port limited to USB2.0 speeds.
- **Declined**: Farrah reports she rarely uses a laptop now (mostly her phone), and only needs one occasionally for video calls, for which she can borrow Matt's machine. No dedicated replacement needed.
- Her 2013 MBP is still being retired regardless — 12+ years old, capped at macOS Big Sur.

## Zach — inheriting Matt's 2019 MacBook Pro

- Plan: once Matt buys his own new Mac (October birthday), the 2019 MBP (2×TB3, i7, 16GB, Iris Plus 645) passes to Zach.
- Assessed subject-by-subject against Zach's likely A-Levels (Maths, Physics, Computer Science, Music):
  - **Maths/Physics**: no real constraint.
  - **Computer Science**: should be fine long-term — Python/VS Code tooling stays broadly compatible with older macOS for years.
  - **Music — the risk area**: the machine is permanently capped at macOS Sequoia (the 13"/2019 model was dropped from macOS Tahoe/27 support). GarageBand, used at GCSE level, should keep working. Logic Pro, if the A-Level course requires it, has climbing minimum-macOS requirements that could outpace Sequoia within the two-year course window — worth checking the actual exam board/school requirement rather than assuming.
- Battery is degraded but treated as a non-issue given the household's established pattern of running shared machines permanently docked at a desk.

## Nate — gaming PC (Christmas 2026)

- Nate wants to **build** the PC himself, not just receive one — treated as a project/learning opportunity, not just a purchase.
- Build guidance given (parts list deferred until closer to Christmas, since GPU pricing/generations shift fast):
  - **Case**: easiest component to change later — buy for looks/airflow, don't overspend now.
  - **PSU**: worth buying quality and headroom up front — hard to swap later without disruption, and a poor PSU is a real safety/component-damage risk.
  - **Motherboard**: the real long-term constraint — determines CPU socket, RAM generation, and chipset features. Worth choosing one with some roadmap longevity in its socket family and reasonable (not bottom-tier) build quality.
  - **CPU/GPU/RAM/storage**: the genuinely swappable tier — buy reasonably now, upgrade individually later as budget and games demand (GPU typically first).

## Backup Strategy

**Trigger**: no live backup of the ~197GB iCloud Photos library existed — only iCloud sync plus two static external-drive archives (2019, October 2025). This matters because a real corruption event already happened: pre-2019 photos were corrupted in iCloud and only recoverable via the old 2019 archive.

**Time Capsule assessment**:
- No firmware updates since 2018; genuine hardware failure risk at this age.
- **Diagnosed a real throughput problem**: the Xbox, wired directly into the Time Capsule, measured only ~95 Mbps, versus Grandad's laptop (wired directly into the main router) getting close to full package speed. Since the Time Capsule was running in bridge mode (no routing/NAT overhead to explain a slowdown), this pointed more toward a cable or port fault than general processing slowness — never conclusively isolated with a cable-swap test before the household switched ISP/router entirely.
- **macOS 27 will drop AFP protocol support entirely**, which Time Capsule relies on for network Time Machine backups. This only becomes an active problem once a Mac capable of running macOS 27 joins the household (i.e. after Matt's October purchase) — none of the current fleet can run it, so this was a dormant, not urgent, risk.
- **Decision**: retire the Time Capsule from network duty. Repurpose the old Sagemcom (surplus once the new ISP router arrived) as a bridge-mode Wi-Fi access point in the same downstairs spot — a stronger radio (4×4 antennas) than the Time Capsule's, at zero cost.

**NAS**: decided to go straight to a NAS rather than an interim external-drive-on-a-laptop stopgap (rejected specifically because the only always-on candidate, Nate's MacBook Air, is old and would need migrating again once Nate's Christmas PC arrives anyway). Budget options discussed: UGREEN NASync DH2300 (~£243 diskless) as the leading budget pick, versus Synology DS223j/DS224+ alternatives. Leaning toward a single 4TB NAS-rated drive rather than a RAID 1 pair — RAID judged to mainly buy convenience-of-recovery rather than being essential, given the other protections in place. **Not yet purchased; model and configuration left open.** No hard deadline (see Time Capsule/macOS 27 point above) — ideally before October, not urgent before then.

**Cloud backup (Backblaze) — considered, decided against**: iCloud's existing 30-day "Recently Deleted" window already matches Backblaze's default retention tier, and the household's existing habit of periodic manual full-drive archive copies serves the same "point-in-time, long-term" purpose as Backblaze's paid Forever-retention tier, at zero ongoing cost. The genuine remaining gaps (offsite disaster protection, protection against an Apple-account-specific failure) were judged narrow enough — given the manual-archive habit continues — not to justify the ~£70/year ongoing cost.

## Broadband

Started as a simple TalkTalk Fibre 150→500 upgrade question, expanded into a full market comparison once checking the bundled router specs showed the 500 Mbps tier's TalkTalk Wi-Fi Hub 3 wasn't a meaningful upgrade (still Wi-Fi 5, no mesh — same downstairs coverage limitation as the existing Sagemcom).

**Options compared** (24-month total cost, calculated in full):
- TalkTalk Fibre 150 (new contract): £648
- TalkTalk Fibre 500 (upgrade): £792
- Rise Fibre, 900 Mbps symmetric: £740 — uswitch's top result, but confirmed to be a **sponsored placement**, not a genuine best-value ranking. Likely runs over the existing Openreach line (no new cable needed). Well-reviewed (Trustpilot 4.5/5), but not price-fixed — three scheduled rises over the contract.
- Community Fibre 1 Gbps (original leaflet offer): £525
- Community Fibre 2.5 Gbps (phone offer): £486–558, depending on price-fix status
- Community Fibre 1 Gbps, later offer (12 months free, £23/month, confirmed fixed in writing): £276 — cheapest by a wide margin at the time

**Decision**: Community Fibre — final agreed deal was **2.5 Gbps, £25/month, first 12 months free, fixed price**, requiring a new independent FTTP cable install (not reusing Openreach). Completed and working well (~1200 Mbps measured on iPhone 17 Pro).

**Symmetric upload** was a deciding factor beyond price alone — directly relevant to the NAS/backup plans, Xbox Remote Play, and potential future Minecraft server hosting. This ruled out the TalkTalk options on merit as well as price, since their packages are typically asymmetric.

**Declined**: Community Fibre's "Premium WiFi" mesh add-on (confirmed a paid extra, not included in the base package). Judged that the repurposed Sagemcom access point achieves a similar practical outcome for free. Also relevant: Matt had previously tested a same-SSID setup across two access points and found devices exhibit "sticky client" behaviour (won't roam to the closer access point) — so the household is sticking with its existing two-SSID approach rather than paying for proper mesh roaming.

## Router: Linksys SPNM60-CF

Supplied by Community Fibre — Wi-Fi 7, dual-band, part of the Velop Cognitive Mesh family (expandable with further mesh nodes if ever needed). Independent user reports flagged some real quirks: a flaky web admin interface, no companion app, and a long-standing "ghost SSID" bug reported across several Linksys mesh generations. Independent testing (Rtings) suggests no Wi-Fi 7 router currently delivers its full marketed potential — an industry-wide immaturity, not specific to this unit. Early real-world result: ~1200 Mbps measured on iPhone 17 Pro.

## Open Items / Not Yet Resolved

- NAS model and configuration not yet purchased.
- Time Capsule cable/port fault never conclusively isolated (moot now given the new ISP setup, but the diagnostic technique — testing a known-good device at both ends of a suspect link — is reusable if a similar issue crops up elsewhere).
- Xbox Remote Play showing NAT type "Moderate" instead of "Open" on the new router — troubleshooting steps given (try UPnP first; then manual port forwarding with a DHCP reservation or static IP for the Xbox; check for double NAT on the ONT) but not confirmed resolved.
- Zach's USB-to-Ethernet adapter for reducing his Minecraft/gaming lag on Wi-Fi (~£15 fix) — recommended, not confirmed purchased.
- Church's potential switch to MacBook Neo for staff use — status unknown; would affect whether Matt needs a personal Mac at all after October.
- Exact cable needed to drive the KTC monitor at full 1440p200Hz spec from Nate's eventual gaming PC — to be sorted once that machine exists.
