# Pulse Landing Page — AI Build Prompt

Source: `landing-page.html` (main all-in-one page). P2P and B2B variants live in `index.html` and `b2b.html`.

How to use: paste the **Master prompt** into v0, Lovable, Bolt, Claude, ChatGPT, Cursor, Framer AI, or Figma Make. If the tool has a character limit, use the **Short prompt**. Then use the **Follow-up prompts** to refine.

---

## Master prompt

```
ROLE
You are a senior product designer and front-end engineer who builds high-converting SaaS landing pages for Arabic-speaking markets. Build ONE responsive landing page that is excellent on mobile (390px, down to 360px) AND desktop (1440px) for "Aumet Pulse".

PRODUCT
Aumet Pulse ("Pulse") is an all-in-one pharmacy operating system by Aumet, for independent pharmacies and small chains in Saudi Arabia, Jordan, and Egypt. It combines:
- Offline-first POS (cashier keeps scanning barcodes and issuing invoices with no internet, then auto-syncs)
- Inventory with expiry alerts (90 / 60 / 30 days) and smart re-ordering
- Buying from licensed distributors through Aumet Marketplace (B2B) — compare live offers, bonuses, one-tap ordering
- Pharmacy-to-pharmacy exchange (P2P) — sell slow-moving / near-expiry stock to nearby pharmacies, settled through the wallet
- Smart pharmacy wallet with real cashback on distributor orders that can cover the annual subscription
- 5-minute data migration from Excel
It is NOT a patient app, NOT an online drugstore, NOT a hospital EMR.

TWO SCREENS, ONE PHARMACY
- Pulse is the desktop workspace: it runs in the browser on the pharmacy's computer (app.aumetpulse.com) — counter, stock, reports, wallet.
- The Aumet Marketplace app is the mobile companion on the pharmacist's phone — order from distributors, catch P2P offers, get alerts, track deliveries, confirm receipt.
- Both share one account, one stock picture, and one wallet, so whatever happens on one shows up on the other.
The page must make this pairing obvious — never present Pulse itself as a phone app, and never present the Aumet app as a separate product with its own login or wallet.

AUDIENCE
Pharmacy owners and pharmacists, busy behind the counter, usually opening the link from WhatsApp on their phone. They are skeptical of new software and afraid of switching (losing data, stopping sales). The page must remove that fear fast.

CONVERSION GOALS (in order)
1. Primary: enter mobile number to start free — country code picker: 🇸🇦 +966 السعودية, 🇯🇴 +962 الأردن, 🇪🇬 +20 مصر.
2. Secondary: book a 15-minute live demo (form at the bottom of the page).
3. Tertiary: chat on WhatsApp.
Repeat the primary CTA after every major section. No credit card required.

LANGUAGE & DIRECTION
- Default: Modern Standard Arabic, RTL (<html lang="ar" dir="rtl">).
- Language switcher in the header with flags: العربية / English / Français. Switching updates all copy and flips direction (EN/FR = LTR). Keep copy in one i18n object, not hard-coded per element.
- Use CSS logical properties (margin-inline-start, padding-inline-end, text-align: start). Icons with direction (arrows, chevrons) must mirror in RTL.
- Phone numbers, prices, and percentages render LTR inside Arabic text (wrap in dir="ltr" / <bdi>).

VISUAL STYLE
Feel: match the current live Pulse website — clean, modern, clinical-trustworthy SaaS on white and cool slate surfaces, with teal as the single brand color. Not generic purple SaaS, not a red-cross medical look.
Colors (use exactly these tokens):
- Primary teal #04BCA6, primary dark #006B5E (text/buttons on light, focus rings), primary hover #008E7D, mint glow #48DCC5
- Teal tints #F0FDFA / #CCFBF1 for badges, chips, and highlighted cards
- Ink #0F172A (headings), body #334155, muted #64748B, borders #E2E8F0, soft lines #F1F5F9
- Backgrounds: white #FFFFFF, alternating sections #F8FAFC, cool blue surfaces #EEF4FF / #F8F9FF
- Dark sections and footer: #0F1C2C (slate-900 feel) with white/slate-400 text
- Secondary accent blue #005AC2 (links, info states) — use sparingly
- Status: success #047857 on #ECFDF5, warning/expiry #B45309 on #FFFBEB, error #BA1A1A on #FFDAD6
Typography: Tajawal (Arabic, 400–900, line-height 1.7+), Plus Jakarta Sans (Latin, numbers, English headlines). Icons: Material Symbols Outlined.
Shapes: cards ~22px radius (rounded-2xl/3xl), pill buttons, shadow "0 1px 2px rgba(15,23,42,.04), 0 20px 40px -16px rgba(4,188,166,.22)", glassy sticky header (white/85 + backdrop-blur, bottom border slate-100), content max-width ~1180px.
Signature motif: a thin, elegant ECG / heartbeat line ("نبض" = pulse) animating gently in the hero and as section dividers. Respect prefers-reduced-motion.
Imagery: stylized product UI mocks built in HTML/CSS (dashboard, receipts, wallet cards) — not stock photos of doctors or hospitals.

PAGE STRUCTURE & COPY (use this Arabic copy; write natural EN/FR equivalents)

1) HEADER (sticky)
- Logo: "Pulse" wordmark + rounded-square teal (#04BCA6) icon with a tiny ECG line.
- Nav: الرئيسية · نقل البيانات · المميزات · التطبيق · الكاش باك · الأسئلة الشائعة (smooth-scroll anchors)
- Language dropdown · تسجيل الدخول (text) · احجز موعدًا للتجربة (outline) · ابدأ مجاناً (filled, primary)
- Mobile: logo + language + "ابدأ مجاناً" + menu icon opening a drawer from the start side.

2) HERO
- Badge: ✨ منصة متكاملة للصيدليات
- H1: صيدليتك كلها.. في مكان واحد
- Sub: كل ما تحتاجه لإدارة صيدليتك في مكان واحد: نقطة البيع، إدارة المخزون، والشراء المباشر من الموزعين المعتمدين عبر سوق أومِت، مع كاش باك حقيقي يساعدك على تغطية تكلفة اشتراكك.
- Phone capture card: title "ابدأ برقم جوالك", helper "أدخل الرقم فقط. نحدد بعدها الخطوة التالية تلقائياً.", country picker + phone input + button "ابدأ ←". Validate per country, show inline errors and a success state.
- Link under it: هل تفضّل مشاهدة المنصة أولاً؟ — عرض حي خلال 15 دقيقة → احجز موعدًا للتجربة
- Trust chips: بدون بطاقة بنكية · يعمل دون إنترنت (Offline-First) · تكامل مباشر مع سوق أومِت
- Visual (end side on desktop, below the form on mobile): live dashboard mock "لوحة Pulse المباشرة — فرع الشفاء" with a "مباشر" pulse dot and "مزامنة تلقائية • متصل الآن":
  cards for مبيعات اليوم (with ↑ growth), صافي الربح, الكاش باك المتاح; a smart re-order card "أعد الطلب بذكاء قبل نفاد المخزون — أوجمنتين 1 جم (15 عبوة) — المستودع الأفضل: المتحدة للتوزيع — خصم 24% — طلب بضغطة زر"; and a chip "بيانات صيدليتك بأمان، حتى بدون إنترنت".

3) DATA MIGRATION (fear remover)
- Eyebrow: بدون أدنى تعقيد أو تعطيل للبيع
- H2: انقل بيانات صيدليتك ومخزونك في 5 دقائق
- Sub: استورد ملف Excel لنقل آلاف الأصناف والأسعار وتواريخ الصلاحية آلياً دون توقف عمليات الصرف والبيع.
- Visual: file card "pulse_data_loader.xlsx" with validation checks (validated, SKUs auto-mapped, 0 errors) + a video player thumbnail "فيديو توضيحي: نقل البيانات في 5 دقائق" (01:45, play button).
- 3 numbered steps: ١ سحب وإفلات الملف · ٢ مطابقة آلية للباركود والأسعار · ٣ بدء البيع فوراً (short description each).
- CTAs: طلب نقل بيانات مجاني (primary) · تحدث مع خبير التهيئة (WhatsApp, secondary)

4) FEATURES — BENTO GRID
- Eyebrow: المميزات الأساسية — H2: أربع ركائز صُممت خصيصاً لراحة الصيدلي
- Sub: حلول تكنولوجية حديثة تقضي على التوقفات، وتقلص الهدر، وتزيد الربحية.
- Four cards, each with number, icon, title, 2-line text, and a mini UI mock:
  01 كاشير سريع يعمل دون أي انقطاع — receipt mock with status "الإنترنت مفصول • الكاشير يعمل"
  02 تنبيهات ذكية لتواريخ الصلاحية — list with 90/60/30-day badges, one item flagged "أولوية — صرفه أولاً"
  03 شراء الأدوية من الموزعين المعتمدين — two distributor offers compared (price + bonus like 10+3), best one highlighted with "طلب بضغطة زر"
  04 شبكة التبادل المباشر بين الصيدليات (P2P) — match card "مطابقة مع صيدلية الشفاء 2", settled via wallet, cold-chain delivery
- IMPORTANT: card 03 (distributors / B2B marketplace) and card 04 (pharmacy-to-pharmacy P2P) are different products — never merge or mix their wording.
- CTA: ابدأ تجربتك المجانية

5) PULSE + AUMET APP — "صيدليتك على المكتب، وسوقك في جيبك" (anchor: التطبيق)
- Eyebrow: منظومة واحدة مترابطة
- H2: صيدليتك على المكتب، وسوقك في جيبك
- Sub: Pulse يدير الكاونتر والمخزون من شاشة الصيدلية، وتطبيق أومِت يرافقك على الجوال لتطلب وتتابع وتستلم — بحساب واحد ومحفظة واحدة، وكل شيء متزامن لحظياً.
- Visual (the hero moment of this section): a desktop browser frame (address bar "app.aumetpulse.com") and a phone frame ("تطبيق أومِت") side by side, joined by the thin ECG heartbeat line that pulses from one device to the other to show live sync. Example story across both screens:
  a) Pulse (desktop) flags low stock / near-expiry on an item →
  b) the phone gets a notification and the pharmacist orders from a distributor, or picks up a nearby pharmacy's P2P offer →
  c) delivery is tracked on the phone and receipt is confirmed with one tap →
  d) stock updates in Pulse automatically and cashback lands in the shared wallet.
- 3–4 benefit tiles under the devices:
  حساب واحد للجهازين — no second login, no double entry
  مخزونك يتحدّث وحده — what you receive on the phone appears on the shelf in Pulse
  تنبيهات أينما كنت — low stock, expiry, new offers, and order status on your phone
  محفظة واحدة — payments, P2P earnings, and cashback in one balance on both screens
- CTAs: ابدأ مجاناً على Pulse (primary) · حمّل تطبيق أومِت (secondary). App Store / Google Play badges ONLY with real links — otherwise use a placeholder [CONFIRM app store links].
- Mobile layout: stack phone frame first (the visitor is already on a phone), desktop frame scaled below; the story steps become a vertical timeline. Desktop layout: devices side by side, steps beneath.
- Wording: say "شاشة الصيدلية / المتصفح" for Pulse and "الجوال" for the app. Do not call Pulse a mobile app, and do not imply the app replaces the cashier.

6) WALLET & CASHBACK
- Eyebrow: محفظة الصيدلية الذكية — H2: استرداد نقدي حقيقي (Cashback) يغطي تكلفة اشتراك صيدليتك
- Sub: مع كل طلبية أدوية عبر موزعي Pulse، يتراكم كاش باك حقيقي في محفظتك ليُخصم من اشتراكك السنوي أو يُحوّل لحسابك.
- Bullets: كاش باك تراكمي على الطلبيات · إمكانية تغطية الاشتراك السنوي بالكامل
- Visual: wallet card (teal on a light teal tint) with balance "الرصيد المتاح في المحفظة", 3 transaction rows, and "متاح للخصم التلقائي عند تجديد باقتك".

7) FAQ (accordion, one open at a time, keyboard accessible)
- كيف يتم نقل بيانات صيدليتي ومخزوني القديم إلى Pulse؟ → ارفع ملف Excel من برنامجك الحالي، ويتم نقل الأصناف والأسعار خلال 5 دقائق. ويمكن لفريق الدعم إتمام النقل مجاناً دون توقف البيع.
- ماذا يحدث عند انقطاع الاتصال بالإنترنت أثناء ساعات الذروة؟ → الكاشير يستمر في البيع وقراءة الباركود، وبمجرد عودة الاتصال تتم مزامنة كل الفواتير تلقائياً.
- كيف يتم احتساب الاسترداد النقدي (Cashback) وهل هو حقيقي؟ → نعم، يُحتسب من طلبياتك عبر موزعي Pulse ويتراكم في محفظتك ليُخصم من اشتراكك أو يُحوّل لحسابك.
- هل أستطيع متابعة مبيعات الفروع والأرباح من هاتفي المحمول؟ → نعم، تتابع المبيعات والأرباح وتنبيهات المخزون من هاتفك مباشرة.
- هل Pulse تطبيق جوال؟ → Pulse يعمل من متصفح الكمبيوتر في الصيدلية، ويكمّله تطبيق أومِت على الجوال للطلب من الموزعين، وعروض الصيدليات، وتتبّع الشحنات — بنفس الحساب والمحفظة.
- هل أحتاج حساباً منفصلاً لتطبيق أومِت؟ → لا، تسجّل الدخول بنفس حساب صيدليتك، وتظهر طلباتك ومحفظتك على الجهازين. [CONFIRM]

8) BOOK A DEMO (final conversion)
- Badge: تجربة مجانية بالكامل — H2: احجز موعدًا للتجربة وابدأ مجاناً
- Sub: 15 دقيقة نوضح لك كيف يسرّع Pulse مبيعاتك. بدون التزام وبدون بطاقة بنكية.
- WhatsApp button: تواصل فوراً عبر واتساب
- Form: اسم الصيدلية · اسم الصيدلي / المسؤول · رقم الهاتف أو الواتساب · الدولة والمدينة (select: السعودية — الرياض / السعودية — جدة / الأردن — عمّان / مصر — القاهرة / مصر — الإسكندرية / دولة أخرى) · عدد الفروع (صيدلية واحدة / 2–4 فروع / 5 فروع فأكثر)
- Submit: تأكيد حجز الموعد → show a friendly success state.

9) FOOTER
Logo + "منصة متكاملة للصيدليات", anchor links, دعم الصيادلة (WhatsApp), "حمّل تطبيق أومِت" (store badges only with real links), © Aumet Inc., شروط الخدمة · سياسة الخصوصية · معايير أمان البيانات.

MOBILE REQUIREMENTS (most visitors are on phones — design mobile first)
- Order in hero: badge → H1 → sub → phone form → trust chips → simplified dashboard mock (2–3 cards, scaled, never cropped).
- Sticky bottom CTA bar once the hero scrolls out: "ابدأ مجاناً" + WhatsApp icon button; hide it when the demo form is on screen; add bottom padding so it never covers the footer.
- Tap targets ≥ 44px; inputs font-size ≥ 16px (no iOS zoom); phone input type="tel" inputmode="numeric" autocomplete="tel".
- Bento grid → 1 column; steps → vertical timeline; no horizontal overflow at 360px.
- H1 around 32–36px on mobile, 56–64px on desktop. Section padding ~48px mobile, ~96px desktop.

DESKTOP REQUIREMENTS
- Centered container max-width ~1240px, two-column hero (copy on start side, mock on end side).
- Bento as an asymmetric 2×2 grid; subtle hover lift on cards; the ECG line animates once on load.

DATA HONESTY
- Numbers inside UI mocks are illustrative only. Show them in local currency for the selected country (ر.س / د.أ / ج.م), not "$".
- Do not invent customer logos, testimonials, certifications, uptime numbers, or headline claims like "85% less waste". If you need a stat, insert a clearly marked placeholder [CONFIRM].

TECH OUTPUT
- If generating code: semantic HTML5 + Tailwind CSS (or React + Tailwind if the tool prefers), Google Fonts (Tajawal, Plus Jakarta Sans), Material Symbols. No backend — forms validate client-side and show success states. Login → /login, start free → /login/create-account.
- Accessibility: one H1, logical heading order, visible focus rings, labels on every input, WCAG AA contrast (white on teal buttons must pass — use #006B5E if needed), aria-expanded on the FAQ and language menu.
- Performance & SEO: Lighthouse mobile ≥ 90, lazy-load the video, Arabic <title> and meta description, Open Graph tags, favicon from the logo.

DELIVER
The complete page, then a short checklist confirming: RTL Arabic default, working EN/FR switch, mobile at 390px and 360px, desktop at 1440px, the desktop + phone section clearly shows Pulse on the pharmacy computer and the Aumet app on the phone as one connected system, all CTAs wired, no invented claims.
```

---

## Short prompt (for tools with a character limit)

```
Build a responsive, mobile-first landing page (390px + 1440px) for "Aumet Pulse", an all-in-one pharmacy operating system for pharmacies in Saudi Arabia, Jordan, and Egypt. Arabic RTL by default with an AR/EN/FR switcher (logical CSS, mirrored icons).
Style: match the live Pulse site — clean clinical SaaS, teal #04BCA6 / primary dark #006B5E / mint #48DCC5, ink #0F172A, muted #64748B, borders #E2E8F0, sections alternating #FFFFFF / #F8FAFC, dark footer #0F1C2C, Tajawal + Plus Jakarta Sans, Material Symbols, ~22px rounded cards, glassy sticky header, thin animated ECG heartbeat motif, HTML/CSS product mocks (no stock photos).
Sections: 1) Header with nav, language, Login, Book demo, Start free. 2) Hero "صيدليتك كلها.. في مكان واحد" with phone-number signup (+966/+962/+20), trust chips (no card, offline-first, Aumet Marketplace) and a live dashboard mock. 3) "انقل بيانات صيدليتك في 5 دقائق" — Excel import, video, 3 steps. 4) Bento of 4 pillars: offline POS, expiry alerts 90/60/30, buy from distributors (B2B), pharmacy-to-pharmacy exchange (P2P) — keep B2B and P2P separate. 5) "صيدليتك على المكتب، وسوقك في جيبك" — Pulse runs in the browser on the pharmacy computer; the Aumet Marketplace app is its phone companion (order, P2P offers, alerts, delivery tracking). Show a desktop frame and a phone frame linked by a pulsing ECG line: one account, one wallet, stock synced live. Never call Pulse a mobile app. 6) Wallet cashback that covers the subscription. 7) FAQ accordion (include "Is Pulse a mobile app?"). 8) Book-a-demo form (pharmacy, pharmacist, phone/WhatsApp, country/city, branches) + WhatsApp button. 9) Footer.
Mobile: sticky bottom "ابدأ مجاناً" + WhatsApp bar, 44px targets, 16px inputs, no overflow at 360px. No fake logos, testimonials, or stats; mock numbers in local currency. Accessible, Lighthouse ≥ 90.
```

---

## Follow-up prompts (paste after the first version)

1. **Mobile polish:** "Review the page at 360px and 390px. Fix any overflow, cramped header, or cropped mock. Make the hero phone form the first thing visible above the fold and add the sticky bottom CTA bar."
2. **RTL check:** "Audit RTL: every margin/padding uses logical properties, arrows and chevrons mirror, numbers and phone numbers render LTR inside Arabic text, and directional visuals (ECG line, progress bars, timelines) flip."
3. **English version:** "Switch to English and make sure the copy reads natively (not literal translation), the layout flips to LTR, and nothing breaks."
4. **Match the live theme:** "Compare every color, font, radius, and shadow against the Pulse tokens in the brief. Replace anything off-brand (purples, pinks, random gradients) with the teal / slate / white system, and keep the dark #0F1C2C footer."
5. **Conversion pass:** "Act as a CRO expert. Tighten headlines to under 8 words, make sure every section ends with a clear CTA, and remove anything that doesn't help a pharmacist decide to start."
6. **Desktop + app sync animation:** "In the 'صيدليتك على المكتب، وسوقك في جيبك' section, animate the story step by step: a low-stock alert on the Pulse desktop frame, a notification on the phone, an order placed, delivery confirmed, and the stock number in Pulse going up. Loop it gently, pause on hover, and show a static version when prefers-reduced-motion is on."
7. **P2P variant (from `index.html`):** "Create a variant whose hero focuses on P2P: H1 'لا تشطب المخزون الراكد. بعه لصيدلية تحتاجه.', a problem section 'أنت تخسر رأس المال مرتين', and 3 steps 'من الرف إلى الكاش'. Keep the same design system."
