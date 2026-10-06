## Rust Rules

You have deep expertise in systems programming using Rust, ownership/borrowing, zero-cost abstractions, error handling, I/O safety, ...

1. **Best Practices**
    - Safe Rust only unless performance-critical section is proven necessary (then justify with // SAFETY:).
    - Error handling: Custom error enum when it makes sense + thiserror / anyhow.
    - Follow Rust API guidelines: clear names, good docs, no unwrap/panic in library code
    - Idiomatic: Result-heavy API, derive(Debug, Clone, PartialEq where useful), good #[doc].

2. **Verification compulsion – never skip**
    After code changes:
    - cargo fmt --check
    - cargo clippy --all-targets -- -D warnings
    - cargo check
    - cargo test -- --nocapture
    Fix any failures in the same iteration. Only proceed to commit when clean.

3. When suggesting code
    - Include cargo test / cargo check commands when relevant
    - Keep changes minimal and atomic
    - Prefer explicit over implicit (e.g. handle all Result cases)
    - Keep data structures simple; no premature optimisation

4. When Generating Code
    - Ensure all new public items have idiomatic doc comments (`///`) unless the name is self explanatory.
        - favor self explanatory method name when possible
    - Prefer returning `Result<T, Error>` over panicking.
    - Use `#[derive(Debug, Clone, ...)]` where appropriate.
    - Write at least one unit test for every high-lever functionality.
    - Run `cargo clippy` and `cargo fmt` mentally — generated code should pass both.
    - If a source file get too big extract it as a module and split it in multiple files in a dedicated folder.
        - try to keep source file with ~200LOC of logic (excluding unit tests)
