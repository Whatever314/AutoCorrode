# AGENTS.md - AutoCorrode Development Guide

This file provides development guidance for agents working on the AutoCorrode project.

## Project Overview

AutoCorrode is an Isabelle/HOL verification framework for reasoning about imperative programs (µRust).

**Note**: For I/R (Isabelle/REPL) development, see `ir/AGENTS.md`.

## Build Commands

```bash
# Build all AutoCorrode sessions (requires Isabelle2025-2)
make build

# Open Isabelle/jEdit for interactive development
make jedit

# Register AFP Word_Lib component
make register-afp-components
```

## Environment Variables

- `ISABELLE_HOME` - Path to Isabelle2025-2 installation
- `AFP_COMPONENT_BASE` - Path to AFP dependencies (default: `./dependencies/afp`)
- `ISABELLE_FLAGS` - Build flags (default: `-b -j 1 -o "threads=N" -v`)
- `QUICK_AND_DIRTY` - Allow `sorry` in proofs

## Code Style

### Isabelle Theory Files (.thy)

- **Header**: Include MIT license header
  ```
  (* Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved.
     SPDX-License-Identifier: MIT *)
  ```
- **Theory declarations**: Use `(*<*)` and `(*>*)` markers for hidden content
  ```
  (*<*)  
  theory MyTheory
    imports OtherTheory
  begin
  (*>*)
  ```
- **Sectioning**: Use `section`, `subsection`, `subsubsection` with LaTeX markup
- **Naming**: `Upper_Snake_Case` for theory names, `camelCase` for constants
- **Comments**: Use LaTeX-style `\<comment> \<open>text\<close>`
- **Unicode**: Use Isabelle's unicode translation (e.g., `\<forall>`, `\<Rightarrow>`)

### Isabelle/ML (.ML)

- **Signatures**: Define `signature` before `structure`
- **Types**: Explicit type annotations in signatures
- **References**: Use `Synchronized.var` for thread-safe state
- **Exception handling**: Use `Exn.capture` / `Exn.release`
- **Indentation**: 2 spaces
- **Naming**: `camelCase` for values/functions, `PascalCase` for structures

## Project Structure

```
AutoCorrode/
├── Makefile              # Main build commands
├── ROOT                  # Isabelle session definitions
├── AutoCorrode.thy       # Root theory
├── ir/                   # I/R REPL (see ir/AGENTS.md)
├── Shallow_Micro_Rust/   # µRust monad
├── Shallow_Separation_Logic/ # Separation logic
├── Crush/                # Verification tactics
├── Micro_Rust_*/         # Runtime, interfaces, stdlib
├── ip/                   # Isabelle/Proxy
├── iq/                   # Isabelle/Q
└── isabelle-assistant/   # AI assistant plugin
```

## Testing

```bash
# Full build (tests all proofs)
make build

# Quick build
isabelle build -b -d . AutoCorrode

# Single session
isabelle build -b -d . Session_Name
```

## Common Tasks

### Adding a theory

1. Create `Your_Theory.thy` in appropriate directory
2. Add to `ROOT`:
   ```
   session Your_Session = HOL +
     theories Your_Theory
   ```
3. Import in parent theory

## CI/CD

See `.github/workflows/`:
- `ci.yml` - Main CI
- `cd.yml` - Documentation
- `ir.yml` - I/R tests

## Resources

- [Isabelle2025-2](https://isabelle.in.tum.de/website-Isabelle2025-2/)
- [Documentation](https://awslabs.github.io/AutoCorrode/)
- [WordLib AFP](https://www.isa-afp.org/entries/Word_Lib.html)
