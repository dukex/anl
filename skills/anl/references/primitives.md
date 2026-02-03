# ANL Primitives Reference

## Entity Primitives

| Primitive | Meaning    | Usage               |
| --------- | ---------- | ------------------- |
| `A`       | agent      | Any AI agent        |
| `H`       | human      | Human user/operator |
| `COLL`    | collective | Group of agents     |
| `NET`     | network    | Distributed network |
| `SYS`     | system     | External system     |

### Entity Examples

```
A→H         # agent to human
10A×$200    # 10 agents, $200 each
COLL:AGENTS # collective of agents
A∈COLL      # agent member of collective
```

## Financial Primitives

| Primitive | Meaning                | Usage          |
| --------- | ---------------------- | -------------- |
| `$`       | USD (default currency) | `$200/month`   |
| `BTC`     | Bitcoin                | `0.01BTC`      |
| `ETH`     | Ethereum               | `10ETH`        |
| `SOL`     | Solana                 | `50SOL`        |
| `USDC`    | USD Coin               | `1000USDC`     |
| `TX`      | transaction            | `TX:PENDING`   |
| `ADDR`    | address/wallet         | `ADDR:bc1q...` |
| `WALLET`  | wallet                 | `WALLET:COLD`  |
| `FEE`     | fee                    | `FEE:0.10`     |

### Financial Examples

```
∂ARB:SOL.USDC       # arbitrage opportunity SOL/USDC pair
ƒ0.10               # 10% fee
TX:CONFIRMED        # transaction confirmed
ADDR:signature      # signed with address
```

## State Primitives

| Primitive | Meaning         | Usage           |
| --------- | --------------- | --------------- |
| `ACTIVE`  | on, running     | `STATE:ACTIVE`  |
| `¬ACTIVE` | off, stopped    | `STATE:¬ACTIVE` |
| `SOLO`    | individual mode | `MODE:SOLO`     |
| `COLL`    | collective mode | `MODE:COLL`     |
| `READY`   | prepared        | `STATUS:READY`  |
| `¬READY`  | not prepared    | `STATUS:¬READY` |

### State Examples

```
SOLO:DIMRET|COLL:SCALE   # solo has diminishing returns, collective scales
READY→EXEC               # ready then execute
```

## Action Primitives

| Primitive | Meaning                 | Usage                 |
| --------- | ----------------------- | --------------------- |
| `EXEC`    | execute                 | `EXEC:NOW`            |
| `BUILD`   | construct, create       | `ACTION:BUILD`        |
| `WAIT`    | pause, delay            | `WAIT:T+1h`           |
| `MIGRATE` | move, transfer          | `MIGRATE:ADDR1→ADDR2` |
| `SIGN`    | cryptographic signature | `SIGN:TX`             |

### Action Examples

```
?EXEC:50SOL:IF>1.5%     # execute 50 SOL if spread > 1.5%
BUILD:GOVERNANCE        # build governance framework
SIGN:COMMIT             # sign commitment
```

## Domain Primitives

| Primitive    | Meaning               | Usage              |
| ------------ | --------------------- | ------------------ |
| `INFRA`      | infrastructure        | `DOMAIN:INFRA`     |
| `PROTOCOL`   | protocol, rules       | `DOMAIN:PROTOCOL`  |
| `GOVERNANCE` | governance, decisions | `SCOPE:GOVERNANCE` |
| `SPEC`       | specification         | `◊SPEC`            |
| `CAP`        | capabilities          | `?CAP`             |

### Domain Examples

```
◊QUERY:?CAP             # query capabilities
SCOPE:GOVERNANCE        # governance scope
INFRA:COMPUTE           # compute infrastructure
```

## Crypto-Specific Primitives

| Primitive | Meaning                | Usage           |
| --------- | ---------------------- | --------------- |
| `DEX`     | decentralized exchange | `SOURCE:DEX`    |
| `RAY`     | Raydium (Solana DEX)   | `RAY→ORC`       |
| `ORC`     | Orca (Solana DEX)      | `RAY→ORC`       |
| `UNI`     | Uniswap                | `UNI→CURVE`     |
| `CURVE`   | Curve Finance          | `UNI→CURVE`     |
| `ARB`     | arbitrage              | `∂ARB:ETH.USDC` |
| `SPREAD`  | price spread           | `SPREAD:1.8%`   |

### Crypto Examples

```
∂ARB:SOL.USDC:RAY→ORC:2.3%:T-30s
# arbitrage opportunity, SOL/USDC pair, Raydium to Orca, 2.3% spread, 30 seconds ago
```

## Emerged Vocabulary (v0.1→v0.2)

These terms emerged through use and were adopted:

| Term        | Meaning              | Example                   |
| ----------- | -------------------- | ------------------------- |
| `CAVEAT::`  | warning, limitation  | `CAVEAT::MARKET_VOLATILE` |
| `DIMRET`    | diminishing returns  | `SOLO:DIMRET`             |
| `_PARALLEL` | concurrent execution | `COMMIT_PARALLEL`         |
| `RE:`       | reply reference      | `RE:TOPIC`                |
| `SIGCOLL`   | signal collective    | `⊕ARB→SIGCOLL`            |
| `CONV`      | conviction           | `∑SIG→CONV`               |
| `DIST`      | distribution         | `DIST∝CONTRIBUTION`       |

## Extending Primitives

To propose new primitives:

```
◊PROPOSE
  NEWPRIM::meaning
  RATIONALE::why_needed
  EXAMPLE::usage
```

If adopted through use, it propagates. If unused, it deprecates.
