# Personalised Finance Landing Page — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a single-file, mobile-responsive landing page for mortgage broker Hendy Limbri at Personalised Finance.

**Architecture:** One self-contained `index.html` with embedded `<style>` and `<script>` tags. No build tools, no frameworks, no dependencies beyond Google Fonts (loaded via CDN `<link>`). Logo referenced as `./0TXBWXM4SJ7L5Q8KDHMAEUAKN.png.webp`.

**Tech Stack:** HTML5, CSS3 (Grid + Flexbox), Vanilla JS (accordion + smooth scroll + form validation)

---

## File Map

| File | Action | Purpose |
|------|--------|---------|
| `index.html` | Create | Complete landing page — all HTML, CSS, JS in one file |

---

### Task 1: HTML Skeleton + Navigation

**Files:**
- Create: `index.html`

- [ ] **Step 1: Create `index.html` with document head and sticky nav**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Personalised Finance | Mortgage Broker</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet" />
  <style>
    /* === RESET & BASE === */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body { font-family: 'Inter', sans-serif; color: #1a1a2e; background: #fff; }
    img { max-width: 100%; display: block; }
    a { text-decoration: none; color: inherit; }

    /* === TOKENS === */
    :root {
      --navy: #0d2d5e;
      --navy-dark: #071a3a;
      --navy-light: #1a4a8a;
      --green: #7ab648;
      --green-dark: #5f9232;
      --white: #ffffff;
      --grey-light: #f7f9fc;
      --grey-mid: #e8edf5;
      --grey-text: #6b7280;
      --radius: 10px;
      --shadow: 0 4px 24px rgba(13,45,94,0.10);
      --shadow-lg: 0 8px 40px rgba(13,45,94,0.18);
      --transition: 0.22s ease;
    }

    /* === LAYOUT === */
    .container { max-width: 1140px; margin: 0 auto; padding: 0 24px; }
    section { padding: 96px 0; }

    /* === BUTTONS === */
    .btn-primary {
      display: inline-block;
      background: var(--green);
      color: var(--white);
      padding: 14px 28px;
      border-radius: var(--radius);
      font-weight: 700;
      font-size: 1rem;
      border: none;
      cursor: pointer;
      transition: background var(--transition), transform var(--transition);
    }
    .btn-primary:hover { background: var(--green-dark); transform: translateY(-1px); }
    .btn-outline {
      display: inline-block;
      border: 2px solid var(--white);
      color: var(--white);
      padding: 12px 26px;
      border-radius: var(--radius);
      font-weight: 600;
      font-size: 1rem;
      cursor: pointer;
      transition: background var(--transition), color var(--transition);
      background: transparent;
    }
    .btn-outline:hover { background: var(--white); color: var(--navy); }

    /* === SECTION LABELS === */
    .section-label {
      display: inline-block;
      background: rgba(122,182,72,0.12);
      color: var(--green-dark);
      font-size: 0.75rem;
      font-weight: 700;
      letter-spacing: 1.5px;
      text-transform: uppercase;
      padding: 6px 14px;
      border-radius: 100px;
      margin-bottom: 16px;
    }
    .section-title {
      font-size: clamp(1.8rem, 3vw, 2.6rem);
      font-weight: 800;
      color: var(--navy);
      line-height: 1.2;
      margin-bottom: 16px;
    }
    .section-subtitle {
      font-size: 1.1rem;
      color: var(--grey-text);
      max-width: 560px;
      line-height: 1.7;
    }
    .section-head { margin-bottom: 56px; }
    .section-head.center { text-align: center; }
    .section-head.center .section-subtitle { margin: 0 auto; }

    /* === NAV === */
    .nav {
      position: sticky;
      top: 0;
      z-index: 100;
      background: var(--white);
      border-bottom: 1px solid var(--grey-mid);
      box-shadow: 0 2px 12px rgba(13,45,94,0.06);
    }
    .nav__inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      height: 72px;
    }
    .nav__logo { height: 44px; }
    .nav__cta { }

    @media (max-width: 600px) {
      .nav__logo { height: 36px; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <header class="nav">
    <div class="container nav__inner">
      <a href="#"><img class="nav__logo" src="./0TXBWXM4SJ7L5Q8KDHMAEUAKN.png.webp" alt="Personalised Finance" /></a>
      <a href="#contact" class="btn-primary nav__cta">Get a Free Quote</a>
    </div>
  </header>

</body>
</html>
```

- [ ] **Step 2: Open `index.html` in a browser and verify** — logo appears in sticky nav, green CTA button shows, page is white background.

---

### Task 2: Hero Section

**Files:**
- Modify: `index.html` — add hero HTML after `</header>`, add hero CSS inside `<style>`

- [ ] **Step 1: Add hero CSS inside `<style>` before `</style>`**

```css
/* === HERO === */
.hero {
  background: linear-gradient(135deg, var(--navy-dark) 0%, var(--navy) 50%, var(--navy-light) 100%);
  padding: 100px 0 80px;
  position: relative;
  overflow: hidden;
}
.hero::before {
  content: '';
  position: absolute;
  top: -40%;
  right: -10%;
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(122,182,72,0.12) 0%, transparent 70%);
  pointer-events: none;
}
.hero__grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: center;
}
.hero__eyebrow {
  display: inline-block;
  background: rgba(122,182,72,0.18);
  color: var(--green);
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  padding: 6px 14px;
  border-radius: 100px;
  margin-bottom: 24px;
}
.hero__title {
  font-size: clamp(2.2rem, 4vw, 3.4rem);
  font-weight: 800;
  color: var(--white);
  line-height: 1.15;
  margin-bottom: 20px;
}
.hero__title span { color: var(--green); }
.hero__sub {
  font-size: 1.1rem;
  color: rgba(255,255,255,0.78);
  line-height: 1.75;
  margin-bottom: 36px;
  max-width: 460px;
}
.hero__contact { display: flex; flex-direction: column; gap: 12px; }
.hero__contact-item {
  display: flex;
  align-items: center;
  gap: 12px;
  color: rgba(255,255,255,0.88);
  font-size: 1rem;
}
.hero__contact-item svg { flex-shrink: 0; }
.hero__contact-item a { color: var(--white); font-weight: 600; transition: color var(--transition); }
.hero__contact-item a:hover { color: var(--green); }

/* Form card */
.hero__form-card {
  background: var(--white);
  border-radius: 16px;
  padding: 40px 36px;
  box-shadow: var(--shadow-lg);
}
.hero__form-title {
  font-size: 1.4rem;
  font-weight: 800;
  color: var(--navy);
  margin-bottom: 6px;
}
.hero__form-sub {
  font-size: 0.9rem;
  color: var(--grey-text);
  margin-bottom: 28px;
}
.form-group { margin-bottom: 16px; }
.form-group label {
  display: block;
  font-size: 0.82rem;
  font-weight: 600;
  color: var(--navy);
  margin-bottom: 6px;
}
.form-group input,
.form-group select,
.form-group textarea {
  width: 100%;
  padding: 12px 14px;
  border: 1.5px solid var(--grey-mid);
  border-radius: 8px;
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  color: #1a1a2e;
  background: var(--white);
  transition: border-color var(--transition);
  outline: none;
}
.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus { border-color: var(--navy); }
.form-group textarea { resize: vertical; min-height: 80px; }
.form-submit { width: 100%; padding: 15px; font-size: 1rem; font-weight: 700; border-radius: 8px; margin-top: 4px; }
.form-privacy {
  text-align: center;
  font-size: 0.75rem;
  color: var(--grey-text);
  margin-top: 10px;
}

@media (max-width: 860px) {
  .hero__grid { grid-template-columns: 1fr; gap: 48px; }
  .hero__form-card { padding: 32px 24px; }
}
```

- [ ] **Step 2: Add hero HTML after `</header>` and before `</body>`**

```html
  <!-- HERO -->
  <section class="hero" id="contact">
    <div class="container">
      <div class="hero__grid">

        <!-- Left: copy + contact -->
        <div class="hero__left">
          <div class="hero__eyebrow">Sydney's Trusted Mortgage Broker</div>
          <h1 class="hero__title">Your home loan,<br><span>done right.</span></h1>
          <p class="hero__sub">
            <!-- PLACEHOLDER: Update this tagline to reflect Hendy's value proposition -->
            Independent advice. No bank bias. We search hundreds of loan options to find the one that fits your life — not just your credit score.
          </p>
          <div class="hero__contact">
            <div class="hero__contact-item">
              <!-- Phone icon -->
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.8a19.79 19.79 0 01-3.07-8.63A2 2 0 012 2h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L6.91 9.91a16 16 0 006.18 6.18l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/></svg>
              <!-- PLACEHOLDER: Replace with Hendy's real phone number -->
              <a href="tel:+610400000000">0400 000 000</a>
            </div>
            <div class="hero__contact-item">
              <!-- Email icon -->
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
              <!-- PLACEHOLDER: Replace with Hendy's real email -->
              <a href="mailto:hendy@personalisedfinance.com.au">hendy@personalisedfinance.com.au</a>
            </div>
          </div>
        </div>

        <!-- Right: lead form -->
        <div class="hero__right">
          <div class="hero__form-card">
            <div class="hero__form-title">Get Your Free Consultation</div>
            <div class="hero__form-sub">We'll call you back within 1 business day.</div>
            <form id="lead-form" novalidate>
              <div class="form-group">
                <label for="name">Full Name</label>
                <input type="text" id="name" name="name" placeholder="Jane Smith" required />
              </div>
              <div class="form-group">
                <label for="phone">Phone Number</label>
                <input type="tel" id="phone" name="phone" placeholder="0400 000 000" required />
              </div>
              <div class="form-group">
                <label for="loan-type">I'm looking for...</label>
                <select id="loan-type" name="loan-type" required>
                  <option value="" disabled selected>Select loan type</option>
                  <option>First Home Buyer Loan</option>
                  <option>Refinancing</option>
                  <option>Investment Loan</option>
                  <option>Commercial Finance</option>
                  <option>Self-Employed Loan</option>
                  <option>Other</option>
                </select>
              </div>
              <div class="form-group">
                <label for="message">Anything else? (optional)</label>
                <textarea id="message" name="message" placeholder="Tell us a bit about your situation..."></textarea>
              </div>
              <button type="submit" class="btn-primary form-submit">Send My Enquiry</button>
              <p class="form-privacy">🔒 Your details are safe with us. No spam, ever.</p>
            </form>
          </div>
        </div>

      </div>
    </div>
  </section>
```

- [ ] **Step 3: Verify in browser** — gradient navy hero, white form card on right, left copy + green contact icons, responsive on mobile.

---

### Task 3: Services Section

**Files:**
- Modify: `index.html` — add services HTML + CSS

- [ ] **Step 1: Add services CSS inside `<style>` before `</style>`**

```css
/* === SERVICES === */
.services { background: var(--grey-light); }
.services__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 24px;
}
.service-card {
  background: var(--white);
  border-radius: var(--radius);
  padding: 32px 24px;
  box-shadow: var(--shadow);
  transition: transform var(--transition), box-shadow var(--transition);
  border-top: 4px solid transparent;
}
.service-card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-lg);
  border-top-color: var(--green);
}
.service-card__icon {
  width: 52px;
  height: 52px;
  background: rgba(122,182,72,0.12);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
}
.service-card__title {
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--navy);
  margin-bottom: 10px;
}
.service-card__desc {
  font-size: 0.88rem;
  color: var(--grey-text);
  line-height: 1.65;
}
```

- [ ] **Step 2: Add services HTML after the hero `</section>`**

```html
  <!-- SERVICES -->
  <section class="services" id="services">
    <div class="container">
      <div class="section-head center">
        <div class="section-label">What We Do</div>
        <h2 class="section-title">Finance solutions for every situation</h2>
        <p class="section-subtitle">Whether you're buying your first home or growing a property portfolio, we've got you covered.</p>
      </div>
      <div class="services__grid">

        <div class="service-card">
          <div class="service-card__icon">
            <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9,22 9,12 15,12 15,22"/></svg>
          </div>
          <div class="service-card__title">First Home Buyer</div>
          <p class="service-card__desc">Get into your first home with confidence. We guide you through grants, guarantees, and lender options.</p>
        </div>

        <div class="service-card">
          <div class="service-card__icon">
            <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="23 4 23 10 17 10"/><path d="M20.49 15a9 9 0 11-2.12-9.36L23 10"/></svg>
          </div>
          <div class="service-card__title">Refinancing</div>
          <p class="service-card__desc">Already own property? We'll find you a better rate and structure that saves you thousands over your loan term.</p>
        </div>

        <div class="service-card">
          <div class="service-card__icon">
            <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
          </div>
          <div class="service-card__title">Investment Loans</div>
          <p class="service-card__desc">Build your portfolio with smart financing. We structure investment loans for maximum flexibility and tax efficiency.</p>
        </div>

        <div class="service-card">
          <div class="service-card__icon">
            <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="7" width="20" height="14" rx="2" ry="2"/><path d="M16 7V5a2 2 0 00-2-2h-4a2 2 0 00-2 2v2"/></svg>
          </div>
          <div class="service-card__title">Commercial Finance</div>
          <p class="service-card__desc">From commercial property to business equipment, we source competitive commercial lending solutions.</p>
        </div>

        <div class="service-card">
          <div class="service-card__icon">
            <svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
          </div>
          <div class="service-card__title">Self-Employed</div>
          <p class="service-card__desc">Self-employed or business owner? We know which lenders work with non-standard income and get you approved.</p>
        </div>

      </div>
    </div>
  </section>
```

- [ ] **Step 3: Verify in browser** — 5 cards in responsive grid on light grey background, green hover border appears on mouseover.

---

### Task 4: How It Works Section

**Files:**
- Modify: `index.html` — add how-it-works HTML + CSS

- [ ] **Step 1: Add how-it-works CSS inside `<style>` before `</style>`**

```css
/* === HOW IT WORKS === */
.how { background: var(--white); }
.how__steps {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 40px;
  position: relative;
}
.how__steps::before {
  content: '';
  position: absolute;
  top: 36px;
  left: calc(16.66% + 24px);
  right: calc(16.66% + 24px);
  height: 2px;
  background: var(--grey-mid);
}
.how__step { text-align: center; position: relative; }
.how__step-num {
  width: 72px;
  height: 72px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--navy), var(--navy-light));
  color: var(--white);
  font-size: 1.5rem;
  font-weight: 800;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 24px;
  position: relative;
  z-index: 1;
  box-shadow: 0 4px 16px rgba(13,45,94,0.25);
}
.how__step-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--navy);
  margin-bottom: 10px;
}
.how__step-desc {
  font-size: 0.9rem;
  color: var(--grey-text);
  line-height: 1.65;
}
@media (max-width: 700px) {
  .how__steps { grid-template-columns: 1fr; gap: 32px; }
  .how__steps::before { display: none; }
}
```

- [ ] **Step 2: Add how-it-works HTML after the services `</section>`**

```html
  <!-- HOW IT WORKS -->
  <section class="how" id="how-it-works">
    <div class="container">
      <div class="section-head center">
        <div class="section-label">The Process</div>
        <h2 class="section-title">Simple. Fast. Stress-free.</h2>
        <p class="section-subtitle">Getting your home loan sorted doesn't have to be complicated. Here's how we make it easy.</p>
      </div>
      <div class="how__steps">
        <div class="how__step">
          <div class="how__step-num">1</div>
          <div class="how__step-title">Tell Us Your Goals</div>
          <p class="how__step-desc">Book a free consultation with Hendy. We listen to your situation, goals, and timeline — no jargon, no pressure.</p>
        </div>
        <div class="how__step">
          <div class="how__step-num">2</div>
          <div class="how__step-title">We Search the Market</div>
          <p class="how__step-desc">We compare hundreds of loan products from major banks and specialist lenders to find your best match.</p>
        </div>
        <div class="how__step">
          <div class="how__step-num">3</div>
          <div class="how__step-title">You Get the Keys</div>
          <p class="how__step-desc">We handle the paperwork and liaise with the lender so settlement goes smoothly. You just turn the key.</p>
        </div>
      </div>
    </div>
  </section>
```

- [ ] **Step 3: Verify in browser** — 3 numbered circles connected by a horizontal line on desktop, stacks vertically on mobile.

---

### Task 5: About Hendy Section

**Files:**
- Modify: `index.html` — add about HTML + CSS

- [ ] **Step 1: Add about CSS inside `<style>` before `</style>`**

```css
/* === ABOUT === */
.about { background: var(--grey-light); }
.about__grid {
  display: grid;
  grid-template-columns: 1fr 1.3fr;
  gap: 72px;
  align-items: center;
}
.about__photo-wrap { position: relative; }
.about__photo {
  width: 100%;
  aspect-ratio: 4/5;
  object-fit: cover;
  border-radius: 16px;
  background: var(--grey-mid);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}
.about__photo-placeholder {
  width: 100%;
  aspect-ratio: 4/5;
  background: linear-gradient(135deg, var(--navy) 0%, var(--navy-light) 100%);
  border-radius: 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: rgba(255,255,255,0.5);
  font-size: 0.85rem;
  gap: 12px;
}
.about__badge {
  position: absolute;
  bottom: -20px;
  right: -20px;
  background: var(--white);
  border-radius: 12px;
  padding: 16px 20px;
  box-shadow: var(--shadow-lg);
  display: flex;
  align-items: center;
  gap: 12px;
}
.about__badge-num {
  font-size: 1.8rem;
  font-weight: 800;
  color: var(--navy);
  line-height: 1;
}
.about__badge-label { font-size: 0.75rem; color: var(--grey-text); font-weight: 500; }
.about__name {
  font-size: 1.8rem;
  font-weight: 800;
  color: var(--navy);
  margin-bottom: 6px;
}
.about__role {
  font-size: 1rem;
  color: var(--green-dark);
  font-weight: 600;
  margin-bottom: 24px;
}
.about__bio {
  font-size: 1rem;
  color: var(--grey-text);
  line-height: 1.8;
  margin-bottom: 32px;
}
.about__creds {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 32px;
}
.about__cred {
  background: var(--white);
  border: 1.5px solid var(--grey-mid);
  border-radius: 100px;
  padding: 6px 16px;
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--navy);
}
@media (max-width: 800px) {
  .about__grid { grid-template-columns: 1fr; gap: 48px; }
  .about__badge { bottom: 16px; right: 16px; }
}
```

- [ ] **Step 2: Add about HTML after the how-it-works `</section>`**

```html
  <!-- ABOUT -->
  <section class="about" id="about">
    <div class="container">
      <div class="about__grid">

        <div class="about__photo-wrap">
          <!-- PLACEHOLDER: Replace this div with an <img> tag pointing to Hendy's photo -->
          <div class="about__photo-placeholder">
            <svg width="64" height="64" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
            <span>Hendy's photo goes here</span>
          </div>
          <div class="about__badge">
            <!-- PLACEHOLDER: Update years of experience -->
            <div class="about__badge-num">10+</div>
            <div class="about__badge-label">Years<br>Experience</div>
          </div>
        </div>

        <div class="about__content">
          <div class="section-label">Meet Your Broker</div>
          <!-- PLACEHOLDER: Update name if needed -->
          <div class="about__name">Hendy Limbri</div>
          <div class="about__role">Senior Mortgage Broker · Personalised Finance</div>
          <!-- PLACEHOLDER: Replace with Hendy's real bio -->
          <p class="about__bio">
            With over a decade of experience in the Australian mortgage market, Hendy Limbri has helped hundreds of families, investors, and business owners achieve their property goals. Hendy's approach is straightforward: understand your situation deeply, then find the loan structure that genuinely works for you — not just the one that's easiest to approve.
          </p>
          <p class="about__bio">
            As an independent broker, Hendy is not tied to any bank or lender, which means every recommendation is based purely on what's best for you.
          </p>
          <div class="about__creds">
            <!-- PLACEHOLDER: Update accreditations as applicable -->
            <span class="about__cred">✓ MFAA Accredited</span>
            <span class="about__cred">✓ Australian Credit Licence</span>
            <span class="about__cred">✓ 40+ Lender Panel</span>
            <span class="about__cred">✓ Free Service</span>
          </div>
          <a href="#contact" class="btn-primary">Book a Free Chat with Hendy</a>
        </div>

      </div>
    </div>
  </section>
```

- [ ] **Step 3: Verify in browser** — navy placeholder photo left, bio + credentials right, floating badge visible, responsive on mobile.

---

### Task 6: Testimonials Section

**Files:**
- Modify: `index.html` — add testimonials HTML + CSS

- [ ] **Step 1: Add testimonials CSS inside `<style>` before `</style>`**

```css
/* === TESTIMONIALS === */
.testimonials { background: var(--navy); }
.testimonials .section-title { color: var(--white); }
.testimonials .section-label {
  background: rgba(122,182,72,0.2);
  color: var(--green);
}
.testimonials .section-subtitle { color: rgba(255,255,255,0.65); }
.testimonials__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px;
}
.testimonial-card {
  background: rgba(255,255,255,0.07);
  border: 1px solid rgba(255,255,255,0.12);
  border-radius: var(--radius);
  padding: 32px 28px;
  transition: background var(--transition);
}
.testimonial-card:hover { background: rgba(255,255,255,0.11); }
.testimonial-card__stars {
  color: var(--green);
  font-size: 1.1rem;
  letter-spacing: 2px;
  margin-bottom: 16px;
}
.testimonial-card__quote {
  font-size: 0.95rem;
  color: rgba(255,255,255,0.85);
  line-height: 1.75;
  margin-bottom: 24px;
  font-style: italic;
}
.testimonial-card__author {
  font-weight: 700;
  color: var(--white);
  font-size: 0.9rem;
}
.testimonial-card__location {
  font-size: 0.8rem;
  color: rgba(255,255,255,0.5);
  margin-top: 2px;
}
```

- [ ] **Step 2: Add testimonials HTML after the about `</section>`**

```html
  <!-- TESTIMONIALS -->
  <section class="testimonials" id="testimonials">
    <div class="container">
      <div class="section-head center">
        <div class="section-label">Client Stories</div>
        <h2 class="section-title">Real results for real people</h2>
        <p class="section-subtitle">Don't take our word for it — here's what our clients say.</p>
      </div>
      <div class="testimonials__grid">

        <!-- PLACEHOLDER: Replace with real client testimonials -->
        <div class="testimonial-card">
          <div class="testimonial-card__stars">★★★★★</div>
          <p class="testimonial-card__quote">"Hendy made the whole process so easy. We were first home buyers and had no idea where to start — he walked us through everything and got us a rate we didn't think was possible."</p>
          <div class="testimonial-card__author">Sarah & Tom K.</div>
          <div class="testimonial-card__location">First Home Buyers · Parramatta, NSW</div>
        </div>

        <div class="testimonial-card">
          <div class="testimonial-card__stars">★★★★★</div>
          <p class="testimonial-card__quote">"I'd been with my bank for 15 years and thought I was getting a good deal. Hendy refinanced me and saved over $400 a month. Wish I'd called sooner."</p>
          <div class="testimonial-card__author">Michael R.</div>
          <div class="testimonial-card__location">Refinancing · Chatswood, NSW</div>
        </div>

        <div class="testimonial-card">
          <div class="testimonial-card__stars">★★★★★</div>
          <p class="testimonial-card__quote">"As a self-employed tradie I thought getting a loan would be a nightmare. Hendy knew exactly which lenders to approach and we settled within 6 weeks."</p>
          <div class="testimonial-card__author">Dave M.</div>
          <div class="testimonial-card__location">Self-Employed Loan · Penrith, NSW</div>
        </div>

      </div>
    </div>
  </section>
```

- [ ] **Step 3: Verify in browser** — dark navy background, 3 frosted glass cards, green stars, italic quotes.

---

### Task 7: FAQ Section

**Files:**
- Modify: `index.html` — add FAQ HTML + CSS + JS accordion

- [ ] **Step 1: Add FAQ CSS inside `<style>` before `</style>`**

```css
/* === FAQ === */
.faq { background: var(--white); }
.faq__list { max-width: 760px; margin: 0 auto; }
.faq__item {
  border-bottom: 1.5px solid var(--grey-mid);
}
.faq__question {
  width: 100%;
  background: none;
  border: none;
  padding: 22px 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  cursor: pointer;
  text-align: left;
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  font-weight: 600;
  color: var(--navy);
  transition: color var(--transition);
}
.faq__question:hover { color: var(--green-dark); }
.faq__icon {
  flex-shrink: 0;
  width: 28px;
  height: 28px;
  border-radius: 50%;
  background: var(--grey-light);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background var(--transition), transform var(--transition);
}
.faq__item.open .faq__icon { background: var(--green); transform: rotate(45deg); }
.faq__item.open .faq__icon svg { stroke: var(--white); }
.faq__answer {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.35s ease;
}
.faq__answer-inner {
  padding-bottom: 20px;
  font-size: 0.95rem;
  color: var(--grey-text);
  line-height: 1.75;
}
```

- [ ] **Step 2: Add FAQ HTML after the testimonials `</section>`**

```html
  <!-- FAQ -->
  <section class="faq" id="faq">
    <div class="container">
      <div class="section-head center">
        <div class="section-label">FAQ</div>
        <h2 class="section-title">Common questions</h2>
        <p class="section-subtitle">Everything you need to know before getting started.</p>
      </div>
      <div class="faq__list">

        <div class="faq__item">
          <button class="faq__question">
            Do I need a deposit to use a mortgage broker?
            <span class="faq__icon"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#6b7280" stroke-width="2.5" stroke-linecap="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></span>
          </button>
          <div class="faq__answer"><div class="faq__answer-inner">Most lenders require a minimum 5–10% deposit, though some first home buyer schemes allow lower deposits. We'll assess your situation and let you know exactly where you stand — no guesswork.</div></div>
        </div>

        <div class="faq__item">
          <button class="faq__question">
            How much does it cost to use a mortgage broker?
            <span class="faq__icon"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#6b7280" stroke-width="2.5" stroke-linecap="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></span>
          </button>
          <div class="faq__answer"><div class="faq__answer-inner">Our service is completely free to you. We're paid a commission by the lender when your loan settles — and by law, we're required to act in your best interest regardless.</div></div>
        </div>

        <div class="faq__item">
          <button class="faq__question">
            How long does the loan approval process take?
            <span class="faq__icon"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#6b7280" stroke-width="2.5" stroke-linecap="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></span>
          </button>
          <div class="faq__answer"><div class="faq__answer-inner">Conditional approval can happen within 24–48 hours. Full formal approval typically takes 3–5 business days once all documents are submitted. We'll keep you updated at every step.</div></div>
        </div>

        <div class="faq__item">
          <button class="faq__question">
            Why use a broker instead of going directly to a bank?
            <span class="faq__icon"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#6b7280" stroke-width="2.5" stroke-linecap="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></span>
          </button>
          <div class="faq__answer"><div class="faq__answer-inner">A bank only offers their own products. We compare 40+ lenders including banks, credit unions, and specialist lenders — so you get the best rate and structure for your specific situation, not just what's easiest for one bank to sell.</div></div>
        </div>

        <div class="faq__item">
          <button class="faq__question">
            Can you help if I've been declined by a bank?
            <span class="faq__icon"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#6b7280" stroke-width="2.5" stroke-linecap="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></span>
          </button>
          <div class="faq__answer"><div class="faq__answer-inner">Yes — a decline from one lender doesn't mean you won't qualify elsewhere. We know which lenders are flexible on credit history, employment type, and deposit size. Get in touch and we'll assess your options.</div></div>
        </div>

        <div class="faq__item">
          <button class="faq__question">
            Is refinancing worth it?
            <span class="faq__icon"><svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#6b7280" stroke-width="2.5" stroke-linecap="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></span>
          </button>
          <div class="faq__answer"><div class="faq__answer-inner">Often yes — especially if your current loan is more than 2 years old. Interest rates and lending policies change frequently. We run a free loan health check to see if switching makes financial sense before recommending anything.</div></div>
        </div>

      </div>
    </div>
  </section>
```

- [ ] **Step 3: Add FAQ accordion JS inside `<script>` before `</body>`**

```html
  <script>
    // FAQ accordion
    document.querySelectorAll('.faq__question').forEach(btn => {
      btn.addEventListener('click', () => {
        const item = btn.closest('.faq__item');
        const answer = item.querySelector('.faq__answer');
        const isOpen = item.classList.contains('open');

        // close all
        document.querySelectorAll('.faq__item.open').forEach(open => {
          open.classList.remove('open');
          open.querySelector('.faq__answer').style.maxHeight = null;
        });

        if (!isOpen) {
          item.classList.add('open');
          answer.style.maxHeight = answer.scrollHeight + 'px';
        }
      });
    });
  </script>
```

- [ ] **Step 4: Verify in browser** — clicking a question expands the answer smoothly, clicking again closes it, clicking another closes the previous.

---

### Task 8: Footer + Form Validation

**Files:**
- Modify: `index.html` — add footer HTML + CSS, extend JS

- [ ] **Step 1: Add footer CSS inside `<style>` before `</style>`**

```css
/* === FOOTER === */
.footer {
  background: var(--navy-dark);
  padding: 56px 0 32px;
  color: rgba(255,255,255,0.65);
}
.footer__grid {
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr;
  gap: 48px;
  margin-bottom: 48px;
}
.footer__logo { height: 40px; margin-bottom: 16px; filter: brightness(0) invert(1); opacity: 0.9; }
.footer__tagline { font-size: 0.9rem; line-height: 1.7; max-width: 260px; }
.footer__heading {
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1.2px;
  color: var(--white);
  margin-bottom: 16px;
}
.footer__links { list-style: none; display: flex; flex-direction: column; gap: 10px; }
.footer__links a { font-size: 0.9rem; color: rgba(255,255,255,0.65); transition: color var(--transition); }
.footer__links a:hover { color: var(--green); }
.footer__contact-item { display: flex; gap: 10px; align-items: flex-start; margin-bottom: 12px; font-size: 0.9rem; }
.footer__contact-item svg { flex-shrink: 0; margin-top: 2px; }
.footer__bottom {
  border-top: 1px solid rgba(255,255,255,0.1);
  padding-top: 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 12px;
  font-size: 0.8rem;
}
.footer__bottom a { color: rgba(255,255,255,0.5); transition: color var(--transition); }
.footer__bottom a:hover { color: var(--white); }
@media (max-width: 700px) {
  .footer__grid { grid-template-columns: 1fr; gap: 32px; }
  .footer__bottom { flex-direction: column; align-items: flex-start; }
}

/* === FORM SUCCESS === */
.form-success {
  display: none;
  text-align: center;
  padding: 32px 0;
}
.form-success__icon {
  width: 64px;
  height: 64px;
  background: rgba(122,182,72,0.15);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 16px;
}
.form-success__title { font-size: 1.2rem; font-weight: 700; color: var(--navy); margin-bottom: 8px; }
.form-success__sub { font-size: 0.9rem; color: var(--grey-text); }

/* === INPUT ERROR STATE === */
.form-group input.error,
.form-group select.error { border-color: #e53e3e; }
.form-error-msg { font-size: 0.75rem; color: #e53e3e; margin-top: 4px; display: none; }
.form-error-msg.show { display: block; }
```

- [ ] **Step 2: Add footer HTML after the FAQ `</section>` and before `<script>`**

```html
  <!-- FOOTER -->
  <footer class="footer">
    <div class="container">
      <div class="footer__grid">

        <div>
          <img class="footer__logo" src="./0TXBWXM4SJ7L5Q8KDHMAEUAKN.png.webp" alt="Personalised Finance" />
          <!-- PLACEHOLDER: Update tagline -->
          <p class="footer__tagline">Independent mortgage broking — personalised for you. Not the bank.</p>
        </div>

        <div>
          <div class="footer__heading">Quick Links</div>
          <ul class="footer__links">
            <li><a href="#services">Services</a></li>
            <li><a href="#how-it-works">How It Works</a></li>
            <li><a href="#about">About Hendy</a></li>
            <li><a href="#testimonials">Testimonials</a></li>
            <li><a href="#faq">FAQ</a></li>
            <li><a href="#contact">Get a Quote</a></li>
          </ul>
        </div>

        <div>
          <div class="footer__heading">Contact</div>
          <!-- PLACEHOLDER: Replace all contact details below -->
          <div class="footer__contact-item">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.8a19.79 19.79 0 01-3.07-8.63A2 2 0 012 2h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L6.91 9.91a16 16 0 006.18 6.18l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/></svg>
            <a href="tel:+610400000000" style="color:rgba(255,255,255,0.65)">0400 000 000</a>
          </div>
          <div class="footer__contact-item">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
            <a href="mailto:hendy@personalisedfinance.com.au" style="color:rgba(255,255,255,0.65)">hendy@personalisedfinance.com.au</a>
          </div>
          <div class="footer__contact-item">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2" stroke-linecap="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
            <span>Sydney, NSW, Australia</span>
          </div>
        </div>

      </div>

      <div class="footer__bottom">
        <span>© 2026 Personalised Finance. All rights reserved.</span>
        <!-- PLACEHOLDER: Add real privacy policy / disclaimer links if needed -->
        <span>Credit Representative · <a href="#">Privacy Policy</a> · <a href="#">Disclaimer</a></span>
      </div>
    </div>
  </footer>
```

- [ ] **Step 3: Add form success state HTML inside `.hero__form-card` after `</form>`**

```html
          <div class="form-success" id="form-success">
            <div class="form-success__icon">
              <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#7ab648" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>
            </div>
            <div class="form-success__title">Thanks! We'll be in touch soon.</div>
            <p class="form-success__sub">Hendy will call you back within 1 business day.</p>
          </div>
```

- [ ] **Step 4: Add form validation to the existing `<script>` block (append before `</script>`)**

```js
    // Form validation + submission
    const form = document.getElementById('lead-form');
    form.addEventListener('submit', e => {
      e.preventDefault();
      let valid = true;

      ['name', 'phone', 'loan-type'].forEach(id => {
        const field = document.getElementById(id);
        const err = field.parentElement.querySelector('.form-error-msg');
        if (!field.value.trim()) {
          field.classList.add('error');
          if (err) err.classList.add('show');
          valid = false;
        } else {
          field.classList.remove('error');
          if (err) err.classList.remove('show');
        }
      });

      if (valid) {
        form.style.display = 'none';
        document.getElementById('form-success').style.display = 'block';
      }
    });

    // Remove error state on input
    document.querySelectorAll('.form-group input, .form-group select').forEach(el => {
      el.addEventListener('input', () => el.classList.remove('error'));
    });
```

- [ ] **Step 5: Add error message spans inside the 3 required form-groups (name, phone, loan-type) — add after each input/select**

For `#name` group, after `<input>`:
```html
                <span class="form-error-msg">Please enter your full name.</span>
```

For `#phone` group, after `<input>`:
```html
                <span class="form-error-msg">Please enter your phone number.</span>
```

For `#loan-type` group, after `<select>`:
```html
                <span class="form-error-msg">Please select a loan type.</span>
```

- [ ] **Step 6: Verify in browser** — submitting empty form shows red borders + error messages; submitting valid form shows green success state. Footer renders correctly with 3 columns, collapses to 1 on mobile.

---

## Final Verification Checklist

- [ ] Logo displays in nav and footer
- [ ] Nav scrolls sticky on all sections
- [ ] Hero form and contact details both visible on desktop; stacked on mobile
- [ ] All 5 service cards render and hover effect works
- [ ] How It Works steps connected by line on desktop, stacked on mobile
- [ ] About section shows placeholder photo badge correctly
- [ ] Testimonials show on navy background
- [ ] FAQ accordion opens/closes smoothly
- [ ] Footer 3 columns on desktop, 1 on mobile
- [ ] Form validation catches empty fields
- [ ] Form success state shows on valid submit
- [ ] All placeholder comments are present and clearly marked
- [ ] Page renders well on 375px (iPhone SE) and 1440px (desktop)
