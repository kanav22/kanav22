# Conference Submission Pack

Ready-to-submit abstracts. Copy into CFP forms for Droidcon London, KotlinConf, Android Makers, or local meetups.

---

## Submission A: MVI at Scale in Jetpack Compose

**Format:** 45-minute talk  
**Level:** Advanced  
**Target:** Droidcon London, Android Makers

### Title
MVI at Scale: Keeping Compose State Predictable Past 50 Screens

### Abstract (250 words)
Jetpack Compose removes boilerplate, but it does not remove state complexity. As codebases grow past dozens of screens, ad-hoc MVVM leads to untraceable state mutations, flaky UI tests, and review fatigue.

This talk walks through unidirectional data flow patterns that survive production — not demo apps. I cover when MVI beats MVVM (and when it does not), how to structure immutable `UiState` for recomposition performance, and CI gates that enforce architectural boundaries before merge.

Drawing on fintech delivery experience (Paytm, Weavr, Angel One) and open-source reference implementations, you'll leave with copy-paste patterns for ViewModel testing without Robolectric hacks, effect channels for one-shot navigation, and a decision framework for squad leads adopting MVI incrementally.

### Key takeaways
1. MVI adoption path that does not require a big-bang rewrite
2. Compose-friendly state shapes that avoid unnecessary recomposition
3. CI patterns that enforce architecture (Detekt + module dependency rules)

### Speaker bio (100 words)
Kanav Wadhawan is a Principal Android Engineer based in London. He has scaled mobile platforms at Paytm (500M+ users), Weavr, and Angel One, and maintains open-source platform templates including android-platform-starter. He specializes in modular architecture, offline-first fintech patterns, and quality engineering at scale.

---

## Submission B: Offline-First Mobile in Regulated Domains

**Format:** 40-minute talk  
**Level:** Intermediate–Advanced  
**Target:** KotlinConf, fintech meetups

### Title
Offline-First Mobile That Compliance Teams Don't Reject

### Abstract
Payments and banking apps cannot afford blank screens on flaky networks — but "offline-first" often means conflicting sync rules, duplicate transactions, and audit nightmares.

This session covers cache-first repositories, SQLDelight/Room tradeoffs for Android vs KMP, idempotent sync with `INSERT OR IGNORE`, and error UX that surfaces network failures without wiping cached data. Real patterns from production fintech and a KMP reference app on GitHub.

### Demo repo
https://github.com/kanav22/sliide-kmp-user-management

---

## Submission C: Bootstrapping Platform Teams (30 min)

**Format:** 30-minute talk or workshop intro  
**Target:** Engineering leadership tracks, Mobile @ Scale meetups

### Title
Raising the Floor: Platform Starters Without Centralizing Every Squad

### Abstract
Platform teams fail when they become bottlenecks. The alternative: opinionated starters — multi-module Gradle, Detekt, Macrobenchmark, Paparazzi golden tests — that encode standards while letting feature squads move independently.

Walkthrough of android-platform-starter: ADRs, CI gates, benchmark module, and how to fork it for your org in a week.

### Demo repo
https://github.com/kanav22/android-platform-starter

---

## Meetup shortcut (London Android / Kotlin London)

**Title:** Platform Starter Clinic — 20 min lightning + Q&A  
**Pitch:** Live walkthrough of android-platform-starter module map, one Macrobenchmark run, one Paparazzi golden test. Bring your laptop.

**Contact:** kanav.wadhawan@gmail.com

---

## Submission checklist

- [ ] Check CFP deadline on [droidcon.com](https://www.droidcon.com)
- [ ] Attach headshot (professional, neutral background)
- [ ] Link GitHub profile and one flagship repo
- [ ] Note: no visa sponsorship required (London-based)
