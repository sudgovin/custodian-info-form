# ChartRequest — Custodian Information Form

A standalone, GitHub Pages-ready webpage that allows healthcare custodians listed in the **ChartRequest Public Provider Directory** to submit key profile information:

1. **Record types** they can provide (Medical, Billing, Diagnostic Images)
2. **Turnaround time** for record retrieval
3. **Primary specialty** of the facility

## Live Demo

Once deployed, accessible at:
`https://<your-org>.github.io/custodian-info-form/`

---

## Deploying to GitHub Pages

### Option A — Via GitHub UI (quickest)

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Source**, select **Deploy from a branch**.
4. Choose `main` branch, `/ (root)` folder, and click **Save**.
5. Your form will be live within ~60 seconds.

### Option B — Via GitHub Actions (automated)

A workflow file is included at `.github/workflows/pages.yml` for automatic deployment on every push to `main`.

---

## Connecting a Form Backend

The form currently shows a success state via JavaScript after simulated submission.
To wire it to a real backend, replace the `setTimeout(showSuccess, 1200)` block in
`index.html` with one of the following:

### Formspree (zero-backend, free tier)
```html
<form id="custodianForm" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```
Remove the `novalidate` attribute and the `submit` event listener's `e.preventDefault()` to let Formspree handle the POST.

### Custom REST API
```js
fetch('https://api.yourbackend.com/custodian-profile', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(payload),
}).then(() => showSuccess());
```

---

## Form Questions

| # | Question | Input Type | Options |
|---|----------|------------|---------|
| 1 | Record types available | Multi-select checkboxes | Medical Records, Billing Records, Diagnostic Images |
| 2 | Turnaround time | Single-select radio | Instant / 2–3 Days / 3–5 Days / 5+ Days |
| 3 | Primary specialty | Dropdown (grouped) | 50+ specialties across 10 categories |

---

## Tech Stack

- Pure HTML5 / CSS3 / Vanilla JS — no frameworks, no build step
- Zero external dependencies
- Mobile-responsive
- Accessible (ARIA labels, keyboard-navigable)

---

&copy; ChartRequest. All rights reserved.
