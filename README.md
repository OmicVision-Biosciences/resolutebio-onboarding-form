# Resolute Bio Onboarding Form

Static onboarding form hosted on GitHub Pages.

**Live form:** [https://omicvision-biosciences.github.io/resolutebio-onboarding-form/](https://omicvision-biosciences.github.io/resolutebio-onboarding-form/)

## Enable GitHub Pages (one-time)

If the form is not live yet:

1. Open the repo on GitHub → **Settings** → **Pages**
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**
3. Choose branch `main` and folder `/ (root)`
4. Save — the form will be available at the URL above within a few minutes

## Update the form

The site is a single file: `index.html`.

1. Replace `index.html` with a new .html file of the form
2. Commit and push to `main`:

```bash
git add index.html
git commit -m "Update onboarding form"
git push origin main
```

1. Wait a minute or two, then refresh the live URL to confirm the change

No build step is required. GitHub Pages serves `index.html` from the root of `main` as-is.