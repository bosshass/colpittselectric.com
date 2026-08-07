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

## After launch

- Submit `sitemap.xml` in Google Search Console
- Match Google Business Profile services to the service names used here
- Add Google Analytics or Plausible if wanted
