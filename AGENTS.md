# Amici Pitch Deck — Context for Claude

## What is Amici

Amici is a Swedish pre-seed startup building an event platform for mid-market companies (20-500 employees) that don't have dedicated event staff. The platform lets companies describe an event, see pre-negotiated prices from matched suppliers instantly, adjust inputs with live price updates, and book in minutes.

## Current stage

- Founding team of 4: Carol (CEO), Anders (Chef/Co-founder), Daniel (Product & Design), Edin (Engineering). Team goes full-time with this round.
- ~20 events delivered through manual concierge operations (chef bookings for Hermès, Prada, Sail Racing, Chimi)
- V2 platform live with user accounts, event management, transaction messaging
- Raising 10M SEK pre-seed to take the team full-time, hire sales and marketing in parallel, and scale the multi-service platform

## Business model

- Amici charges suppliers a 20% commission (supplier-side, not customer-side)
- The customer sees transparent, direct pricing with no markup
- This is a key differentiator from agencies who charge the customer 15-20% on total cost
- Future revenue streams: concierge services (white-glove add-on), supplier SaaS tools, supplier kickbacks on volume

## Key narrative decisions

- Traction is framed as "we ran events by hand on purpose" — deliberate customer discovery, not a pivot
- The manual concierge phase validated demand, buyer profile, and founder-market fit
- Amici targets companies that would never hire an agency — a different tier of the market, not competing with agencies directly
- The competitive advantage is multi-service orchestration (coordinating the whole event), not just matching a single supplier

## Market data sources

- 9.1% CAGR: Sweden's event market, fastest-growing in Europe. Source: Allied Market Research, Europe Events Industry Forecast 2021-2030
- 8.7% CAGR: European corporate events market overall. Same source
- 7.2B SEK TAM: Bottom-up math — 30K companies × 4 events/year × 60K SEK avg. spend
- 30K+ companies: SCB (Statistics Sweden) company registry, companies with 20-500 employees

## Technical notes for the deck

- Single self-contained HTML file — all CSS, JS, and content in one file
- Dark theme, blue accent (#3B82F6), green for market/business model slides (#22C55E)
- Slide navigation via keyboard arrows, click dots, or swipe
- Responsive with breakpoints at 1280px, 900px, and 600px
- Staggered fade-up animations on slide transitions
- Two product mockups on the Vision slide: mobile phone frame (event organizer view) and desktop browser frame (supplier dashboard)

## When editing this deck

- Always ask before making changes to files
- Preserve the existing visual design system (colors, typography, spacing, animations)
- Follow pitch-copy best practices: no em dashes, no buzzwords, assertion headlines, human tone
- Source any market claims with credible data
- The deck is deployed to Vercel via GitHub — changes to main auto-deploy
- **IMPORTANT: The deck is bilingual (Swedish + English).** When changing any text, always update BOTH the HTML default text AND the corresponding entries in the `translations.sv` and `translations.en` objects in the `<script>` block. Swedish is the default language. Both versions must have matching tone of voice — natural and idiomatic in each language, not stiff direct translations.
- After every decision or direction change agreed with the user, update the "Decision log" section below with what was decided and why

## Decision log

- **2026-03-09:** Replaced the duplicate "15-20% agency markup" card on the Why Now slide with a digitization gap card. Stat: #3 from bottom in digitization. Source: McKinsey Global Institute, Industry Digitization Index. Reason: the agency markup was already shown on the Problem slide.
- **2026-03-09:** Refined the third Why Now card from "0 platforms that do this" to "0 digital alternatives to agencies." Reframed to acknowledge single-service platforms and agencies exist, but highlight the gap: no platform combines multi-service orchestration with digital delivery. Positions Amici as the "digital event agency" without using that phrase.
- **2026-03-09:** Added decision log rule to CLAUDE.md. Every decision or direction change agreed with the user must be appended here so future sessions inherit full context.
- **2026-03-09:** Repositioned Amici as a "digital event agency" throughout the deck. Updated cover subtitle, insights quote, business model headline ("Commission today. Scale tomorrow."), competitive landscape, Ask roadmap, and traction step 4 to use "digital event agency" language consistently.
- **2026-03-09:** Removed exact revenue/income numbers from the deck. Removed ~50K SEK/month booking value from traction stats and business model slide. Changed "Revenue growing" to "Demand growing" on the Ask slide. Kept 20% commission rate on business model slide (describes the model, not revenue).
- **2026-03-09:** Overhauled traction slide timeline to tell the founder journey: (1) consumer app for chef bookings, (2) pivot to B2B with V2 platform, (3) crossroads — become supplier or build the orchestrator customers keep asking for, (4) next steps. Moved brand names (Hermès, Prada, Sail Racing, Chimi) to the right side panel as a subtle "Trusted by" list, replacing the old stats. Kept ~20 events delivered as the one remaining metric.
- **2026-03-09:** Removed EventLogic from competitive landscape slide. Simplified to 4 columns: DIY → Single platforms → Amici → Traditional agencies. Reframed Amici as the more accessible, powerful digital alternative to traditional event firms. Updated moat text to explain why Amici beats traditional agencies.
- **2026-03-13:** Removed Airbnb reference, customer service fee, and ~50K SEK/month booking volume from Business Model slide (slide 10, data-slide="9"). Kept only the 20% supplier commission. Customer service fee may be added in the future but isn't live yet. Note: slide numbers in this log refer to the UI indicator at the bottom of the deck, not the data-slide attribute.
- **2026-03-13:** Trimmed Competitive Landscape slide (slide 11) boxes to max ~3 lines each, focusing on market positioning not pricing. Reframed Amici box from "built for companies that would never hire an agency" to "agency power without the agency price tag" — Amici pulls from both ends of the spectrum (DIY/single-platform users moving up, and potential agency customers moving down).
- **2026-03-14:** Strategic overhaul of product positioning. Amici is a "supplier network and matching platform," not a "digital event agency." Amici never coordinates events. Coordination responsibility sits with the customer (self-service) or a professional event coordinator (add-on). Replaced all "digital event agency" and "orchestrate" language throughout the deck.
- **2026-03-14:** Added customer user flow slide (slide 9) showing the two paths: simple events (supplier contacts customer directly) and complex events (platform recommends event coordinator add-on). When coordinator is booked, Amici guarantees coherent experience. When declined, customer self-coordinates with no coherence guarantee from Amici.
- **2026-03-14:** Added "Agencies sell human hours. Amici sells software and network effects." as the key competitive framing on the business model and competitive landscape slides. This is the core scalability argument for investors.
- **2026-03-14:** Clarified supplier offer flow: suppliers respond to Amici, Amici packages and presents offers to customer. Customer does not interact with suppliers during the matching phase.
- **2026-03-14:** Event coordinators are not a marketplace. They are professionals Amici collaborates with explicitly. This is a curated relationship, not an open marketplace.
- **2026-03-14:** Traditional agencies are positioned as the main competitor. The competitive advantage is structural: platform economics vs. labor economics.
- **2026-03-14:** Kept the "supplier engine" vision slide (now slide 7, data-slide="6") but broadened it. Changed "agencies can plug into" to "anyone can plug into." Changed "coordination" to "matching" and made the potential audience more open-ended (agencies, other platforms, corporate tools).
- **2026-03-14:** Merged Why Now cards #2 (digitization gap) and #3 (zero digital alternatives) into one card. They made the same point. Added new third card: "The tech to match suppliers at scale finally exists" (10x cheaper to build today). Stat-label: CHEAPER TO BUILD TODAY.
- **2026-03-14:** Shortened traction slide timeline titles: "Started with chef bookings", "Pivoted to B2B", "Supplier or platform?", "Now: concierge to platform". Design rule: no title should have exactly one word on the second line (must be 0 or 2+ words wrapping).
- **2026-03-14:** Changed "Most events need more than one supplier" to "Many events" on the Insights slide. Too bold a claim without data.
- **2026-03-14:** Removed standalone How It Works slide (was too complex). Integrated a 5-step flow into the Product slide instead: (1) Describe your event, (2) We match suppliers, (3) Review offers, (4) Book and pay, (5) Want coordination? Step 5 uses amber styling as a decision point. The split is about whether the user wants coordination, not about event complexity.
- **2026-03-14:** Reordered slides. New order: Cover, Problem, Why Now, Traction, Insights, Product, Competitive Landscape, Vision (mockups), Vision (supplier engine), Market, Business Model, Team, The Ask. Rationale: product and competitive positioning right after insights (concrete before visionary). Vision slides expand on where the company is going after establishing what it does and how it's different. Deck is now 13 slides.
- **2026-03-19:** Narrative overhaul: "going full-time" to "platform built, proving demand." Daniel and Edin stay part-time this round. Raise funds sales/marketing hires, not founder salaries. Changes: (1) Traction slide final step updated to "platform built, proving demand." (2) Team slide headline changed to "Built lean. Staying lean." with transparency about part-time roles framed as capital efficiency; added "Hiring with this round" card for sales/marketing. (3) Ask slide headline changed to "Platform built. Time to find customers." with use-of-funds section (no percentages) and 2-year roadmap (Year 1: prove demand, Year 2: scale platform). All "full-time" references removed.
- **2026-03-19:** Updated traction timeline steps 3 and 4. Replaced "The crossroads: supplier or platform?" (step 3) with "Level up sales and marketing" as an upcoming step (arrow, not checkmark). Changed step 4 to "Next: build the multi-service platform" in future tense. Both steps 3-4 now use arrow styling to indicate forward-looking goals.
- **2026-03-19:** Renamed section labels for slides 6, 7, and 8 from "Product" and "The Vision" to "Product Vision" across all three slides. Groups the product demo and vision slides under one consistent label.
- **2026-03-19:** Full deck consistency pass. Key clarification: platform is already multi-service (chef-focused with venues/rentals/equipment as add-ons), not something being built. Changes: (1) Traction step 4 changed to "expand across verticals" with AI-powered workflows mention. (2) Insights quote changed from "we're building" to "we built." (3) Business model "Next" card: "add supplier categories" changed to "deepen coverage across supplier categories." (4) Team subheadline rewritten to avoid part-time/full-time labels entirely; removed "Part-time" from Daniel and Edin role labels. (5) Ask slide: removed use-of-funds cards, enhanced roadmap cards with bold on cost items, removed italic CTA line.
- **2026-03-20:** Added "The Platform" slide (slide 13, data-slide="12") between Team and The Ask. Three stat cards: 84 shared components, 4 apps from one codebase, 0 legacy debt. Plus a full-width bottom card on technical debt avoidance. Translates Edin's monorepo architecture into investor-relevant business value (capital efficiency, speed, reduced risk). Source: technical-overview.md from Edin. Deck is now 14 slides. The Ask slide bumped to data-slide="13".
- **2026-03-20:** Added bilingual support (Swedish + English) with a language selector. Swedish is the default language. Language selector is a subtle "SV ▾" / "EN ▾" toggle in the fixed top-right corner with a dropdown showing "Svenska (SV)" and "English (EN)". 155 text elements translated using `data-i18n` attributes and a JS translations object. Language persists via localStorage and supports `?lang=sv`/`?lang=en` URL parameter override. Swedish copy is idiomatic, not direct translations. Source citations stay in English. All future text changes must update both `translations.sv` and `translations.en` in the script block.
- **2026-04-18:** Product repositioning — instant pricing. Amici now holds enough supplier pricing data and vertical coverage to show confident prices directly in the booking request. Users adjust inputs (guests, date, format) and watch prices update live. Replaces the old "suppliers respond within 24h, Amici packages offers" flow on slides 5 (product flow) and 7 (mockups). Changes: Slide 5 steps rewritten to "Describe → See prices instantly → Adjust and book." Connector copy, time metric (`< 24 hrs` → `Minutes`), and bottom summary rewritten around live-updating pricing. Slide 7 subheadline and arrow description rewritten to describe real-time pricing from pre-negotiated rates.
- **2026-04-26:** Swedish translation polish. Rule: use established English loanwords where they're standard in Swedish startup/business context rather than direct translations. Applied: "Traktion" → "Traction", "funktion/funktioner" → "feature/features" (platform slide), "skeppas" → "rullas ut", "arkitektuerades" → "byggdes från grunden", "designdrift" → "Konsekvent design", "Per event, från start till mål" → "från start till slut", and a grammar fix ("prissätter realtid" → "prissätter i realtid"). Reverted: "ackumuleras" and "Skräddarsytt" were fine as-is.
- **2026-04-26:** Removed all source citations from the deck for consistency (previously: Allied Market Research on Why Now + Market slides, McKinsey on Why Now, SCB on Market). Replaced Why Now card 2 stat "#3 / Från botten i digitalisering" (McKinsey 2015, outdated and US-focused) with "0 / Heldigitala alternativ till byråer" — a direct market observation requiring no source. Trimmed the CAGR tail ("Sverige växer med 9,1% CAGR, europeiska marknaden med 8,7%") from the Market bottom-up calculation.
- **2026-04-26:** Strengthened Why Now card 1 description to connect growth to the slide's tension. Old: generic growth stats. New (SV): "Snabbast växande i Europa. Fler event per år, större budgetar, och ändå bokas de fortfarande via mejl och telefon." This directly echoes the slide headline ("Eventbudgetarna växer. Verktygen hänger inte med.") and bridges into cards 2 and 3.
- **2026-04-26:** Rewrote Insights slide (slide 5). Headline: "Samma mönster, varje gång" — shifts from "what we learned" framing to the repeating buyer pattern. Card 2 replaced: "Många event kräver fler än en leverantör" (structural fact, weak) → "Kunden ville alltid ha mer" (grounded in real customer conversations — they came for the chef, then asked about venue, then transport). Card 3 title sharpened to "Och nästa gång börjar de om igen" — adds the cyclical dimension, making it a systemic problem not a one-off. Quote sub rewritten from product explanation to direct customer voice: 'Inte "kan du hitta en kock?" utan "kan du ta hand om hela grejen?"'. Removed orphaned "3–5" hardcoded stat from card 2 since it no longer matched the new narrative.
- **2026-04-26:** Rewrote traction slide timeline to reflect accurate founder story. Step 1: Network-driven chef bookings with no marketing spend — customers kept asking for a full event tool, not just a chef. Step 2: Built MVP with the first three supplier categories (chef, venue, rentals) in one digital flow. Step 3: Forward-looking, vision-titled — "Bygger verktyget kunderna efterfrågar" / "Building the tool customers are asking for" — with description explaining how a full-time team enables the product, partnerships, and sales/marketing needed.
- **2026-04-26:** Added "Recreate a past event" / "Återskapa ett tidigare event" as a merged step on the Product Vision slide (slide 6, data-slide="5"), below the "Add a coordinator" and "Coordinate yourself" branches, connected by converging dotted lines. Framing: rebook from suppliers already tried, keep what worked, swap out the rest. Translation keys: s5_merge_title, s5_merge_desc in both sv and en.
- **2026-04-18:** Funding narrative flip — founder team goes full-time with this round, sales/marketing ramps in parallel. Reverses the 2026-03-19 "staying lean, proving demand first" entry above; that framing is retired. Changes: Team slide headline "Byggt lean. Förblir lean." → "Byggt lean. Nu går vi på heltid." / "Built lean. Now going full-time." Daniel and Edin descriptions no longer say "alongside a full-time role." Hiring card reframed as "Full-time + new hires." Ask slide headline → "Grundarteamet på heltid. Dags att skala." / "Founders full-time. Time to scale." Year 1 roadmap body now leads with "Founding team goes full-time." Traction step 3 retitled to "Founders full-time, sales and marketing live." Behind the scenes: product isn't fully there yet — complex requests handled manually while surface polish lands, marketing scales, then the real infrastructure gets rebuilt. The deck presents the end-state vision confidently without referencing the manual phase.
- **2026-04-27:** Added European TAM (200B SEK) as a new first box on the Market slide, making it 4 horizontal boxes: TAM (EU) 200B SEK → TAM (SE) 7.2B SEK → SAM 1.8B SEK → SOM 50M SEK. The EU figure is a bottom-up extrapolation: ~30x Sweden's SE TAM based on Eurostat mid-market company counts (~900K EU vs 30K SE). The (EU) and (SE) suffixes were added to both TAM labels for clarity.
