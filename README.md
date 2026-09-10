# SariSmart — Smart Restocking for a Smarter Sari-Sari Store

A simple, free, camera-based inventory & sales tracker for sari-sari stores, based on the
SariSmart business plan (BPSU-Main Campus, Technopreneurship 101, Group 5).

- **`index.html`** — the app itself: scan a product's QR code, log it as Inventory (Stock)
  or Sale (Benta), and see a live dashboard (stock levels, today's profit, top sellers).
- **`manifest.json`** + **`service-worker.js`** + **`icons/`** — turn the app into an
  installable PWA (Progressive Web App), which is what makes it possible to package as
  a real `.apk` (see "Paano makakuha ng tunay na APK" below).
- **`qr-codes.html`** — a printable sheet of 5 sample QR labels you can cut out and stick
  on products to test the scanner right away.
- **`qr_labels.pdf`** — the same 5 QR labels already laid out as a ready-to-print PDF
  (no browser needed — open and print directly).
- **`qr_png/`** — the 5 QR codes as individual PNG images, in case you want to paste them
  into Word, Canva, or a label maker.
- **`logo.png`** — the SariSmart logo used in the app header.

No backend needed — it runs entirely in the browser and saves data on the device using
`localStorage`, so it works even offline once loaded.

## Paano i-upload sa GitHub (step by step)

1. **Gumawa ng GitHub account** kung wala ka pa: https://github.com/signup

2. **Gumawa ng bagong repository**
   - Sa GitHub, i-click ang **"+"** sa taas-kanan → **New repository**.
   - Repository name: `sarismart` (o anumang gusto mo)
   - Public
   - Huwag muna i-check ang "Add a README" (mayroon na tayong README dito)
   - I-click **Create repository**

3. **I-upload ang mga files**
   - Sa page ng bagong repo, i-click **"uploading an existing file"**
   - I-drag-and-drop ang lahat ng files: `index.html`, `manifest.json`, `service-worker.js`,
     `qr-codes.html`, `logo.png`, `README.md`, ang buong `icons` folder, at ang buong
     `qr_png` folder (opsyonal, `qr_labels.pdf` din kung gusto mong naka-attach)
   - I-scroll pababa, ilagay ang commit message (hal. "Initial SariSmart app"), tapos
     i-click **Commit changes**

4. **I-enable ang GitHub Pages (para may live link ang app)**
   - Sa repo, pumunta sa **Settings** → **Pages** (nasa left sidebar)
   - Sa ilalim ng "Build and deployment" → Source: **Deploy from a branch**
   - Branch: **main**, folder: **/ (root)** → **Save**
   - Maghintay ng 1–2 minuto, mag-a-appear ang link, hal.:
     `https://<iyong-username>.github.io/sarismart/`

5. **Buksan sa phone**
   - Buksan ang link sa Chrome ng phone (dapat gumamit ng HTTPS link mula sa GitHub Pages
     para gumana ang camera/scanner — hindi gagana ang camera kung `file://` lang o plain HTTP).
   - Payagan (allow) ang camera permission kapag hiningi.
   - Buksan din ang `https://<iyong-username>.github.io/sarismart/qr-codes.html` para
     i-print o i-screenshot ang 5 QR labels.

## Paano gamitin ang app

1. Sa tab na **Scan**, piliin muna kung **Inventory (Stock)** o **Sale (Benta)** ang gagawin.
2. I-scan ang QR/barcode na nakadikit sa produkto gamit ang camera (o "enter code manually"
   kung walang camera access).
3. Ilagay ang quantity — awtomatikong mag-a-update ang stock at profit.
4. Tingnan sa tab na **Dashboard** ang current stock, profit ngayong araw, at top-selling
   products.
5. Sa tab na **Products**, pwede kang magdagdag/mag-edit ng mga produkto at ng kanilang code.
6. Sa tab na **QR Labels**, pwede kang gumawa ng bagong QR para sa bagong produkto at i-print
   agad.

## Mga sample na produkto (nasa `qr-codes.html` at preloaded sa app)

| Code | Product |
|---|---|
| SARISMART-P001 | Nescafe 3in1 |
| SARISMART-P002 | Kopiko Blanca |
| SARISMART-P003 | Lucky Me Pancit Canton |
| SARISMART-P004 | Coke 1L |
| SARISMART-P005 | Purefoods Corned Beef |

Idikit ang mga printed label na ito sa aktwal na produkto, then i-scan sa **Scan** tab para
subukan agad ang app.

## Paano makakuha ng tunay na .apk (para hindi na kailangang buksan sa browser)

Ang `index.html` na ito ay ginawa na ring **PWA (installable web app)** — meron nang
`manifest.json`, `service-worker.js`, at `icons/`. Ibig sabihin, dalawang paraan ka na ngayong
pwedeng piliin:

### Paraan A — "Add to Home Screen" (pinakamabilis, walang APK file)
1. Buksan ang GitHub Pages link mo (`https://<username>.github.io/sarismart/`) sa Chrome
2. I-tap ang tatlong tuldok (⋮) sa Chrome → **"Add to Home Screen"** o **"Install app"**
3. Lalabas ito bilang icon sa home screen ng phone, parang normal na app — walang address
   bar, may sarili itong window

Hindi ito literal na `.apk` file, pero kumikilos at itsura ay parang naka-install na app.

### Paraan B — Gumawa ng tunay na .apk file (libre, walang code)
1. Pumunta sa **https://www.pwabuilder.com** gamit ang Chrome o Edge
2. I-paste ang GitHub Pages link mo (`https://<username>.github.io/sarismart/`)
3. I-click **Start**. Ia-analyze ni PWABuilder ang manifest at service worker mo
4. Pumunta sa tab na **Android** → i-click **Generate Package**
5. Piliin ang package type (Signed APK o AAB) — sundin ang mga default settings
6. I-download ang `.apk` file na binuo nila
7. I-transfer sa Android phone at i-install (kailangan mong payagan ang
   "Install from unknown sources" sa Settings ng phone, dahil hindi ito galing sa
   Google Play Store)

Ito ang parehong paraan na ginagamit ng maraming maliliit na negosyo para i-convert ang
website nila (mismong ganito ka-simple ang SariSmart) papuntang totoong Android app na
naka-install sa telepono, kumpleto na may sariling icon.

**Bakit hindi ako direktang gumawa ng .apk?** Ang pagbuo ng `.apk` file ay
nangangailangan ng Android build tools (Android Studio / Gradle) na kumukuha ng mga
component mula sa internet — hindi available ang mga ito sa environment ko. Ang
PWABuilder ay libreng website na gumagawa ng APK mula sa isang PWA link, kaya iyon ang
pinakamadali at ligtas na paraan para dito.
