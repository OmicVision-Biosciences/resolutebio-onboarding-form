# Resolute Bio Onboarding Form

Static onboarding form hosted on GitHub Pages.

**Version:** 1.0.0 ([changelog](CHANGELOG.md))

**Live form:** [https://omicvision-biosciences.github.io/resolutebio-onboarding-form/](https://omicvision-biosciences.github.io/resolutebio-onboarding-form/)

The form shows this version in a badge after it unpacks. The number comes from `version.js` (`window.FORM_VERSION`). bumpversion updates that file and the version line in this README, then commits and tags `vX.Y.Z`.

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
   - the post-`replaceWith` `#form-version` badge mount
3. Commit and push to `main`:

```bash
git add index.html
git commit -m "Update onboarding form"
git push origin main
```

4. Wait a minute or two, then refresh the live URL to confirm the change

No build step is required. GitHub Pages serves `index.html` and `version.js` from the root of `main` as-is.

## Release a new version

Working tree must be clean. Commit form and changelog edits first, then bump.

1. Record differences in [CHANGELOG.md](CHANGELOG.md) (move `[Unreleased]` into a `## [x.y.z] - YYYY-MM-DD` heading for the version you are about to mint)
2. Commit those changes
3. Bump (updates `version.js` and the version line above, commits, tags `vX.Y.Z`):

```bash
bumpversion patch   # 1.0.0 -> 1.0.1
bumpversion minor   # 1.0.0 -> 1.1.0
bumpversion major   # 1.0.0 -> 2.0.0
```

4. Push the commit and tag:

```bash
git push origin main --follow-tags
```
