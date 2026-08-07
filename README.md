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

1. **Phone number** — currently `(303) 000-0000`. Update the display text AND
   every `tel:+13030000000` href, plus `telephone` in the LocalBusiness schema.
2. **Email** — confirm `info@colpittselectric.com` is monitored.
3. **CO Master Electrician license number** — appears in the footer of all
   pages and on the About page.
4. **Years of experience** — copy says "more than 20 years"; the old site said
   18. Pick the accurate number.
5. **Certification (Manpower page)** — the page has a visible internal warning
   block and blank certification table. Do not publish claiming MWBE unless the
   certificate says MWBE. Fill in exact designation, agency, number, NAICS
   codes, status, and expiration; then delete the `.warn` block.
6. **Contact form** — inert. Wire to Formspree/Netlify Forms/serverless handler
   and add spam protection.
7. **Photos** — every `.ph` block is a placeholder describing the shot needed
   and the alt text to use. Replace with real project photos; never publish
   invented project captions.

## After launch

- Submit `sitemap.xml` in Google Search Console
- Match Google Business Profile services to the service names used here
- Add Google Analytics or Plausible if wanted
