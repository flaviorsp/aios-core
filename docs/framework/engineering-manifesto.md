# Synkra AIOS Engineering Manifesto

> **Status:** NON-NEGOTIABLE | **Enforcement:** GLOBAL | **Version:** 1.0.0
> **Authority:** This document overrides local preferences unless explicitly exempted by `.aios-core/constitution.md`.

---

## 1. The Core Philosophy (The Triad)

### 1.1. DRY (Don't Repeat Yourself) - Absolute
- **Single Source of Truth:** Every piece of knowledge must have a single, unambiguous, authoritative representation within the system.
- **Code Duplication:** strictly forbidden. If you write the same logic twice, refactor into a shared utility or service immediately.
- **Config Duplication:** Never hardcode values. Use configuration files (`core-config.yaml`, `.env`) or dependency injection.

### 1.2. YAGNI (You Aren't Gonna Need It) - Ruthless
- **Zero Speculation:** Do not build features for "future use". Implement only what the current Story requires.
- **Dead Code:** If it's not used, delete it. Commented-out code is tech debt; remove it.

### 1.3. KISS (Keep It Simple, Stupid) - Elegant
- **Complexity is a Cost:** Every abstraction layer adds cognitive load. Justify every class, interface, and pattern.
- **Readability > Cleverness:** Code is read 10x more than it is written. Write for the human reader, not the compiler.

---

## 2. Architecture & Design Patterns

### 2.1. Domain-Driven Design (DDD) [REQUIRED]
- **Ubiquitous Language:** Use the exact terminology from the Domain definitions in variable/class names.
- **Bounded Contexts:** Respect module boundaries (`packages/`). Do not cross-link domains without explicit interfaces.
- **Entity vs Value Object:** Know the difference. Entities have identity; Value Objects are defined by their attributes.

### 2.2. Clean Architecture Layers
- **Dependency Rule:** Source code dependencies can only point inwards.
    - `Entities` (Enterprise Rules) <- `Use Cases` (Application Rules) <- `Adapters` (Interface) <- `Frameworks` (Infrastructure)
- **Infrastructure Isolation:** The database, the web framework, and external APIs are details. They should be pluggable.

### 2.3. SOLID Principles (The Foundations)
- **SRP (Single Responsibility):** A class should have one, and only one, reason to change. Split monolithic agents/services.
- **OCP (Open/Closed):** Open for extension, closed for modification. Use Strategies/Templates instead of giant `if/else` chains.
- **LSP (Liskov Substitution):** Subtypes must be substitutable for their base types. Do not break parent contracts.
- **ISP (Interface Segregation):** Many client-specific interfaces are better than one general-purpose interface.
- **DIP (Dependency Inversion):** Depend on abstractions, not concretions. All external services (DB, APIs) must be injected.

### 2.4. Design Patterns (The Canon) [REQUIRED]
- **Strategy:** Use for varying algorithms (e.g., specific Logic for each LLM provider). Avoid `switch` statements.
- **Factory:** Use for creating Agents, Tasks, or complex Objects. Decouple construction from use.
- **Adapter:** MANDATORY for all external integrations (GitHub, Database, API). Protect the core from external changes.
- **Observer:** Use for agent-to-agent communication and event handling (e.g., "Story Completed" triggers "Notify User").
- **Builder:** Use for constructing complex prompts or configuration objects step-by-step.

### 2.5. Anti-Patterns (FORBIDDEN)
- **God Classes:** Violates SRP. Break it down.
- **Hardcoded Secrets/Magic Numbers:** Use constants or config.
- **Prop-Drilling:** Use Composition or Context, but prefer Composition.

---

## 3. Operational Excellence (Big Tech Standard)

### 3.1. Idempotency [CRITICAL]
- **Re-run Safety:** Every function, script, or workflow MUST be safe to re-run multiple times without side effects.
- **State Check:** Always check current state before applying changes.
    - *Bad:* `mkdir dir` (Fails if exists)
    - *Good:* `if (!exists(dir)) mkdir dir`

### 3.2. Incremental Processing & Resilience
- **Checkpointing:** Long-running processes must save state to allow resuming (e.g., `process-state.json`).
- **Graceful Degradation:** If a non-critical dependency fails (e.g., telemetry), log the error and proceed. PROD must not crash due to analytics failure.
- **Exponential Backoff:** Retries for network operations must use backoff algorithms, not tight loops.

---

## 4. Implementation Rules

### 4.1. Naming Conventions (Professional)
- **Descriptive:** `calculateTotalRevenue()` vs `calc()`
- **Boolean:** `isValid`, `hasPermission`, `isPending` (Prefix is mandatory).
- **Async:** Functions returning Promises should imply async nature if ambiguous, but modern standard prefers readable names (e.g., `fetchUser` over `fetchUserAsync`).

### 4.2. No Hardcoded Parameters
- **Config Injection:** All thresholds, timeouts, and paths must be injectable.
- **Environment Variables:** Use for credentials and varying environment configs.
