### Codename: Kaarawan (WORKING TITLE ONLY)

**Critical note:** "Kaarawan" is a temporary working title leftover from the Philippines phase. It will be replaced with a proper Brazilian Portuguese name before any public release or marketing. Do **not** use any Tagalog words, phrases, or references anywhere in code, UI, strings, or comments. All text must be in Brazilian Portuguese from day one.

## What This Is

A mobile-first mutual-network birthday wishlist app for Brazil.  
Users set their birthday, build a circle of mutuals (friends/family), maintain a personal gift wishlist, and receive gentle reminders. Mutuals click affiliate links to buy gifts directly from stores. On the birthday the receiver sees only one pooled, anonymous message (“Seus mutuals te surpreenderam com X presentes!”).  

No money ever moves through the app. Core value is the social graph + reminders + surprise mechanic.

## Strategic Decisions

- **Pivot reason**: Switched to Brazil after Involve Asia blocked signup and proved unusable for international publishers. Brazil was the cleanest remaining high-fit market with strong birthday/gift culture and easy remote affiliate access.
- **Regulatory choice**: Dropped the original “set-and-forget automatic Pix transfers” idea completely. Any automation would require a BCB Payment Institution license — not viable for an indie solo project. We stay 100% on external affiliate links only.
- **Monetization**: Pure affiliate commissions, no subscriptions, no ads, no fees. Keeps the app free and frictionless.
- **Build approach**: We are shipping **both** a Progressive Web App (PWA) **and** a native Android app (not one or the other). PWA for instant testing and homescreen install; native Android for push reliability and store presence.
- **Launch focus**: Zero-budget viral growth via WhatsApp shares. Mutual network is the moat.

## Stack Requisites (what the features force us to have)

The app requires:
- Real-time database + social graph (mutual invites, accept/reject, who-can-see-what) → forces a backend that supports fast reads/writes and relationships.
- Push notifications for birthday reminders (7/3/1 day + day-of) → forces Firebase Cloud Messaging or equivalent push service with reliable delivery.
- User auth (phone/email + simple profile) → forces secure auth that works in Brazil (phone verification is non-negotiable for spam control).
- Deep-linking and URL rewriting for affiliate partners (Lomadee + Awin) → forces a system that can take any store URL, convert it to a tracked affiliate link on the fly, and store it cleanly.
- Homescreen install + offline-first feel on Android → forces PWA capabilities (manifest, service worker).
- Native Android build for better notification permissions and Play Store distribution → forces a cross-platform or native mobile framework that can target Android directly while sharing most code with the PWA.
- All strings externalized in pt-BR JSON → forces easy localization from the start.

Anything that adds payment SDKs, bank APIs, or scheduled transfers is explicitly forbidden — it would create regulatory risk.

## Main Features (MVP)

1. Signup + birthday profile
2. Mutual network (invite via WhatsApp share link, accept requests, simple graph)
3. Wishlist (add items by pasting any Brazilian store URL → auto-convert to affiliate link where possible)
4. Mutual view (“Comprar este presente” buttons)
5. Self-reported “I’m buying this” toggle for pooled counter
6. Birthday day screen with single anonymous surprise total
7. Automatic push reminders

## Monetization

100% affiliate commissions from Lomadee and Awin (Magalu, Americanas, Casas Bahia, Dafiti, Renner, etc.).  
Users buy directly on the store. App never touches money.

## Additional Must-Haves

- Strong privacy: mutuals never see each other’s exact commitments.
- Anti-spam: phone verification on signup.
- Viral hook: “Convide 5 mutuals” prompt on first use.
- Track every affiliate click with publisher ID.

Start with auth + mutual invites + basic wishlist. That’s the engine. Everything else layers on top.
