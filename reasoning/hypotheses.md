# Hypotheses - BONK Mean Reversion Failure

## Hypothesis 1: The Transaction Cost Trap
**Statement**: The bot achieves 70% directional accuracy but loses money because average wins (0.5-1.5%) are smaller than losses plus transaction costs (0.2% per round trip).

**Predictions**:
- Average winning trade: <1.0% after costs
- Average losing trade: >1.5% after costs
- Break-even requires 1.5% profit target minimum
- Current targets create negative expectancy despite high win rate

**Falsification**: Show profitable periods with sub-1% profit targets

---

## Hypothesis 2: Oversold Signals Don't Mean Revert in Downtrends
**Statement**: RSI oversold signals in downtrends lead to continued decline, not bounces. The 48% win rate at RSI<35 confirms this.

**Predictions**:
- RSI<30 in downtrend: <40% win rate
- Holding longer makes losses worse (confirmed: -3.81% at 30 bars)
- Mean reversion only works in ranging markets
- Current market structure (downtrend) invalidates strategy

**Falsification**: Find profitable oversold signals during the downtrend period

---

## Hypothesis 3: Position Size Creates Slippage Death Spiral
**Statement**: 50-80% position sizes cause market impact that degrades entry/exit prices by 0.1-0.3%, eliminating theoretical edge.

**Predictions**:
- Slippage increases non-linearly above 30% position size
- Actual fills 0.2% worse than signal prices
- Reducing to 10-20% positions would restore profitability
- Large positions signal intent, attracting adverse selection

**Falsification**: Demonstrate no correlation between position size and slippage

---

## Hypothesis 4: Optimal Parameters for Current Market
**Statement**: Given the data patterns, profitable parameters exist but are far from current settings.

**Predictions**:
- Optimal RSI threshold: 25-30 (not 35-40)
- Optimal profit target: 0.8-1.0% (matching 95th percentile moves)
- Optimal stop loss: -0.5% (just beyond noise)
- Optimal position size: 20-30% max
- Optimal holding: 3-5 bars maximum

**Falsification**: Show these parameters also fail in backtesting

---

## Hypothesis 5: The Frequency Paradox
**Statement**: The bot overtrades, taking 10+ trades/hour when only 2-3 quality setups exist, diluting edge with noise trades.

**Predictions**:
- 80% of trades are noise (move <0.4%)
- Filtering for "oversold + volume spike" reduces trades 70%
- Quality signals occur 2-3 times per hour maximum
- Cooldown period of 20+ bars improves performance

**Falsification**: High-frequency trades show similar win rates to low-frequency

---

## Hypothesis 6: Wrong Timeframe for Strategy
**Statement**: Mean reversion works on 1-min bars (noise) or daily bars (swings), but 5-min bars capture neither edge.

**Predictions**:
- 1-min bars would show 55%+ win rate
- Daily bars would show 60%+ win rate
- 5-min bars in the "dead zone" of no edge
- Strategy can't be profitable on 5-min regardless of parameters

**Falsification**: Find any profitable mean reversion on 5-min bars

---

## Hypothesis 7: Exit Timing Destroys Edge
**Statement**: Fixed percentage exits ignore market structure. Exits should be time-based or volatility-adjusted.

**Predictions**:
- Time-based exits (e.g., 5 bars) outperform percentage
- Volatility-scaled exits improve risk/reward
- Current fixed exits cut winners, let losers run
- Dynamic exits based on momentum would be profitable

**Falsification**: Fixed percentage exits outperform alternatives

---

## Hypothesis 8: The Meta-Hypothesis
**Statement**: The "70% win rate" is measuring something other than profitable trades - perhaps directional accuracy without considering magnitude.

**Predictions**:
- Win rate counts any positive return as "win"
- Actual profit-weighted win rate is <50%
- Small wins counted equally to large losses
- Proper accounting shows strategy never had edge

**Falsification**: Detailed trade logs show 70% of trades are meaningfully profitable