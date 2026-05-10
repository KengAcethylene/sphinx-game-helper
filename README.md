# sphinx-game-helper

Binary-search assistant for the TalesRunner Sphinx number-guessing event (range 1–9999, max 14 guesses per round).

English · [ภาษาไทย](README.th.md)

**Live**: <https://kengacethylene.github.io/sphinx-game-helper/>

## Open it

Visit the live URL above, or double-click `index.html` locally.

## How to use

1. The big number is the next guess (binary-search optimal). Type it into the game.
2. Tap a button based on the game's response:
   - **Lower** — answer is below your guess
   - **Correct** — you found it (auto-saves to history, resets after 2s)
   - **Higher** — answer is above your guess
3. The next guess updates automatically.

## Manual override

Click the big number to edit it. Useful for trying lucky numbers (e.g. 1004, 7777) on the first guess. Click the pill below to snap back to the binary-search suggestion.

## Jitter mode

Optional toggle at the bottom of the page. When enabled, the suggested number gets a random ±3% offset (of the current range) for the first 5 guesses, so different rounds traverse different paths instead of always 5000 → 2500/7500 → … This slightly increases the risk of running out of guesses on hard rounds, but makes your guess pattern less repetitive. The toggle state persists across sessions.

## Keyboard shortcuts

(when the number isn't focused)

| Key | Action |
|---|---|
| `J` / `←` | Lower |
| `K` | Correct |
| `L` / `→` | Higher |
| `R` | Reset round |
| `Enter` (in input) | Submit as Correct |
| `Esc` (in input) | Blur input |

## Answer history

Every win is saved to `localStorage` with timestamp, answer, and guess count. View it under "Past Wins" at the bottom of the page. **Export CSV** downloads the full log for analysis (e.g., to check whether the answer distribution is actually uniform).

## Round persistence

The current in-progress round (range, history, guess count) is saved to `localStorage` on every action and restored on page reload — so accidentally closing the tab or refreshing mid-round doesn't lose your progress. Hit **Reset** (or `R`) to start fresh.

## Strategy notes

- Worst case: 14 guesses (information-theoretic minimum for 9999 numbers).
- Average with binary search: ~12.3 guesses against a uniform random target.
- You cannot beat this average if the target is truly uniform random — the only strategy is volume, and low-guess rounds are a lottery.
- Per round: P(finish ≤ k) = (2ᵏ − 1) / 9999. A ≤7-guess round happens ~1.3% of the time.

### Daily budget

Each daily quest grants 50 keys → **50 rounds/day** is the hard ceiling. Across those 50 rounds:

| At least one round in ≤ k guesses | Probability per day |
|---|---|
| ≤ 4 (jackpot tier) | ~7% (≈ 1 every 2 weeks) |
| ≤ 7 (top tier) | ~47% (about every other day) |
| ≤ 10 | ~99.5% (nearly every day) |

Formula: `P = 1 − (1 − (2ᵏ−1)/9999)⁵⁰`. Run all 50 keys daily; the variance does the work.

## License

MIT — see [LICENSE](LICENSE).
