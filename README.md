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

   REAL photos of Melissa now in use: `melissa-colpitts.jpg` (studio headshot,
   Home owner block), `melissa-field-rough-in.jpg` (jobsite rough-in, About
   owner block), `melissa-crew-briefing.jpg` (directing a crew — used on About,
   Commercial, and Manpower to support the foreman/superintendent credential).
   AI-generated images were NOT used. Do not add composite or generated jobsite
   photos to this site: it now claims SBA 8(a), and staged imagery suggesting
   crew size or another company's branding creates real exposure in a
   prequalification or size/capability challenge.

## CERTIFICATIONS — two separate credentials

Colpitts Electric appears to hold TWO distinct certifications. They are different
programs, different agencies, and serve different buyers. Do not conflate them:

1. SBA 8(a) — U.S. Small Business Administration, federal. Supports 8(a)
   set-aside and sole-source federal contracting. Currently on the site.
2. MWBE — City and County of Denver (Division of Small Business Opportunity).
   Supports MWBE participation on City-funded projects. NOT currently on the
   site — it was removed earlier when it couldn't be verified.

VERIFY AND RESTORE the MWBE credential: exact designation (MBE, WBE, or MWBE —
they are not interchangeable), certifying agency, certificate number, and
expiration. Then add it to the Manpower and Commercial pages alongside 8(a).
This is the credential that won the Convention Center work, so it matters.

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
