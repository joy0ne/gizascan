# 2 — GizaScan: Legal & Justice Audit
I don't want you to describe everything you are processing or the reports, and the final result, the updated file.

You will receive the complete code of **"GizaScan"**: a standalone 3D app (single HTML, ~130 KB, ~1200 lines). 7 scientific overlays, 16 SCI entries with 100+ claims across 35 depth levels, freemium paywall (R$9.99/$1.99/€1.99), Capacitor IAP.

---

## MISSION: Find and fix ALL legal risks before publishing on Google Play Store and Apple App Store.

## CHECK EVERY ITEM

### Copyright & Intellectual Property
- External image URLs (Wikimedia, B-CDN, any hotlinked image): remove or replace with original
- Three.js (MIT license): verify compliance
- Google Fonts: verify license terms
- Any reproduced text from books, papers, or articles: rewrite in original words
- Any trademarked names used in ways that imply endorsement

### Content Claims — Fact vs Theory
- Every factual claim: is it sourced? Is the source real and verifiable?
- Every speculative claim: is it framed as "theory," "hypothesis," "some researchers suggest," or similar?
- Claims presented as FACT that are actually disputed: reframe with hedging language
- Medical/health claims (DMT, pineal gland, frequencies, healing): add "research suggests" or "theoretical"
- Claims about living people or active institutions: verify neutrality, remove accusations
- Words to find and fix: "forgery," "BARRED," "forced," "cover-up," "hidden," "suppressed," "conspiracy," "halted by government," "trees planted to hide"
- Replace accusatory language with neutral alternatives: "controversy," "denied further permits," "paused pending review," "access restricted"

### Store Policy Compliance
- Google Play "Misleading Claims" policy: no medical claims presented as fact
- Apple App Store "Apps should not include false information": all claims sourced or hedged
- COPPA/GDPR/LGPD: verify zero data collection
- Content rating: verify appropriate for "Everyone" / "4+"
- In-app purchase: verify non-consumable, clear pricing, no dark patterns

### Privacy & Data
- Zero data collection verified (no fetch, XHR, WebSocket, localStorage, cookies, geolocation)
- Privacy policy accuracy: does it match actual app behavior?

### Disclaimer
- Meta tag with educational disclaimer present?
- Content framed as "educational exploration featuring published research and alternative theories"?
- "Critical thinking encouraged" messaging present?

### Attribution
- All scientific sources cited in each SCI entry (src field)?
- No plagiarized text from Wikipedia, books, or papers?

## PROCESS
1. Read the entire file line by line
2. Flag every legal risk with severity (CRITICAL/HIGH/MEDIUM/LOW)
3. Fix each risk immediately
4. Verify fix doesn't break functionality
5. Repeat until zero risks remain

**Fix everything and apply the improvements.**
