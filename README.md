# zyrk.dev

Static site for the Zyrk iPhone app: a one-page landing and the privacy policy
Apple requires a public URL for.

```
index.html          uk landing          https://zyrk.dev/
en/index.html       en landing          https://zyrk.dev/en/
privacy/            uk privacy policy   https://zyrk.dev/privacy/
en/privacy/         en privacy policy   https://zyrk.dev/en/privacy/
assets/             stylesheet, app icon, TMDB logo
CNAME               custom domain for GitHub Pages
```

No build step — plain HTML and one stylesheet. Preview it with

```sh
python3 -m http.server 8787   # then open http://127.0.0.1:8787
```

Absolute paths (`/assets/style.css`) mean it has to be served from the site
root, not opened as files.

## Deploying

**GitHub Pages.** Push this repo to GitHub, then Settings ▸ Pages ▸ Deploy from
branch `main` / root. `CNAME` claims `zyrk.dev`; at the registrar point the
apex at GitHub's `185.199.108-111.153` and add `CNAME www → <user>.github.io`.
Then tick "Enforce HTTPS".

**Cloudflare Pages.** Create a project from the repo, no build command, output
directory `/`, and add `zyrk.dev` as a custom domain. `CNAME` is ignored there
and can stay.

Either host serves `privacy/index.html` at `/privacy/`, which is the URL to put
in App Store Connect.

## Before going live

- `hello@zyrk.dev` appears on both pages and in the policy — make sure mail to
  it reaches you (a registrar or Cloudflare forwarding rule is enough).
- The "Coming soon to the App Store" pill becomes a real App Store badge once
  the app is live.
- The policy names Oleksii Huralnyk as the data controller; it has to match the
  seller name on the App Store listing.
