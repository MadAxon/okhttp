# Claude Code Guidelines - OkHttp

This guide provides concise, actionable instructions for Claude Code and related Anthropic AI tools.
The complete, authoritative guide is maintained in [AGENTS.md](file:///c:/Users/rusgo/.gemini/antigravity/scratch/okhttp/AGENTS.md).

---

## Commands Cheat Sheet

```bash
# Build & check everything
./gradlew check

# Fast check (excludes heavy test matrices)
./gradlew check -x jvmTest -x test -x allTests

# Run tests
./gradlew :okhttp:test                                      # Core module tests
./gradlew :okhttp:test --tests "okhttp3.CallTest"            # Specific test class
./gradlew :okhttp:test --tests "okhttp3.CallTest.testMethod" # Specific test method
./gradlew :mockwebserver:test                               # MockWebServer tests

# Formatting & Linting (Spotless + ktlint + Checkstyle)
./gradlew spotlessApply                                     # Auto-format Kotlin/KTS
./gradlew spotlessCheck checkstyleMain                      # Verify formatting

# API Compatibility Verification (Android API 21 & Java 8)
./gradlew animalSnifferMain
```

---

## Architectural & Code Rules

1. **Public API Invariance**: Never alter or remove public methods/classes in public packages (`okhttp3.*`, `mockwebserver3.*`). Maintain backward binary compatibility.
2. **Encapsulation**: Treat `okhttp3.internal.*` as strictly internal. Never expose internal classes in public method signatures.
3. **Android API 21 Constraint**: Do not use JDK 9+ APIs without checking desugaring support. Always verify with `./gradlew animalSnifferMain`.
4. **Test-First Discipline**: For any bug fix, write a reproducing unit test first using `MockWebServer` or test doubles, then apply the fix.
5. **Code Style**: Indent with 2 spaces. Follow existing Kotlin conventions. Always run `./gradlew spotlessApply` before committing.
6. **Class Authorship Tag**: Whenever creating a new class (Kotlin or Java), annotate it with `// Developed by BROgrammer` immediately above the class declaration.
7. **Commit Style**: Native OkHttp imperative English sentence (e.g. `Fix connection leak in HTTP/2 duplex test (#123)`).

For detailed rationale and module architecture, refer to [AGENTS.md](file:///c:/Users/rusgo/.gemini/antigravity/scratch/okhttp/AGENTS.md).
