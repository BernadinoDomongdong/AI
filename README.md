# BERN-AI 🚌

*A free, multilingual AI chatbot with a jeepney soul.*

Every Filipino jeepney wears its route on a hand-lettered signboard and
carries its own little universe of chrome, LEDs, and personality. **BERN-AI**
borrows that spirit for a chat app: an amber destination-sign clock that
tracks your real local time, a sky that shifts from day to night as the
hours actually pass, a Matrix-style code-rain running underneath it all —
and a genuinely free AI chatbot riding along inside.

Pick your language, pick a model, and start talking. The whole interface —
not just the AI's replies — follows you there.

## Highlights

- 🪧 **Jeepney signboard identity** — chrome-lettering title, an amber LED
  clock that just *tells the time* (no gimmicks), and a single switch for
  day/night mode, the same way you'd flip a light switch.
- 🌗 **A sky that's actually alive** — the theme follows your device's real
  local time, upgrading to your precise timezone if you share your location.
- 🌐 **Speaks your language, fully** — switch languages and every label,
  button, and error message re-renders, not just what the AI says.
- 💸 **Always free to run** — only ever talks to OpenRouter models that are
  currently priced at zero, double-checked live before every request.
- 🌧️ **Ambient hacker aesthetic** — falling code-rain, a scattered star
  field, and a subtle grain texture, all respecting reduced-motion settings.
- 🛡️ **Built to survive the internet** — rate limiting, timeouts, and a
  locked-down set of security headers keep a small free app from folding
  under a bad day of traffic.

## Built with

Plain HTML/CSS/JS on the frontend (no framework), two small serverless
functions on Vercel for the backend, and OpenRouter's free-tier models for
the AI itself. No database, no build step — just static files and two
functions.

## Getting your own copy running

1. Push this repo to GitHub.
2. Grab a free API key from [OpenRouter](https://openrouter.ai/keys).
3. Import the repo into Vercel — framework preset **"Other."**
4. In Vercel's Environment Variables, add:
   - `OPENROUTER_API_KEY` — required.
   - `ALLOWED_ORIGIN`, `FORM_TOKEN_SECRET`, `GLOBAL_RATE_LIMIT_PER_MINUTE` —
     optional, tighten security and abuse protection for production.
5. Deploy. Your key stays inside Vercel's environment store — it never
   touches the repo, the browser, or view-source.

**Testing locally:**
```bash
npm install -g vercel
cp .env.example .env   # paste your key in here
vercel dev
```

## Adding a language

Add one entry to `LOCALES` in `js/i18n.js` (a label, a prompt name, and a
translated copy of every string) — the language picker and the AI's
replies both pick it up automatically. Mark it as `RTL_LOCALES` if it reads
right-to-left.

## Security, in brief

The API key never reaches the browser. Requests are rate-limited per
visitor *and* across all visitors combined, timed out if OpenRouter hangs,
and checked against a short-lived anti-automation token. Security headers
lock down scripts, framing, and permissions site-wide. This is a real,
layered defense for a small app — not a claim that it's immune to a
determined attacker. Volumetric attacks and sophisticated bot traffic are
better handled by Vercel's own platform protections (Attack Mode, BotID)
than by application code.

## Credits

Created by **Bernadino T. Domongdong** — [bernadinodomongdong.github.io/mysite](https://bernadinodomongdong.github.io/mysite/)

Licensed under MIT.
