<!-- # Damilare Hamed — @thinkdare -->

**I build revenue-generating SaaS and production-grade platforms for real-world problems.**

Fullstack engineer and DevSecOps practitioner based in Lagos, Nigeria. I architect systems that handle payments, multi-tenancy, clinical data, real-time events, and production failure modes correctly — from day one.

---

## 🚀 What I'm Building

### Live & In Development

---

### 🏥 Healthcare EMR
> *Multi-tenant Electronic Medical Records platform for hospitals, clinics, pharmacies, and laboratories across Nigeria*

A production-grade EMR SaaS that enables healthcare organisations to manage patient records, clinical workflows, cross-facility referrals, compliance auditing, and billing in a single system.

**Architecture highlights:**
- **Dual-database multi-tenancy** — every facility gets its own isolated PostgreSQL database; a breach of one tenant cannot expose another facility's records
- **Field-level AES-256 encryption** — PII fields encrypted at rest with HMAC-SHA256 searchable hashes
- **Post-response audit middleware** — immutable HIPAA-style audit trail written in the termination phase so audit writes never delay clinical responses
- **Offline sync** — Flutter clients write while offline; server detects conflicts and returns structured `409 VERSION_CONFLICT` responses
- **Clinical rank hierarchy** — capability-flag RBAC (`can_prescribe`, `can_order_labs`, `can_perform_emergency_access`) replacing flat role checks
- **Break-glass emergency access** — always logged, notified, and escalated if not reviewed within SLA

**Stack:** Laravel 11 · PostgreSQL 16 (dual-DB) · Redis · Laravel Sanctum (TOTP 2FA) · Flutter (iOS/Android/Web) · Stripe · Paystack · Flutterwave · Docker · GitHub Actions

---

### 👗 Drape
> *Multi-tenant SaaS platform powering virtual garment try-on for fashion brands*

Brands subscribe, upload their garment catalogue, and embed a fitting room experience directly in their storefront. Customers create measurement profiles, virtually try on garments, and receive a fit confidence score before buying.

**Architecture highlights:**
- **Three-guard auth** — separate Sanctum guards for tenant (brand), customer, and platform admin
- **Async garment pipeline** — uploaded garments processed into try-on-ready assets via queued workers
- **White-labelled embed** — brands embed the fitting room on any storefront via a scoped embed key
- **Sizing analytics** — try-on trends, fit score distributions, and pipeline health per brand
- **Multi-processor billing** — Paystack, Flutterwave, and Stripe under a unified subscription layer

**Stack:** Laravel 12 · PostgreSQL 16 · Redis · Laravel Horizon · React Native (Expo) · AWS S3 · Resend · Livewire 4 · Docker · GitHub Actions · Sentry

---

### 🧾 AI Invoice Chaser *(in development)*
> *WhatsApp-native invoice automation for Nigerian and Kenyan SMBs*

Automates payment reminders via WhatsApp, generates Paystack payment links, and tracks outstanding invoices — purpose-built for African SMBs who currently chase 60–70% of invoices manually with zero audit trail.

**Architecture highlights:**
- **6-tier escalation engine** — configurable reminder sequences from 7 days before due to 14+ days overdue, with per-channel fallback (WhatsApp → SMS → email)
- **Webhook idempotency** — `processed_webhooks` table checked before any Paystack state mutation; no double-credit on replay
- **Multi-tenant isolation** — `BelongsToTenant` global Eloquent scope on every tenant-owned model, enforced at DB query layer
- **Dead-letter observability** — failed reminder jobs surface to dashboard; nothing drops silently

**Stack:** Fastify · PostgreSQL · BullMQ · Redis · React · Paystack · Meta Cloud API · Termii · Resend · Railway · Sentry

---

### 🏫 School Fee & Report Card Portal *(planned)*
> *Fee collection and digital report card delivery for Nigerian private schools*

Replaces the school accountant's spreadsheet and the printer. Fee payment via Paystack, auto-generated receipts, report card PDF delivery, and a parent portal — with per-school tenant isolation.

**Stack:** Laravel 11 · MySQL · Livewire · Paystack · Termii · dompdf · Railway

---

### 🍽️ Restaurant POS + WhatsApp Ordering *(planned)*
> *Tablet-based POS with real-time kitchen display and WhatsApp order intake for Nigerian restaurants*

Connects front-of-house, kitchen, and delivery in one system. WhatsApp ordering via a structured conversation state machine tied to each restaurant's menu.

**Stack:** Laravel 11 · MySQL · Livewire · Pusher · Meta Cloud API · Paystack · DigitalOcean

---

### 💳 AI Failed Payment Recovery *(planned)*
> *Payment-processor-agnostic recovery layer for global SaaS businesses*

Analyses Stripe failure reason codes, customer payment history, and behavioural signals to determine the optimal recovery channel and timing — targeting the 5–9% MRR SaaS businesses silently lose to failed payments.

**Stack:** Node.js · Fastify · BullMQ · PostgreSQL · OpenAI · Next.js · Stripe · Twilio · Resend · Vercel

---

## 🧱 Core Stack

**Backend**
![Node.js](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![Fastify](https://img.shields.io/badge/Fastify-000000?style=for-the-badge&logo=fastify&logoColor=white)
![PHP (Laravel)](https://img.shields.io/badge/laravel-%23FF2D20.svg?style=for-the-badge&logo=laravel&logoColor=white)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white)

**Frontend**
![React.js](https://img.shields.io/badge/react-%2320232b.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![Next.js](https://img.shields.io/badge/Next.js-black?style=for-the-badge&logo=next.dot.js&logoColor=white)
![React Native](https://img.shields.io/badge/react_native-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![Flutter](https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white)
![Alpine.js](https://img.shields.io/badge/Alpine.js-%238BC0D0.svg?style=for-the-badge&logo=alpinedotjs&logoColor=white)

**Infrastructure & Data**
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/mysql-%2300f.svg?style=for-the-badge&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![AWS S3](https://img.shields.io/badge/AWS_S3-FF9900?style=for-the-badge&logo=amazons3&logoColor=white)

**Payments & Messaging**
![Paystack](https://img.shields.io/badge/Paystack-011B33?style=for-the-badge&logo=Paystack&logoColor=white)
![Stripe](https://img.shields.io/badge/Stripe-626CD9?style=for-the-badge&logo=Stripe&logoColor=white)

---

## ⚙️ Engineering Principles I Ship With

- **Webhook idempotency first.** Payment-adjacent systems deduplicate before they process. Always.
- **Multi-tenancy at the DB layer.** Application-level scoping is not enough — global query scopes, per-tenant DB isolation, or both depending on the compliance requirement.
- **Encryption at the field level for sensitive data.** AES-256 at rest with searchable HMAC hashes. Not optional for clinical or financial PII.
- **Audit trails in the termination phase.** Compliance logging never delays the response the user is waiting for.
- **Queues over synchronous processing.** If it can fail silently, it belongs in a queue with a dead-letter alert.
- **Security is architecture, not a feature.** HMAC webhook verification, rate limiting, RBAC at the policy layer, and input validation are Week 1 requirements — not Week 7 hardening.

---
<!--
## 📊 Activity

<p align="center">
<img src="https://github-readme-stats.vercel.app/api?username=thinkdare&show_icons=true&theme=radical&rank_icon=github&include_all_commits=true" alt="Thinkdare Stats" />
</p>

---
-->

## 🤝 Work With Me

Available for freelance engagements — specifically:

- **Healthcare & compliance systems** — EMR, audit trails, field-level encryption, HIPAA/NDPA-aligned architecture
- **Fintech & payment integrations** — Paystack, Stripe, Flutterwave, webhooks, reconciliation, multi-processor billing
- **WhatsApp API automation** — Meta Cloud API, structured conversation flows, state machines
- **SaaS architecture** — multi-tenant systems, queue-driven backends, DevSecOps, CI/CD

If you're a founder building in Africa or a team that needs senior fullstack and DevSecOps execution, let's talk.

[📩 Email](mailto:thinkdare.dev@gmail.com) · [𝕏 @thinkdare_dev](https://x.com/thinkdare_dev) · [💼 LinkedIn](https://www.linkedin.com/in/damilare-hamed-50322952) · [🌐 thinkdare.dev](https://thinkdare.dev)
