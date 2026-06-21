# MVI, Offline-First, and KMP: Architecture Decisions That Survive Production

*Originally published on [kanavwadhawan.com](https://www.kanavwadhawan.com) · Companion repo: [sliide-kmp-user-management](https://github.com/kanav22/sliide-kmp-user-management)*

---

User-management flows look simple in a demo: fetch a list, show details, handle errors. In production they fail in predictable ways — network drops mid-scroll, token misconfiguration causes silent 401 loops, iOS and Android teams diverge on state handling, and UI tests pass while integration paths regress.

This article documents the decisions in a Kotlin Multiplatform reference app built to survive those failures.

## Decision 1: MVI over ad-hoc MVVM

**Choice:** Unidirectional data flow with explicit `UiState`, `UiEvent`, and `UiEffect`.

MVVM without discipline becomes "state everywhere." MVI forces every user action through a single reducer path, which makes Compose recomposition predictable, ViewModel tests deterministic, and code review faster.

**Tradeoff:** More boilerplate for trivial screens. For list+detail flows with pagination and error recovery, the upfront cost pays back in testability.

## Decision 2: SQLDelight for shared offline storage

**Choice:** SQLDelight in `commonMain` instead of Room.

Single schema across Android and iOS, type-safe queries at compile time, and `INSERT OR IGNORE` semantics for idempotent sync.

**Production lesson:** Define your sync contract at the SQL layer first. UI state should reflect what's in the database, not what's in memory.

## Decision 3: Cache-first, not network-first

Repository returns local data immediately; network refresh updates the cache in the background. Users on mobile networks experience latency spikes — fintech and consumer apps that blank the screen on every refresh feel broken.

## Decision 4: Ktor in commonMain

Retrofit is JVM/Android-centric. Ktor keeps HTTP in shared code with expect/actual only where needed.

## Decision 5: CI as an architecture gate

GitHub Actions runs JVM tests, Android unit tests, and debug builds on every PR. If it's not in CI, it's not a standard.

## Summary

Production mobile architecture is about **boundaries**: MVI for UI discipline, SQLDelight for offline truth, cache-first for resilient UX, CI for enforcement.

Full code and diagrams: [github.com/kanav22/sliide-kmp-user-management](https://github.com/kanav22/sliide-kmp-user-management/blob/main/docs/architecture/kmp-mvi-offline-first.md)

---

**About the author:** Kanav Wadhawan is a Principal Android Engineer in London. He has scaled mobile platforms at Paytm, Weavr, and Angel One. [LinkedIn](https://www.linkedin.com/in/kanav-wadhawan/) · [GitHub](https://github.com/kanav22)
