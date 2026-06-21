# Video Walkthrough Script — android-platform-starter

**Target length:** 10–12 minutes  
**Record with:** Loom, OBS, or Android Studio screen capture + voiceover  
**Upload to:** YouTube (unlisted or public) · Link from GitHub profile README

---

## Setup before recording

1. Clone https://github.com/kanav22/android-platform-starter  
2. Open in Android Studio · run `demoDebug` on emulator or device  
3. Have these files open in tabs:
   - `settings.gradle.kts`
   - `feature/home/.../HomeViewModel.kt`
   - `docs/adr/README.md`
   - `benchmark/.../StartupBenchmark.kt`

---

## Script

### Intro (0:00 – 0:45)

> "Hi, I'm Kanav Wadhawan, Principal Android Engineer. This is a walkthrough of android-platform-starter — a multi-module template I maintain for teams who want production-shaped architecture from day one, not after a rewrite in month six."

Show GitHub repo README on screen.

---

### Problem (0:45 – 1:30)

> "Most new Android projects start as a single app module. Features, networking, and UI primitives get tangled. Build times grow, tests get slow, and nobody can draw the dependency graph from memory."

Show module diagram from README (mermaid or ASCII).

---

### Module map (1:30 – 3:30)

Open `settings.gradle.kts`.

> "The starter enforces layers: app wires navigation, feature modules own screens and ViewModels, core domain is pure Kotlin with use cases, core data implements repositories, and designsystem holds Compose theme components."

Navigate to `HomeViewModel` — show `StateFlow` UI state.

> "Every feature exposes immutable UI state as StateFlow — testable without Compose, predictable recomposition."

---

### ADRs (3:30 – 4:30)

Open `docs/adr/README.md`.

> "Principal engineers document decisions, not just code. These ADRs capture why we chose multi-module boundaries, Hilt, Detekt in CI, and Macrobenchmark. When you fork this, add your own ADRs for auth and analytics."

---

### Quality gates (4:30 – 6:00)

Show `.github/workflows/ci.yml` briefly.

> "CI runs Detekt, unit tests, and assembles debug plus the benchmark module. If it's not in CI, it's not a standard."

Optional: show a green GitHub Actions run.

---

### Performance (6:00 – 7:30)

Open `StartupBenchmark.kt`.

> "The benchmark module measures cold startup on a physical device and generates baseline profiles. Performance is architecture — this module exists so teams measure before users complain."

Mention command: `./gradlew :benchmark:connectedBenchmarkReleaseAndroidTest`

---

### Demo (7:30 – 9:00)

Run the app. Show home screen.

> "This is intentionally minimal — one feature screen. The value is the skeleton: swap the fake repository for Retrofit and Room, add features as new modules, keep boundaries."

---

### Close (9:00 – 10:00)

> "Link in the description. Star the repo if it's useful, open issues if you want ADRs on specific topics. I'm Kanav — find me on LinkedIn and kanavwadhawan.com. Thanks."

---

## Post-production checklist

- [ ] Add chapters: Intro · Modules · ADRs · CI · Benchmark · Demo  
- [ ] Description links: GitHub repo, LinkedIn, portfolio  
- [ ] Pin comment with clone command  
- [ ] Add URL to profile README under Writing & Speaking  
