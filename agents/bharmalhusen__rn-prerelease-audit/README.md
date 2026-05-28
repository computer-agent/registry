# RN Pre-Release Audit Agent

> Catch every App Store & Play Store rejection reason before you submit — a Claude AI agent for React Native developers.

**Author:** [bharmalhusen](https://github.com/bharmalhusen) · **License:** MIT · **Version:** 1.0.0

---

## What It Does

This Claude Code agent performs a deep, automated pre-release audit of any React Native project. It reads your native config files, manifest files, and all TypeScript/JavaScript source, then runs **30+ structured compliance checks** across 20 categories. The output is a prioritised severity report:

- 🔴 **Error** — will cause a store rejection
- 🟡 **Warning** — likely rejection risk
- 🔵 **Info** — good to know
- ✅ **Passed** — clean

No more last-minute rejections. No more store policy rules you didn't know existed.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/bharmalhusen/rn-prerelease-audit
```

Or install as a Claude Code plugin and invoke:

```
/rn-prerelease-audit
```

---

## Checks — 30+ Across 20 Categories

| Category | What It Catches |
|---|---|
| 📡 **ATT** | Missing `NSUserTrackingUsageDescription`, no `requestTrackingAuthorization` |
| 🍎 **Sign in with Apple** | Third-party login without Apple login (guideline 4.8) |
| 🔏 **Auth Sessions** | Token not cleared on logout, missing refresh, no re-auth on destructive actions |
| 💳 **Payments & Billing** | No IAP for digital goods, external payment links on iOS |
| 🔐 **Permissions** | Declared but unused, used but undeclared, missing runtime handling |
| 🖼 **Icons & Assets** | Missing densities, alpha channel on iOS icons (hard rejection) |
| 🌅 **Splash Screen** | Missing config, broken image paths |
| 🔒 **iOS Privacy Descriptions** | Missing `NS*UsageDescription` keys |
| 🌐 **Network Security** | `usesCleartextTraffic=true`, `NSAllowsArbitraryLoads=true` |
| 🔑 **Secrets & API Keys** | Hardcoded tokens in config/source; tokens in AsyncStorage |
| 📊 **Crash Monitoring** | No Sentry/Crashlytics installed or initialised |
| 🏗 **New Architecture** | Inconsistent `newArchEnabled` across Gradle and app.json |
| 🔁 **Network Resilience** | No timeout, no retry, no offline handling |
| 🔗 **Deep Links** | Missing `autoVerify`, single-platform-only config |
| 📦 **Deprecated Dependencies** | Known rejected packages, unpinned `"*"` versions |
| 🗑️ **Account Deletion** | Apps with sign-up but no delete flow (Play Store policy) |
| 🔒 **Privacy Policy** | No in-app privacy policy link |
| 📂 **Target SDK** | `targetSdkVersion` below Play Store floor (≥ 34) |
| 📝 **Privacy Manifests** | Missing `PrivacyInfo.xcprivacy`, empty `NSPrivacyAccessedAPITypes` |
| 🎯 **Version Consistency** | `versionCode`/`versionName`/`CFBundleVersion` out of sync |

---

## Repository

https://github.com/bharmalhusen/rn-prerelease-audit
