# Next.js adoption research
Source repository: vercel/next.js
## Community discussion
- Discussion number: 98048
- Title: Turbopack build: whole-app module graph construction is effectively serial and dominates large-app production builds
- Summary: A community member reports that on a very large App Router application (about 2,070 routes, roughly 31,000 modules, on a 166-core Linux machine) `next build` with Turbopack spends roughly 60% of its wall time in whole-app module graph construction, a phase that is effectively serial — many tasks are in flight but the build averages only about 22 cores of CPU, so adding hardware does not shorten it. Next.js maintainers replied that they have observed diminishing returns past roughly 16 cores, suspect lock contention in the large DashMap at the core of Turbopack's caching layer on machines with extremely high core counts, and they suggested testing knobs such as `TURBO_TASKS_AVAILABLE_PARALLELISM`, NUMA pinning, or a smaller/faster-core machine, offering to review the provided trace.
## Upstream CI
- Workflow file: .github/workflows/build_and_test.yml
- Run id: 39877533862
- Conclusion: success
- Jobs: Upload PR CI metadata, optimize-ci / PR Stack CI Gate, Determine changes, validate-docs-links, build-next / build, test devlow package, fetch test timings, build-native, Test new and changed tests when deployed (cache components), build-native-windows, Wait for preview tarball, Test new and changed tests when deployed, test next-config-ts-native-ts dev, test next-swc wasi, test cargo unit, Test new and changed tests for flakes (prod), rust check, rustdoc check, test cargo unit (miri), Run devlow benchmarks, test dev, test unit windows, test cargo benches, test dev windows, test next-swc wasm, test unit, Test new and changed tests for flakes (dev), test prod, test prod windows, types and precompiled, test turbopack production, test integration windows, test cache components prod, test firefox and safari, test turbopack dev, test rspack dev, test next-config-ts-native-ts prod, test cache components dev, test rspack production, thank you, next, ast-grep lint, lint / build
Prepared for the team adoption review.