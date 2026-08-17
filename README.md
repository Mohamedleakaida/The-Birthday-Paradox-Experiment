# Birthday Paradox

A small Python experiment exploring the classic **birthday paradox**: given
a group of people with birthdays drawn uniformly at random from 365 days,
what can we say about when the first shared birthday (collision) is likely
to occur?

## Overview

This project computes and visualizes two related probability functions:

- **`Q(n)`** — the probability that the first `n` people all have distinct
  birthdays.
- **`f(k)`** — the probability that the `k`-th person is exactly the one
  who causes the **first** collision (i.e. the first `k-1` people all have
  distinct birthdays, and the `k`-th person shares a birthday with one of
  them).

`f(k)` is a full probability distribution over the rank of the first
collision — unlike the commonly cited "23 people" result, which only
answers when the *cumulative* probability of a collision crosses 50%.

## Formulas

\`\`\`
Q(n) = (365/365) × (364/365) × (363/365) × ... × ((365-n+1)/365)

f(k) = Q(k-1) × (k-1)/365
\`\`\`

## Results

- `f(k)` peaks around **k = 20**, the single most likely rank for the first
  collision to occur.
- The cumulative probability `1 - Q(k)` crosses 50% at **k = 23**, the
  classic birthday paradox threshold.

## Usage

\`\`\`bash
pip install matplotlib
python birthday_paradox.py
\`\`\`

This generates a plot of `f(k)` for `k` in `[2, 50]`.

\`\`\`python
from birthday_paradox import Q, f

print(Q(23))       # ~0.4927 -> probability of no collision among 23 people
print(1 - Q(23))   # ~0.5073 -> probability a collision already happened
print(f(20))        # ~0.0323 -> probability the collision happens exactly at person 20
\`\`\`

## Files

| File | Description |
|---|---|
| `birthday_paradox.py` | Core functions (`Q`, `f`) and plotting script |

## Requirements

- Python 3
- `matplotlib`

## License

MIT
