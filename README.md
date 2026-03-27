# Aplazo — Programa Embajadores 🚀

A self-served onboarding web app for Aplazo's Ambassador Program, built entirely on **Google Apps Script (GAS)**. No external hosting required.

## What it does

Replaces a manual, unscalable ambassador registration process with a fully automated 5-step flow:

1. **Personal data** — name, email, phone, city, referral source
2. **Document upload** — INE/IFE, bank statement, proof of address
3. **Data review** — ambassador verifies everything before signing
4. **Contract acceptance** — digital signature on a pre-filled Comisión Mercantil contract (pdf-lib)
5. **Success screen** — contract PDF download + confirmation email

## Tech stack

| Layer | Tool |
|---|---|
| Hosting & backend | Google Apps Script Web App |
| Storage | Google Drive (per-ambassador subfolder) |
| Database | Google Sheets (`Registros` tab) |
| Notifications | Gmail via `MailApp` |
| PDF filling | pdf-lib (client-side, browser) |
| Frontend | Vanilla JS + Bootstrap Icons + Plus Jakarta Sans |

## Live URL

```
https://script.google.com/macros/s/AKfycby6TD1f3mdhm7uFIOlL3JJ5EBrkLtnSd0gi1lkihfNhF4MxXa9gZMi698SVNSuFGYronQ/exec
```

## Script Properties (required)

Set these in **Project Settings → Script Properties** before deploying:

| Key | Description |
|---|---|
| `ANTHROPIC_API_KEY` | Anthropic API key (reserved for future AI features) |
| `ADMIN_EMAIL` | Email that receives new registration alerts |
| `DRIVE_FOLDER_ID` | Google Drive folder ID where ambassador files are stored |
| `SHEET_ID` | Google Sheets ID for the `Registros` log |

## Deploy instructions

1. Open [script.google.com](https://script.google.com)
2. Paste `Code.gs` and `PDF.gs` into the editor
3. Set Script Properties (see above)
4. Click **Deploy → New deployment → Web App**
5. Set: Execute as **Me** · Who has access: **Anyone**
6. Copy the live URL

## Key files

```
Code.gs   — Backend: form submission, Drive upload, Sheets logging, email dispatch
PDF.gs    — Base64-encoded blank contract PDF (pre-signed by Alexander Wieland Castillo)
```

## Data collected per ambassador

| Field | Description |
|---|---|
| `nom` / `ap` | First and last name |
| `nin` | Full name as it appears on INE |
| `rfc` | RFC fiscal |
| `email` / `tel` | Contact info |
| `ciudad` | City / branch |
| `banco` / `cuenta` / `clabe` | Banking details for commission payouts |
| `titular` | Account holder name |
| `dom` | Full address |
| `fuente` | How they heard about the program |

## Commission structure

- **$250 MXN** per activated user
- Paid next business day after activation
- Contract valid for **2 months** from signing date
- Ambassador must issue a *factura* to receive payment

## Context

Part of Aplazo's **Ambassadors Program** initiative — scaling offline customer acquisition by enabling anyone to register as an ambassador, receive a personal QR code, and earn commissions for every new Aplazo user they activate.

Replaces a 5-step manual process (KAM → merchant Excel → manual contracts → DocuSign → Drive folder) with a fully self-served flow.

---

*Built and maintained by the Aplazo Growth / Central Ops team.*
