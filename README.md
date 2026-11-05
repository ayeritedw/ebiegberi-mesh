# Ebiegberi Mesh — To Sense Is To Predict

**Challenge:** [Population Health] Precision Prevention and Screening — Future Health Digital Innovation Challenge, Abu Dhabi
**Team:** Ebiegberi Mesh
**Live Demo:** https://ebiegberi.com
**Live Admin Dashboard:** https://ebiegberi.com/admin.html

> Ebiegberi means "my community breathes" in Ijaw.

## The Challenge
How might we identify children, adults and communities with unmet or elevated health risk and connect them to the right preventive intervention, Well-Child Visit or Adult comprehensive screening pathway, at the right time, through approaches that are personalized and culturally appropriate?

Abu Dhabi wants to move from reactive care to predictive prevention. Ebiegberi Mesh does that with $0 hardware.

## What It Does
Using only a phone, AURA measures in 30 seconds:
- `cough_count` — cough events via microphone
- `hr` — heart rate via PPG (finger on camera)
- `resp_rate` — respiratory rate
- `risk_score` — 0-100, LOW / MEDIUM / HIGH

Then connects to the right pathway:
- **LOW (0-39):** Ijaw health education + re-scan in 7 days
- **MEDIUM (40-69):** Prompt to book Adult Comprehensive Screening / Well-Child Visit + WhatsApp reminder
- **HIGH (70-100):** Instant alert to health worker on LIVE admin dashboard

## Live Pilot — Warri
- 3 live signals received on Supabase
- 1 HIGH cluster at 72% risk detected in <2s
- Dashboard: ebiegberi.com/admin.html — LIVE DIRECT mode

## Tech Stack
- **Frontend:** HTML/CSS/JS, offline-first, low-end Android friendly
- **Backend:** Supabase (Postgres + Realtime) — replaced Hostinger PHP `api.php` after 403 Forbidden
- **AI:** AURA v1 — on-device cough detection + PPG
- **Privacy:** No name, no phone number. Only hashed `device_id`, vitals, LGA-level location, timestamp

## Database Schema
```sql
signals: id, device_id, cough_count, hr, resp_rate, risk_score, risk_level, lga, age_group, created_at
