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

- **Publications** — edit the `<ol class="pubs">` lists in `index.html`. Each group has its own
  `start=` attribute so numbering stays continuous; bump the later ones if you add entries to an
  earlier group. The list intentionally shows only accepted work, no under-review submissions.
- **Portrait** — replace `assets/profile.jpg` with another square crop (512×512 is plenty; it renders
  at 160&nbsp;px). To re-crop from an original:
  ```python
  from PIL import Image
  Image.open('profile.jpg').crop((200, 150, 760, 710)).resize((512, 512), Image.LANCZOS) \
       .save('assets/profile.jpg', 'JPEG', quality=88, optimize=True, progressive=True)
  ```
- **Colors / type** — the CSS custom properties at the top of `style.css` (`:root` and the
  `prefers-color-scheme: dark` block) drive the whole palette.

## Publishing

Settings → Pages → Source: *Deploy from a branch* → `main` / `root`.

Note: GitHub Pages on a **private** repository requires a paid plan (Pro/Team/Enterprise).
On the free plan, make the repository public when you are ready to publish.
