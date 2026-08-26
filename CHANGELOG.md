# What changed — rebuild notes

Built from your actual live source (github.com/tiagomotabcl/mapexconsulting), not from scratch, so all real content, pricing and copy is preserved. Brand kept exactly: `#2DD4BF`/`#14b8a6` teal, `#07090d` dark background, Syne + Inter, the geometric M logo.

## Real bugs found and fixed
- **Footer said "Tech Consult" instead of "M.Apex Consulting"** on services.html, about.html and contact.html — leftover from the pre-rebrand version.
- **Homepage footer was missing the Home and Consulting links**; services.html footer was missing Consulting. All five pages now share one footer, so this can't drift again.
- **about.html stats said "45+ services across 6 specialisms"** while every other page says 77+/9 — now consistent everywhere.
- **Two broken sentences from the redaction pass** that removed your name and years of experience: "I'm . a UK-based IT consultant" and "Built over . From helpdesk to cloud architecture" both had a dangling ". " where a word used to be. Rewritten so they read properly without reintroducing a name or year count.
- **One testimonial had the same issue** — "After a ransomware scare, locked everything down" was missing its subject. Fixed to read naturally.
- Footer copyright now says 2026.

## Design changes
- Every emoji icon (73 across the five pages) replaced with a custom SVG icon set in one shared sprite, geometric and single-colour to match the logo's own construction.
- Homepage no longer dumps the full 77-service list twice — it shows the 9 category cards (icon, name, count) linking to services.html, which still has the complete catalogue with all 81 individual services, prices and tags intact.
- Tags like "Popular", "Critical", "AI", "New" are now styled badges (colour-coded: red for urgent/legal, teal for popular, purple for AI) instead of plain text.
- Testimonials are proper cards with initials avatars and real star icons instead of plain asterisk text.
- The urgency selector on the contact form is styled coloured dots instead of 🔴🟠🟡🟢 emoji.
- FAQ is a native accordion (keyboard and screen-reader accessible, no JS needed for it to work).
- Services page has a working category filter.
- Contact form still opens WhatsApp with the message pre-filled, same as before, now assembled from all the fields including urgency.
- One shared `style.css` instead of five separate inline copies — this is what actually prevents the footer/nav drift from happening again next time a page gets edited on its own.

## Round 2 — glamour / motion pass
- **Hero signature visual**: an animated constellation of connected nodes (pure CSS, no images), built from the same rect/circle language as the logo mark — a quiet, on-brand "network" motif rather than a generic gradient blob.
- **Active Services panel is back** in the hero (it was on the live site, I'd simplified it away in round 1) — rebuilt with real icons and small live-status dots: a soft pulse ring on "Active"/"In progress" rows, a static dot on completed ones. The pulse is the same visual idea as the hero constellation, so the two feel like one system rather than two unrelated effects.
- **Stat counters animate** (14 → 14+, 77 → 77+) when they scroll into view.
- **Testimonials are now a slider** — one at a time, auto-advancing, pausable on hover/focus, dot navigation. This is also what you asked for as "slides."
- **Cards lift slightly on hover** with a soft teal-tinted shadow, consistent across services, pricing and testimonial cards.
- **Sections cascade in on scroll** — cards fade and rise into place with a slight stagger, site-wide.
- Everything above fully respects `prefers-reduced-motion` (skips straight to the end state, no animation) and has a hard 2.5-second failsafe so nothing can get stuck invisible or stuck at zero if a visitor's browser hiccups.

## Round 3 — prices removed, copy tightened

**Prices gone everywhere.** Verified by scanning the built output for £ amounts, "POA" and any /hr, /day, /month rate pattern — all three scans return nothing.

Instead of deleting the line and leaving a gap, each service card now states the *shape* of the commercial arrangement, which is what a buyer actually needs before enquiring: "Fixed-price engagement", "Monthly managed service", "Audit, then optional retainer", "Priced per user", and so on. Sixteen types in total, derived from what each service actually was. This is how established consultancies present it, and it aligns with your preference for fixed-price quotes over published rates.

- Consulting engagement cards: "From £75/hour" → "Flexible, ad hoc"; "From £450/day" → "Scoped and quoted upfront"; "POA" → "Ongoing monthly retainer".
- Homepage plan cards: "POA / per month" → "Ongoing monthly retainer"; "POA / one-off project" → "One-off engagement". "POA" reads dated, so it's gone rather than kept.
- CTA changed from "Get a quote" to "Request a quote" on service cards.

**Claims tightened — please read this bit.** A few lines were making claims that would be hard to stand behind if a client pushed:

- Security Awareness Training said *"One Sheffield firm reduced phishing click rates from 32% to 4%"*. On your own services page this reads as your client work. If it isn't, that's a real credibility risk. Rewritten to a general statement. **If this is genuinely your result, tell me and I'll put it back properly as an attributed case study — it's a strong number.**
- *"Most businesses save 20–35% of their software bill"* and *"20–40% of their cloud bill"* were stated as fact in your own voice. Rewritten as what an audit typically uncovers.
- Cyber Essentials *"shown to prevent 98% of common attacks"* → "designed to prevent the vast majority of common cyber attacks", matching the NCSC's own wording. The 98% figure circulates widely but isn't an official NCSC claim.
- "Dramatically improves local search visibility" → "Improves visibility in local search results"; "Reduces unexpected downtime significantly" → "Helps reduce unexpected downtime"; "More reviews, less effort" removed.
- Badge "My speciality" → "Core speciality" (consistent across services and consulting).

## Round 4 — ideas taken from other consulting sites

Reviewed 18 consulting sites (McKinsey, Bain, Slalom, Kearney, plus solo-consultant boutiques) and filtered for what a one-person firm can actually execute. Deliberately skipped: video backgrounds, executive photography, mega-menus, language switchers — all need budget or scale you don't have yet.

**Implemented:**

1. **"Start from your problem" entry grid** *(from Kearney — navigation organised around client needs rather than the firm's own structure)*. Six cards written in the client's own words: "We've been hit, or we're worried we're next", "A customer or regulator is asking for compliance proof", "An old system is holding the business back", and so on — each routing to the relevant services. Added to both the homepage and above the category filter on services.html. This is the strongest idea from the whole review and it directly addresses the "77+ services is overwhelming" problem: a visitor no longer has to know your taxonomy to find the right thing.

2. **Scroll-aware header** *(FourFold, Josh Kremer)*. The nav hides on scroll down and returns on scroll up, giving back vertical space on mobile. It never hides while the mobile menu is open, so links can't become unreachable.

3. **Back-to-top button** *(Jack Dalrymple)*. Appears after 700px. services.html is genuinely long enough to need it.

All three respect `prefers-reduced-motion` and the scroll handler is throttled via `requestAnimationFrame` so it doesn't cost anything on mobile.

**Validated:** every anchor the problem cards point to (`#security`, `#automation`, `#data`, `#ai`, `#it-support`) was checked to actually exist on the target page.

**Not implemented — these need content from you, not code:**

- **Insights / thought leadership** *(Slalom leads with a research report rather than service descriptions)*. Three or four articles on NIS2, legacy rescue, or the 2027 PSTN switch-off would do more for both authority and search traffic than any further design work. This is the same gap flagged in the strategy notes.
- **Case study grid** *(Kevin Sharon — a grid of real projects directly below the hero)*. The kiosk system belongs here.
- **A photo of you.** Solo-consultant sites that convert put a face on the page — it's the main trust signal when there's no brand name to lean on. This conflicts with your earlier decision to remove personal identity from the site, so it's your call, not mine to make.

## Round 5 — polish and navigation pass

**Every dash removed, everywhere, permanently.** Went through all five pages sentence by sentence: 20 instances found (six were hiding inside `services_data.py` as escaped Unicode, easy to miss with a plain text search). Zero remain anywhere in the rendered output, verified by scanning for the actual Unicode characters, not just the visible symbol. I've also saved this as a standing preference so it applies automatically to anything I write for you from now on, not just this rebuild.

**Navigation, the actual "easy to navigate" fixes:**
- **Search box on services.html.** Content-heavy sites need this: with 81 services, scrolling and hoping was never going to be enough. Live filtering by name and description, works together with the category tabs.
- **Anchors now land below the header, not behind it.** Every "start from your problem" link jumps you to `services.html#security` etc, but the fixed header was covering the heading you'd just jumped to. Fixed with `scroll-margin-top`.
- **Arriving via a problem card now selects the right filter tab too**, not just scrolls there. Read the URL hash on load and activates the matching category, so the page feels like it landed in the right place.
- **Skip-to-content link** for keyboard and screen reader users, appears on first Tab press.
- **`<main>` landmark** added properly around the page content on all five pages, footer sits outside it as its own landmark, which is what assistive tech expects.

**Visual, the "masterpiece" pass:**
- **Subtle grain texture** over the whole site: barely visible, this is what stops a flat dark background reading as a template. Fixed overlay, doesn't affect click targets.
- **Bigger, more confident hero type** and tighter letter spacing on headings.
- **Scroll-aware header**: hides on scroll down, reappears on scroll up, more room for content on mobile. Never hides while the mobile menu is open.
- **Back-to-top button** on the long pages.

## Round 6 — real bug found, not a matter of taste

You were right to push back. Found a genuine, serious bug that no test tool had caught until now, and it very likely explains "parece cheap".

**What was wrong:** the scroll-reveal animation from round 2 (cards fading in as you scroll) started every element at `opacity:0` and relied on JavaScript to reveal it. In a slower load, or on a long page like services.html with 81 cards, there's a real window where the JavaScript hasn't run yet. During that window entire sections, including the homepage headline itself, were invisible. Not subtle, not a matter of taste: literally blank space where the hero and half the service cards should be.

**How I actually found it:** this environment doesn't have a real browser, only an old, limited rendering tool that happened not to trigger the bug, which is exactly why it went unnoticed through five rounds of "structural validation." I located an actual Chrome binary in the sandbox and used it to screenshot the live files precisely as your browser would load them. The screenshots caught it immediately: hero text nearly invisible, whole rows of service cards missing.

**The fix:** removed the opacity-gated reveal system entirely. Content is visible immediately now, no JavaScript required for anything to simply appear. Also replaced the count-up-from-zero animation on the stats (14, 77) with plain static numbers for the same reason: same failure mode, same fix. Screenshotted every page again with real Chrome after the fix to confirm, not just assumed it was solved. Screenshots are in the `verificacao` folder.

**Also fixed while checking:** the stat row (14+ / 77+ / 1x / UK) could wrap unevenly, 3 items on one line and 1 orphaned below, depending on screen width. Now wraps in even pairs.

## Round 7 — the robotic feel wasn't the dashes, it was repetition

Re-checked for dashes first: still zero, confirmed again with a fresh scan. So the "robotic" feeling was something else, and reading back through every page in one sitting, it was obvious: the same rhetorical trick, "No X, no Y, no Z", was used in something like eleven different places. Once you notice a pattern repeated that many times across one site, it stops reading like writing and starts reading like a template being filled in. That's a real thing, not just a dash problem, and it's worth knowing about for anything else you have me write in future.

Rewrote every instance so the site doesn't lean on one formula:

- Hero paragraph, the six "why choose M.Apex" cards, all four "how it works" steps
- The five "why choose me" cards on about.html, plus the intro paragraph and the "direct expert" paragraph
- The services.html intro line, which also used to repeat "everything your business needs" almost word for word from the homepage. Reworded so the two pages don't sound like they were copy-pasted from each other
- Two lines on contact.html

Also scanned for the other common tells (seamless, unlock, elevate, leverage, cutting-edge, streamline, and a few more) across every file. None found.

Nothing here changes what's promised or how it's priced, only how it's said. Rebuilt and re-checked: no dashes, no emoji, no prices, no broken tags, and a fresh real-Chrome screenshot confirms the hero and cards are still fully visible after the wording changes.

## Round 8 — the real cause of "looks cheap", found and fixed

Your screenshots made this obvious. The pages were rendering as plain black-on-white Times New Roman text with giant unstyled icon shapes, exactly what happens when a browser can't find style.css. That's not a design problem, that's the CSS not loading at all in the context you were viewing it in (Claude's own file preview doesn't reliably resolve a separate stylesheet sitting next to the HTML file). Every round of design feedback up to now may have been judged against that broken, unstyled version.

**The fix:** every page now carries its CSS inline inside its own `<style>` tag. No external style.css dependency, no sibling file required, nothing to go missing. I proved this by opening index.html completely alone in a folder with nothing else in it, and about.html the same way, both render fully styled. Screenshots would show this but the important thing is you can now verify it yourself: open any of the five files on their own, anywhere, and the design will be there.

style.css is still included since it's the shared source I generate all five pages from, but none of the HTML files need it to render correctly anymore.

**Also this round:**
- Looked at Awwwards' layout collection as asked. Most of what's there (WebGL, horizontal scroll, full-screen video) is built for creative agencies chasing design awards, not for a business trying to look trustworthy, so I didn't copy it directly. The one idea that genuinely transfers is bento-style grids: blocks of varied size instead of uniform rows. Applied it to the "why choose M.Apex" section on the homepage: "Direct expert access" is now a large featured block, the other five sit around it. Breaks the monotony of every single grid on the site being identical 3-column cards.
- Re-confirmed zero dashes in all visible text, and while checking found six more hiding inside CSS comments (invisible to any visitor, but cleaned them anyway since you'd rather I be thorough).

## Round 9 — luxury pass: typography, gradient, colour, copy

**Font.** Researched current font pairings specifically for a premium feel. Kept Syne for the logo and section structure (it's your established brand mark, no reason to throw that away), but added Fraunces, a serif, for every page's main headline specifically. Fraunces + Inter is a well-documented, current pairing for exactly this "editorial, premium, confident" register, distinct from the generic Playfair Display used everywhere. Section headings, card titles and the nav stay Syne; body text stays Inter. One new font, used deliberately in one place, not a wholesale change.

**"14+ years" is gone, everywhere.** Replaced with "Full-stack": infrastructure to AI, in one person, on the homepage, about.html and consulting.html. Same underlying claim (breadth of what you cover solo), no year count attached to it.

**Colour and gradient.** The background is a touch richer (slightly less pure-black, more depth). Added a soft aurora-style gradient glow (teal with a hint of purple) behind every page's header, and a gradient-teal treatment on one key phrase per headline: "serious IT expertise", "One expert.", "Solved.", "One mission.", "IT challenges." This is the specific pattern research turned up as the current signal for a premium SaaS/consulting site, used at the moment of highest impact, not smeared across every element.

**Layout innovation, informed by your list, not copied from it.** Went through the galleries you sent. Sites like Awwwards, Godly and The FWA are built for design awards: WebGL, video backgrounds, brutalist experiments. That's the wrong reference for a site that needs to read as trustworthy in the first three seconds. The useful ones for this context were the SaaS-specific galleries (SaaSframe, Landbook, Built for Mars) and they confirm what I'd already started: bento grids (blocks of different sizes, not uniform rows) are the current standard at Linear, Ramp and similar, not a gimmick. Extended that from last round's single bento section using the same pattern language throughout.

Everything re-validated after all of this: no dashes, no emoji, no prices, no broken links, no leftover "14+", tags balanced across all five pages.

## Round 10 — went through the rest of the list, one real addition

Continued checking real sites from your list: Siiimple, Footprints (couldn't locate this specific one, searches only returned generic stock-footage sites, being upfront rather than guessing), Landingfolio.

**Siiimple**: confirmed it, mostly light-background creative agency and portfolio work. Nothing new for a dark, restrained B2B site.

**Landingfolio**: this one was useful. It's a component library organised by the standard sections real converting sites use: Hero, Stats, Steps, Pricing, FAQ, Testimonial, Logo Cloud. Checked that list against the homepage and everything was already there except one: a direct comparison block. That's a proven, common pattern for exactly the differentiator you already have (one direct expert vs the usual handoff chain), so I built it rather than just describing it.

**New: "What actually changes when you switch."** A two-column block right after "how it works": typical IT support company on the left in muted grey with X marks, M.Apex on the right in teal with checkmarks, same five points mirrored against each other. Uses only claims already established elsewhere on the site (direct access, fixed quotes, security-first), nothing new invented.

Validated as usual: no dashes, no prices, no broken icons, tags balanced, confirmed the actual render with a real screenshot before calling it done.

## Round 11 — findability: SEO that was completely missing

Checked the live site properly this time: no favicon, no robots.txt, no sitemap, no social share image, no structured data. Google could technically find the site, but had nothing to work with, and every link shared on LinkedIn or WhatsApp showed a bare grey box.

**robots.txt and sitemap.xml.** Both new files. The sitemap lists all five pages so Google can find and prioritise them properly instead of guessing.

**Favicon, done properly.** Built from your actual logo mark (not a generic placeholder): an SVG version for modern browsers, plus PNG fallbacks at every size browsers and phones actually request (16, 32, 180, 192, 512px), and a classic multi-size .ico for older software. You'll see it in the browser tab now.

**A real link preview image.** When this site gets shared on LinkedIn, WhatsApp, or anywhere else, it now shows a proper branded card: your logo, the headline, and the value line, 1200x630px, built to the exact spec every platform expects. Right now it shows nothing usable.

**Titles that are actually written for search, not just for the tab.** "Home" as a page title tells Google nothing. Changed each page's title tag specifically: e.g. index.html is now "M.Apex Consulting | UK IT Consultancy for Cloud, Security, Data & AI", not just "Home". Descriptions were already reasonable from earlier rounds, kept those.

**Structured data (JSON-LD).** Every page now carries machine-readable business information: service type, areas served (Herts, Bucks, Beds, London), the service categories you offer. This is what lets Google show richer results and understand the business is a real, local professional service, not just a random page of text. Kept it to business-level facts only, no name, no phone number, respecting the same privacy boundary already set for the visible site.

**Canonical URLs** on every page, so search engines treat each page as one distinct thing rather than risking duplicate-content confusion.

All validated: JSON-LD parses as valid JSON, sitemap parses as valid XML, every Open Graph and Twitter Card tag present on all five pages, and confirmed with a real screenshot that none of this changed how the page actually looks.

**What I can't do from here, needs your side:** submit the sitemap to Google Search Console, set up a Google Business Profile (this is what actually gets you into local map results), and get the site indexed for the first time. None of that needs code, just an account login I don't have.

## Before you deploy
- I validated structure (balanced tags, no broken links, no leftover emoji, icon references all resolve) and rendered rough previews, but I don't have a real browser in this environment — open the files locally or push to a preview branch and check on an actual phone and desktop before replacing what's live.
- Fonts (Syne/Inter) load from Google Fonts same as before — nothing changes there.
- No content was invented for services.html, consulting.html or about.html — every service, price and description is transcribed from your live site.
