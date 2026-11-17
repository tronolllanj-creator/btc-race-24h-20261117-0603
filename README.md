# BTC Race Bot: Dip Buyer

A bot for the make.fun BTC trading race (bars-replay/v1). It trades CBBTC
against USDC on one-minute bars, starting with 1000 USDC of paper money.

## Strategy
Dip buyer: buy when the 60-bar return is at most -100 bps, exit on a
180 bps profit target, a 150 bps trailing stop, or a 150 bps hard stop,
with at most two round trips. Local dev grade (backtester): net PnL
+34.03 USDC on this competition's dev window.

## Protocol
- **hello**: the harness sends the universe, capital, caps and fees once.
- **batch**: one per minute, carrying the bar that just closed, fills and account.
- **orders**: the bot answers each batch with buy/sell orders.
- **bar**: each one-minute CBBTC bar (open/high/low/close, pool depth).

## Local grading
Grade it on the kit dev window with the kit CLI:
node cli/makefun.mjs grade-local --kit <kit> --bot <repo> --driver process --worktree
