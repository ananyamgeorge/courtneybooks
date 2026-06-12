# courtneybooks.com

Landing page for **Courtney** — a court-finding concierge for pickleball, padel and
badminton, anywhere in India. Tell her the sport, area and time on WhatsApp or
Telegram; she checks Hudle, KheloMore and Playo at once and sends back open courts
with a direct link to book.

- **WhatsApp:** [+91 90826 67025](https://wa.me/919082667025?text=Hi%20Courtney)
- **Telegram:** [@CourtneyBooks_Bot](https://t.me/CourtneyBooks_Bot)

## Stack

Plain static site — no build step.

```
index.html      # single page
styles.css
assets/         # WhatsApp + Telegram QR codes
vercel.json     # cleanUrls
```

## Local preview

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Deploy (Vercel + courtneybooks.com)

1. Go to **vercel.com → Add New → Project** and import this GitHub repo.
2. Framework preset: **Other**. No build command, output dir = repo root. Click **Deploy**.
3. In the project: **Settings → Domains → Add** `courtneybooks.com` (and `www.courtneybooks.com`).
4. At your domain registrar, set the DNS records Vercel shows:
   - `A` record `@` → `76.76.21.21`
   - `CNAME` `www` → `cname.vercel-dns.com`
5. Wait for the cert to issue — the site is live at https://courtneybooks.com.

### Updating the QR codes / number

QR PNGs in `assets/` were generated with:

```bash
npx qrcode "https://wa.me/919082667025?text=Hi%20Courtney" -o assets/qr-whatsapp.png -w 600
npx qrcode "https://t.me/CourtneyBooks_Bot"               -o assets/qr-telegram.png  -w 600
```

If the WhatsApp number changes, regenerate the QR and update the links in `index.html`.
