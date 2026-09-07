# Staging checklist

Two deploys. Do them in order - the second depends on the first being right.

## Deploy 1 - scaffolding (`shell-test`)

Nothing on the site changes. All 43 original pages are byte-identical.

Open `/shell-test` and check:

- [ ] Header bar at the top with logo and nav pills
- [ ] Headings are **Sora**, body is **DM Sans** - not Times New Roman
- [ ] Narrow the window under 720px - top nav is replaced by a hamburger
- [ ] Tap the hamburger - menu opens and closes
- [ ] Green WhatsApp bar stuck to the bottom on mobile width, hidden on desktop
- [ ] Footer at the bottom with logo and links
- [ ] Scroll - a thin blue/green progress bar fills along the very top

Then open `/pricing` and `/reviews`. They are **not** converted and must look
exactly as they do on the live site. If they changed, the scaffolding is
leaking into pages it should not touch. Stop and say so.

## Deploy 2 - homepage

Open `/` and check:

**Content**
- [ ] H1 reads "Computer & Laptop Repair Perth / Flat $120 - Diagnosis and Repair Included"
- [ ] Under it: "No hourly rates · No call-out fee · No surprises"
- [ ] New comparison section below the hero: $205/hour vs $120 flat, two cards
- [ ] Comparison cards sit side by side on desktop, stack on mobile
- [ ] "About $85 cheaper on a typical job" band in light blue
- [ ] $49 appears only as the pre-purchase check, never as a repair price
- [ ] Rating says 4.8, never 5.0
- [ ] Hours read "24 hours Monday to Saturday, 2:30am to 10pm Sunday"

**Function** - this is what broke before, so check it properly
- [ ] The 2-step quote form advances from step 1 to step 2
- [ ] Submitting it sends the email
- [ ] Countdown timer in the quote card is running
- [ ] FAQ accordions open and close
- [ ] Sections fade in as you scroll
- [ ] WhatsApp buttons open WhatsApp with the message prefilled
- [ ] GA4 realtime shows `phone_call_click` and `quote_form_click` when clicked

**Source** - right-click, View Page Source
- [ ] Exactly one `<h1>`
- [ ] Five `application/ld+json` blocks
- [ ] Canonical is `https://www.fixmypcperth.com/`
- [ ] No `aggregateRating` anywhere

## Only then

Once both are confirmed on staging, the same two commits go to the live repo.
Tag before pushing.
