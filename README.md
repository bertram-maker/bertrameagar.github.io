# bertrameagar.com — raw rebuild

Plain HTML/CSS replacement for the old Wix site. No build step, no framework —
just three pages (`index.html`, `about.html`, `contact.html`) and one
stylesheet. Content on Home/About was pulled from the old Wix export sitting
next to this folder (`../bertrameagar.com/`); the itch.io links came from
`games.md` in that export.

## Before pushing

- **`contact.html`** still has a placeholder email address
  (`REPLACE_WITH_EMAIL@example.com`) — swap that for a real one. The old
  site used a Wix contact form, which needs a backend Pages doesn't have; a
  mailto link plus the itch.io link stand in for now. If a real form is
  wanted later, a service like Formspree works without a backend.
- **`CNAME`** is set to `bertrameagar.com`. Only keep this file if the plan
  is to point the existing domain at GitHub Pages (see DNS step below).
  Delete it to publish only at `<username>.github.io/<repo>` instead.
- Images from the old site weren't ported over — they're sitting in
  `../bertrameagar.com/static.wixstatic.com/media/` if any are worth pulling
  in.

## Publishing with GitHub Pages

1. Create a new (empty) repo on GitHub.
2. From this folder:
   ```
   git init
   git add .
   git commit -m "Raw rebuild of bertrameagar.com"
   git branch -M main
   git remote add origin <your-repo-url>
   git push -u origin main
   ```
3. In the repo's Settings → Pages, set the source to the `main` branch,
   root folder.
4. If keeping the `CNAME` file and the custom domain: in your domain's DNS
   settings, point `bertrameagar.com` at GitHub Pages (an `A` record set to
   GitHub's Pages IPs, or a `CNAME` record for a `www` subdomain — GitHub's
   docs have the current values). Then set the custom domain in
   Settings → Pages too, so GitHub can issue HTTPS for it.
