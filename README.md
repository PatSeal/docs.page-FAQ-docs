# Avodah FAQ — docs.page prototype

This is a docs.page-based version of the same FAQ/help center content, built to compare against the Nuxt.js prototype delivered earlier.

## How to get this live

docs.page has no build step — it renders directly from a public GitHub repo. To publish:

1. Add these files (`docs.json` and the whole `docs/` folder) to the root of **https://github.com/PatSeal/docs.page-FAQ-docs**. Easiest way if you're not comfortable with git commands: open that repo on github.com, click **Add file → Upload files**, and drag the extracted `docs.json` file and the `docs` folder in together (modern browsers keep the folder structure intact when you drag a whole folder).
2. Commit the upload (the button at the bottom of that upload page).
3. Visit **https://docs.page/PatSeal/docs.page-FAQ-docs** — it should be live within moments, no deploy step needed.

If you'd rather use git directly:
```
git clone https://github.com/PatSeal/docs.page-FAQ-docs.git
# copy docs.json and the docs/ folder into that cloned folder
cd docs.page-FAQ-docs
git add .
git commit -m "Add Avodah FAQ content"
git push
```

## What's different from the Nuxt.js prototype

**The admin edit panel has been dropped for this version — by design, not as an oversight.** docs.page is a hosted renderer with no server of its own to run custom code against; it only understands a `docs.json` config plus Markdown/MDX files pulled live from GitHub. There's no way to bolt on a custom in-browser editor the way the Nuxt prototype has one, so per your instruction, that feature is cancelled here rather than forced. Editing content on this platform means editing the Markdown files directly (in GitHub's own web editor, or locally) and pushing — which is actually the same "docs-as-code" foundation the AI-agent maintenance workflow (recommendation doc, Section 4) was built around, so that part still works unchanged.

Also different:
- **No custom visual design** — docs.page has its own fixed theme (you can set a primary color and logo, which `docs.json` here does with a blue accent, but you don't get the fully custom nuxt.com-style layout the Nuxt prototype has).
- **The repo must stay public** for the hosted docs.page service to render it. If any content here ever needs to be private, this isn't the right platform for it.
- **Versioning** works via git branches (docs.page serves branch/tag previews at distinct URLs) rather than folders.
- Once live, a custom domain (`docs.avodahapp.com`) is possible via a CNAME record plus a pull request to docs.page's own repo — that's a separate step once this is live and you're happy with it.

## Content

Same information architecture as the Nuxt prototype: Getting Started, Using Avodah, Groups, Events, Giving, FAQ — same placeholder text, same caveat that it was drafted from a low-resolution site-map image and needs checking against the real app before this goes anywhere public.
