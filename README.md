# EA31337 for MT5 (compiled)

Compiled `.ex5` builds of [EA31337](https://github.com/EA31337/EA31337), the open-source multi-strategy Forex
robot, made from upstream commit `9b9bd38` (master, September 2024). GitHub Actions checks out EA31337 with all its
submodules, applies `patches/compile-fixes.patch` and compiles it with the current MetaEditor.

The upstream code no longer compiles on current MetaEditor builds (the newer MQL5 compiler is stricter), and the old
MetaEditor upstream used is no longer available. The patch only fixes compile errors and changes no trading logic;
[`patches/README.md`](patches/README.md) lists each fix.

## Editions

| File | Edition |
|---|---|
| `EA31337-Lite.ex5` | One strategy per timeframe (M1-H12), simple inputs |
| `EA31337-Advanced.ex5` | Adds signal filters, account tasks and global close loss/profit |
| `EA31337-Rider.ex5` | Advanced with trend-riding stops (Envelopes on H8); M30 runs Meta Martingale by default |
| `EA31337-Elite.ex5` | One main strategy (MA Cross) across 8 timeframes |

Each build is compiled with upstream's `__input__` mode (every strategy parameter is visible as an input) and
`__resource__` mode (the custom indicators are embedded, so nothing else needs installing).

## Install

Download the zip from [Releases](../../releases), copy the `.ex5` files to `MQL5\Experts` in your terminal's data
folder (File -> Open Data Folder), refresh the Navigator and attach one EA to a chart.

The default settings were optimised by upstream for EURUSD. Backtest and demo-test before trading other symbols
or a live account. See the [EA31337 wiki](https://github.com/EA31337/EA31337/wiki) for the inputs.

## License

EA31337 is GPL-3.0 (`LICENSE`). Source: https://github.com/EA31337/EA31337/tree/9b9bd38c4e49dd6916f4fe3936e50e97fca7a692
