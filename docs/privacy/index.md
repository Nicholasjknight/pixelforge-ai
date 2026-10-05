---
title: PixelForge AI Privacy Policy
permalink: /privacy/
---
# PixelForge AI Privacy Policy

Effective date: 2026-10-02

This policy explains how PixelForge AI ("the app"), a Windows desktop application published by Knight Logics, handles information.

## 1. Summary
- Your videos and images are processed **only on your computer**. PixelForge AI never uploads media, frames, previews or file names.
- The app contacts the Knight Logics licensing service to manage free and purchased credits, and Stripe to process payments.
- We do not sell personal information and do not use advertising trackers.

## 2. Processed locally (never leaves your device)
- Source and output videos and images, preview frames, and rendered results
- File names and folder paths
- Hardware detection results (GPU model, VRAM, CPU, RAM), used to pick engines and estimate render time
- Local settings, logs, render checkpoints, and a local copy of your credit/account state (access token, purchase email if provided, recovery code, pending render charges). These are stored in your Windows user profile (`%APPDATA%\KnightLogics\PixelForgeAI`, which Windows redirects into the app's package folder for the Microsoft Store version) and are removed when you uninstall the Store version.

## 3. Sent to the Knight Logics licensing service
The app sends HTTPS requests to `https://knightlogics.com/api/pixelforge-license` to:
- start your free trial and check your credit balance;
- reserve credits when a render starts, then either confirm them when the output is valid or return them if the render is cancelled or fails;
- start a checkout, confirm a completed payment, and restore purchases.

Each request can include:
- an **app-scoped device ID**: a one-way SHA-256 hash derived from your Windows installation ID. The raw Windows identifier is never sent, and the hash is useless outside PixelForge;
- the app version and the product identifier;
- your account access token and, if you provide one or enter it at checkout, your email address;
- for a render reservation: number of credits, chosen profile and model, scale, source resolution (for example 1920x1080), a coarse duration bucket, target frame rate, and whether frame interpolation is on.

**Anonymous diagnostics.** The app also sends a small number of anonymous events (app opened, first launch, checkout cancelled, render outcome or quality feedback). Each contains only the app-scoped device ID, app version, selected profile/model, coarse source dimensions/duration, and the outcome. File names, media, computer name, raw machine identifiers and email are never part of diagnostics. To opt out, set the environment variable `V11B_DISABLE_ANONYMOUS_DIAGNOSTICS=1`.

## 4. Payments
Credit packs are one-time purchases processed by **Stripe** on behalf of Knight Logics, not by Microsoft. Checkout opens on Stripe's hosted page. Your card details go directly to Stripe and are never seen or stored by the app or by Knight Logics. Stripe provides Knight Logics with the purchase email, amount, pack purchased, and a payment reference, which we use to add the credits to your account and to handle refunds and support. A short-lived listener on your own computer (`localhost`) receives the "payment finished" redirect so the app can confirm the purchase. Stripe's privacy policy: https://stripe.com/privacy

## 5. Service providers
- Stripe (payment processing)
- Vercel (hosting of knightlogics.com and the licensing API)
- Neon (database for licensing and credit records)

They process data only to provide these services to Knight Logics.

## 6. Retention
Licensing and purchase records (device ID hash, email if given, credit ledger, payment references) are kept while your account is active and for as long as tax and accounting law requires afterward. Diagnostic events are kept in aggregate for product improvement.

## 7. Your choices and rights
You can use the free credits without giving an email. You can ask us to access, correct or delete the data linked to your device ID or email by writing to support@knightlogics.com. We will answer within 30 days. Records we must keep for tax purposes are retained only as long as the law requires.

## 8. Children
PixelForge AI is a general-audience tool. It is not directed at children under 13, and we do not knowingly collect their personal information.

## 9. Security
All network traffic uses HTTPS. No payment secrets, signing keys or database credentials ship inside the app. You are responsible for securing your own device and Windows account.

## 10. Changes
We may update this policy. The effective date above shows the latest revision. Material changes will also be noted in the app's release notes.

## 11. Contact
Knight Logics, Tampa Bay, Florida, USA
Email: support@knightlogics.com
Website: https://knightlogics.com/pixelforge-ai
