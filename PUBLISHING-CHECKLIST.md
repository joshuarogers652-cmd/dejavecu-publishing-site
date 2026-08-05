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

## 3. Email / Newsletter — Kit (formerly ConvertKit)
1. Create a free account at kit.com (free up to 10,000 subscribers).
2. Create a new "Landing Page & Forms" → Form (inline style to match the site's minimal look).
3. Grab your Form ID from the embed/share code.
4. In `index.html`, replace `REPLACE_WITH_YOUR_FORM_ID` in the newsletter `<form action="...">` with your real ID.
5. Tag subscribers on signup (e.g. `book-2-notify`) so you can segment later.

## 4. Content Still Needed From You
- [ ] **Author bio** — more background, influences, what led you to write EMMA (current bio is a placeholder draft)
- [ ] **Retailer links** — once EMMA is published, replace the "Coming Soon" badge in the Buy section with real Amazon/Audible/etc. buttons
- [ ] **Pull quote** — the "I hope this story reminds you..." line is a placeholder; swap for a real quote if you have one

## 5. Nice-to-Haves (Later)
- Book cover reveal / preview chapter as lead magnet for the newsletter signup
- Social share meta tags (Open Graph image) using the EMMA cover
- Analytics (Azure has built-in, or add Plausible/GA4)
