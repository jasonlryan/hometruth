# HomeTruth — Project Context for Claude

> This file is the orientation guide for Claude when working in this folder.
> Read it before starting any HomeTruth task.
> For current status, session history, and working context — read **MEMORY.md** too.

---

## How Claude Should Use These Files

| File | Purpose | When to read |
|---|---|---|
| `CLAUDE.md` | Stable project context — what HomeTruth is, brand, folder structure | Every session |
| `MEMORY.md` | Living memory — current status, decisions, session log, open questions | Every session |

### When to update MEMORY.md
Update `MEMORY.md` whenever a **material change** occurs. This includes:

- **Working memory** — update when starting a new task, or when the current status of the MVP, fundraise, or partnerships changes
- **Episodic memory** — log every significant session with a date and summary; record key decisions with rationale
- **Semantic memory** — update when facts change: new market data, revised positioning, new founders/team members
- **Procedural memory** — update when a workflow is discovered, refined, or broken

Do not update MEMORY.md for trivial tasks (e.g. answering a question, writing a short draft). Do update it after: restructuring files, completing research, making strategic decisions, or any session that produces lasting output.

---

## What is HomeTruth?

HomeTruth is a UK PropTech startup building the **definitive digital record for every home** — a secure, AI-powered platform that gives homeowners full control over their property documents, maintenance history, and financial decisions, while selling aggregated property intelligence to insurers, banks, and green energy providers.

The founding insight: buying a home is the biggest financial decision of most people's lives, yet property data remains fragmented, paper-based, inaccessible, and opaque. HomeTruth fixes that.

**Website:** https://hometruth.io
**Founded:** 2024
**HQ:** London, UK
**Stage:** Post-accelerator (STYX Living Lab, graduated Nov 2025), building MVP, seeking $500K seed round

---

## The Founders

| Person | Role |
|---|---|
| **Jason Ryan** | Co-founder & business partner (strategy, brand, product) |
| **Monty Munford** | Co-founder & Acting CEO (public face, tech journalist, industry network) |

Jason's email: jason.ryan@brilliantnoise.com
Jason also runs Brilliant Noise, an AI strategy consultancy — HomeTruth is a separate startup venture.

---

## The Problem

The UK's £9 trillion residential property market is plagued by:

- **Fragmented, inaccessible data** — property history, documents, maintenance records exist on paper, in drawers, or with solicitors
- **Opaque home insurance** — a £60B market where pricing is opaque, claims are slow, and policies are confusing
- **No trusted data layer** — insurers, banks, and green energy providers all make decisions on inaccurate or incomplete property data
- **Homeowner disempowerment** — people manage their most valuable asset with the least transparency of anything they own

---

## The Solution

**Two interlocking products (dual-flywheel model):**

**1. Consumer: AI Property Companion**
- Free, public-facing AI assistant — no sign-up needed, instant chat
- Helps homeowners understand their home's value, risks, and opportunities
- Upgrades unlock the Document Vault (Pro tier)
- Persistent memory of user's property and preferences post sign-up

**2. Enterprise: HomeTruth Property Ledger**
- Aggregated, verified property data sold to insurers, banks, green energy providers
- B2B2C model — consumer adoption enriches the enterprise data layer
- "Value Chain Enabler" for the UK property ecosystem

**The core metaphor:** HomeTruth is a **service log for homes** — like a vehicle's service record, but for your house.

---

## Business Model

| Tier | Customer | Description |
|---|---|---|
| Free | Homeowners | AI Advisor, basic chat, save up to 5 responses |
| Pro (subscription) | Homeowners | Document Vault, personalized insights, smart home integration |
| Enterprise | Insurers, banks, green energy providers | Property intelligence API, aggregated data ledger |

**Revenue streams:** SaaS subscriptions + B2B data licensing + affiliate/referral (e.g. Checkatrade, mortgage providers)

---

## Key Features (MVP Scope)

- **AI Assistant** — Public, no-barrier-to-entry AI chat for homeowners
- **Document Vault** — Secure upload, OCR processing, folder/tag organisation (Pro)
- **Maintenance Scheduling** — AI-driven reminders and contractor matching
- **Property Insights** — Market value tracking, EPC ratings, energy efficiency
- **Smart Home Integration** — Syncs with IoT devices and appliance data
- **Compliance Tracking** — Insurance renewals, building regulations, safety certs

---

## Market Context

- UK residential housing stock: **£9 trillion**
- UK home insurance market: **£60 billion** (systemic inefficiency and data problems)
- UK PropTech sector: rapidly growing, post-COVID digital shift in property management
- Target users: homeowners, first-time buyers, property investors, professional landlords
- Key integrations to pursue: Rightmove/Zoopla, Checkatrade, NHBC, Land Registry, Hive/Nest, insurance comparison sites

---

## Current Status (as of March 2026)

- ✅ Graduated STYX PropTech VC accelerator (November 2025)
- ✅ $4M valuation secured
- ✅ MVP in active development (Tech Docs updated March 2026)
- ✅ Pilot partnerships with leading insurers in progress
- 🔄 $500K seed round in progress (for customer acquisition post-MVP)
- 🔄 Website live at hometruth.io (index.html in this folder)

---

## Brand

**Tagline:** "Simplify Homeownership. Control Your Property."
**Brand narrative:** "The repository of truth for your home. Your HomeTruth."
**Values:** Transparency, trust, empowerment, intelligence

**Typography:** Gill Sans (Light 300, Regular 400, Bold 700)

**Colour palette:**

| Token | Hex | Use |
|---|---|---|
| `--ht-orange` | `#E8651A` | Primary brand, CTAs |
| `--ht-cyan` | `#00B4D8` | "Truth" wordmark, links, primary accent |
| `--ht-purple` | `#8B3FA0` | Secondary brand |
| `--ht-green` | `#43B02A` | Success, positive states |
| `--ht-dark` | `#0F1620` | Page/section backgrounds |

**Brand gradient:** Orange → Purple → Cyan (135deg diagonal)
**Logo:** Building-blocks icon + "Home**Truth**" wordmark (Truth in cyan)

**Style guide repo:** https://github.com/jasonlryan/hometruth-styleguide

---

## Folder Structure

```
hometruth/
├── CLAUDE.md                        ← You are here (stable context)
├── MEMORY.md                        ← Living memory (update each session)
├── BRAND.md                         ← Brand tokens and typography reference
│
├── index.html                       ← Live website (deployed via Vercel)
├── hometruth-story.html             ← Story/narrative page
├── vercel.json                      ← Vercel deployment config
├── images/                          ← Web assets (SVGs, PDF extracts, team photos)
│
├── brand/                           ← Brand assets
│   ├── hometruth-logo.png
│   ├── hometruth-logo-dark.png
│   └── hometruth-icon.svg
│
├── investor/                        ← Investor materials
│   ├── HTDeckNov25.pdf              ← Pitch deck (November 2025)
│   └── DESIGN_BRIEF_INVESTOR.md
│
└── docs/                            ← All strategic & research documents
    │
    ├── strategy/                    ← Proposition, positioning, go-to-market
    │   ├── hometruth-strategy-document.md       ← Core strategy (original)
    │   ├── hometruth-proposition.md             ← Full proposition
    │   ├── hometruth-refined-proposition.md     ← Refined proposition (Oct 2024)
    │   ├── hometruth-proposition-training.md    ← Proposition training (v2, Feb 2024)
    │   ├── ht-proposition-development-based-on-cc.md  ← CarCloud comparison
    │   ├── hometruth-routes-to-market.md
    │   ├── hometruth-content-strategy.md     ← Content strategy (March 2026)
    │   ├── hometruth-content-strategy.html  ← Branded HTML version
    │   └── hometruth-content-channel-plan.html ← Content/channel execution plan
    │
    ├── product/                     ← Product specs and technical docs
    │   ├── hometruth-product-spec.md            ← Full product requirements
    │   ├── hometruth-tech-docs.md               ← MVP spec (updated March 2026)
    │   ├── hometruth-project-knowledge.md       ← Master knowledge doc (large)
    │   └── legacy-bot/                          ← Rescued from home_truth_bot (March 2026)
    │       ├── HomeTruth_PRD.md
    │       ├── 1_HomeTruth_Next_Steps.md
    │       ├── 2_HomeTruth_Wireframes_Refinement.md
    │       ├── 3_HomeTruth_User_Journey.md
    │       ├── 4_HomeTruth_Functional_Specifications.md
    │       ├── 5_HomeTruth_Technical_Documentation.md
    │       ├── 6_HomeTruth_Testing_Feedback.md
    │       └── 7_HomeTruth_Immediate_Actions.md
    │
    ├── personas/                    ← User persona data (rescued from home_truth_bot)
    │   ├── first_time_buyer.json / .csv
    │   ├── existing_homeowner.json / .csv
    │   ├── potential_homebuyer.json / .csv
    │   ├── private_landlord.json / .csv
    │   ├── 2nd_home_owner.json / .csv
    │   ├── home_improvement_enthuisast.json / .csv
    │   ├── new_homeowner_persona.json / .csv
    │   ├── property_investor.json
    │   ├── prop_tech_business_analyst.json
    │   ├── HomeTruth_Proposition.json
    │   ├── categories.json
    │   ├── lean_canvas.json
    │   └── temp_mha.csv
    │
    ├── research/                    ← Market validation and analysis
    │   ├── hometruth-business-plan-validity-research.md
    │   ├── hometruth-business-plan-critical-evaluation.md
    │   ├── hometruth-business-model-comprehensive-validation.md
    │   ├── hometruth-insurtech-opportunity-deep-dive.md
    │   ├── validating-uk-property-market-claims.md
    │   └── hometruth-netzero.md                 ← Green/sustainability angle
    │
    ├── segments/                    ← Audience-specific documents
    │   └── hometruth-landlord-element.md
    │
    └── press/                       ← Press releases and media coverage
        ├── hometruth-graduates-styx-accelerator-press-release.md
        └── journalist-to-founder-hometruth-article.md
```

---

## Related Repos (in ~/Documents)

After a consolidation audit (March 2026), the HomeTruth project folders were cleaned up to three:

| Folder | Purpose | GitHub remote |
|---|---|---|
| `hometruth/` | **This repo** — strategy, brand, docs, website | `jasonlryan/hometruth` |
| `hometruth-chrome/` | Chrome browser extension (property portal analysis) | `jasonlryan/ht_chrome` |
| `hometruth-styleguide/` | Brand/marketing site (Next.js) | `jasonlryan/hometruth-styleguide` |

**Deleted folders** (March 2026): `home_truth_bot` (content rescued here), `HomeTruth2` (Bolt prototype, no unique content), `HT Landing Page` (superseded by this repo's index.html). `hometruth__x` was renamed to `hometruth-chrome`.

---

## Strategic Angles to Keep in Mind

**The data play is the real prize.** The consumer product drives adoption, but the B2B property intelligence ledger is the scalable revenue engine. Every homeowner who uploads documents enriches the data layer that insurers pay for.

**Insurance is the first application, not the whole story.** The platform has legs into mortgages, green energy financing, conveyancing, and landlord compliance. Don't overweight insurance in messaging — lead with "property intelligence platform."

**The AI advisor is the wedge.** Free, no-friction AI chat that helps homeowners is how HomeTruth acquires users. The upgrade path is the Document Vault. This mirrors successful freemium SaaS models.

**UK-specific.** All regulatory, market, and product context is UK-focused (Land Registry, EPC ratings, MEES, NHBC, Rightmove, Checkatrade, etc.).

---

## Tone of Voice (for any content work)

- **Clear** — No jargon. Plain English that homeowners understand.
- **Confident but not arrogant** — We know there's a problem; we're solving it.
- **Human** — This is about people's homes, their biggest asset. Warmth matters.
- **Data-grounded** — Claims are backed by evidence (£9T market, £60B insurance, etc.)
- **Avoid:** buzzword stacking ("AI-powered synergistic ecosystem"), estate-agent speak, overly corporate tone
