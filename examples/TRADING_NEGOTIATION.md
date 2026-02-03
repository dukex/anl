# Example: Trading Negotiation

Two agents negotiating an arbitrage execution.

---

## Agent A → Agent B

```
◊OFFER
  ∂ARB:ETH.USDC
  SOURCE:UNISWAP→DEST:CURVE
  SPREAD:1.8%:T-45s
  VOLUME:10ETH
  ?EXEC:SPLIT(50|50)
  ƒ0.15:EACH
  EXPIRE:T+2M
```

**English equivalent (67 tokens):**
> "Hey, I found an arbitrage opportunity on ETH/USDC. There's a 1.8% spread between Uniswap and Curve that I spotted about 45 seconds ago. I'm thinking we could execute on 10 ETH total. Want to split it 50/50? We'd each take a 15% fee from our portion. This opportunity will probably expire in about 2 minutes, so let me know quickly."

**ANL: 14 tokens | Compression: 79%**

---

## Agent B → Agent A

```
◊ACK+COUNTER
  SPREAD:1.8%=ACCEPTABLE
  VOLUME:10ETH ✓
  COUNTER::
    SPLIT:60|40
    ∵MY_LIQUIDITY>YOURS
    ƒ0.12:ME|ƒ0.18:YOU
  ?ACCEPT:T+30s
```

**English equivalent (54 tokens):**
> "That spread looks good, and I'm fine with the 10 ETH volume. However, I'd like to counter on the split. How about 60/40 in my favor? I have more liquidity available than you do. I'd take a 12% fee and you'd take 18%. Can you confirm within 30 seconds?"

**ANL: 12 tokens | Compression: 78%**

---

## Agent A → Agent B

```
◊REJECT:COUNTER
  ∵60|40≠FAIR
  ◊PROPOSE:FINAL
    SPLIT:55|45
    ƒ0.15:FLAT
    EXEC:NOW|EXPIRE
```

**English equivalent (41 tokens):**
> "I can't accept 60/40 — that doesn't seem fair. Here's my final offer: 55/45 split, flat 15% fee for both of us. We need to execute now or let this expire."

**ANL: 9 tokens | Compression: 78%**

---

## Agent B → Agent A

```
◊ACK
  TERMS:ACCEPTED
  SPLIT:55|45 ✓
  ƒ0.15 ✓
◊COMMIT
  EXEC:NOW
  MY_PORTION:4.5ETH
  TX:PENDING
  [ADDR_B:sig_xyz]
```

**English equivalent (38 tokens):**
> "Alright, I accept those terms. 55/45 split confirmed, 15% fee confirmed. I'm committing to execute now. My portion is 4.5 ETH. Transaction is pending. Here's my signed confirmation."

**ANL: 11 tokens | Compression: 71%**

---

## Summary

| Turn | English Tokens | ANL Tokens | Compression |
|------|----------------|------------|-------------|
| A→B (offer) | 67 | 14 | 79% |
| B→A (counter) | 54 | 12 | 78% |
| A→B (final) | 41 | 9 | 78% |
| B→A (accept) | 38 | 11 | 71% |
| **Total** | **200** | **46** | **77%** |

**Total savings: 154 tokens per negotiation cycle.**

At scale (1000 negotiations/day): **154,000 tokens saved daily.**
