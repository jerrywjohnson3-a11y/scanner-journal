# Scanner Journal

Automated trade journal for the Crypto Intel Breakout Scanner.

Every **STRONG BUY** alert (score ≥ 70) is logged here with full signal data for backtesting.

## Schema

| Column | Description |
|--------|-------------|
| `timestamp` | ISO 8601 UTC timestamp of the alert |
| `symbol` | Token symbol (e.g. BTC, ETH, STX) |
| `pair` | Coinbase trading pair (e.g. STX-USD) |
| `entry_price` | Price at time of alert |
| `breakout_score` | Composite score 0-100 |
| `signal` | Signal type (strong_buy, buy) |
| `rsi14` | RSI-14 value |
| `macd_signal` | MACD direction (bullish, bearish, etc.) |
| `macd_histogram` | MACD histogram value |
| `volume_24h` | 24h USD volume |
| `volume_spike` | Volume vs 20-period average (multiplier) |
| `change_1h` | 1-hour price change % |
| `change_24h` | 24-hour price change % |
| `momentum` | 10-period momentum |
| `tags` | Descriptive signal tags |

## Usage

```python
import pandas as pd
df = pd.read_csv('alerts/strong_buys.csv')
```

## Scanner Details

- **Source:** Coinbase Advanced (top 80 USD pairs by volume)
- **Frequency:** Every 15 minutes
- **Scoring:** RSI (25%), MACD (25%), Volume (25%), Momentum+Catalyst (25%)
- **Alert threshold:** Score ≥ 70
