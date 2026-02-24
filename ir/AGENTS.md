# AGENTS.md - Isabelle/REPL (I/R) Development Guide

## Overview

I/R provides a TCP-based REPL and MCP server for Isabelle/ML proof exploration outside of Isabelle/jEdit.

## Project Structure

```
ir/
├── repl.py           # TCP server wrapping Isabelle/Poly/ML console
├── ir.ML             # Standard ML REPL implementation (loads into Isabelle)
├── mcp_server.py     # MCP wrapper for AI agent integration
├── test_repl.py      # TCP server tests (single/multi-client)
├── test_console.py   # Console/readline tests
├── requirements.txt  # Python dependencies
└── docker/           # Docker configurations
```

## Build Commands

```bash
# Install Python dependencies
pip install -r requirements.txt

# Run I/R REPL server
python3 ./repl.py --isabelle /path/to/Isabelle/bin/isabelle --session HOL

# Run with MCP server enabled
python3 ./repl.py --isabelle /path/to/Isabelle/bin/isabelle --session HOL --mcp

# Run REPL with specific session directory
python3 ./repl.py --isabelle $ISABELLE_HOME/bin/isabelle --session My_Session --dir /path/to/session
```

## Test Commands

```bash
# Run all REPL tests (requires Isabelle heap built)
python3 ./test_repl.py --isabelle /path/to/isabelle --session HOL

# Run console tests
python3 ./test_console.py

# Run a single test by name
python3 -c "
import test_repl
test_repl.run_test('test_name', lambda: test_function())
"
```

## Docker Commands

```bash
# Build standalone Docker image
docker build -t isabelle-repl:standalone -f docker/Dockerfile.standalone .

# Run container with MCP server
docker run --rm -it -p 9148:9148 isabelle-repl:standalone
```

## Code Style

### Python

- **Shebang**: `#!/usr/bin/env python3`
- **License**: MIT header required
  ```python
  # Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved.
  # SPDX-License-Identifier: MIT
  ```
- **Types**: Use type hints for all function signatures
- **Naming**: `snake_case` functions/variables, `PascalCase` classes, `UPPER_CASE` constants
- **Line length**: Target < 100 characters
- **Error handling**: Define custom exceptions, include context in messages

### Standard ML (ir.ML)

- **Signatures**: Always define `signature` before `structure`
- **Types**: Explicit type annotations in signatures
- **References**: 
  - Use `Synchronized.var` for thread-safe state
  - Use `Unsynchronized.ref` for global refs (not thread-safe)
- **Exception handling**: Use `Exn.capture` / `Exn.release`
- **Indentation**: 2 spaces
- **Naming**: `camelCase` for values/functions, `PascalCase` for structures/signatures

## I/R REPL Commands

Common commands when interacting with I/R:

```
%> Ir.init "R" ["Main"]          # Create REPL importing theories
%> Ir.step "lemma test: True"    # Execute Isar command
%> Ir.state ~1                   # Show proof state (~1 = latest)
%> Ir.sledgehammer 10            # Run automated proof (10s timeout)
%> Ir.find_theorems 5 "name: conjI"  # Search theorems
%> Ir.theories ()                # List loaded theories
%> Ir.back ()                    # Revert last step
%> Ir.help ()                    # Show all commands
```

## Testing Notes

- Tests require an Isabelle heap to be built first. Just use the default `HOL` session for testing.
- Tests connect to TCP server on localhost with retries
- Each test sends commands and reads until `<<DONE>>` sentinel
- Tests cover single-client and multi-client scenarios. We focus on the single-client tests for faster development feedback.
- Testing environment:
  - Always use the python venv at `$HOME/.venvs/seL4-prover`. Use uv to manage the venv.
  - Use Isabelle2025 installation at `$APP_HOME/Isabelle/Isabelle2025-2`

## Environment Variables

- `ISABELLE_HOME` - Path to Isabelle installation
- `SENTINEL` - Response delimiter (default: `<<DONE>>`)

## Related Resources
- Isabelle2025 Source code at `$APP_HOME/Isabelle/Isabelle2025-2/src`
  Reference doc: `isar-ref.md`
  Implementation doc: `isar-impl.md`


