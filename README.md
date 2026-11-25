# Upkeep — public Privacy and Support website

**Owner-approved for TestFlight beta; legal review recommended before public release.** Approval recorded November 25, 2026. The website is already published; this local revision removes the previous pending-approval labels and has not been uploaded automatically. Approval is the owner's beta-content decision, not a claim of attorney clearance or legal compliance.

This folder is separate from the Expo application. It contains a dependency-free static website; no build, JavaScript, analytics, backend or accounts are needed.

## Pages

- `index.html`: Privacy Policy, based on the verified Phase 10 draft.
- `support.html`: Support contact and bug-reporting guidance.
- `wellness.html`: Health & Wellness Disclaimer, owner-approved for the initial TestFlight beta. Its substantive disclaimer text is unchanged.
- `styles.css`: shared responsive dark charcoal, orange, cyan and lime presentation.
- `assets/`: unchanged copies of the approved Upkeep wordmark and app icon. No newly generated artwork.
- `.nojekyll`: serves this static site without a Jekyll build.

All website paths are relative so the pages work under a GitHub Pages project path such as `/upkeep-legal/`. No application source, tracking data, credentials or signing files belong in this public repository.

## Owner review before publishing

1. The Privacy Policy effective date remains **November 25, 2026**, matching the published policy. This approval-label correction changes no privacy practices and does not reset that effective date. Change it for an actual later policy revision/effective date, rather than merely because a deployment occurs later.
2. Responsible developer: **Blair Atkins**. Official privacy/support contact: **support.upkeep@gmail.com**. Keep the mailbox monitored and ensure actual support handling matches the policy.
3. The owner has approved the existing Health & Wellness Disclaimer for the initial TestFlight beta. Pending-approval labels have been removed from all three HTML pages, including metadata and footer/cross-reference text. **Legal review is recommended before public release.** No Terms of Use or acceptance mechanism is created by this update.
4. Confirm any additional legal requirements for intended jurisdictions, audiences and developer status with counsel, including whether a postal address or additional rights/complaints language is required. None has been invented. This website does not include Terms of Use or an acceptance mechanism.
5. Confirm data practices still match the release binary if the application changes. The policy distinguishes app-local records, OS backups, Apple/TestFlight services, voluntary support email and GitHub hosting logs. It does not claim that GitHub collects no visitor data.
6. Review all three pages on a phone and desktop. Verify the email links, navigation and accessibility. This local revision is not public until you upload/commit it and GitHub Pages deploys it.

## Manual publication through GitHub Pages

These instructions are for the repository owner to perform **after review**. No repository, commit or deployment has been created automatically. The current local folder is **not a Git checkout**; use a separate clone for the existing public repository so its history is retained.

### Update the existing repository using PowerShell and Git

Run these commands manually after reviewing the local revision. The new clone directory below must not already exist. If you already have a checkout, use that checkout instead and review its status before copying files; do not reset it or overwrite unrelated work.

```powershell
$legalSource = 'C:\Users\batki\Projects\upkeep-legal'
$publishFolder = 'C:\Users\batki\Projects\upkeep-legal-publish'
if (Test-Path -LiteralPath $publishFolder) { throw 'Publish folder already exists. Use a clean checkout or choose a new clone directory.' }

git clone https://github.com/batkins22/upkeep-legal.git $publishFolder
if ($LASTEXITCODE -ne 0) { throw 'Clone failed. Stop and resolve the Git error.' }
Set-Location $publishFolder
git switch main
if ($LASTEXITCODE -ne 0) { throw 'Could not select main. Stop and review the repository branches.' }
git status --short

Copy-Item -LiteralPath @(
  "$legalSource\index.html",
  "$legalSource\support.html",
  "$legalSource\wellness.html",
  "$legalSource\README.md"
) -Destination $publishFolder

git diff --check
if ($LASTEXITCODE -ne 0) { throw 'Diff check failed. Review before committing.' }
git diff -- index.html support.html wellness.html README.md
git add -- index.html support.html wellness.html README.md
git diff --cached --check
if ($LASTEXITCODE -ne 0) { throw 'Staged diff check failed. Review before committing.' }
git diff --cached
git commit -m "Approve wellness disclaimer for TestFlight beta"
if ($LASTEXITCODE -ne 0) { throw 'Commit failed or no changes were present. Review before pushing.' }
git push origin main
git status --short
```

The push publishes through the repository's existing Pages configuration; GitHub may ask you to sign in. These commands do not stage application files, assets or CSS. Review each diff before proceeding. After deployment, verify all three public pages no longer describe the disclaimer as pending/draft. The public repository, not the local source folder, owns the Git history.

### Browser upload alternative / Pages configuration

1. Sign in to the desired GitHub account. Create a **public** repository named `upkeep-legal`, or open it if it already exists. Do not add the private Expo project.
2. Upload/commit the **contents of this folder at the repository root**, not a wrapping `upkeep-legal` folder. The root must contain `index.html`, `support.html`, `wellness.html`, `styles.css`, `.nojekyll` and the `assets` folder. GitHub's **Add file → Upload files** supports the website files/folder; ensure the hidden `.nojekyll` file is included (use **Add file → Create new file** if needed). Commit to `main`. README may be included too.
3. In that repository, open **Settings → Pages**.
4. Under **Build and deployment → Source**, select **Deploy from a branch**.
5. Select branch **main**, folder **/(root)**, then **Save**. No custom Actions workflow, package installation or build command is required.
6. Wait for GitHub's Pages deployment to finish; GitHub notes this can take up to 10 minutes. Use the actual **Visit site** link shown in Pages settings. Keep HTTPS enabled where available. A custom domain is not required.
7. Verify the published pages, including the project-path links and local images. Tap **Email support** and confirm your email application addresses the message to `support.upkeep@gmail.com`; sending a test message is optional and manual.
8. Only after verifying the live URLs, supply the Privacy Policy and Support URLs for the release checklist/App Store Connect. This task does not change the app or App Store Connect records.

The existing `batkins22/upkeep-legal` website uses:

- Privacy: `https://batkins22.github.io/upkeep-legal/`
- Support: `https://batkins22.github.io/upkeep-legal/support.html`
- Disclaimer: `https://batkins22.github.io/upkeep-legal/wellness.html`

All three URLs were verified over HTTPS during final pre-build preparation on November 25, 2026. That verification predates this local approval-label revision; verify the updated live content after your manual deployment. No app changes are part of this website task.

## Local review

Open `index.html` in a browser for a simple offline review, or serve this folder with an existing static HTTP server. No server installation is required for deployment. Check 375px and 393px phone widths and a desktop width. Use keyboard Tab to reach the skip link, navigation and email links. Check that enlarged text wraps and no draft or pending-approval labels remain in any HTML page.

## Privacy and hosting notes

The website makes no script, analytics or third-party font requests. External privacy references are ordinary links opened only when followed. GitHub Pages itself logs/stores visitor IP addresses for security. Support correspondence is voluntarily sent through the user's email service; this site contains no submission form.

Official publication/hosting references:

- [GitHub Pages publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [GitHub Pages quickstart](https://docs.github.com/en/pages/quickstart)
- [GitHub Pages data collection](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages#data-collection)

The Privacy Policy is separate from the Health & Wellness Disclaimer. **Owner-approved for TestFlight beta; legal review recommended before public release.** These materials are not a guarantee of legal compliance.

## Preparation checks — November 25, 2026

- All three pages passed local headless Chrome checks at 320px, 375px, 393px and 1440px widths (12 page/viewport combinations), served under the `/upkeep-legal/` project path.
- No horizontal overflow; images loaded; local page links and fragment destinations resolved; one main heading per page; primary navigation/contact controls at least 44px high.
- Keyboard skip links and 200% text at 375px passed. Phone and desktop screenshots were visually reviewed; these are browser checks, not physical-iPhone or screen-reader certification.
- No scripts, forms, cookies, local-storage entries or automatically requested external resources were observed. GitHub's own hosting behavior is separate and disclosed in the policy.
- Approved artwork copies match the original assets. No Expo application files were changed; the app working-tree/content fingerprint remained identical.
- No publication, Git commit/push or EAS build was performed. Public URLs and live email delivery remain for owner verification after manual publication.

## Beta approval revision checks — November 25, 2026

- All three local pages passed browser checks at 320px, 375px, 393px and 1440px (12 combinations), including image loading, navigation/fragment targets, keyboard skip links, minimum navigation/contact target heights and 200% text at 375px. No horizontal overflow was found.
- HTML text and metadata contain no draft, pending-approval or awaiting-approval labels. The wellness page at 393px was visually reviewed after removing the banner.
- Every substantive disclaimer section matches the previous version exactly. Privacy and Support changes are limited to removing obsolete approval-status wording from cross-references and footer links.
- Shared CSS, artwork, contacts and the Privacy Policy effective date are unchanged. The main Expo application working-tree/content fingerprint is identical before and after this task.
- The existing public repository is `batkins22/upkeep-legal`, with default branch `main`, verified read-only. The local source folder has no `.git` directory; no clone, staging, commit or push was performed. The publishing commands above are for manual execution after review.
