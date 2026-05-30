# HomeTruth — Memory File

> This file is maintained by Claude. Update it whenever a material change occurs.
> Organised into four memory types: Procedural, Semantic, Episodic, Working.
> Last updated: 2026-03-29

---

## 🔧 Procedural Memory
*How things work — recurring tasks, processes, workflows*

### Deploying the website
- `index.html` and `hometruth-story.html` are deployed via **Vercel** from the repo root
- `vercel.json` is at the root — do not move it or the web files
- Web assets (`images/`) must remain at root for correct relative paths
- Style guide repo: https://github.com/jasonlryan/hometruth-styleguide

### Adding new documents from Google Drive
1. Use `google_drive_search` with query: `fullText contains 'hometruth' or name contains 'hometruth'`
2. Fetch content with `google_drive_fetch` using document IDs
3. Save as `.md` files into the correct `docs/` subfolder:
   - Strategy → `docs/strategy/`
   - Product/technical → `docs/product/`
   - Market research → `docs/research/`
   - Audience-specific → `docs/segments/`
   - Press/media → `docs/press/`
4. Update this MEMORY.md (episodic section) and check if CLAUDE.md folder map needs updating

### Working with brand assets
- Logos and icon live in `brand/`
- Brand tokens (colours, typography, gradients) are in `BRAND.md`
- Full style guide PDF: https://github.com/jasonlryan/hometruth-styleguide/blob/main/brand/HomeTruth%20Development%20Style%20Guide%2014.08.pdf

### Folder hygiene rules
- `gdrive-docs/` no longer exists — docs are now in `docs/` subfolders
- Always MD5-check for duplicates before keeping files (`md5sum file1 file2`)
- Use `mcp__cowork__allow_cowork_file_delete` before attempting `rm` on mounted files

---

## 🧠 Semantic Memory
*What is true — facts, concepts, definitions, stable knowledge about HomeTruth*

### The business in one sentence
HomeTruth is a UK PropTech startup building the definitive digital record for every home — giving homeowners AI-powered control over their property data, while selling aggregated property intelligence to insurers, banks, and green energy providers.

### Core metaphor
**A service log for homes** — like a vehicle's service record, but for your house.

### The dual-flywheel model
1. **Consumer flywheel** — Free AI advisor → homeowner sign-up → Document Vault upgrade (Pro)
2. **Enterprise flywheel** — Consumer data enriches the Property Ledger → sold to B2B partners

### Key market facts (always cite these)
- UK residential housing stock: **£9 trillion**
- UK home insurance market: **£60 billion** — opaque, slow, data-poor
- Target: homeowners, first-time buyers, property investors, landlords

### Business model tiers
| Tier | Who | What |
|---|---|---|
| Free | Homeowners | AI Advisor, save up to 5 responses |
| Pro | Homeowners | Document Vault, insights, smart home integration |
| Enterprise | Insurers, banks, green energy | Property intelligence API, data ledger |

### The founders
| Person | Role | Contact |
|---|---|---|
| **Jason Ryan** | Co-founder, strategy/brand/product | jason.ryan@brilliantnoise.com |
| **Monty Munford** | Co-founder & Acting CEO | monty.munford@gmail.com |

Jason also runs **Brilliant Noise** (AI strategy consultancy) — HomeTruth is separate.

### Strategic messaging priorities
1. Lead with **"property intelligence platform"** — not "insurance"
2. Insurance is the *first application*, not the whole story
3. The AI Advisor is the **acquisition wedge** — free, frictionless, no sign-up
4. The **data ledger** is the scalable revenue engine

### UK-specific context
- Land Registry, EPC ratings, MEES, NHBC, Rightmove, Zoopla, Checkatrade
- Green angle: MEES regulations force landlords to hit EPC minimums
- Key integration targets: Hive/Nest, insurance comparison sites, Checkatrade

### Brand
- **Tagline:** "Simplify Homeownership. Control Your Property."
- **Brand narrative:** "The repository of truth for your home. Your HomeTruth."
- **Font:** Gill Sans (Light 300, Regular 400, Bold 700)
- **Colours:** Orange `#E8651A` (CTAs) · Cyan `#00B4D8` (accent/links) · Purple `#8B3FA0` (secondary)
- **Gradient:** Orange → Purple → Cyan, 135deg diagonal

### Tone of voice
- Clear, confident, human, data-grounded
- Avoid: buzzword stacking, estate-agent speak, overly corporate tone
- No jargon — plain English that homeowners understand

---

## 📅 Episodic Memory
*What has happened — key events, decisions, milestones, session logs*

### Milestones
| Date | Event |
|---|---|
| Jan 2024 | HomeTruth founded by Jason Ryan and Monty Munford |
| Feb 2024 | First proposition and product spec drafted |
| Jun 2024 | Net zero / green angle documented |
| Oct 2024 | Refined proposition written (Jason Ryan, 18.10.24) |
| Nov 2025 | Graduated STYX PropTech VC Living Lab |
| Nov 2025 | $4M valuation secured; pilot partnerships with insurers initiated |
| Nov 2025 | Press release published; journalist article written |
| Mar 2026 | Tech docs updated (MVP scope confirmed) |
| Mar 2026 | $500K seed round in progress |

### Session log
| Date | What happened |
|---|---|
| 2026-03-19 | First Cowork session. Searched local files and Google Drive for all HomeTruth documents. Fetched 18 docs from Google Drive and saved to `docs/` subfolders. Removed 7 confirmed duplicate files. Reorganised folder structure (brand/, investor/, docs/). Created CLAUDE.md and MEMORY.md. |
| 2026-03-19 | Created full content strategy (`docs/strategy/hometruth-content-strategy.md`). Analysed the live website, researched competitors (Home Owner's Passport, Hometree, Neos/Sky), mapped user needs across 4 audience segments. Defined creative platform: "Every home has a truth. Know yours." Four content pillars: Know Your Home, Protect Your Investment, Build Real Value, The Property Intelligence Revolution. 90-day launch plan included. |
| 2026-03-19 | Created content/channel plan (`docs/strategy/hometruth-content-channel-plan.html`). 40+ individual content pieces mapped to pillars with titles, formats, channels, CTAs. Channels: Blog (HomeTruths), X (@HomeTruthUK), LinkedIn (Monty/Jason), Email newsletter, PR. AI drafting workflow defined. Sample week view. Monty's PR calendar. 7 recurring series formats defined. |
| 2026-03-29 | **Folder consolidation audit.** Audited 6 HT-related folders in ~/Documents. Rescued 8 documentation files (PRD, wireframes, user journeys, specs) and 20 persona files from `home_truth_bot` → saved to `docs/product/legacy-bot/` and `docs/personas/`. Deleted 3 redundant folders: `home_truth_bot` (broken git remote, pointed at bmw_season_start), `HomeTruth2` (Bolt.new prototype, no git), `HT Landing Page` (superseded, no git). Renamed `hometruth__x` → `hometruth-chrome`. Updated CLAUDE.md folder map and related repos section. |
| 2026-03-29 | **Cowork folder deep clean.** Deduplicated PDFs (removed 8 exact copies including 5 style guide dupes). Then audited all remaining files for staleness — deleted 26 superseded/redundant files total (20 old investor decks including a 182MB HT.pdf, 5 proposition/spec PDFs now in markdown, 1 duplicate deck mislabelled as Document.pdf). Organised remaining 13 files into subfolders: investor-decks/ (5), strategy-and-product/ (5), brand-and-style/ (1), admin/ (2), plus hometruth-story.html at root. Cowork folder went from ~48 loose files to 13 organised files. |

### Key decisions made
- **2026-03-19** — Moved brand assets to `brand/`, investor materials to `investor/`, all GDrive docs into `docs/` with strategy/product/research/segments/press subfolders
- **2026-03-19** — Web files (`index.html`, `hometruth-story.html`, `vercel.json`, `images/`) kept at root to preserve Vercel deployment
- **2026-03-19** — Content strategy: creative platform is "Every home has a truth. Know yours." Consumer messaging must lead; investor content should be repositioned behind a dedicated section. The AI advisor IS the content product — all content funnels toward it.
- **2026-03-29** — Consolidated HT project folders from 6 down to 3. `hometruth` (this repo) is the single source of truth for strategy/docs. `hometruth-chrome` for the extension. `hometruth-styleguide` for the brand site. All others deleted after rescuing unique content.
- **2026-03-29** — Cowork folder (COWORK/HomeTruth) reorganised: only current/essential PDFs kept, grouped into investor-decks/, strategy-and-product/, brand-and-style/, admin/. The hometruth repo docs/ folder is the canonical source for all strategy, product, and research content in markdown.

### Key competitive intelligence
- **Home Owner's Passport** — direct competitor, already piloting Land Registry title deed access for estate agents (March 2026). One of only three regulated digital property logbook apps. Focused on conveyancing/transactions, not ongoing homeownership.
- **UK Government** — exploring mandating digital property logbooks (2026 consultation). Major regulatory tailwind.
- **Hometree** — 100K+ customers for home services subscriptions. Practical, maintenance-focused. Now pivoting to green home upgrades and financing.
- **Neos** — acquired by Sky in 2021. Smart home insurance with IoT sensors. Prevention-focused model.

---

## 🗂️ Working Memory
*Current state — active tasks, open questions, what's in flight right now*

### Current status (as of 2026-03-29)
- ✅ MVP in active development — tech docs updated today
- 🔄 $500K seed round in progress (for customer acquisition post-MVP)
- 🔄 Pilot partnerships with leading insurers ongoing
- 🔄 Website live at hometruth.io

### Open questions / things to resolve
- Exact MVP launch date not confirmed in documents
- Seed round investor targets not documented here yet
- No Asana project found for HomeTruth — tasks managed informally?

### Active working context
- Jason is working across both HomeTruth and Brilliant Noise — keep them separate
- HomeTruth is at the **build and fundraise** stage — content and strategy work should support both investor narrative and product development

### Files to be aware of
- `docs/product/hometruth-project-knowledge.md` — **the largest file (583KB)**, master knowledge doc, updated 2026-03-19
- `docs/product/hometruth-tech-docs.md` — MVP spec, also updated 2026-03-19
- `investor/HTDeckNov25.pdf` — most recent pitch deck
- `docs/product/legacy-bot/` — 8 docs rescued from deleted `home_truth_bot` folder (PRD, wireframes, user journeys, specs)
- `docs/personas/` — 20 persona files rescued from deleted `home_truth_bot` folder (JSON/CSV data for 7 user segments + lean canvas + proposition)
