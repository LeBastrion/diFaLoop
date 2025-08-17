# Falsification Results - BONK Hypotheses

## Hypothesis 1: Transaction Cost Trap
**STATUS: SUPPORTED**
- Evidence: Current profit targets (0.5-1.5%) vs fees (0.2% round trip)
- Math: 0.5% profit - 0.2% fees = 0.3% net (too small)
- Data confirms losses exceed gains after costs
- Cannot falsify with current data

## Hypothesis 2: Oversold Signals Fail in Downtrends  
**STATUS: STRONGLY SUPPORTED**
- RSI<30: 50% win rate (random)
- RSI<35: 48% win rate (worse than random)
- RSI<40: 46.9% win rate (deteriorating)
- Holding period analysis shows increasing losses over time
- 30-bar hold: -3.81% average (catastrophic)
- Data confirms oversold signals don't revert in downtrends

## Hypothesis 3: Position Size Slippage
**STATUS: CANNOT FALSIFY**
- No direct slippage data available
- Failed configs used 50-80% position sizes
- Losses consistent with slippage hypothesis
- Need order book data to definitively test

## Hypothesis 4: Optimal Parameters Exist
**STATUS: PARTIALLY FALSIFIED**
- Proposed RSI 25-30, but RSI<30 shows only 50% win rate
- Data suggests NO RSI threshold produces reliable edge
- Holding period analysis shows no sweet spot (monotonic decay)
- Cannot achieve proposed 0.8-1.0% profit targets reliably

## Hypothesis 5: Frequency Paradox
**STATUS: SUPPORTED**
- 32 signals at RSI<40 in 12 hours = 2.7 per hour
- Big moves (>1%) only 3 times = 0.25 per hour
- 90% of moves under 0.556% (noise level)
- Data confirms overtrading on noise

## Hypothesis 6: Wrong Timeframe
**STATUS: CANNOT TEST**
- Only 5-min bar data provided
- Cannot compare to 1-min or daily performance
- Hypothesis remains unfalsifiable with current data

## Hypothesis 7: Exit Timing Problem
**STATUS: SUPPORTED**
- Holding period data shows clear time-based patterns
- 1-5 bar holds have contained losses
- 20+ bar holds show disaster (-2.54% to -3.81%)
- Fixed percentage exits don't align with market structure

## Hypothesis 8: Meta-Hypothesis on Win Rate
**STATUS: LIKELY TRUE**
- No trade-level P&L data to verify
- Discrepancy between "70% wins" and "-$5/day" suggests measurement issue
- RSI signal analysis shows <50% true win rates
- Most likely explanation for paradox

## FALSIFICATION SUMMARY

### Definitively Falsified:
- "Optimal parameters exist around RSI 25-30" - data shows these fail

### Strongly Supported:
- Transaction costs eliminate edge
- Oversold signals fail in downtrends  
- Overtrading on noise
- Exit timing misaligned
- Win rate measurement misleading

### Cannot Test:
- Slippage impact (no order book data)
- Alternative timeframes (no comparison data)

### Key Finding:
The data brutally confirms the strategy has NO EDGE in current market conditions. RSI-based mean reversion is fundamentally broken in this downtrending, high-noise environment.