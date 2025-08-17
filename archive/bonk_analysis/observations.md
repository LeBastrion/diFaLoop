# Observations - BONK Market Data

## Data Structure Observations
- Dataset contains 144 5-minute bars covering 12 hours
- Price range: $0.00002275 to $0.00002436 (7.1% range)
- Current price: $0.00002372
- Overall trend: DOWN across the 12-hour period

## RSI Signal Performance Patterns
### Entry Threshold Analysis (5-min bars)
- RSI < 30: 12 occurrences, -0.06% avg return, 50.0% win rate
- RSI < 35: 25 occurrences, -0.06% avg return, 48.0% win rate  
- RSI < 40: 32 occurrences, -0.08% avg return, 46.9% win rate
- Pattern: More frequent signals correlate with worse performance

## Holding Period Return Degradation
### From RSI < 40 Entry
- 1 bar (5min): -0.10% avg, 45.2% win rate
- 5 bars (25min): -0.56% avg, 33.3% win rate
- 10 bars (50min): -1.32% avg, 31.8% win rate
- 20 bars (100min): -2.54% avg, 0.0% win rate
- 30 bars (150min): -3.81% avg, 0.0% win rate
- Pattern: Monotonic degradation with holding time

## Price Move Distribution (5-min)
- 50th percentile: 0.216% (typical move)
- 75th percentile: 0.375% (larger move)
- 90th percentile: 0.556% (big move)
- 95th percentile: 0.819% (extreme move)

## Volatility Structure
- 5-min volatility: 0.402%
- 15-min volatility: 0.632%
- 1-hour volatility: 1.313%
- Pattern: Sub-linear scaling with timeframe

## Failed Configuration Documentation
- Config 1: RSI<40, Profit 0.5%, Stop -0.3%, Size 80% → -$5/day
- Config 2: RSI<35, Profit 1.0%, Stop -0.6%, Size 80% → Still losing
- Config 3: RSI<35, Profit 1.5%, Stop -0.8%, Size 50% → Too few trades

## Market Microstructure
- Oversold signals (RSI<30): 15 instances marked "OS!"
- Overbought signals (RSI>70): 17 instances marked "OB!"
- Volume spikes (>2x avg): 8 instances marked "VOL"
- Big moves (>1%): 3 instances marked "BIG"

## Temporal Patterns
- Hour 14-15: Sharp decline, high oversold count
- Hour 20-22: Recovery phase, high overbought count
- Hour 15: Lowest point ($0.00002275)
- Hour 22: Highest RSI readings (96)

## Key Anomaly
- Bot claims 70% win rate but loses $5/day
- Win rate measurements don't align with profitability
- Transaction costs (0.2% round trip) not reflected in simple win rate