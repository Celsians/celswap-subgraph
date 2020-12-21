# Celswap Protocol Analytics Subgraph

Gain insights in the Celswap ecosystem.

This subgraph displays analytics for Celswap, including trading pairs, liquidity, tokens, transactions, and more. If you are new to Celswap, you might want to check our FAQ first.

We are always looking for more like-minded developers to give back to the community. Join us and help give back at weare@celswap.org

Documentation: https://github.com/Celsians/celswap-core

Github repo: https://github.com/Celsians

## Running Locally

Make sure to update package.json settings to point to your own graph account.

## Queries

Below are a few ways to show how to query the uniswap-subgraph for data. The queries show most of the information that is queryable, but there are many other filtering options that can be used, just check out the [querying api](https://thegraph.com/docs/graphql-api). These queries can be used locally or in The Graph Explorer playground.

## Key Entity Overviews

#### UniswapFactory

Contains data across all of Celswap. This entity tracks important things like total liquidity (in ETH and USD, see below), all time volume, transaction count, number of pairs and more.

#### Token

Contains data on a specific token. This token specific data is aggregated across all pairs, and is updated whenever there is a transaction involving that token.

#### Pair

Contains data on a specific pair.

#### Transaction

Every transaction on Uniswap is stored. Each transaction contains an array of mints, burns, and swaps that occured within it.

#### Mint, Burn, Swap

These contain specifc information about a transaction. Things like which pair triggered the transaction, amounts, sender, recipient, and more. Each is linked to a parent Transaction entity.

## Example Queries

### Querying Aggregated Uniswap Data

This query fetches aggredated data from all uniswap pairs and tokens, to give a view into how much activity is happening within the whole protocol.

```graphql
{
  uniswapFactories(first: 1) {
    pairCount
    totalVolumeUSD
    totalLiquidityUSD
  }
}
```
