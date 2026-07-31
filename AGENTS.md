# AGENTS.md — geekycomputerservices.com

An archive site for **Geeky Computer Services**, a computer repair and web design
business founded in Ludington, Michigan on **September 30, 2003** by Brandon
Martinez, then fifteen. It ran until its hosting was cancelled on
**March 13, 2005**; the domain expired **March 17, 2005**.

This is a museum piece, not a business. Nothing is for sale.

## The one rule: do not invent content

Every quoted word on the page comes from the original source archives or the
single Internet Archive capture. Typos, grammar, and 2004 phrasing are preserved
verbatim ("instant messagin friends", "virii (plural of virus)", "being to know
more people"). **Do not fix them.**

Editorial voice is confined to:

- section intros and captions (clearly the archivist speaking, present tense)
- the `#story` section
- the `Notes` column of the release table

If you need to add a fact, it must be traceable to a row in the provenance table
below.

## Provenance

| On the page                     | Source                                                                       |
| ------------------------------- | ---------------------------------------------------------------------------- |
| "Leave It to the Geeks" welcome | `GCS - Version 3_0_2/index.aspx`                                             |
| "Why we started"                | `GCS - Version 3_0_2/about.aspx`                                             |
| Five service write-ups          | `GCS - Version 1_0_0/services/{pc,web,net,pub,custom}/index.html`            |
| Teacher Tech copy               | `GCS - Version 3_0_2/index.aspx`                                             |
| Contract / DBA fine print       | `GCS - Version 1_0_0/services/web/avail.html`                                |
| Release dates                   | File mtimes across the twelve `GCS - Version *.zip` archives                 |
| "Things to Do"                  | `GCS - Version 3_0_2/Things to Do.txt` (verbatim, complete)                  |
| 2004 screenshot                 | Wayback `20040528151106`, re-rendered with original image slices             |
| Hosting / domain dates          | DiscountASP.NET + registrar emails in Gmail (account `geekycomput`)          |
| Logo, banner, Teacher Tech mark | `GCS - Version 3_0_2/img/` and `graphics/`                                   |

Source ZIPs: `~/src/_archive/Martinez Media/ZIP Backups/GCS - Version *.zip`
(twelve, 1.0.0 → 3.0.2). Extracted working copies: `/tmp/bm-archive-dig/`.
Research writeup:
`brandonmartinez-secondbrain/02-Areas/Web Presence/Docs/2026-07-31 - Legacy Site & Band Archive Inventory.md`.

## Deliberately excluded — do not add these

- **`_database/db.mdb` and `samples.mdb`** — real customer records and sample
  invoices with client names and phone numbers.
- **The 2004 contact page's mailing address and telephone number** — a residential
  address and home phone. The `admin@` / `support@` / `sales@` addresses are also
  omitted since the domain is not ours to receive mail on.
- **`clsCrypt.vb` and the DES key it hard-codes.** Never publish, never quote.
- **Login, register, profile, payments, and requests pages** — account
  functionality has no place in an archive.

## Build

House pattern (see `Static Site Build & Deploy.md` in the vault):

```sh
npm install
npm run dev     # tailwind --watch + vite on :4174
npm run build   # → _site/
```

- Tailwind **v4**, no `tailwind.config.js`; theme lives in `@theme` in
  `styles/tailwind.css`.
- Exactly three dev dependencies plus the `shell-quote` override. **`npm audit`
  must report zero.**
- `src/` ships as-is; the build is `cp -R src/. _site/`. Vite is a dev server
  only, never a bundler.
- `src/styles.css` is generated and gitignored.

## Deploy

GitHub Pages via Actions. After the first push, flip the Pages source:

```sh
gh api -X PUT /repos/brandonmartinez/geekycomputerservices/pages -f build_type=workflow
```

The domain `geekycomputerservices.com` must be registered before this resolves;
it lapsed in 2005 and was still unregistered as of July 2026.
