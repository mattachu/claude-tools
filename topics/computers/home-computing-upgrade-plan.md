# Household Computing — Upgrade Decisions & Reasoning

Covers a single extended planning conversation, June–July 2026. Updated October 2026 for Zach's MacBook Neo purchase and Matt's decision not to buy a new Mac. Companion file: `home-computing-overview.md` for current-state summary.

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
5. **Cheaper alternative emerged**: hand Matt's 2019 MBP down to Zach once Matt buys his own new machine, and build Nate a proper (upgradeable) gaming PC at Christmas instead. Solves both boys' situations without the Mac mini spend. *Superseded October 2026: Matt is not buying a new Mac, so the 2019 MBP stays with him and Zach is getting a MacBook Neo instead (see Zach section). The Christmas gaming PC for Nate is unchanged.*

## Farrah — MacBook Neo considered, declined

- Explored the MacBook Neo (£599, A18 Pro chip) to replace her 2013 MBP. Surprisingly strong single-core and even Minecraft performance for the price, but real constraints: 8GB RAM with no upgrade option, no Thunderbolt, one USB-C port limited to USB2.0 speeds.
- **Declined**: Farrah reports she rarely uses a laptop now (mostly her phone), and only needs one occasionally for video calls, for which she can borrow Matt's machine. No dedicated replacement needed.
- Her 2013 MBP is still being retired regardless — 12+ years old, capped at macOS Big Sur.
- **Update October 2026**: Farrah's birthday passed without a new machine, consistent with the above. The MacBook Neo was bought for Zach instead.

## Zach — MacBook Neo (updated October 2026)

**Previous plan (June–July 2026)**: inherit Matt's 2019 MacBook Pro once Matt bought a new Mac. **Dropped**: Matt is not buying a new Mac this year (coffee machine chosen as his main birthday present), and a work MacBook Air is expected. The old concern about the 2019 MBP being capped at macOS Sequoia no longer applies to Zach.

**Decision**: MacBook Neo, 512GB, Touch ID, Citrus, as Zach's birthday present (due end of Oct 2026). Matt's expectation: Zach likely to study Maths at university rather than Music, though A-Level Music is still possible; he doesn't expect Logic Pro to be required at home (exam board/school requirement not checked).

**Specs checked 18 Oct 2026** (Apple's spec page and iFixit):
- A18 Pro, 8GB unified memory (not upgradeable).
- **Two USB-C ports, not equal**: one USB 3 (10Gb/s, supports DisplayPort 1.4), one USB 2 (480Mb/s, charging only). Wi-Fi 6E (not Wi-Fi 7). No built-in Ethernet.
- Per Matt, it runs the latest macOS, so Zach is no longer stuck on an old macOS ceiling.

**Ethernet for Minecraft stability**: the Neo has no built-in Ethernet, so Gigabit vs 100Mbps depends on the adapter, not the laptop. Port choice matters:
- *USB 3 port*: can carry a full Gigabit adapter. It is also the only port that supports DisplayPort, so a monitor and fast Ethernet on this port would need a dock or hub.
- *USB 2 port*: a Gigabit adapter would work but be capped below 1Gbps by the port (inference; no measured throughput found). For Minecraft stability (latency and jitter, not bandwidth) this is probably still ample (judgement).
- Not yet bought. Check the adapter's macOS compatibility before purchase.

**Logic Pro on 8GB (checked 18 Oct 2026; sources are mostly third-party, treat as moderate confidence)**:
- Apple publishes no RAM minimum for current Logic Pro on Mac, according to logicpros.net (third-party). The Apple pages retrieved were older cached versions (macOS 14.4+), so this is not confirmed against Apple's current page.
- One review (OneTwoOneTwo, summarising a creator's benchmark, ~5 months old) reported ~75% CPU at 64 tracks and no memory swap in a Kontakt test, with CPU headroom (about half an M4 Air's performance cores) as the limit.
- Inference: likely fine at A-Level-scale projects; large sample libraries are where 8GB would bite. Untested.
- Education pricing: Apple Creator Studio (includes Logic Pro) listed at £2.99/month or £29.99/year for verified students/educators (Mark Ellis Reviews). A more recent third-party page says eligibility is limited to verified college students and educators, so a school pupil may not qualify; UK eligibility not verified. Standalone Logic Pro is $199.99 in US pricing; UK price not found.
- Suggested test: try Logic on a free trial once the Neo arrives (third-party sites say Creator Studio has a one-month trial, three months with an eligible device; confirm with Apple). Confirm the A-Level Music requirement with the school only if he chooses the subject.

**Other subjects**: Maths/Physics — no real constraint. Computer Science — Python/VS Code tooling should be fine.

## Nate — gaming PC (Christmas 2026)

- Nate wants to **build** the PC himself, not just receive one — treated as a project/learning opportunity, not just a purchase.
- Build guidance given (parts list deferred until closer to Christmas, since GPU pricing/generations shift fast):
  - **Case**: easiest component to change later — buy for looks/airflow, don't overspend now.
  - **PSU**: worth buying quality and headroom up front — hard to swap later without disruption, and a poor PSU is a real safety/component-damage risk.
  - **Motherboard**: the real long-term constraint — determines CPU socket, RAM generation, and chipset features. Worth choosing one with some roadmap longevity in its socket family and reasonable (not bottom-tier) build quality.
  - **CPU/GPU/RAM/storage**: the genuinely swappable tier — buy reasonably now, upgrade individually later as budget and games demand (GPU typically first).

## Backup Strategy

**Trigger**: no live backup of the ~197GB iCloud Photos library existed — only iCloud sync plus two static external-drive archives (2019, October 2025). This matters because a real corruption event already happened: pre-2019 photos were corrupted in iCloud and only recoverable via the old 2019 archive.

**Time Capsule assessment**: currently serves as a Time Machine target (excluding the Photos library) as well as downstairs Wi-Fi. Its **backup role** is being retired — superseded by the planned NAS below, and separately, network Time Machine backups will stop working once macOS 27 drops the AFP protocol it depends on. Its **network role** is not being retired: it's being repositioned as a Gigabit switch in the boys' room rather than downstairs (see `home-computing-network.md` for the full network plan), and will remain in service there until it dies.

**Update October 2026**: Zach's MacBook Neo (arriving end of Oct) runs the latest macOS, so the macOS 27/AFP problem is no longer dormant for him. Matt's view is that the NAS is now needed for wireless backup. Before buying, check the chosen NAS supports Time Machine over SMB (not verified for the UGREEN DH2300). The Photos-library backup need stands separately.

**NAS**: decided to go straight to a NAS rather than an interim external-drive-on-a-laptop stopgap (rejected specifically because the only always-on candidate, Nate's MacBook Air, is old and would need migrating again once Nate's Christmas PC arrives anyway). Budget options discussed: UGREEN NASync DH2300 (~£243 diskless) as the leading budget pick, versus Synology DS223j/DS224+ alternatives. Leaning toward a single 4TB NAS-rated drive rather than a RAID 1 pair — RAID judged to mainly buy convenience-of-recovery rather than being essential, given the other protections in place. **Not yet purchased; model and configuration left open.** Originally no hard deadline ("ideally before October"); priority is now higher given Zach's Neo (see update above).

**Cloud backup (Backblaze) — considered, decided against**: iCloud's existing 30-day "Recently Deleted" window already matches Backblaze's default retention tier, and the household's existing habit of periodic manual full-drive archive copies serves the same "point-in-time, long-term" purpose as Backblaze's paid Forever-retention tier, at zero ongoing cost. The genuine remaining gaps (offsite disaster protection, protection against an Apple-account-specific failure) were judged narrow enough — given the manual-archive habit continues — not to justify the ~£70/year ongoing cost.

## Broadband & Network

Moved to its own file: see `home-computing-network.md` for the full ISP comparison, router notes, and Wi-Fi coverage / Time Capsule retirement plan. The backup-relevant parts of that (NAS as eventual Time Machine target) are covered below under Backup Strategy.

## Open Items / Not Yet Resolved

- NAS model and configuration not yet purchased (priority raised Oct 2026; check Time Machine over SMB support first).
- Zach's Ethernet adapter for Minecraft stability on the Neo — not yet bought. Originally recommended for his old setup; for the Neo, pick the port deliberately (USB 3 vs USB 2; see Zach section).
- Work machine: Matt expects to get a MacBook Air at work, so no personal Mac purchase is planned (updated Oct 2026; replaces the earlier church MacBook Neo item).
- Logic Pro on the Neo's 8GB: no Apple RAM minimum found; test with a trial once the Neo arrives.
- Exact cable needed to drive the KTC monitor at full 1440p200Hz spec from Nate's eventual gaming PC — to be sorted once that machine exists.
- See `home-computing-network.md` for open network/router items (Sagemcom repurposing, Xbox Remote Play NAT issue, Time Capsule's final fate).