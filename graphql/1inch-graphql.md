# 1inch GraphQL (The Graph Subgraphs)

## Description

1inch exposes on-chain DeFi data through multiple subgraphs deployed on The Graph protocol. These GraphQL APIs index Ethereum mainnet events from 1inch's Mooniswap AMM, Limit Order Protocol, and Candles (OHLCV) contracts, providing queryable historical swap, liquidity, order, and price data without requiring direct RPC calls.

## Subgraphs

### Mooniswap Subgraph

Indexes the Mooniswap AMM (1inch's native AMM, deployed at `0x71CD6666064C3A1354a3B4dca5fA1E2D3ee7D303` on Ethereum mainnet). Tracks pairs, swaps, liquidity positions, and aggregated volume/liquidity stats.

- **Repository:** https://github.com/1inch/mooniswap-subgraph
- **Network:** Ethereum Mainnet
- **Factory Address:** `0x71CD6666064C3A1354a3B4dca5fA1E2D3ee7D303`
- **Hosted Service Endpoint:** `https://api.thegraph.com/subgraphs/name/1inch/mooniswap`

### Limit Order Protocol Subgraph

Indexes the 1inch Limit Order Protocol contract (`0x45F05B5BA0cbC05801426EA0366D987C35033768` on Ethereum mainnet). Tracks limit order creation, updates, and fills.

- **Repository:** https://github.com/1inch/LimitSwapSubgraph
- **Network:** Ethereum Mainnet
- **Contract Address:** `0x45F05B5BA0cbC05801426EA0366D987C35033768`
- **Hosted Service Endpoint:** `https://api.thegraph.com/subgraphs/name/1inch/limit-orders`

### Candles (OHLCV) Subgraph

Indexes Uniswap V2/V3 swap events to derive OHLCV candlestick data for token pairs at configurable time durations. Used to power the 1inch Charts API.

- **Repository:** https://github.com/1inch/candles-subgraph
- **Network:** Ethereum Mainnet
- **Hosted Service Endpoint:** `https://api.thegraph.com/subgraphs/name/1inch/candles`

## Authentication

The Graph's hosted service endpoints are publicly accessible without authentication for read queries. Decentralized network deployments via The Graph Gateway require a billing API key.

## Documentation

- **The Graph Docs:** https://thegraph.com/docs/
- **1inch GitHub (subgraph repos):** https://github.com/1inch
- **1inch Developer Portal:** https://business.1inch.com/portal/documentation
- **Mooniswap Subgraph Source:** https://github.com/1inch/mooniswap-subgraph
- **Limit Order Subgraph Source:** https://github.com/1inch/LimitSwapSubgraph
- **Candles Subgraph Source:** https://github.com/1inch/candles-subgraph

## Example Query

```graphql
# Get recent swaps from Mooniswap
{
  swaps(first: 10, orderBy: timestamp, orderDirection: desc) {
    id
    timestamp
    pair {
      token0 { symbol }
      token1 { symbol }
    }
    srcAmount
    destAmount
    amountUSD
    sender
  }
}
```
