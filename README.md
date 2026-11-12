# THE ALPHA GAMER — v0.3

Needs Node.js 22.5 or newer. No `npm install` needed (zero dependencies).

## Start
1. Edit `start.bat` (Windows) or `start.sh` (Mac/Linux): put your Gmail App Password (see below).
2. Run it. Open http://localhost:3000 (players) and http://localhost:3000/admin (admin, private).
3. `npm test` runs all automatic tests.

## Becoming admin (no command, no OTP)
- Your Gmail is listed in ADMIN_EMAILS (default: ghatwindow@gmail.com; add more with commas).
- Create an account in the app with that Gmail. Then open /admin and login with the same Gmail + password. That's it.
- IMPORTANT: create YOUR account with this Gmail FIRST, before you share the website link with anyone.
  (Whoever registers that Gmail first and logs in at /admin becomes admin.) After you are admin, nobody else can register it.
- Forgot the admin password? Use "Forgot password?" in the player app (OTP goes to your Gmail).

## Gmail OTP (forgot password only)
- Google Account > Security > turn on 2-Step Verification > App passwords > create one > 16 characters.
- Put it in SMTP_PASS (start.bat/start.sh). SMTP_USER = the Gmail that sends mails.
- If SMTP is NOT set, OTPs are printed only in the server console (nobody else can see them) — fine for testing, not for real players.
- OTP rules: 6 digits, valid 10 minutes, 5 wrong tries kill it, resend after 60 seconds, 5 per hour per email.

## Admin panel (/admin)
- Deposits: check payment in your bank/Jio app, then Approve (coins added once; UTR can't be reused).
- Withdrawals: pay the UPI yourself, then "Mark paid" with your payout UTR. Reject = refund.
- Tournaments: create/edit, upload banner (JPG/PNG/WEBP up to 20 MB), room ID/pass, publish results, cancel & refund.
- Settings: change UPI ID and QR image any time, category thumbnails (Home tiles), WhatsApp care number, announcement,
  min withdrawal, referral reward.
- Uploaded images are stored in the `uploads/` folder next to server.js — back it up with `alpha.db`.

## Referral rule
Friend registers with your code. When that friend's FIRST deposit (10 or more) is approved, you get 5 coins (once per friend).
Reward and minimum are editable in Admin > Settings.

## Customer care
Menu > Customer Care opens WhatsApp chat with +63 930 941 5509 (change in Admin > Settings).

## Before going public
HTTPS (Caddy/Nginx), NODE_ENV=production, daily backup of alpha.db + uploads/, Privacy Policy + Terms text, legal check for
real-money gaming in India, and test every payment with a small amount first.
Not built: rewarded ads/daily coins (need ad network keys), automatic gateway payments, push notifications, Android APK wrapper.
