# qianniu0304.github.io

Personal academic website for **Qian NIU**, Researcher, Matsuo–Iwasawa Laboratory, The University of Tokyo.

Site copy deliberately avoids em dashes; use commas, colons, or semicolons instead when editing.

Live site (once GitHub Pages is enabled): <https://qianniu0304.github.io>

## Structure

```
index.html            single-page site (all sections)
style.css             all styling; light + dark via prefers-color-scheme
assets/profile.jpg    portrait, cropped square to 512×512
assets/favicon.svg    favicon
.nojekyll             serve files as-is, skip Jekyll processing
```

No build step, no dependencies. Static HTML/CSS with ~15 lines of JS for the
active-section nav highlight.

Source files (`CV_NiuQian_260526.pdf`, the uncropped `profile.jpg`) stay local and are
gitignored — only the derived web assets are published.

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Updating content

- **Publications** — edit the `<ol class="pubs">` list in `index.html`. It sits inside a
  `.pubs-scroll` box that caps the visible height at about five entries and scrolls for the rest;
  the cap is `max-height` on `.pubs-scroll` in `style.css`, and printing ignores it. Adding or
  removing entries needs no other change.
- **Portrait** — replace `assets/profile.jpg` with another square crop (512×512 is plenty; it renders
  at 160&nbsp;px). To re-crop from an original:
  ```python
  from PIL import Image
  Image.open('profile.jpg').crop((200, 150, 760, 710)).resize((512, 512), Image.LANCZOS) \
       .save('assets/profile.jpg', 'JPEG', quality=88, optimize=True, progressive=True)
  ```
- **Colors / type** — the CSS custom properties at the top of `style.css` (`:root` and the
  `prefers-color-scheme: dark` block) drive the whole palette.

## Analytics

Page views are counted by [GoatCounter](https://www.goatcounter.com/) via one `<script>` tag at
the bottom of `index.html`. It stores no cookies and no personal data, so no consent banner is
needed, and the free tier covers non-commercial sites.

Setup, one time:

1. Register the code `qianniu0304` at <https://www.goatcounter.com/signup>. The code becomes the
   dashboard subdomain, `https://qianniu0304.goatcounter.com`.
2. If a different code is registered, change the `data-goatcounter` URL in `index.html` to match,
   otherwise hits are dropped.

The dashboard reports visit counts, referrers, countries, browsers, and screen sizes. It does not,
and cannot, identify individual visitors by name.

Worth pairing with [Google Search Console](https://search.google.com/search-console), which shows
the queries that lead people here. It needs a verification meta tag in `<head>`.

## Publishing

Settings → Pages → Source: *Deploy from a branch* → `main` / `root`.

Note: GitHub Pages on a **private** repository requires a paid plan (Pro/Team/Enterprise).
On the free plan, make the repository public when you are ready to publish.
