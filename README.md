# 📧 WhatsApp to Email Migration Tool
### Insurance Market — Document Collection System

A lightweight, zero-backend web tool that helps advisors migrate client document collection from WhatsApp to email — cleanly, compliantly, and instantly.

---

## 🧩 The Problem

Advisors were collecting client documents (Emirates ID, passports, visas, salary certificates) informally over WhatsApp. This created:
- No audit trail
- Data protection concerns
- Documents lost in chat threads
- No CC visibility for compliance team

---

## ✅ The Solution

A single hosted HTML page that gives every advisor a **personalised, shareable link or QR code** — when a client taps it, their email app opens pre-filled and ready to send. No app downloads, no logins, no backend.

---

## 🔄 How It Works

### Step 1 — Share base URL with advisors
```
https://symphonious-salamander-e63cff.netlify.app
```

### Step 2 — Advisor fills in the form
- Their **email address**
- **CBD ID / Quote Number** *(optional — appears in email subject)*
- **List of documents** required from the client

### Step 3 — Advisor clicks Generate
They receive:
- ✅ A **unique shareable link**
- ✅ A **QR code** (downloadable)
- ✅ A **Share on WhatsApp** button with pre-written message

### Step 4 — Client taps the link
Client sees a clean page with a **"Send Your Documents"** button. One tap opens their email app with everything pre-filled:

| Field | Value |
|-------|-------|
| **To** | Advisor's email |
| **CC** | jake.romasanta@insurancemarket.ae, tausif.memon@insurancemarket.ae |
| **Subject** | CBD ID (if entered) or "WhatsApp to Email Migration" |
| **Body** | Thank you message + numbered document checklist |

Client just attaches documents and hits **Send**.

---

## 📧 Email Body (Client Sends)

```
Hello,

Thank you for moving your communication with us to email — this helps 
us serve you better and keep your documents safe and on record.

To proceed with your policy, please reply to this email with the 
following documents attached:

1. Emirates ID (front & back)
2. Passport copy
3. Visa copy

Once we receive your documents, our team will review and get back 
to you promptly.

Should you have any questions, simply reply to this email.

Warm regards,
advisor@insurancemarket.ae
```

---

## 🏗️ Technical Architecture

```
Single HTML file — no backend, no database, no server
│
├── Advisor View        → Form to enter email, CBD ID, doc list
├── URL Encoding        → All data encoded in the shareable URL params
├── Client View         → Decoded from URL, shows Send button
└── mailto: link        → Pre-fills To, CC, Subject, Body in email app
```

### URL Structure
```
https://[domain]/?e=[base64 email]&n=[advisor name]&c=[CBD ID]&d=[docs joined by ||]
```

### Fixed CC Addresses (hardcoded)
```
jake.romasanta@insurancemarket.ae
tausif.memon@insurancemarket.ae
```

---

## 📁 File Structure

```
WHATSAPPMIGRATOR/
└── index.html          # Entire application — one file
```

---

## 🚀 Deployment

Hosted on **Netlify** via GitHub auto-deploy.

### To deploy changes:
```bash
git add .
git commit -m "your change description"
git push
```
Netlify auto-deploys in ~30 seconds. No manual steps needed.

### To set up from scratch:
```bash
git clone https://github.com/thisisanoopshekhar89-jpg/whatsappmigrator.git
cd whatsappmigrator
# Open index.html in browser to run locally
# Or push to Netlify/GitHub Pages to host
```

---

## ⚙️ Configuration

To change the fixed CC addresses, open `index.html` and edit line:
```javascript
var CC = 'jake.romasanta@insurancemarket.ae,tausif.memon@insurancemarket.ae';
```

To change the email body template, search for `var body =` in the script section.

---

## 🖥️ Compatibility

| Platform | Works? | Notes |
|----------|--------|-------|
| iPhone (Safari) | ✅ | Opens Mail app |
| Android (Chrome) | ✅ | Opens Gmail/Mail app |
| PC — Gmail users | ✅ | Opens Gmail in browser |
| PC — Outlook users | ✅ | Opens Outlook if set as default |
| WhatsApp Web link | ✅ | Client taps, browser opens |
| QR Code scan | ✅ | Opens page, then email |

---

## 👥 Team

| Role | Person |
|------|--------|
| Product Owner | Anoop Shekhar |
| CC (Compliance) | Jake Romasanta |
| CC (Compliance) | Tausif Memon |

---

## 📌 Live URL

```
https://symphonious-salamander-e63cff.netlify.app
```

---

## 🗺️ Roadmap / Future Improvements

- [ ] Custom domain (e.g. `docs.insurancemarket.ae`)
- [ ] Advisor name field alongside email
- [ ] Pre-set document templates per insurance type (Motor, Medical, Life)
- [ ] WhatsApp Business API integration
- [ ] Admin dashboard to track links generated
- [ ] Analytics — how many clients opened the link

---

*Built to solve a real problem. Simple by design.*
