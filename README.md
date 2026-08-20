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

## AI-agent maintenance workflow (included)

This package now includes `.github/workflows/ai-docs-update.yml`, which wires up the maintenance-automation approach from the recommendation doc (Section 4) specifically for this docs.page repo. Once it's uploaded to GitHub along with everything else, here's how it works and what you still need to do to turn it on.

**What it does:** anyone can open a GitHub Issue describing a documentation change (e.g. "the Giving page needs to mention recurring gifts can now be paused") and either label it `ai-docs` or mention `@claude` in the text, or comment `@claude <instruction>` on an existing issue/PR. Claude reads the instruction, edits the relevant `.mdx` files under `docs/` (and `docs.json`'s sidebar if a page is added), and opens a pull request. It's told explicitly never to touch `.github/` or merge anything itself — a human always reviews and merges the PR. You can also trigger it manually from the Actions tab (`workflow_dispatch`) without needing an issue at all.

**One-time setup you need to do on github.com (I don't have push access to your repo, so this part can't be done for you):**
1. Upload this whole package (`docs.json`, `docs/`, and now `.github/`) to **https://github.com/PatSeal/docs.page-FAQ-docs** the same way as before — drag-and-drop via **Add file → Upload files** keeps the `.github/workflows/` folder structure intact, or use `git add . && git commit && git push` if you're working from a clone.
2. Get an Anthropic API key (from the Claude Console, if you don't already have one for the org).
3. In the repo, go to **Settings → Secrets and variables → Actions → New repository secret**, name it `ANTHROPIC_API_KEY`, and paste the key in as the value.
4. That's it — the workflow is now live. Test it by opening an issue with `@claude` in the body.

**Note on scope:** the action has no built-in mechanism to hard-restrict which files it can touch — the "only edit `docs/` and `docs.json`" boundary is enforced by instructing Claude in the workflow's prompt, not by file permissions. Treat every PR it opens as a draft to review, the same as you would a human contributor's — that's the whole point of the PR-based workflow rather than auto-merge.
