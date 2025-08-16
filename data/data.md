# BONK Market Dataset for Strategy Optimization

## 🎯 THE QUESTION

**What trading bot architecture would be able to predictably accumulate capital trading the BONK/USDC pair given the market conditions shown in the 12-hour dataset below?**

## 📖 CONTEXT & BACKGROUND

### The Bot's Current Strategy
Our trading bot operates on the BONK/USDC pair using a **mean reversion strategy** with the following logic:
1. **Entry**: Waits for oversold conditions (RSI < threshold) combined with other indicators (Bollinger Bands, momentum)
2. **Exit**: Takes profit at X% gain or stops loss at -Y% loss
3. **Position Sizing**: Uses Z% of available capital per trade
4. **Trade Frequency**: Currently executing ~10 trades/hour (TOO MANY - causing losses)

### Current Problem
The bot is **losing money** (-$5/day) despite a 70% win rate because:
- Profit targets (0.5-1.5%) are too small relative to fees/slippage (0.2%)
- Over-trading on noise instead of real signals
- Position sizes too large (50-80%) causing slippage

### Adjustable Parameters
```
ENTRY CONDITIONS:
- rsi_threshold: When RSI drops below this, consider entry (range: 20-45)
- oversold_score: How many indicators must align (range: 1-6)
- min_momentum: Minimum price momentum to enter (range: -0.01 to 0.01)

EXIT CONDITIONS:
- profit_target: Exit when position gains X% (range: 0.5% to 3.0%)
- stop_loss: Exit when position loses Y% (range: -0.3% to -2.0%)
- min_holding_bars: Don't exit before N 5-min bars (range: 0-30)
- max_holding_bars: Force exit after N bars (range: 20-100)

RISK MANAGEMENT:
- max_exposure: Max % of capital per trade (range: 10% to 80%)
- cooldown_bars: Wait N bars between trades (range: 0-20)
- risk_mode: STANDARD (6% risk) or TURBO (9% risk)
```

### Sub-Questions to Answer
To solve this puzzle, we need to determine:
1. **Entry**: What RSI level actually produces bounces in THIS market?
2. **Exits**: What profit/stop targets are realistic given current volatility?
3. **Frequency**: How many QUALITY trades exist per hour (not noise)?
4. **Sizing**: What position size avoids excessive slippage?
5. **Trend Filter**: Should we avoid trading entirely in downtrends?

### Recent Failed Configurations
These settings have been tried and FAILED:
```
Config 1 (Original): RSI<40, Profit: 0.5%, Stop: -0.3%, Size: 80%
Result: Churning positions, -$5/day loss

Config 2 (First Fix): RSI<35, Profit: 1.0%, Stop: -0.6%, Size: 80%  
Result: Still losing, slippage eating profits

Config 3 (Current): RSI<35, Profit: 1.5%, Stop: -0.8%, Size: 50%
Result: Too few trades, missing opportunities
```

---

## 📊 MARKET OVERVIEW
- **Symbol**: BONK/USDT
- **Current Price**: $0.00002372
- **12h Range**: $0.00002275 - $0.00002436 (7.1%)
- **12h Trend**: DOWN
- **Data Period**: 12 hours (144 bars)
- **Generated**: 2025-08-16T02:25:24.176142

## 📈 VOLATILITY PROFILE
| Timeframe | Volatility % | Implication |
|-----------|-------------|-------------|
| 5-min | 0.402% | Noise level for stops |
| 15-min | 0.632% | Short-term targets |
| 1-hour | 1.313% | Swing trade targets |

## 🎲 PRICE MOVE DISTRIBUTION (5-min bars)
| Percentile | Move Size | Meaning |
|------------|-----------|----------|
| 50% (median) | 0.216% | Typical move |
| 75% | 0.375% | Larger move |
| 90% | 0.556% | Big move |
| 95% | 0.819% | Extreme move |

## 🔔 RSI SIGNAL PERFORMANCE (5-min)
| Entry Signal | Count/12h | Avg Return | Win Rate |
|-------------|-----------|------------|----------|
| RSI_30 | 12 | -0.06% | 50.0% |
| RSI_35 | 25 | -0.06% | 48.0% |
| RSI_40 | 32 | -0.08% | 46.9% |

## ⏱️ OPTIMAL HOLDING ANALYSIS (Entry: RSI<40)
| Hold Time | Avg Return | Win Rate | Max Gain | Max Loss |
|-----------|------------|----------|----------|----------|
| 1 bars (5min) | -0.10% | 45.2% | 0.87% | -0.91% |
| 5 bars (25min) | -0.56% | 33.3% | 0.85% | -2.90% |
| 10 bars (50min) | -1.32% | 31.8% | 0.99% | -3.80% |
| 20 bars (100min) | -2.54% | 0.0% | -0.66% | -3.99% |
| 30 bars (150min) | -3.81% | 0.0% | -3.81% | -3.82% |

## 📊 HOURLY SUMMARY (12 hours)
```
Hour | Open       | High       | Low        | Close      | Chg%  | RSI | Vol
-----|------------|------------|------------|------------|-------|-----|-----
13:00 | 0.00002426 | 0.00002436 | 0.00002387 | 0.00002391 | -1.44% | 50 | 1.0x
14:00 | 0.00002385 | 0.00002395 | 0.00002292 | 0.00002301 | -3.52% | 31 | 1.7x
15:00 | 0.00002320 | 0.00002332 | 0.00002275 | 0.00002291 | -1.25% | 29 | 0.9x
16:00 | 0.00002312 | 0.00002354 | 0.00002282 | 0.00002327 | +0.65% | 51 | 0.7x
17:00 | 0.00002314 | 0.00002338 | 0.00002307 | 0.00002311 | -0.13% | 58 | 0.5x
18:00 | 0.00002320 | 0.00002325 | 0.00002290 | 0.00002302 | -0.78% | 41 | 0.8x
19:00 | 0.00002303 | 0.00002316 | 0.00002287 | 0.00002313 | +0.43% | 47 | 0.6x
20:00 | 0.00002313 | 0.00002337 | 0.00002307 | 0.00002330 | +0.73% | 69 | 1.1x
21:00 | 0.00002331 | 0.00002363 | 0.00002324 | 0.00002362 | +1.33% | 72 | 0.9x
22:00 | 0.00002364 | 0.00002392 | 0.00002344 | 0.00002356 | -0.34% | 75 | 1.4x
23:00 | 0.00002356 | 0.00002376 | 0.00002349 | 0.00002363 | +0.30% | 47 | 0.6x
00:00 | 0.00002372 | 0.00002386 | 0.00002362 | 0.00002372 | +0.00% | 63 | 0.9x
```

## 📜 DETAILED 5-MIN PRICE ACTION (Full 12 hours)
```
Time |    Price    | Chg% | Range% | RSI | Vol | Signal
-----|-------------|------|--------|-----|-----|--------
13:30 | 0.00002426 | +0.00 | 0.70% |  50 | 1.0x |     
13:45 | 0.00002403 | -0.25 | 0.62% |  50 | 1.0x |     
14:00 | 0.00002416 | +0.37 | 1.38% |  50 | 1.0x |     
14:15 | 0.00002406 | +0.17 | 0.50% |  50 | 1.0x |     
14:30 | 0.00002385 | -0.25 | 0.76% |  50 | 1.0x |     
14:45 | 0.00002380 | -0.13 | 0.89% |  32 | 1.0x |     
15:00 | 0.00002371 | -0.17 | 0.68% |  38 | 1.0x |     
15:05 | 0.00002361 | -0.42 | 0.85% |  27 | 1.7x | OS! 
15:10 | 0.00002366 | +0.21 | 0.55% |  24 | 0.8x | OS! 
15:15 | 0.00002371 | +0.21 | 0.63% |  30 | 2.1x | VOL 
15:20 | 0.00002352 | -0.80 | 1.37% |  27 | 2.2x | OS! 
15:25 | 0.00002301 | -2.17 | 2.66% |  16 | 6.3x | OS! 
15:30 | 0.00002320 | +0.83 | 1.00% |  28 | 1.4x | OS! 
15:35 | 0.00002315 | -0.22 | 0.73% |  27 | 0.9x | OS! 
15:40 | 0.00002294 | -0.91 | 1.31% |  25 | 1.7x | OS! 
15:45 | 0.00002287 | -0.31 | 0.88% |  21 | 1.9x | OS! 
15:50 | 0.00002313 | +1.14 | 1.18% |  32 | 1.2x | BIG 
16:00 | 0.00002288 | -0.69 | 0.92% |  31 | 0.7x |     
16:05 | 0.00002279 | -0.39 | 0.70% |  27 | 0.9x | OS! 
16:15 | 0.00002289 | +0.09 | 0.75% |  32 | 0.5x |     
16:30 | 0.00002312 | +0.92 | 1.14% |  41 | 0.5x |     
16:45 | 0.00002311 | +0.57 | 0.74% |  49 | 0.3x |     
17:00 | 0.00002299 | -0.39 | 0.52% |  44 | 0.3x |     
17:15 | 0.00002290 | -0.09 | 0.35% |  55 | 0.4x |     
17:25 | 0.00002327 | +1.62 | 2.84% |  65 | 4.8x | BIG 
17:30 | 0.00002314 | -0.56 | 0.91% |  56 | 1.2x |     
17:45 | 0.00002329 | -0.17 | 0.34% |  60 | 0.9x |     
18:00 | 0.00002322 | -0.13 | 0.60% |  55 | 0.7x |     
18:15 | 0.00002311 | -0.04 | 0.26% |  54 | 0.2x |     
18:30 | 0.00002320 | +0.39 | 0.78% |  63 | 0.8x |     
18:45 | 0.00002311 | +0.00 | 0.56% |  29 | 0.7x | OS! 
18:55 | 0.00002298 | -0.91 | 1.35% |  30 | 3.0x | VOL 
19:00 | 0.00002294 | -0.17 | 0.44% |  32 | 0.8x |     
19:15 | 0.00002311 | +0.04 | 0.48% |  49 | 1.4x |     
19:30 | 0.00002303 | +0.04 | 0.39% |  45 | 0.4x |     
19:45 | 0.00002298 | -0.13 | 0.35% |  40 | 0.3x |     
20:00 | 0.00002303 | +0.35 | 0.74% |  40 | 2.2x | VOL 
20:15 | 0.00002309 | +0.00 | 0.22% |  60 | 0.5x |     
20:30 | 0.00002313 | +0.00 | 0.52% |  68 | 0.6x |     
20:45 | 0.00002309 | +0.00 | 0.30% |  62 | 1.1x |     
20:55 | 0.00002326 | +0.43 | 0.47% |  77 | 1.0x | OB! 
21:00 | 0.00002330 | +0.17 | 0.56% |  81 | 2.9x | OB! 
21:05 | 0.00002324 | -0.26 | 0.39% |  75 | 1.7x | OB! 
21:15 | 0.00002323 | +0.04 | 0.52% |  67 | 1.5x |     
21:30 | 0.00002331 | +0.04 | 0.26% |  75 | 0.8x | OB! 
21:45 | 0.00002334 | +0.30 | 0.30% |  67 | 0.3x |     
21:50 | 0.00002337 | +0.13 | 0.21% |  73 | 0.1x | OB! 
21:55 | 0.00002345 | +0.34 | 0.39% |  76 | 0.8x | OB! 
22:00 | 0.00002346 | +0.04 | 0.47% |  73 | 1.7x | OB! 
22:15 | 0.00002355 | +0.34 | 0.43% |  79 | 0.9x | OB! 
22:20 | 0.00002359 | +0.17 | 0.30% |  84 | 0.8x | OB! 
22:25 | 0.00002362 | +0.13 | 0.30% |  84 | 2.1x | OB! 
22:30 | 0.00002364 | +0.08 | 0.17% |  82 | 1.2x | OB! 
22:35 | 0.00002369 | +0.21 | 0.30% |  87 | 1.5x | OB! 
22:40 | 0.00002367 | -0.08 | 0.17% |  83 | 1.1x | OB! 
22:45 | 0.00002370 | +0.13 | 0.30% |  96 | 1.3x | OB! 
22:50 | 0.00002379 | +0.38 | 0.46% |  96 | 1.3x | OB! 
22:55 | 0.00002384 | +0.21 | 0.46% |  96 | 1.5x | OB! 
23:00 | 0.00002370 | -0.59 | 0.93% |  75 | 3.0x | OB! 
23:05 | 0.00002362 | -0.34 | 0.68% |  63 | 2.2x | VOL 
23:15 | 0.00002354 | -0.25 | 0.43% |  56 | 1.1x |     
23:30 | 0.00002356 | +0.00 | 0.30% |  48 | 0.5x |     
23:45 | 0.00002356 | +0.13 | 0.34% |  42 | 0.3x |     
00:00 | 0.00002364 | +0.04 | 0.34% |  40 | 0.7x |     
00:15 | 0.00002365 | -0.34 | 0.64% |  52 | 1.0x |     
00:30 | 0.00002372 | +0.38 | 0.47% |  69 | 0.4x |     
00:45 | 0.00002382 | +0.04 | 0.29% |  67 | 1.3x |     
00:50 | 0.00002378 | -0.17 | 0.25% |  73 | 0.8x | OB! 
01:00 | 0.00002374 | -0.08 | 0.21% |  65 | 1.1x |     
01:15 | 0.00002368 | -0.42 | 0.38% |  50 | 0.6x |     
```

## 🔍 PATTERN ANALYSIS
- **Oversold Bounces**: 2 successful vs 2 failed
- **Big Moves (>1%)**: 3 times in 12h
- **Consolidation Periods**: 33 detected
- **Trend**: DOWNTREND

## 💡 STRATEGY RECOMMENDATIONS
Based on this 12-hour analysis:

### ⚠️ DOWNTREND DETECTED - CAUTION
1. **Avoid Mean Reversion**: RSI bounces failing (48% win rate)
2. **Wait for Trend Reversal**: Don't fight the trend
3. **If Trading**: Use tighter stops (-0.5%) and quicker profits (0.8%)

### 📊 OPTIMAL PARAMETERS (Current Market)
- **Entry Signal**: RSI < 30
- **Profit Target**: 0.56% (90th percentile move)
- **Stop Loss**: -0.38% (beyond noise)
- **Min Hold**: 5 bars
- **Position Size**: 30% of capital

### 🎯 CURRENT ACTION
**STAY CASH** - Downtrend + neutral RSI = no edge

## 📋 REQUIRED OUTPUT FORMAT

Please analyze this data and provide SPECIFIC parameter recommendations:

```python
# ENTRY CONDITIONS
rsi_threshold = ???  # Below what RSI to consider entry
oversold_score = ???  # How many indicators must confirm (1-6)
min_momentum = ???  # Minimum price momentum % to enter

# EXIT CONDITIONS  
profit_target = ???  # Take profit at X% gain
stop_loss = ???  # Stop loss at -Y% loss
min_holding_bars = ???  # Don't exit before N bars
max_holding_bars = ???  # Force exit after N bars

# RISK MANAGEMENT
max_exposure = ???  # % of capital per trade
cooldown_bars = ???  # Bars to wait between trades
trade_in_downtrend = ???  # True/False

# EXPECTED PERFORMANCE
expected_trades_per_day = ???
expected_win_rate = ???
expected_avg_profit = ???
expected_daily_return = ???
```

### Additional Considerations
1. **Fees**: Each trade costs ~0.1% in fees/slippage (0.2% round trip)
2. **Volatility**: Current 5-min volatility is 0.40% (see data above)
3. **Trend**: Market is in DOWNTREND over last 12 hours
4. **RSI Performance**: RSI<35 signals showing only 48% win rate
5. **Goal**: Achieve consistent 2-4% daily returns with <30% drawdown
