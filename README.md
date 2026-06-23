# slk350.xyz — single-car sales site

A static, single-page listing for the 2008 Mercedes-Benz SLK350, modeled on
Bring a Trailer's layout. Hosts free on GitHub Pages with the custom domain
**slk350.xyz**. The contact form runs on **Web3Forms** and emails every inquiry
to both sellers — no phone number is exposed anywhere on the site.

Files:
- `index.html` — the entire site (HTML, CSS, JS in one file)
- `CNAME` — tells GitHub Pages to serve the site at slk350.xyz (don't delete)
- `photos/` — drop the car photos here (see the txt note inside)
- `README.md` — this file

---

## 1. Add the photos
Put images in `photos/` named `01.jpg`, `02.jpg`, ... `01.jpg` is the hero shot.
Details and tips are in `photos/README-PUT-PHOTOS-HERE.txt`. If you add more than
12, edit the `PHOTOS` list near the bottom of `index.html` to match.

## 2. Wire up the contact form (Web3Forms — 2 minutes)
1. Go to https://web3forms.com and enter **r32wagn@gmail.com** to create a free
   access key. The key is emailed to you instantly.
2. In `index.html`, find this line and paste your key in place of the placeholder:
   ```
   <input type="hidden" name="access_key" value="YOUR_WEB3FORMS_ACCESS_KEY">
   ```
3. To send every inquiry to **both** of you: log into the Web3Forms dashboard,
   open this access key's settings, and add **myers06@gmail.com** as an additional
   recipient (CC). Now both inboxes get every message.
4. (Optional) Until the key is added the form will show a "not configured yet"
   message instead of failing silently — so it's safe to deploy first and add the
   key after.

## 3. Deploy on GitHub Pages
1. Create a new **public** repo on GitHub (any name, e.g. `slk350`).
2. Upload everything in this folder (`index.html`, `CNAME`, `photos/`, `README.md`)
   to the repo root. Either drag-and-drop in the GitHub web UI, or:
   ```
   git init
   git add .
   git commit -m "SLK350 listing site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/slk350.git
   git push -u origin main
   ```
3. In the repo: **Settings → Pages**. Under "Build and deployment", set
   **Source = Deploy from a branch**, **Branch = main**, **folder = / (root)**. Save.
4. Still on the Pages screen, under "Custom domain" enter **slk350.xyz** and Save.
   (The included `CNAME` file already sets this, but entering it here triggers
   GitHub's verification.) Leave "Enforce HTTPS" checked once it becomes available.

## 4. Point DNS for slk350.xyz
At your domain registrar, set these records for the **apex** domain (`slk350.xyz`):

**A records** (all four, host `@`):
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
**AAAA records** (optional but recommended, host `@`):
```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```
**CNAME record** for `www` → `<your-username>.github.io`

> These are GitHub's published Pages IPs. They rarely change, but if the site
> won't verify, confirm the current values at:
> https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site

DNS can take anywhere from a few minutes to a few hours to propagate. Once it does,
GitHub auto-issues a free HTTPS certificate (can take up to ~24h the first time).

## 5. Updating the listing later
Edit `index.html` and re-upload (or `git commit` + `git push`). Changes go live in
under a minute. Common edits:
- **VIN**: search `To be added` in `index.html` and drop the VIN in.
- **Price/wording**: the price shows as "Open to serious offers" — search that
  phrase to change it.
- **Specs**: the sidebar table is plain HTML near the middle of the file.

---

### Quick reference
| Item | Value |
|------|-------|
| Domain | slk350.xyz |
| Host | GitHub Pages (free) |
| Form service | Web3Forms (free) |
| Form recipients | r32wagn@gmail.com + myers06@gmail.com |
| Price shown | "Open to serious offers" |
| Location | Eugene, OR |
