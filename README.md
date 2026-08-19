# colpittselectric.com

Static site for Colpitts Electric LLC — Denver Metro electrical contractor.
No build step. Plain HTML + inline CSS. Deployed on Vercel as a static site.

## Structure

| File | URL |
|---|---|
| `index.html` | `/` |
| `commercial-electrical-services-denver.html` | `/commercial-electrical-services-denver` |
| `residential-electrician-denver.html` | `/residential-electrician-denver` |
| `commercial-electrical-manpower-denver.html` | `/commercial-electrical-manpower-denver` |
| `about-colpitts-electric.html` | `/about-colpitts-electric` |
| `contact.html` | `/contact` |

`vercel.json` sets `cleanUrls: true`, so links are extensionless. Short vanity
paths (`/about`, `/commercial`, `/residential`, `/manpower`) 301 to the SEO URLs.

## Local preview

Open with a local server, not `file://` — extensionless links need a server:

    python3 -m http.server 8000

Then visit http://localhost:8000

## BEFORE GOING LIVE — unresolved items

Every unconfirmed value is wrapped in `<span class="tbd">` and renders with an
amber highlight so it's visible on the page. Find them all:

    grep -rn 'class="tbd"' *.html

1. ~~Phone number~~ — done: (303) 979-9422.
2. ~~Email~~ — done: melissa@colpittselectric.com.
3. ~~License number~~ — removed by request; footer reads "Licensed & insured".
4. ~~Years of experience~~ — confirmed: "more than 20 years".
5. **Certification** — confirmed: **SBA 8(a) Business Development Program**
   (NOT MWBE — that was wrong in the original SEO draft and has been removed
   sitewide). The 8(a) badge and messaging now appear on Home, Commercial,
   About, Contact, and Manpower.
   Still needed on the Manpower page certification table (5 fields):
   case/certificate number, program entry date, program exit date, approved
   NAICS codes, and UEI/CAGE from SAM.gov. Then delete the `.warn` block at the
   top of that page.
   NOTE: 8(a) has a strict 9-year program term. Put the exit date in the
   calendar — the page must be updated when the term ends.
6. **Contact form** — Formspree is wired; needs the form ID.
   a. Sign up at formspree.io with melissa@colpittselectric.com and create a
      new form. Confirm the verification email or nothing will deliver.
   b. Copy the endpoint (looks like `https://formspree.io/f/xdorwkyz`).
   c. In `contact.html`, replace `YOUR_FORM_ID` in the form `action` with the
      ID portion. One occurrence.
   d. Push, then send a real test submission and confirm it arrives.
   Spam protection: a `_gotcha` honeypot field is already in place; also turn on
   reCAPTCHA in the Formspree dashboard. Free tier is 50 submissions/month —
   upgrade if volume exceeds that or messages will be held.
7. **Photos** — `/images/` holds three illustrative lighting photos used on the
   Residential page. These are NOT Colpitts project photos and are captioned by
   what they show, never by city or as completed work. Do not re-caption them
   with a city or present them as past performance.
   The `brave-church-*.jpg` files ARE real Colpitts work (Brave Church
   renovation, in progress) and are captioned as such on Home and Commercial.
   Get written client sign-off before naming Brave Church publicly.
   `colpitts-van.jpg` is a dealer-lot photo of an unbranded van — replace once
   the vehicle is wrapped.
   IMAGE FILENAMES: all images use descriptive, keyword-bearing filenames
   (e.g. `commercial-electrical-rough-in-overhead-cable.jpg`, not `IMG_2049.jpg`).
   Keep this convention for anything added later — filename and alt text are
   both ranking signals for image search. Do NOT put a city in a filename
   unless the photo was genuinely taken there.


   ADDED 2026-08-19 — BRAVE Church (Cherry Hills Village) LED retrofit photos.
   Source: Colpitts_Electric_Web_Photos.zip supplied by the client, installed
   as-is (11 subjects, each as .jpg + .webp, plus a 1920x1080 cafe hero crop and
   two portrait crops). Three extra frames were processed here to fill gaps the
   zip did not cover: commercial-exit-emergency-lighting-denver,
   commercial-open-office-led-lighting-denver, commercial-corridor-rough-in-denver.
   The auditorium and demolition frames were re-exported from the full-resolution
   originals; commercial-church-auditorium-denver-hero.jpg is a 16:10 crop of the
   auditorium made for the home page hero.

   CLIENT NAMING: approved 2026-08-19 for indexed pages. BRAVE Church is now
   named on the home page hero alt text, the Commercial page ("Recent work"),
   and /case-studies. The Brave Cafe signage photo is on indexed pages by that
   approval. If the approval is ever withdrawn, the strings to change are the
   "Recent work" heading and copy on the Commercial page plus the alt text on
   both hero images.

   FILENAME CAVEAT: the supplied files are named "...-denver.jpg" but the job is
   in CHERRY HILLS VILLAGE, not Denver. That conflicts with the rule below about
   not putting a city in a filename unless the photo was taken there. Names were
   left as supplied to avoid breaking the client's own plan — worth correcting on
   the next pass if nothing depends on them. Alt text and captions correctly say
   Cherry Hills Village.

   IMAGE TREATMENT: photos render grayscale and go to full color on hover
   (desktop) or on scroll-into-view and tap (touch), with a purple hairline on
   the active tile. Implemented as the .gs / .lit classes plus a small inline
   IntersectionObserver script at the bottom of index.html, case-studies.html and
   commercial-electrical-services-denver.html. Any new photo block should carry
   class="gs" (new template) or sit inside .imgrow / .work (case studies) to pick
   the behavior up automatically.

   UNUSED BUT AVAILABLE: commercial-exterior-wall-sconce-denver-portrait.*,
   commercial-hallway-led-lighting-denver-portrait.*.

   REAL photos of Melissa now in use: `melissa-colpitts.jpg` (studio headshot,
   Home owner block), `melissa-field-rough-in.jpg` (jobsite rough-in, About
   owner block), `melissa-crew-briefing.jpg` (directing a crew — used on About,
   Commercial, and Manpower to support the foreman/superintendent credential).
   AI-generated images were NOT used. Do not add composite or generated jobsite
   photos to this site: it now claims SBA 8(a), and staged imagery suggesting
   crew size or another company's branding creates real exposure in a
   prequalification or size/capability challenge.

## CERTIFICATIONS — CORRECTED 2026-08-07

Source of truth: SBA Small Business Search profile for COLPITTS ELECTRIC LLC.

HELD (verified on the SBA record, now on the site):
- WOSB   — Women-Owned Small Business. Certified 4/5/2023.
- EDWOSB — Economically-Disadvantaged Women-Owned Small Business. Certified 4/5/2023.
- UEI PL2PBG5ZPM31 | CAGE 9D5M7 | Primary NAICS 238210 | SAM.gov Active

NOT HELD — REMOVED FROM THE ENTIRE SITE:
- SBA 8(a). It was added earlier on the strength of an 8(a) decal image, but the
  SBA profile lists only WOSB and EDWOSB. Claiming 8(a) without certification is
  a misrepresentation with real consequences under 13 CFR 124 and the False
  Claims Act. Do NOT re-add it unless the SBA profile shows it.
  If an 8(a) application is in progress, the site may say nothing until awarded.

SELF-CERTIFIED IN SAM.gov (attested, NOT vetted by SBA — do not present as
"certified" on the site):
- Self-Certified Small Disadvantaged Business
- DOT Certified DBE  <-- if a real CDOT DBE certification exists, get the
  certificate and it CAN be published; SAM self-attestation alone cannot.

LOCAL — VERIFIED via B2Gnow certified profile (generated 8/7/2026):
- SBE (Small Business Enterprise) — City and County of Denver.
  B2G Vendor ID 21550341. NAICS 238210.
  This is what got Colpitts onto the Colorado Convention Center via Weifield —
  NOT MWBE. All MWBE language has been removed sitewide; the case study now
  correctly says Denver SBE participation.

  Note: SBE is a size/local program, not a minority or gender program. Denver
  also runs MBE/WBE/DBE programs separately. If Colpitts later certifies as WBE
  or DBE with Denver, add those separately — do not conflate them with SBE.

ALSO NOTE — SAM.gov data errors worth fixing:
- Entity structure reads "Partnership or Limited Liability Partnership" but the
  company is an LLC.
- Address on SAM is the home address (public there; deliberately kept off the site).
- Capabilities narrative and capabilities statement link are both blank. Filling
  these improves discoverability for contracting officers searching DSBS.

## Case studies page (/case-studies) — DRAFT

Not in nav, noindex, excluded from sitemap.xml. Reach it by typing the URL.

Before publishing:
1. CLIENT NAMING — the client name was published on index.html and
   commercial-electrical-services-denver.html and has now been REMOVED from both.
   Those indexed pages now describe the work as "a 104,000 sq ft campus in
   Cherry Hills Village," which is accurate, verifiable via permit #26-0472, and
   does not name the client in marketing.
   The client name remains only on /case-studies, which is noindex and unlinked.
   Before naming the client (or Himmelman Construction) on any indexed page or
   social post: check the subcontract for a publicity clause and get written
   approval. Then re-add the name in one pass.
2. ~~Colpitts' scope~~ RESOLVED for BRAVE: 426 LED fixtures + controls +
   occupancy/vacancy sensors across Children's Ministry, upstairs offices,
   fellowship hall, staff kitchen, conference rooms. Commenced June 2026,
   three-month duration, scope still expanding. Naming approved by client.
   NOTE: commercial terms from the SOW (30% restocking fee, cancellation and
   shipping costs) are deliberately NOT on the public page. Those belong in the
   contract, not in marketing.
3. ~~Permit #26-0472~~ VERIFIED as Colpitts Electric LLC's own permit — Cherry
   Hills Village non-residential, application #26-0729, status Approved, filed
   2026-06-26, term through 2028-01-08. Colpitts is the electrical contractor of
   record. This is now cited on the page as verifiable public record.
   NOTE: the permit record shows NO Issued Date. Say "approved," not "issued,"
   until that field is populated. Confirm with Cherry Hills Village whether the
   permit has been issued and update the wording if so.
4. ~~Convention Center~~ RESOLVED: subcontract under Weifield Group (electrical
   prime) under Hensel Phelps (GC), June–Dec 2025, $300,000, fulfilled in full.
   Brought on for Denver MWBE participation. Naming approved by owner.
   Courtesy step worth taking: tell Weifield the case study is going live and
   ask for a link from their site. A prime who used her for participation credit
   has every reason to say yes, and a GC/prime backlink outranks any on-page SEO.
5. Apprenticeship: confirm the REGISTERED program name and participant standing.
6. Then: remove the noindex meta tag, add /case-studies to sitemap.xml, and add
   a nav link to all seven pages.

NOTE: there is no schema.org "Project" type. This page uses Article schema with
contentLocation, plus the sitewide Electrician/LocalBusiness schema with both
Englewood and Cherry Hills Village in areaServed. No markup can assert permit
records to Google.

## AI IMAGES — REMOVED

2026-08-19: about-melissa-hero.jpg was ALSO a stock/AI image — a generic woman in
a hard hat, not Melissa — and it was published as the About page hero with alt
text naming her. DELETED. The About hero is now
commercial-electrician-installation-denver.jpg, a real Colpitts electrician on a
real jobsite, with alt text that does NOT claim the person is Melissa. The real
studio headshot (melissa-colpitts-portrait.jpg) remains further down the page.
Lesson: check every remaining "melissa-*" filename against the actual image —
the filename is not evidence of who is in the photo.


melissa-colpitts-electrical-foreman-jobsite-briefing.jpg was an AI-generated
image (two figures from behind in branded Colpitts apparel). It was saved under a
wrong filename and reached About, Commercial, Manpower and Home before being
caught. It has been DELETED and all references repointed to real photos.

Every remaining image in /images is either a real photograph of Melissa/her work,
a real jobsite photo, an SBA mark, or a people-free illustrative lighting scene.
Do not add generated jobsite imagery to this site — it now claims SBA 8(a) and
cites a public permit record.

## Address / privacy

The business address was REMOVED sitewide (2026-08-07). It was the owner's home
address and should not be published. Do not re-add it.

Colpitts Electric is presented as a SERVICE-AREA BUSINESS:
- Schema: PostalAddress with addressLocality "Denver", addressRegion "CO" only —
  no streetAddress, no postalCode.
- Footer and Contact page: "Denver, Colorado — Serving the Denver Metro area."
- Littleton still appears only as a served city in the service-area list, which
  is correct and carries no address.

IMPORTANT — Google Business Profile: set the profile to "service area business"
and HIDE the street address there too. A GBP listing showing the home address
undoes this entirely, and GBP data outranks the website. Also check Bing Places,
Yelp, Apple Business Connect, and any contractor directories for the same.

## After launch

- Submit `sitemap.xml` in Google Search Console
- Match Google Business Profile services to the service names used here
- Add Google Analytics or Plausible if wanted
