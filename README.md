# Bloom Yoga

Website for Bloom Yoga, Dubai. Yoga and yoga therapy with Shipra Jain.

Live at https://bloomdubai.yoga

## What's here

    index.html      the whole site: markup, styles and script in one file
    images/         photographs, referenced by index.html
    CNAME           tells GitHub Pages to serve the site at bloomdubai.yoga
    .nojekyll       stops GitHub from running Jekyll over the files

## Editing

Open `index.html` in any text editor. Text lives in the HTML near the bottom
half of the file; colours are CSS variables at the very top, under `:root`.

To swap a photo, replace the file in `images/` keeping the same filename, or
change the `src` on the relevant `<img>`.

## Publishing a change

Commit and push to `main`. GitHub Pages rebuilds within a minute or two.

## Enquiry form

The form currently opens the visitor's email app with the message filled in.
It does not collect submissions on its own, and it fails silently on phones
with no mail app configured.

To collect enquiries properly, create a free form endpoint (Formspree or
similar) and change the opening form tag to:

    <form action="https://formspree.io/f/YOUR_ID" method="POST" id="enquiry">

then delete the `form.addEventListener("submit", ...)` block at the bottom of
the script.

## Pointing bloomdubai.yoga at GitHub Pages

Two halves: GitHub needs to know the domain, and the domain needs to know
where GitHub is.

**1. In the repository** — Settings, then Pages. Set Source to "Deploy from a
branch", branch `main`, folder `/ (root)`. Under Custom domain enter
`bloomdubai.yoga` and save. The `CNAME` file in this repo does the same job,
so it may already be filled in.

**2. At the domain registrar** — wherever bloomdubai.yoga was bought, open the
DNS settings and add these five records:

    Type    Name    Value
    A       @       185.199.108.153
    A       @       185.199.109.153
    A       @       185.199.110.153
    A       @       185.199.111.153
    CNAME   www     <github-username>.github.io

Delete any existing A or CNAME records on `@` and `www` first, including
parking-page records the registrar added automatically.

DNS usually takes 15 minutes to an hour, occasionally longer. Once GitHub
shows the domain as verified, tick "Enforce HTTPS" on the Pages settings
screen. That checkbox stays greyed out until the certificate is issued, which
can take another hour. The site will be reachable over plain http before then.
