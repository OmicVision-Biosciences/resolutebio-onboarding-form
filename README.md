# Resolute Bio Onboarding Form

Static onboarding form hosted on GitHub Pages.

**Version:** 1.1.4 ([changelog](CHANGELOG.md))

**Live form:** [https://omicvision-biosciences.github.io/resolutebio-onboarding-form/](https://omicvision-biosciences.github.io/resolutebio-onboarding-form/)

The form shows this version in the footer (`© 2026 · vX.Y.Z`) after it unpacks. The number comes from `version.js` (`window.FORM_VERSION`). bumpversion updates that file and the version line in this README. It does **not** edit `CHANGELOG.md` (see release steps below).

## Enable GitHub Pages (one-time)

If the form is not live yet:

1. Open the repo on GitHub → **Settings** → **Pages**
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**
3. Choose branch `main` and folder `/ (root)`
4. Save — the form will be available at the URL above within a few minutes



## Update the form

The packed form lives in `index.html`. Versioning lives in the outer wrapper (not in a newly exported artifact).

1. Replace `index.html` with a new .html file of the form
2. Restore the outer wrapper pieces if the export overwrote them:
  - `<script src="version.js"></script>` in `<head>`
  - the unpack step that writes `FORM_VERSION` into the footer (`© 2026 · vX.Y.Z`)
3. Commit and push to `main`:

```bash
git add index.html
git commit -m "Update onboarding form"
git push origin main
```

1. Wait a minute or two, then refresh the live URL to confirm the change

No build step is required. GitHub Pages serves `index.html` and `version.js` from the root of `main` as-is.

## Release a new version

Working tree must be clean. Commit form and changelog edits first, then bump.

1. In [CHANGELOG.md](CHANGELOG.md), add a dated release heading **above** `[Unreleased]` for the version you are about to mint, and move the unreleased bullets under it:

   ```markdown
   ## [Unreleased]

   ## [1.1.4] - 2026-09-10
   - [Added] Your change here
   ```

2. Commit those changes
3. Bump (updates `version.js`, the version line above, and `.bumpversion.cfg` only):

```bash
bumpversion patch   # 1.0.0 -> 1.0.1
bumpversion minor   # 1.0.0 -> 1.1.0
bumpversion major   # 1.0.0 -> 2.0.0
```

1. Push the commit and tag:

```bash
git push origin main 
```

