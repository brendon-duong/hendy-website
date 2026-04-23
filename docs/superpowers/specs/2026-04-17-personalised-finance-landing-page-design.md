# Personalised Finance — Landing Page Design Spec

**Date:** 2026-04-17  
**Client:** Personalised Finance  
**Broker:** Hendy Limbri

---

## Overview

A single-page marketing site for a mortgage brokerage. Goal: convert visitors into leads via a contact form and direct contact details. No framework — pure HTML/CSS/JS delivered as a single `index.html` file.

---

## Design Direction

- **Style:** Bold & Premium — full-screen gradient navy hero, green accents
- **Palette:** Navy `#0d2d5e` (primary), Green `#7ab648` (accent), White `#ffffff`, Light grey `#f7f9fc`
- **Font:** Inter (Google Fonts) — modern, clean, highly legible
- **Logo:** `0TXBWXM4SJ7L5Q8KDHMAEUAKN.png.webp` — placed in nav and footer

---

## CTA Strategy

Both direct contact AND a lead capture form:
- Lead form: Name, Phone, Loan Type (select), Submit button
- Direct contact: phone number + email displayed prominently alongside the form

---

## Page Sections (in order)

### 1. Navigation
- Logo (left), "Call Us" CTA button (right)
- Sticky on scroll, collapses gracefully on mobile

### 2. Hero
- Full-screen gradient navy background
- Bold headline + sub-headline
- Two-column layout: left = headline + contact block, right = lead capture form
- Form fields: Full Name, Phone Number, Loan Type (dropdown), Message (optional), Submit

### 3. Services
- Section heading + subtitle
- 5 service cards in a responsive grid: First Home Buyer, Refinancing, Investment Loans, Commercial Finance, Self-Employed Loans
- Each card: icon, title, short description

### 4. How It Works
- 3-step process: "Tell Us Your Goals" → "We Search the Market" → "You Get the Keys"
- Numbered steps with icons, horizontal on desktop / vertical on mobile

### 5. About Hendy
- Two-column: placeholder photo (left) + bio text (right)
- Placeholder bio with credentials, years of experience, accreditation badges
- Clear comment in HTML marking all placeholder text

### 6. Testimonials
- 3 review cards with star ratings, quote, client first name + suburb
- Placeholder testimonials clearly marked

### 7. FAQ
- 5–6 common mortgage questions, collapsible accordion
- Questions: eligibility, process length, broker vs bank, costs, refinancing

### 8. Footer
- Logo, tagline, contact details (phone, email, address — all placeholder)
- Copyright line

---

## Technical Notes

- Single `index.html` file — no build tools, no dependencies beyond Google Fonts
- Logo referenced as relative path `./0TXBWXM4SJ7L5Q8KDHMAEUAKN.png.webp`
- All placeholder content (phone, email, address, Hendy's bio, testimonials) wrapped in `<!-- PLACEHOLDER: ... -->` HTML comments
- Mobile-responsive via CSS Grid and Flexbox
- Smooth scroll, FAQ accordion via vanilla JS (no jQuery)
- Form is non-functional (no backend) but styled and validated client-side
