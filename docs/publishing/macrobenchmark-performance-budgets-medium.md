# Performance Budgets with Macrobenchmark and Baseline Profiles

*Companion repo: [android-platform-starter](https://github.com/kanav22/android-platform-starter)*

---

Teams ship Compose features quickly, then discover cold start regressed by 400ms — after release. Performance work becomes reactive firefighting instead of a platform standard.

Principal engineers treat startup and frame time like API contracts: measurable, gated, and owned.

## Macrobenchmark in the template

The `benchmark` module ships with cold startup measurement and baseline profile generation. Every app cloned from the starter can answer: *"What is our cold start on a physical device?"*

Run on hardware — emulators lie about I/O and JIT:

```bash
./gradlew :benchmark:connectedBenchmarkReleaseAndroidTest
```

## Baseline profiles as compile-time investment

Baseline profiles tell ART which methods to AOT-compile before first launch. For Compose-heavy apps, the win is often hundreds of milliseconds on cold start.

## Performance budgets (the Principal move)

| Metric | Example budget |
|--------|----------------|
| Cold start (p50) | < 800ms on reference device |
| Regression gate | No PR increases p50 by > 5% |
| Baseline profile | Must compile on release builds |

## Summary

Performance is architecture. Shipping Macrobenchmark in a platform starter raises the floor for every squad.

Full article: [github.com/kanav22/android-platform-starter](https://github.com/kanav22/android-platform-starter/blob/main/docs/articles/macrobenchmark-performance-budgets.md)

---

**About the author:** Kanav Wadhawan · Principal Android Engineer · London  
[LinkedIn](https://www.linkedin.com/in/kanav-wadhawan/) · [GitHub](https://github.com/kanav22)
