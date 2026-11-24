# Déjà Vécu Publishing — Site Launch Checklist

## 1. Hosting — Azure Static Web App
1. Push this folder to a new GitHub repo (e.g. `dejavecu-publishing-site`).
2. In Azure Portal: Create Resource → Static Web App.
   - Source: GitHub, select the repo, branch `main`, app location `/`, no build step needed (plain HTML).
3. Azure auto-creates a GitHub Actions workflow that deploys on every push to `main`.
4. Note the default `*.azurestaticapps.net` URL Azure gives you — confirm the site loads there first.

## 2. Connect Your Domain
1. In the Static Web App resource → Custom Domains → Add.
2. Azure will give you a CNAME (or TXT for apex/root domains) to add at your registrar.
3. At your domain registrar's DNS settings, add the CNAME record Azure provides, pointing your domain (or `www` subdomain) at the Azure default hostname.
4. Wait for DNS propagation (up to ~24 hrs, usually much faster), then verify in Azure — SSL certificate is issued automatically.

## 3. EMMA Series — Content Still Needed
Every open slot on the book pages is marked in the HTML with a `<!-- PLACEHOLDER: ... -->` comment (search `books/*.html` for `PLACEHOLDER`).

- [ ] **Release dates**, Books I–IV
- [ ] **ISBNs** (979-8-9969755 block), after Bowker verification. The ISBN rows are commented out until then.
- [ ] **Retailer links**, Books I–IV
- [ ] **Back-cover blurbs**, Books I–IV (approved copy only; no spoilers)
- [x] **Book I cover** updated to the J.P. Rogers version
- [ ] **Pull quote** in the author section ("I hope this story reminds you...") — confirm or replace
- [ ] Later: *EMMA: The Complete Four-Book Collection* (paperback boxed set)

## Notes
- The site is informational only: links out to retailers, no cart or checkout.
- No newsletter signup (removed in the series update).
- This file is hidden from the public site by `staticwebapp.config.json`.
- Always "series", never "trilogy". Byline is J.P. Rogers.
