# wallypaper.app

Marketing and support site for [WallyPaper](https://apps.apple.com/us/app/wallypaper-custom-wallpaper/id6805213479), the iPhone app that turns a photo of your kid or pet into a wallpaper. Static HTML, served by GitHub Pages at **https://wallypaper.app**.

## Pages

| Path | File | Purpose |
| --- | --- | --- |
| `/` | `index.html` | Landing page (App Store Connect: Marketing URL) |
| `/support` | `support.html` | FAQ and contact (App Store Connect: Support URL) |
| `/privacy` | `privacy.html` | Privacy policy, verbatim from the previous Google Sites page (App Store Connect: Privacy Policy URL, `AppConstants.privacyPolicyURL`) |
| `/terms` | `terms.html` | Terms of Use: Apple's Standard EULA plus the WallyPaper Pro subscription terms (App Store Connect: EULA / Terms link) |
| `/404` | `404.html` | Not-found page |

GitHub Pages serves `support.html` at `/support` (and `/support.html`), so the extensionless URLs above work as-is.

## Layout

- `assets/css/site.css` – the one stylesheet, shared by every page. Dark only, to match the app.
- `assets/js/site.js` – mobile nav, scroll reveal, footer year. No dependencies.
- `assets/img/` – app icon sizes, App Store screenshots (WebP), the two framed mockups from the app, the wordmark SVG, Apple's App Store badge, the doodle background from the launch screen, and `og-image.jpg` for link previews.
- `assets/fonts/` – Source Sans 3, Pacifico and Bebas Neue, subset to Latin and self-hosted as WOFF2 (SIL OFL, licenses alongside). The site makes no third-party requests.
- `CNAME` – `wallypaper.app`, so the custom domain survives redeploys.
- `.nojekyll` – tells Pages to publish the files as they are.

## Updating

Edit the HTML, commit to `main`, push. Pages redeploys in about a minute. Feature copy on the landing page follows the App Store description for the live build (1.0.1 as of September 2026); when a new version ships (sports cards, the "Made for" device picker, new fonts), update the Features, Templates and Names sections to match.

To regenerate images: screenshots come from the App Store listing (1284×2778 PNG) resized to 720 wide and encoded with `cwebp -q 82`; the `feat-*.webp` images are the same screenshots with the top 30% (the caption) cropped off.

## Deploying (one-time)

1. GitHub → repo **Settings → Pages** → Source: *Deploy from a branch* → `main` / `/ (root)`.
2. **Settings → Pages → Custom domain**: `wallypaper.app` → Save. (The `CNAME` file in this repo already matches.)
3. **Account Settings → Pages → Add a domain**: verify `wallypaper.app` with the `_github-pages-challenge-<user>` TXT record, so nobody else can claim it on Pages.
4. Porkbun DNS for `wallypaper.app`:
   - Delete the URL forwarding for the apex and `www` (URL Forwarding tab).
   - `A @` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `AAAA @` → `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
   - `CNAME www` → `<user>.github.io.`
5. Once the DNS check in Settings → Pages is green, tick **Enforce HTTPS**. `.app` is HSTS-preloaded, so the site is unreachable in browsers until the certificate is issued (usually within the hour). Don't change DNS while waiting.

## After it's live

- App Store Connect → App Information: Privacy Policy URL `https://wallypaper.app/privacy`; Support URL `https://wallypaper.app/support`; Marketing URL `https://wallypaper.app`; Terms/EULA `https://wallypaper.app/terms`.
- In the app, point `AppConstants.privacyPolicyURL` at `https://wallypaper.app/privacy` (and optionally `termsOfUseURL` at `/terms`) in the next build.
- Turn the Google Sites privacy page into an embed of `https://wallypaper.app/privacy`. The page hides its own header and footer when it detects it is inside an iframe, so only the policy shows.
