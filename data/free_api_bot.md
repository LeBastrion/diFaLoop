# The Question

**What is the bot architecture that will accumulate crypto most rapidly and predictably using only free APIs?**

## Constraints
- Must use ONLY free APIs (no paid subscriptions)
- Can use any LLM (free or paid)
- Elegance and simplicity are positive traits
- No inherent bias toward LLM vs non-LLM architectures

## Available Free APIs in Crypto

### Price & Market Data
1. **CoinGecko Free Tier**
   - Rate limit: 10-30 calls/minute
   - Data: Prices, market cap, volume, historical data
   - Coverage: 10,000+ tokens
   - Delay: 1-5 minutes

2. **CoinMarketCap Free Tier**
   - Rate limit: 333 calls/day (~13/hour)
   - Data: Similar to CoinGecko
   - Coverage: 8,000+ tokens
   - Delay: 1-5 minutes

3. **Binance Public API**
   - Rate limit: 1200 requests/minute
   - Data: Real-time prices, order book, trades
   - Coverage: Binance listed tokens only
   - Delay: <1 second

4. **CoinBase Public API**
   - Rate limit: 10 requests/second
   - Data: Prices, order book, historical
   - Coverage: Coinbase listed tokens
   - Delay: <1 second

### Blockchain Data
1. **Etherscan Free API**
   - Rate limit: 5 calls/second
   - Data: Transactions, balances, contracts
   - Coverage: Ethereum mainnet
   - Delay: 1-2 blocks

2. **BSCScan Free API**
   - Rate limit: 5 calls/second
   - Data: BSC transactions, tokens
   - Coverage: Binance Smart Chain
   - Delay: 1-2 blocks

3. **Public RPC Endpoints**
   - Ethereum: Multiple free endpoints
   - BSC: Multiple free endpoints
   - Polygon: Multiple free endpoints
   - Rate limits: Vary, typically 10-100 req/sec
   - Reliability: 70-90% uptime

### Social & Sentiment
1. **Twitter API v2 Free**
   - Rate limit: 500k tweets/month read
   - Data: Tweet content, metrics
   - Delay: Real-time

2. **Reddit API**
   - Rate limit: 60 requests/minute
   - Data: Posts, comments, scores
   - Coverage: All crypto subreddits
   - Delay: Real-time

3. **CryptoCompare Free**
   - Rate limit: 100k calls/month
   - Data: Social stats, news
   - Coverage: Major tokens
   - Delay: 5-15 minutes

### DeFi & DEX Data
1. **TheGraph Protocol**
   - Rate limit: Varies by subgraph
   - Data: DEX trades, liquidity, TVL
   - Coverage: Major DeFi protocols
   - Delay: 1-5 minutes

2. **DexScreener API**
   - Rate limit: Unknown (generous)
   - Data: DEX prices, new pairs
   - Coverage: 30+ chains
   - Delay: 1-2 minutes

3. **GeckoTerminal API**
   - Rate limit: 30 calls/minute
   - Data: DEX pools, trades
   - Coverage: 100+ DEXs
   - Delay: 1-5 minutes

### On-chain Analytics
1. **Glassnode Free**
   - Rate limit: 10 calls/minute
   - Data: Basic on-chain metrics
   - Coverage: BTC, ETH mainly
   - Delay: 1 hour

2. **Santiment Free**
   - Rate limit: Limited
   - Data: Basic metrics
   - Coverage: Top 50 tokens
   - Delay: 1 hour

## LLM Options

### Potential LLM Uses
1. **Pattern Recognition**: Analyzing price patterns from historical data
2. **Sentiment Analysis**: Processing social media and news
3. **Code Generation**: Creating and updating trading strategies
4. **Risk Assessment**: Evaluating trade setups
5. **Market Regime Detection**: Identifying market conditions
6. **Anomaly Detection**: Finding unusual patterns or opportunities

### Available LLMs
- GPT-4/Claude: ~$10-30 per million tokens
- GPT-3.5: ~$0.50-2 per million tokens
- Open source (Llama, Mistral): Free if self-hosted
- Groq: Free tier available (limited)
- Anthropic Claude: API pricing varies

## Constraints of Free APIs

### Rate Limiting Impact
- Cannot do high-frequency trading
- Must batch and cache requests
- Need fallback APIs for redundancy
- Must optimize request efficiency

### Data Quality Issues
- Delayed data (1-5 minutes typical)
- Missing granular data (no tick data)
- Limited historical data depth
- No order book depth beyond top levels

### Reliability Concerns
- Free endpoints have 70-90% uptime
- No SLA guarantees
- Can be discontinued without notice
- Shared infrastructure (slow during peak times)

## Architectural Patterns for Free API Bots

### Pattern 1: Aggregator Arbitrage
- Aggregate prices from multiple free sources
- Find discrepancies between exchanges
- Execute when spread > fees + buffer

### Pattern 2: Social Sentiment Trader
- Monitor Twitter/Reddit for sentiment shifts
- Correlate with price movements
- Trade on sentiment divergence from price

### Pattern 3: New Pair Sniper
- Monitor DexScreener for new pairs
- Filter by liquidity and volume
- Quick entry on promising launches

### Pattern 4: Mean Reversion on Majors
- Track top 10 tokens on free APIs
- Identify statistical deviations
- Trade reversions to mean

### Pattern 5: LLM-Guided Portfolio
- LLM analyzes all available free data
- Generates daily/weekly allocations
- Executes rebalancing trades

### Pattern 6: Copy Trading Leaders
- Track successful wallets on-chain
- Copy their trades with delay
- Filter for consistent performers

## Elegance Criteria

### What Makes a Bot Architecture Elegant?
1. **Simplicity**: Fewer moving parts, clear logic flow
2. **Robustness**: Handles API failures gracefully
3. **Efficiency**: Maximizes value from limited API calls
4. **Adaptability**: Easy to modify and extend
5. **Clarity**: Code and logic are self-documenting

### Anti-Patterns (Inelegant)
1. Complex dependency chains
2. Over-engineering for edge cases
3. Tight coupling to specific APIs
4. Excessive parameter optimization
5. Black box ML models without explainability

## Historical Performance of Simple Bots

### Successful Simple Strategies
1. **3Commas Grid Bot**: 15-30% monthly using basic grid trading
2. **Shrimpy Rebalancer**: 20-40% annual through simple rebalancing
3. **Cryptohopper Templates**: 10-50% monthly with basic TA
4. **PineScript Alerts**: 30-100% annual with simple indicators

### Failed Complex Strategies
1. ML models that overfit to historical data
2. Multi-factor models with 50+ parameters
3. High-frequency strategies on slow APIs
4. Sentiment models without price confirmation

## Questions to Resolve

1. Can simple strategies outperform complex ones with free API constraints?
2. Does LLM integration provide alpha or just complexity?
3. What is the optimal trade frequency given rate limits?
4. Which free APIs provide the best signal-to-noise ratio?
5. How to handle API failures and inconsistencies elegantly?
6. What is minimum viable complexity for profitability?
7. Can a bot be both simple and adaptive?