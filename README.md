# sphinx-game-helper

Binary-search assistant for the TalesRunner Sphinx number-guessing event (range 1–9999, max 14 guesses per round).

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

## Strategy notes

- Worst case: 14 guesses (information-theoretic minimum for 9999 numbers).
- Average with binary search: ~12.3 guesses against a uniform random target.
- You cannot beat this average if the target is truly uniform random — the strategy is to maximize **rounds per hour** and treat low-guess rounds as a lottery.
- P(finish ≤ k) = (2ᵏ − 1) / 9999. So a ≤7-guess round happens ~1.3% of the time (~1 in 79 rounds).

## License

MIT — see [LICENSE](LICENSE).
