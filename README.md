# wallypaper.app

Marketing and support site for [WallyPaper](https://apps.apple.com/us/app/wallypaper-custom-wallpaper/id6805213479), the iPhone app that turns a photo of your kid or pet into a wallpaper. Static HTML with no build step and no third-party requests, served by GitHub Pages at **https://wallypaper.app**.

## About WallyPaper

WallyPaper makes simple digital portraits of the people and pets you love, and puts them on your Lock Screen. Pick a photo, and the app finds your kid or pet, lifts them off the background and frames them with their face in view, clear of the clock and controls. Drop them on a backdrop, add their name, and save. Four steps, about a minute, entirely on your iPhone.

**Making a wallpaper**

- **Subject lift.** On-device subject and face detection lifts a person or pet out of any photo. If nothing is detected, *Use Whole Photo* keeps the picture as it is.
- **Bring in the whole crew.** Add another photo to put two kids, or a kid and the dog, on the same wallpaper, then choose who is in front.
- **Backgrounds.** Curated solids, gradients and mesh gradients, plus holiday themes that appear as each occasion nears (Halloween, Diwali, Thanksgiving, Hanukkah, Christmas, Lunar New Year, Valentine's and more; Birthday, Rainbow and Space stay all year).
- **Names.** Rounded, Classic, Serif and Mono designs in three weights, with Plain, Shadow, Outline and Pill styles. Any size, any position.
- **Stickers and touches.** Hundreds of emoji stickers, a soft shadow or sticker border for the subject, and drag, pinch and flip to place everything.
- **Built for the Lock Screen.** A Lock Screen preview shows the clock and controls while you design, and every wallpaper is rendered at the iPhone's exact screen resolution. iOS adds the depth effect when it fits.
- **Library and widget.** Every wallpaper is saved automatically so it can be reopened, tweaked, duplicated or remade, with undo and redo. The *Latest Wallpapers* Home Screen widget rotates through your newest creations.

**Privacy.** Photos are processed by Apple's Vision framework on the device and never leave the phone. There is no account, no ads, no analytics, no tracking and no third-party SDKs; the app itself makes no network connections. Purchases go through the App Store, so the developer never sees your name, email or payment details.

**Free and Pro.** WallyPaper is free to download and use; free wallpapers carry a small WallyPaper mark near the bottom. WallyPaper Pro removes it and unlocks every background, custom colors, every font design and name style, and the Pro templates and art styles. It is available as a monthly or yearly subscription or a one-time lifetime purchase.

Requires an iPhone running iOS 18 or later. Made by CaLa Studios LLC. Questions go to support@calastudios.app.

## Pages

| Path | File | Purpose |
| --- | --- | --- |
| `/` | `index.html` | Landing page |
| `/support` | `support.html` | FAQ and contact, linked from the App Store listing |
| `/privacy` | `privacy.html` | Privacy policy, linked from the App Store listing and from inside the app |
| `/404` | `404.html` | Not-found page |

GitHub Pages serves `support.html` at `/support` (and `/support.html`), so the extensionless URLs above work as-is. Terms of Use link to Apple's [Standard EULA](https://www.apple.com/legal/internet-services/itunes/dev/stdeula/); there is no terms page here.

`privacy.html` adds an `embedded` class to `<html>` when it detects it is inside an iframe and hides its header and footer, so the policy alone can be embedded elsewhere.

## Layout

- `assets/css/site.css` – the one stylesheet, shared by every page. Dark only, to match the app.
- `assets/js/site.js` – mobile nav, scroll reveal, footer year. No dependencies.
- `assets/img/` – app icon sizes, App Store screenshots (WebP), the two framed mockups from the app, the wordmark SVG, Apple's App Store badge, the doodle background from the launch screen, and `og-image.jpg` for link previews.
- `assets/fonts/` – Source Sans 3, Pacifico and Bebas Neue, subset to Latin and self-hosted as WOFF2 (SIL OFL, licenses alongside).
- `sitemap.xml`, `robots.txt`, `site.webmanifest` – the usual metadata.
- `CNAME` – `wallypaper.app`, so the custom domain survives redeploys.
- `.nojekyll` – tells Pages to publish the files as they are.

## Updating

Edit the HTML, commit to `main`, push. Pages redeploys in about a minute.

Feature copy on the landing page follows the App Store description for the build that is live in the store, not what is in development. When a new version ships, update the Features, Backgrounds and Names sections to match it.

To regenerate images: screenshots come from the App Store listing (1284×2778 PNG) resized to 720 wide and encoded with `cwebp -q 82`; the `feat-*.webp` images are crops of those screenshots (and of an editor screenshot for the Lock Screen tile).
