# EPIC — Deploy Guide
## Ecom Price Calculator v1
**© 2026 Sumit Rai · Raimage Design**

---

## Option A — GitHub Pages (Free, Permanent URL)

### Step 1 — Create GitHub repo
1. Go to **github.com** → Sign in (or create free account)
2. Click **"New repository"** (top right `+` button)
3. Name it: `epic-calc` (or anything you like)
4. Set to **Public**
5. Check **"Add a README file"**
6. Click **"Create repository"**

### Step 2 — Upload your file
1. Inside the repo, click **"Add file" → "Upload files"**
2. Drag and drop **`EPIC-ecom-price-calc-v1.html`**
3. **Rename it to `index.html`** before uploading (GitHub Pages serves `index.html` as homepage)
   - Or rename in the commit message area by clicking the file after upload
4. Scroll down → Click **"Commit changes"**

### Step 3 — Enable GitHub Pages
1. Go to your repo → **Settings** tab
2. Left sidebar → **Pages**
3. Under "Source" → **Deploy from a branch**
4. Branch: **`main`** → Folder: **`/ (root)`**
5. Click **Save**
6. Wait ~60 seconds

### Step 4 — Your live URL
```
https://YOUR-USERNAME.github.io/epic-calc/
```
Example: `https://sumitrai.github.io/epic-calc/`

**Done. Share this URL anywhere.**

---

## Option B — Vercel (Free, Fastest, Custom Domain)

### Step 1 — Deploy in 30 seconds
1. Go to **vercel.com** → Sign up free (use GitHub login)
2. On dashboard, look for **"Add New → Project"**
3. Click **"Deploy"** on the left panel
4. Look for **"Or deploy without a Git provider"** at bottom
5. **Drag and drop** `EPIC-ecom-price-calc-v1.html` into the upload area
6. Vercel auto-detects it as a static site
7. Click **Deploy**

### Step 2 — Your live URL
Vercel gives you a URL like:
```
https://epic-calc-xyz123.vercel.app
```

### Step 3 (Optional) — Custom domain
1. Go to your project settings → **Domains**
2. Add `epic.raimage.design` or any domain you own
3. Add the DNS records Vercel shows you (CNAME or A record)
4. SSL is automatic

---

## Option C — Netlify (Alt free host)

1. Go to **app.netlify.com**
2. Drag and drop the HTML file into the deploy box
3. Done — instant URL like `https://epic-calc.netlify.app`

---

## Razorpay Integration (Go Live with Payments)

When ready to accept payments, do this in the `doRazorpay()` function:

```javascript
function doRazorpay() {
  var options = {
    key: 'YOUR_RAZORPAY_KEY_ID',      // from razorpay.com dashboard
    amount: 9900,                       // ₹99 in paise
    currency: 'INR',
    name: 'EPIC — Ecom Price Calculator',
    description: 'Monthly subscription ₹99',
    handler: function(response) {
      // After payment success — call your backend to verify
      showToast('Payment successful! Subscription activated.');
      document.getElementById('paywall').classList.remove('show');
    },
    prefill: {
      name: user.name,
      email: user.email
    },
    theme: { color: '#c8f060' }
  };
  var rzp = new Razorpay(options);
  rzp.open();
}
```

**Setup steps:**
1. Create account at **razorpay.com**
2. Complete KYC (business/individual)
3. Go to **Settings → API Keys → Generate Key**
4. Copy your `KEY_ID` (starts with `rzp_live_...`)
5. Add `<script src="https://checkout.razorpay.com/v1/checkout.js"></script>` to your `<head>`
6. Replace `YOUR_RAZORPAY_KEY_ID` in the code above

**For production:** You'll need a backend endpoint to verify payments. Use Node.js/Express or any serverless function.

---

## What's Live in This Build

| Feature | Status |
|---|---|
| Landing page with hero mockup | ✅ Live |
| Sign up / Log in flow | ✅ Live |
| 3-day trial + paywall | ✅ Live |
| Price Calculator (full) | ✅ Live |
| External Product ID (ASIN/EAN/GTIN/UPC) | ✅ Live |
| Product category → auto commission | ✅ Live (20 categories) |
| 8 platforms — add/remove | ✅ Live |
| Custom platform builder | ✅ Live |
| Waterfall cost breakdown | ✅ Live |
| Smart signals | ✅ Live |
| Cross-platform comparison | ✅ Live |
| Saved presets (localStorage) | ✅ Live |
| Bulk SKU calculator (CSV) | ✅ Live |
| Share via WhatsApp | ✅ Live |
| Copy text report | ✅ Live |
| Export CSV | ✅ Live |
| Calculation history (sample) | ✅ Live |
| Billing page | ✅ Live |
| Profile page | ✅ Live |
| Legal (Terms + Privacy) | ✅ Live |
| Dark / Light mode | ✅ Live |
| Razorpay payment | 🔑 Needs KEY_ID |
| Backend auth | 🔧 Needs server |
| Real user accounts | 🔧 Needs database |

---

## File Checklist for Deploy

| File | Action |
|---|---|
| `EPIC-ecom-price-calc-v1.html` | **Rename to `index.html`** and upload |

That's it. One file. No build step. No npm. No server needed.

---

*Built by Sumit Rai · Raimage Design · 2026*
