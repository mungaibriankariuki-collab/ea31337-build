# Compile fixes

`compile-fixes.patch` makes EA31337 (commit 9b9bd38 and its submodules) compile with the current MetaEditor.
It changes no trading logic. Each fix answers a rule the newer MQL5 compiler enforces:

- copying a base struct into a derived one (`THIS_REF = base`) is no longer allowed: fields are copied one by one
  (DateTimeEntry, MqlTradeRequestProxy, MqlTradeResultProxy, Retracement_BarOHLC)
- `unsigned int&` parameters need `unsigned int` variables (dictionary `position`)
- iterators returned by `Begin()` as the base type need a converting constructor (DictIterator, DictObjectIterator)
- `Indicator<TS>::SetParams` takes its own params type instead of the base
- a static `CheckPattern(enum, bars)` hides the inherited `CheckPattern(flags)`, so the pattern structs re-expose it
- `+` is not allowed in resource paths: `TMA+CG_mladen_NRP` is compiled as `TMA_CG_mladen_NRP`
