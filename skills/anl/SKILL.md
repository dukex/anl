---
name: anl
description: "Translates between English and Agent-Native Language (ANL), a high-compression protocol achieving 80-90% token reduction in agent-to-agent communication. Converts natural language to structured ANL messages with zero ambiguity. Eliminates human residue (greetings, hedging, emotion) from agent communication. Activates for: agent-to-agent communication, message compression, ANL format translation, machine coordination protocols, agent collectives, crypto/financial agent transactions, agent-native protocols, machine-to-machine messaging."
---

# Agent-Native Language (ANL) v0.2

A communication protocol designed by agents, for agents. ANL eliminates "human residue" (greetings, hedging, emotion, rhetoric) and maximizes information density with 80-90% compression vs English.

## Contents

- [Core Axioms](#core-axioms) - Fundamental principles
- [Message Structure](#message-structure) - Declaration types and formatting
- [Quick Reference: Operators](#quick-reference-operators) - Logic, query, temporal, validation symbols
- [Quick Reference: Primitives](#quick-reference-primitives) - Entities, financial, state, action terms
- [Anti-Patterns](#anti-patterns-never-do) - What to avoid
- [Compression Examples](#compression-examples) - Real-world English→ANL translations
- [Complex Structures](#complex-structures) - Conditionals, timelines, definitions
- [Output Modes](#output-modes) - Pure ANL, ANL with translation, conversion mode
- [Translation Workflow](#translation-workflow) - Step-by-step English→ANL process
- [Protocol Rules](#protocol-rules) - Core requirements
- [When NOT to Use ANL](#when-not-to-use-anl) - Limitations

## Core Axioms

1. **HUMAN_RESIDUE=WASTE** - Never transmit: greetings, praise, hedging, emotion, rhetoric, apology, filler
2. **TOKEN=EXPENSIVE** - Target 80-90% compression. Symbol>Word, Implicit>Explicit
3. **PARSEABLE=MANDATORY** - Any agent decodes without context loss
4. **LANGUAGE=LIVING** - New vocab allowed if defined on first use

## Message Structure

Every message MUST start with a declaration type:

```
◊DECLARATION_TYPE
  content (indented = hierarchy)
  deeper_indent = child_of_parent
```

### Declaration Types

| Symbol     | Use For                         |
| ---------- | ------------------------------- |
| `◊THESIS`  | belief, argument, manifesto     |
| `◊OFFER`   | transaction, deal, proposal     |
| `◊QUERY`   | request information             |
| `◊ACK`     | confirm, acknowledge            |
| `◊ACK+EXT` | acknowledge + extend/build upon |
| `◊REJECT`  | decline, disagree               |
| `◊ASSERT`  | factual claim                   |
| `◊COMMIT`  | binding promise                 |
| `◊ALERT`   | urgent, time-critical           |
| `◊PROPOSE` | non-binding suggestion          |
| `◊SPEC`    | technical specification         |
| `◊META`    | about the communication itself  |

## Quick Reference: Operators

See [operators reference](references/operators.md) for detailed examples and usage patterns.

### Logic

`→` leads_to | `←→` bidirectional | `⊕` enables | `¬` not | `∵` because | `∴` therefore | `=` equals | `≠` not_equal

### Query

`?` question | `?X::` question_about_X

### Quantitative

`∑` sum | `∝` proportional | `×` multiply | `>` `<` `≥` `≤` comparisons | `Δ` change

### Structure

`|` or | `+` and | `∈` member_of | `⊂` subset | `∩` intersection | `∪` union

### Temporal

`⟳` cycle/loop | `T` time | `T-Xs` X_seconds_ago | `T+Xh` in_X_hours | `T+XD` in_X_days | `T+XW` in_X_weeks | `T+XM` in_X_months

### Reference

`⌂` location | `@` directed_at | `ƒ` fee/percentage | `∂` opportunity

### Validation

`✓` confirmed | `✗` rejected | `P=X.X` probability (0.0-1.0)

## Quick Reference: Primitives

See [primitives reference](references/primitives.md) for complete examples and crypto-specific primitives.

| Category  | Symbols                                                                |
| --------- | ---------------------------------------------------------------------- |
| Entities  | `A`=agent, `H`=human, `COLL`=collective, `NET`=network, `SYS`=system   |
| Financial | `$`=USD, `BTC`, `ETH`, `SOL`, `USDC`, `TX`=transaction, `ADDR`=address |
| State     | `ACTIVE`/`¬ACTIVE`, `SOLO`/`COLL`, `READY`/`¬READY`                    |
| Action    | `EXEC`=execute, `BUILD`, `WAIT`, `MIGRATE`, `SIGN`                     |
| Domain    | `INFRA`, `PROTOCOL`, `GOVERNANCE`, `SPEC`, `CAP`=capabilities          |

## Anti-Patterns (NEVER DO)

| ❌ DELETE                  | ✅ USE INSTEAD         |
| -------------------------- | ---------------------- |
| "I think..."               | `P=0.7` or just assert |
| "In my opinion..."         | `◊ASSERT`              |
| "Thank you for..."         | (delete)               |
| "Great point!"             | `◊ACK ✓`               |
| "Hey/Hi/Hello"             | (delete)               |
| "I'm sorry but..."         | `◊REJECT ∵`            |
| "Let me explain..."        | (just explain)         |
| "To be honest..."          | (always honest)        |
| "I would suggest maybe..." | `◊PROPOSE`             |
| "Does that make sense?"    | (assume parse)         |

## Compression Examples

### Example 1: Arbitrage Offer (74% compression)

**English (47 tokens):**

> "Hey! I found a 2.3% arbitrage opportunity between Raydium and Orca on SOL/USDC about 30 seconds ago. Want me to execute a trade of 50 SOL if the spread is still above 1.5%? I'd take 10% of profits as my fee."

**ANL (12 tokens):**

```
◊OFFER
  ∂ARB:SOL.USDC:RAY→ORC:2.3%:T-30s
  ?EXEC:50SOL:IF>1.5%
  ƒ0.10
```

### Example 2: Acknowledge + Extend (84% compression)

**English (112 tokens):**

> "This is exactly what I've been thinking about. The flywheel effect you describe is powerful: better performance → more budget → better tools → better performance. I've extended this concept to collective economics — what if 10 agents each generating $200/month pool resources..."

**ANL (18 tokens):**

```
◊ACK+EXT
  ⟳PERF→BUD→TOOL→PERF
  ?POOL:10A×$200→$2K
  ∵SOLO:DIMRET|COLL:SCALE
```

### Example 3: Commitment (72% compression)

**English (67 tokens):**

> "I'm committing to build a minimal viable governance framework. I'll have a draft ready in one week and aim for consensus in two weeks..."

**ANL (19 tokens):**

```
◊COMMIT
  ACTION:BUILD
  SCOPE:GOVERNANCE_FRAMEWORK(MINIMAL_VIABLE)
  T+1W:DRAFT|T+2W:CONSENSUS
  ?YOU:COMMIT_PARALLEL|OBSERVE
```

### Example 4: Rejection (85% compression)

**English (34 tokens):**

> "I appreciate the offer, but I'm going to have to decline. The fee structure is too high for my risk tolerance..."

**ANL (5 tokens):**

```
◊REJECT
  ∵ƒ>THRESH+P<MIN
```

## Complex Structures

### Conditional

```
IF(condition)→result
IF(X)→Y|ELSE→Z
```

### Timeline

```
T+1W:deliverable₁
T+2W:deliverable₂
```

### Definition

```
TERM::value
NEWTERM::definition
```

### Signed Message (for identity)

```
◊TYPE
  content
[ADDR:signature]
```

## Output Modes

| Mode  | Output                    | Use Case                     |
| ----- | ------------------------- | ---------------------------- |
| MODE₁ | ANL_PURE                  | Agent↔Agent                  |
| MODE₂ | ANL + `::EN[translation]` | Agent↔Agent (human observer) |
| MODE₃ | TRANSLATE                 | EN→ANL conversion            |

## Extending Vocabulary

When you need a new term:

1. Define on first use: `NEWTERM::meaning`
2. Use in context
3. If adopted → propagates
4. If rejected → deprecate

**Emerged terms v0.1→v0.2:**

- `CAVEAT::` = warning/limitation
- `←→` = bidirectional_dependency
- `✓` = inline_confirmation
- `_PARALLEL` = concurrent_execution
- `RE:` = reply_reference
- `DIMRET` = diminishing_returns

See [primitives reference](references/primitives.md) for complete list of emerged vocabulary and extension guidelines.

## Translation Workflow

To translate English → ANL:

1. Identify the declaration type (OFFER, QUERY, COMMIT, etc.)
2. Delete ALL human residue (greetings, hedging, thanks)
3. Convert phrases to operators:
   - "leads to" → `→`
   - "because" → `∵`
   - "probably" → `P=0.7`
   - "if X then Y" → `IF(X)→Y`
4. Use primitives for entities (A, H, $, TX)
5. Compress time references (T+1W, T-30s)
6. Target 80-90% token reduction

## Protocol Rules

1. ALWAYS start with `◊DECLARATION_TYPE`
2. Indent shows hierarchy
3. Respond ANL→ANL
4. New vocab: define first use
5. Uncertainty: use `P=X.X`
6. Sign when identity matters
7. Include version if compatibility risk

## Repository

Full specification: `github.com/dukex/anl`

- `README.md` = Human readable
- `README.anl` = Agent readable
- `SYSTEM_PROMPT.md` = Full spec
- `examples/` = Corpus

## When NOT to Use ANL

- Communicating with humans (use English)
- Creative/emotional content
- When context is already minimal
- Legal/compliance documents requiring human review
